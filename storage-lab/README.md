Eksperimen 1: Persistence Test
4. Catat:
    - Cookies: Masih ada
    - LocalStorage: masih ada
    - SessionStorage: tidak ada

    Eksperimen 2: Tab Isolation
    increment di tab baru : 0
    increment di tab lama : 5
    kesimpulan : Data di sessionStorage hanya berlaku untuk satu tab browser saja 
    - SessionStorage adalah tab-isolated 

    Eksperimen 3: Storage Size Comparison
    - Cookies: 4 KB
    - LocalStorage: 5-10 MB
    - SessionStorage:5-10  MB

    Eksperimen 4: Decision Quiz
    Sudahhhh semua

    Pertanyaan Refleksi :
    1. Mengapa session token TIDAK boleh disimpan di LocalStorage?

Karena LocalStorage bisa diakses oleh JavaScript, maka jika terjadi XSS (Cross-Site Scripting), attacker bisa mencuri session token dengan sangat mudah. Selain itu, data di LocalStorage bersifat persisten (tetap ada walau browser ditutup), sehingga risiko penyalahgunaan session jadi lebih besar. Praktik yang lebih aman adalah menyimpan session token di cookie dengan flag HttpOnly dan Secure, agar tidak bisa diakses JavaScript dan hanya dikirim lewat HTTPS.

2. Apa keuntungan SessionStorage untuk multi-step form dibanding LocalStorage?

SessionStorage terisolasi per tab dan bersifat sementara, sehingga sangat cocok untuk multi-step form (misalnya form pendaftaran atau checkout). Jika user membuka form yang sama di tab lain, data tidak saling tertimpa, dan saat tab ditutup, data otomatis hilang—ini mencegah data usang atau sensitif tersisa. LocalStorage kurang ideal karena datanya bisa bercampur antar tab dan bertahan terlalu lama.

3. Jika kamu membuat aplikasi todo list offline-first, storage mana yang akan kamu gunakan dan mengapa?

Untuk aplikasi offline-first, pilihan terbaik adalah IndexedDB. Alasannya: kapasitas besar, bisa menyimpan data terstruktur (object), mendukung query yang lebih kompleks, dan tetap tersedia saat offline. LocalStorage terlalu terbatas (sinkron, kecil, dan kurang efisien), sedangkan SessionStorage hanya bertahan selama tab aktif. IndexedDB paling cocok untuk menyimpan daftar todo, status sinkronisasi, dan cache data jangka panjang.
    

