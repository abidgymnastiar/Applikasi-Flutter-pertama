# Cara Menggunakan

1. Langkah 1: Pastikan Git Sudah Terpasang
   ![tuto1](laporan/tuto/peng_1.png)

2. Langkah 2: Dapatkan URL Repository GitHub
   ![tuto2](laporan/tuto/peng_2.png)

3. Langkah 3: Clone Repository Menggunakan Git
   ![tuto3](laporan/tuto/peng_3.png)

4. Langkah 4: Masuk ke Direktori Repository

Note : Sekarang, kamu bisa melihat, mengedit, atau menjalankan kode dari repository yang telah di-clone.

# Info Sekilas Sintax

1.  Membuat project

    - Membuat proyek Flutter pertama Anda
      ![tugas1](laporan/tugas/tug_1.png)

    - pubspec.yaml
      File pubspec.yaml menentukan informasi dasar tentang aplikasi Anda, seperti versi aplikasi saat ini, dependensi aplikasi, dan aset yang digunakan oleh aplikasi untuk pengiriman.
      ![tugas2](laporan/tugas/tug_2.png)

    - analysis_options.yaml
      File ini menentukan seberapa ketat Flutter saat menganalisis kode Anda. Karena percobaan ini adalah percobaan pertama Anda menggunakan Flutter, Anda memberi tahu penganalisis agar tidak terlalu ketat. Anda dapat mengatur ini kapan saja. Bahkan, seiring mendekati pemublikasian aplikasi produksi sebenarnya, Anda kemungkinan besar akan ingin membuat penganalisis lebih ketat dari ini. <br>
      ![tugas2](laporan/tugas/tug_3.png)

    - lib/main.dart
      50 baris kode ini adalah keseluruhan aplikasi sejauh ini. <br
      ![tugas2](laporan/tugas/tug_4.png)>

    <b>Catatan : </b> Codelab ini dipercepat hingga di titik Anda dapat mulai mengubah aplikasi secara interaktif—karena itu cara terbaik mempelajari Flutter. Jika Anda melewatkan penjelasan dari kode di atas, harap bersabar: penjelasannya akan diberikan.

2.  Menambahkan tombol

    - Meluncurkan aplikasi

      Pertama, buka lib/main.dart dan pastikan Anda memilih perangkat target. Di bagian pojok kanan bawah VS Code, Anda akan menemukan tombol yang menampilkan perangkat target saat ini. Klik tombol untuk mengubahnya. <br>
      ![tugas2](laporan/tugas/tug_5.png)>

      Selagi lib/main.dart terbuka, temukan tombol "play" b0a5d0200af5985d.png di pojok kanan atas jendela VS Code lalu klik tombol tersebut. <br
      ![tugas2](laporan/tugas/tug_6.png)>>

      Setelah beberapa saat, aplikasi Anda diluncurkan dalam mode debug. Tampilannya masih terlihat biasa saja:
      ![tugas2](laporan/tugas/tug_7.png)>

    - Hot Reload Pertama

      lib/main.dart
      ![tugas2](laporan/tugas/tug_8.png)

      Perhatikan bagaimana aplikasi segera berubah tetapi kata yang acak tetap sama. Situasi ini menunjukkan fitur stateful Hot Reload Flutter terkenal yang sedang bekerja. Hot reload dipicu saat Anda menyimpan perubahan untuk file sumber.
      ![tugas2](laporan/tugas/tug_9.png)

    - Menambahkan tombol
      Berikutnya, tambahkan tombol di bagian bawah Column, tepat di bawah instance Text kedua.

      lib/main.dart
      ![tugas2](laporan/tugas/tug_10.png)

      Saat Anda menyimpan perubahan, aplikasi diperbarui kembali: Sebuah tombol muncul dan, saat Anda mengklik tombol tersebut, Konsol Debug di VS Code menampilkan pesan button pressed!.
      ![tugas2](laporan/tugas/tug_11.png)

    - Kursus singkat Flutter 5 menit
      Meskipun menyenangkan melihat Konsol Debug, Anda ingin tombol tersebut melakukan sesuatu yang lebih berguna. Namun, sebelum mencapai ke sana, perhatikan kode pada lib/main.dart lebih dekat, untuk memahami cara kerjanya.

      - lib/main.dart
        ![tugas2](laporan/tugas/tug_12.png)

        Di bagian paling atas file tersebut, Anda akan menemukan fungsi main(). Dalam wujudnya saat ini, fungsi ini hanya memberi tahu Flutter untuk menjalankan aplikasi yang ditentukan pada MyApp.

      - lib/main.dart
        ![tugas2](laporan/tugas/tug_13.png)

        Class MyApp memperluas StatelessWidget. Widget adalah elemen tempat Anda membangun setiap aplikasi Flutter. Seperti yang dapat Anda lihat, bahkan aplikasi itu sendiri adalah widget.

        <b>Catatan: </b> Kita akan mencapai penjelasan StatelessWidget (dibandingkan StatefulWidget) kemudian.

        Kode pada MyApp menyusun keseluruhan aplikasi. Kode ini membuat status seluruh aplikasi (Anda akan mempelajari hal ini lebih lanjut nanti), memberi nama aplikasi, menentukan tema visual, dan mengatur widget "home"—titik awal aplikasi Anda.

      - lib/main.dart
        ![tugas2](laporan/tugas/tug_14.png)

        Berikutnya, class MyAppState menentukan...yah...status aplikasi. Percobaan ini adalah percobaan pertama Anda menggunakan Flutter, jadi codelab ini akan menjaga status aplikasi tetap sederhana dan terpusat. Ada banyak cara ampuh untuk mengelola status aplikasi di Flutter. Salah satu yang paling mudah untuk dijelaskan adalah ChangeNotifier, pendekatan yang diambil oleh aplikasi ini.

              - MyAppState menjelaskan data yang diperlukan oleh aplikasi ini agar berjalan dengan baik. Saat ini, kode ini hanya berisi variabel tunggal dengan pasangan kata acak saat ini. Anda akan menambahkannya nanti.
              - Class status memperluas ChangeNotifier, yang artinya kode ini dapat memberi tahu kode lain tentang perubahannya sendiri. Misalnya, jika pasangan kata saat ini berubah, beberapa widget dalam aplikasi perlu mengetahuinya.
              - Status dibuat dan disediakan untuk seluruh aplikasi menggunakan ChangeNotifierProvider (lihat kode di atas pada MyApp). Hal ini memungkinkan widget mana pun pada aplikasi untuk mendapatkan status.

        ![tugas2](laporan/tugas/tug_15.png)

      - lib/main.dart
        ![tugas2](laporan/tugas/tug_16.png)

        Terakhir, ada MyHomePage, widget yang telah Anda modifikasi. Setiap baris bernomor di bawah memetakan ke komentar nomor baris pada kode di atas:

              - Setiap widget menentukan metode build() yang dipanggil secara otomatis setiap kali kondisi widget berubah agar widget selalu dalam kondisi terbaru.
              - MyHomePage melacak perubahan terhadap status aplikasi saat ini menggunakan metode watch.
              - Setiap metode build harus menampilkan widget atau (yang lebih umum) pohon widget bertingkat. Dalam hal ini, widget tingkat tertinggi adalah Scaffold. Anda tidak akan bekerja dengan Scaffold dalam codelab ini, tetapi ini adalah widget yang berguna dan dapat ditemukan di sebagian besar aplikasi Flutter di dunia nyata.
              - Column adalah salah satu widget tata letak paling dasar pada Flutter. Widget tata letak ini mengambil sejumlah turunan dan menempatkannya pada kolom dari atas ke bawah. Secara default, kolom menempatkan turunan-turunannya secara visual di bagian atas. Anda akan segera mengubah ini agar kolom terpusat di tengah.
              - Anda mengubah widget Text ini pada langkah pertama.
              - Widget Text kedua ini mengambil appState, dan mengakses satu-satunya anggota dari class tersebut, current (yang merupakan WordPair). WordPair menyediakan beberapa pengambil yang berguna, seperti asPascalCase atau asSnakeCase. Di sini, kita menggunakan asLowerCase, tetapi Anda dapat mengubah ini sekarang jika Anda lebih menyukai salah satu alternatif yang ada.
              -vPerhatikan bagaimana kode Flutter banyak menggunakan koma di akhir. Koma ini tidak harus ada, karena children adalah anggota terakhir (dan juga satu-satunya) dari daftar parameter Column ini. Namun, menggunakan koma di akhir umumnya adalah ide yang bagus: koma di akhir membuat penambahan anggota menjadi mudah, dan koma di akhir juga berfungsi sebagai petunjuk bagi pemformat otomatis Dart untuk meletakkan baris baru. Untuk informasi lebih lanjut, lihat panduan Pemformatan kode.

    - Perilaku pertama Anda
      Scroll ke MyAppState lalu tambahkan metode getNext.

      - lib/main.dart
        ![tugas2](laporan/tugas/tug_17.png)

        Metode getNext() baru menetapkan ulang current dengan WordPair acak baru. Metode ini juga memanggil notifyListeners()(metode ChangeNotifier) yang memastikan bahwa semua orang yang melihat MyAppState diberi tahu.

        Tindakan terakhir adalah memanggil metode getNext dari callback tombol tersebut.

      - lib/main.dart
        ![tugas2](laporan/tugas/tug_18.png)

        Simpan dan uji coba aplikasi sekarang. Aplikasi akan menghasilkan pasangan kata acak baru setiap kali Anda menekan tombol Next.

        Pada bagian berikutnya, Anda akan memperindah tampilan antarmuka pengguna.
