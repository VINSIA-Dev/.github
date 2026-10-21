# VINSIA Developer Ecosystem Guidelines

Dokumentasi standar arsitektur, konvensi API, pedoman antarmuka (Anti-AI Design), dan protokol keamanan untuk seluruh repositori di organisasi **VINSIA-Dev**.

---

## 1. Arsitektur Terpusat & SSO (VINSIA ID)

Seluruh platform di ekosistem VINSIA (`vinsia-store`, `vinsia-ai`, `vinsia-cloud`, dll.) terintegrasi secara terpusat melalui **VINSIA ID** (`auth.vinsia.web.id`).

### A. Protokol Autentikasi
* Menggunakan standar **OAuth 2.0 Authorization Code Grant (RFC 6749)**.
* **Master Session (Auth Server)**:
  * Masa aktif: **7 s/d 30 hari** melalui cookie HTTP-only secure (`vinsia_auth_session`).
  * Menyimpan status identitas terpusat di browser pengguna.
* **Local Session (Platform Klien)**:
  * Masa aktif: **2 s/d 5 jam idle** untuk membatasi risiko keamanan pada transaksi sensitif (e-commerce/billing).
  * Pengguna yang sesi lokalnya habis cukup mengklik *"Masuk dengan Akun VINSIA"* untuk masuk kembali tanpa perlu mengetik ulang password (One-Click Identity Chooser).
* **OAuth Token Lifecycle**:
  * Authorization Code: **5 menit** (sekali pakai).
  * Access Token: **30 hari**.
  * Refresh Token: **60 hari**.
* **Perilaku Logout**:
  * *Logout Lokal*: Hanya menghapus sesi di platform lokal (pengguna tetap login di VINSIA ID).
  * *Logout Global*: Menghapus sesi di `auth.vinsia.web.id` sehingga seluruh platform meminta autentikasi ulang.

### B. App-Owned Granular Permissions (RBAC)
* Hak akses fitur dikelola secara **independen** oleh masing-masing platform klien, bukan terpusat kaku di Auth Server.
* **Super Admin / Owner**: Memiliki izin wildcard `*` (akses penuh ke seluruh fitur platform).
* **Admin Staf & Role Lain**: Hak akses dibatasi oleh JSON permissions di tabel `roles` database lokal masing-masing platform. Role `admin` biasa **dilarang** membypass izin menu tanpa pengecekan permission granular.

### C. Sinkronisasi Realtime Profil & Password (Webhooks)
* Setiap perubahan profil (`name`, `phone`, `avatar`) atau `password` di Auth Server wajib langsung dibroadcast ke seluruh platform klien terdaftar via Webhook.
* Header keamanan: `X-Vinsia-Signature` berisi signature **HMAC SHA-256** menggunakan `client_secret`.
* Event `user.updated`: Platform klien langsung memperbarui kolom data pengguna di database lokal.
* Event `user.password_changed`: Platform klien langsung memutus token sesi lama (`remember_token = null`) demi keamanan akun.

---

## 2. Standar Format & Penamaan API

Seluruh endpoint API yang dibangun di lingkungan VINSIA wajib mematuhi konvensi berikut:

### A. Struktur URI (Kebab-Case & RESTful)
1. **Resource Plural (Kata Benda Jamak)**:
   * `GET    /api/v1/products`
   * `GET    /api/v1/products/{id}`
   * `POST   /api/v1/categories`
   * `DELETE /api/v1/categories/{slug}`
2. **Kebab-Case untuk segmen URL**:
   * Gunakan tanda minus (`-`), bukan garis bawah (`_`):
     * Benar: `/admin/api/product-secrets`, `/auth/vinsia/webhook`
     * Salah: `/admin/api/product_secrets`, `/auth/vinsia/web_hook`
3. **Explicit Sub-Actions (Kata Kerja)** untuk aksi non-CRUD murni:
   * `POST /checkout/process`
   * `POST /voucher/validate`
   * `POST /qris/create`
   * `POST /orders/{id}/cancel`
4. **Standar OAuth 2.0**:
   * `/oauth/authorize`
   * `/oauth/token`
   * `/oauth/userinfo`

### B. Format Payload JSON (`snake_case`)
* Seluruh key atribut dalam JSON request dan response wajib berformat **`snake_case`**.
* Contoh:
  ```json
  {
    "vinsia_uid": "usr_9a8b7c6d",
    "email_verified_at": "2026-10-21T10:00:00Z",
    "client_id": "vinsia_store",
    "is_active": true
  }
  ```

### C. Struktur Response JSON Standar
* **Sukses**:
  ```json
  {
    "status": "success",
    "message": "Data berhasil diperbarui.",
    "data": { ... }
  }
  ```
* **Error / Validasi Gagal**:
  ```json
  {
    "status": "error",
    "message": "Validasi formulir gagal.",
    "errors": {
      "email": ["Format email tidak valid."]
    }
  }
  ```

---

## 3. Prinsip Desain UI: Anti-AI Design System

Setiap antarmuka web dan aplikasi di VINSIA wajib mengikuti pedoman visual profesional:

1. **Palet Warna**:
   * Background Neutral Gelap: Matte dalam `#07080A`, `#0B0E14`, `#0F1218`.
   * Border: 1px hairline presisi `#1A2230` atau `#1E2638`.
   * Single Brand Accent: Oranye VINSIA `#E28D38` (Hover: `#F39A45`).
   * Kontras tinggi (WCAG AAA compliant), baik dalam dark mode maupun light mode.
2. **Larangan Keras "AI Slop"**:
   * ❌ DILARANG memakai gradien mesh ungu/cyan/neon yang tidak relevan.
   * ❌ DILARANG memakai floating pill badge warna-warni tanpa arti struktural.
   * ❌ DILARANG memakai glassmorphism buram berlebihan (*heavy frosted blur*) yang menurunkan keterbacaan teks.
   * ❌ DILARANG memakai copywriting klise khas AI (contoh: *"Empowering your digital future"*). Gunakan bahasa lugas, profesional, dan to-the-point.
3. **Tipografi**:
   * Font Monospace strictly hanya untuk machine tokens, ID, hash, kode, atau status log.
   * Font Geometric Sans-serif bersih untuk seluruh teks judul, deskripsi, dan antarmuka umum.

---

## 4. Standar Rekayasa & Deployment

1. **Branching & Deployment**:
   * Branch `main`: Khusus lingkungan **Production**.
   * Branch `staging`: Khusus lingkungan **Staging** (`staging.vinsia.web.id`).
2. **Minimal & Surgical Diffs**:
   * Selidiki akar masalah (*root cause*) sebelum menulis kode.
   * Buat perubahan minimal dan terarah; hindari perombakan file yang tidak berhubungan dengan isu.
   * Jaga *backward compatibility*; jangan sampai memicu *breaking changes*.
3. **Keamanan & Secrets**:
   * Cegah SQL Injection dengan parameter binding Eloquent/PDO.
   * Selalu lakukan validasi dan sanitasi input form / API.
   * DILARANG meng-hardcode secret, API key, atau password ke dalam repositori. Seluruh kredensial wajib disimpan di `.env`.
   * Port esensial server (888, 20128, 8030, 9030, 22, 3306) dilarang dimatikan, dan server dilarang di-reboot tanpa instruksi eksplisit.
