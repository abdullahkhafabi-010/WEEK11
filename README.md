<style>
    body {text-align: justify}
</style>

# <b>Laporan Pertemuan 12 - Dasar State Management</b>
<b> Nama: Abdullah Khafabi

Kelas: TI 3A

NIM: 2041720050 </b>

## <b>Praktikum 1: Dasar State dengan Model-View</b>

Selesaikan langkah-langkah praktikum berikut ini menggunakan editor Visual Studio Code (VS Code) atau Android Studio atau code editor lain kesukaan Anda.

### <b>Langkah 1: Buat Project Baru</b>

Buatlah sebuah project flutter baru dengan nama master_plan di folder src week-11 repository GitHub Anda. Lalu buatlah susunan folder dalam project seperti gambar berikut ini.


### <b>Langkah 2: Membuat model task.dart</b>

Praktik terbaik untuk memulai adalah pada lapisan data (data layer). Ini akan memberi Anda gambaran yang jelas tentang aplikasi Anda, tanpa masuk ke detail antarmuka pengguna Anda. Di folder model, buat file bernama task.dart dan buat class Task. Class ini memiliki atribut description dengan tipe data String dan complete dengan tipe data Boolean, serta ada konstruktor. Kelas ini akan menyimpan data tugas untuk aplikasi kita. Tambahkan kode berikut:

![Alt text](img/1.png)

### <b>Langkah 3: Buat file plan.dart</b>

Kita juga perlu sebuah List untuk menyimpan daftar rencana dalam aplikasi to-do ini. Buat file plan.dart di dalam folder models dan isi kode seperti berikut.

![Alt text](img/2.png)

### <b>Langkah 4: Buat file data_layer.dart</b>

Kita dapat membungkus beberapa data layer ke dalam sebuah file yang nanti akan mengekspor kedua model tersebut. Dengan begitu, proses impor akan lebih ringkas seiring berkembangnya aplikasi. Buat file bernama data_layer.dart di folder models. Kodenya hanya berisi export seperti berikut.

![Alt text](img/3.png)

### <b>Langkah 5: Pindah ke file main.dart</b>

Ubah isi kode main.dart sebagai berikut.

![Alt text](img/4.png)

### <b>Langkah 6: buat plan_screen.dart</b>

Pada folder views, buatlah sebuah file plan_screen.dart dan gunakan templat StatefulWidget untuk membuat class PlanScreen. Isi kodenya adalah sebagai berikut. Gantilah teks ‘Namaku' dengan nama panggilan Anda pada title AppBar.

![Alt text](img/5.png)

### <b>Langkah 7: buat method _buildAddTaskButton()</b>

Anda akan melihat beberapa error di langkah 6, karena method yang belum dibuat. Ayo kita buat mulai dari yang paling mudah yaitu tombol Tambah Rencana. Tambah kode berikut di bawah method build di dalam class _PlanScreenState.

![Alt text](img/6.png)

### <b>Langkah 8: buat widget _buildList()</b>

Kita akan buat widget berupa List yang dapat dilakukan scroll, yaitu ListView.builder. Buat widget ListView seperti kode berikut ini.

![Alt text](img/7.png)

### <b>Langkah 9: buat widget _buildTaskTile</b>

Dari langkah 8, kita butuh ListTile untuk menampilkan setiap nilai dari plan.tasks. Kita buat dinamis untuk setiap index data, sehingga membuat view menjadi lebih mudah. Tambahkan kode berikut ini.

![Alt text](img/8.png)

Run atau tekan F5 untuk melihat hasil aplikasi yang Anda telah buat. Capture hasilnya untuk soal praktikum nomor 4.

Hasil Screenshot:
![Alt text](img/9.png)

### <b>Langkah 10: Tambah Scroll Controller</b>

Anda dapat menambah tugas sebanyak-banyaknya, menandainya jika sudah beres, dan melakukan scroll jika sudah semakin banyak isinya. Namun, ada salah satu fitur tertentu di iOS perlu kita tambahkan. Ketika keyboard tampil, Anda akan kesulitan untuk mengisi yang paling bawah. Untuk mengatasi itu, Anda dapat menggunakan ScrollController untuk menghapus focus dari semua TextField selama event scroll dilakukan. Pada file plan_screen.dart, tambahkan variabel scroll controller di class State tepat setelah variabel plan.

![Alt text](img/10.png)


### <b>Langkah 11: Tambah Scroll Listener</b>

Tambahkan method initState() setelah deklarasi variabel scrollController seperti kode berikut.

![Alt text](img/11.png)

### <b>Langkah 12: Tambah controller dan keyboard behavior</b>

Tambahkan controller dan keyboard behavior pada ListView di method _buildList seperti kode berikut ini.

![Alt text](img/12.png)

### <b>Langkah 13: Terakhir, tambah method dispose()</b>

Terakhir, tambahkan method dispose() berguna ketika widget sudah tidak digunakan lagi.

![Alt text](img/13.png)

### <b>Langkah 14: Hasil</b>

Lakukan Hot restart (bukan hot reload) pada aplikasi Flutter Anda. Anda akan melihat tampilan akhir seperti gambar berikut. Jika masih terdapat error, silakan diperbaiki hingga bisa running.

Hasil Running:

![Alt text](img/15.png)

## <b>Tugas Praktikum 1: Dasar State dengan Model-View</b>

1. Selesaikan langkah-langkah praktikum tersebut, lalu dokumentasikan berupa GIF hasil akhir praktikum beserta penjelasannya di file README.md! Jika Anda menemukan ada yang error atau tidak berjalan dengan baik, silakan diperbaiki.

2. Jelaskan maksud dari langkah 4 pada praktikum tersebut! Mengapa dilakukan demikian?

<b>Jawab:</b>

file data_layer.dart pada program tersebut digunakan untuk mempermudah proses impor sehingga lebih tertata dan ringkas dalam pengembangan program.

3. Mengapa perlu variabel plan di langkah 6 pada praktikum tersebut? Mengapa dibuat konstanta ?

<b>Jawab:</b>

variabel plan diperlukan karena beberapa widget dalam file plan_screen.dart membutuhkan data model dari objek Plan itu sendiri. Oleh karena itu, perlu dibuat variabel objek yang berasal dari kelas Plan. Penggunaan konstanta pada variabel ini adalah untuk meningkatkan kinerja aplikasi.

4. Lakukan capture hasil dari Langkah 9 berupa GIF, kemudian jelaskan apa yang telah Anda buat!

<img src="img/1.gif">

Membuat aplikasi planning

5. Apa kegunaan method pada Langkah 11 dan 13 dalam lifecyle state ?

<b>Jawab:</b>

* initState: method initState pada lifecycle state berguna untuk melakukan inisialisasi data yang dibutuhkan oleh widget. Method ini akan dipanggil ketika widget pertama kali dibuat. Pada program ini, method ini digunakan untuk menginisialisasi scrollController yang akan menghapus focus pada masing-masing text field ketika melakukan scroll.
* dispose: methode dispose pada lifecycle state berguna untuk melakukan pembersihan data yang tidak diperlukan lagi. Method ini akan dipanggil ketika widget dihapus dari tree. Pada program ini, method ini digunakan untuk membersihkan data yang tidak diperlukan lagi pada listview yang berisi plan yang telah dibuat.

6. Kumpulkan laporan praktikum Anda berupa link commit atau repository GitHub ke spreadsheet yang telah disediakan!

<b>Jawab:</b>

Baik

## <b>Praktikum 2: Mengelola Data Layer dengan InheritedWidget dan InheritedNotifier</b>

### <b>Langkah 1: Buat file plan_provider.dart</b>

Buat folder baru provider di dalam folder lib, lalu buat file baru dengan nama plan_provider.dart berisi kode seperti berikut.

![Alt text](image-15.png)

### <b>Langkah 2: Edit main.dart</b>

Gantilah pada bagian atribut home dengan PlanProvider seperti berikut. Jangan lupa sesuaikan bagian impor jika dibutuhkan.

![Alt text](image-16.png)

### <b>Langkah 3: Tambah method pada model plan.dart</b>

Tambahkan dua method di dalam model class Plan seperti kode berikut.

![Alt text](image-17.png)

### <b>Langkah 4: Pindah ke PlanScreen</b>

Edit PlanScreen agar menggunakan data dari PlanProvider. Hapus deklarasi variabel plan (ini akan membuat error). Kita akan perbaiki pada langkah 5 berikut ini.

![Alt text](image-18.png)

### <b>Langkah 5: Edit method _buildAddTaskButton</b>

Tambahkan BuildContext sebagai parameter dan gunakan PlanProvider sebagai sumber datanya. Edit bagian kode seperti berikut.

![Alt text](image-19.png)

### <b>Langkah 6: Edit method _buildTaskTile</b>

Tambahkan parameter BuildContext, gunakan PlanProvider sebagai sumber data. Ganti TextField menjadi TextFormField untuk membuat inisial data provider menjadi lebih mudah.

![Alt text](image-20.png)

### <b>Langkah 7: Edit _buildList</b>

Sesuaikan parameter pada bagian _buildTaskTile seperti kode berikut.

![Alt text](image-21.png)

### <b>Langkah 8: Tetap di class PlanScreen</b>

Edit method build sehingga bisa tampil progress pada bagian bawah (footer). Caranya, bungkus (wrap) _buildList dengan widget Expanded dan masukkan ke dalam widget Column seperti kode pada Langkah 9.

![Alt text](image-22.png)

### <b>Langkah 9: Tambah widget SafeArea</b>

Terakhir, tambahkan widget SafeArea dengan berisi completenessMessage pada akhir widget Column. Perhatikan kode berikut ini.

![Alt text](image-23.png)

Akhirnya, run atau tekan F5 jika aplikasi belum running. Tidak akan terlihat perubahan pada UI, namun dengan melakukan langkah-langkah di atas, Anda telah menerapkan cara memisahkan dengan baik antara view dan model. Ini merupakan hal terpenting dalam mengelola state di aplikasi Anda.

![Alt text](image-24.png)

## <b>Tugas Praktikum 2: InheritedWidget</b>

1. Selesaikan langkah-langkah praktikum tersebut, lalu dokumentasikan berupa GIF hasil akhir praktikum beserta penjelasannya di file README.md! Jika Anda menemukan ada yang error atau tidak berjalan dengan baik, silakan diperbaiki sesuai dengan tujuan aplikasi tersebut dibuat.

<b>Jawab:</b>

untuk jawaban soal no 1, ada pada langkah praktikum diatas

2. Jelaskan mana yang dimaksud InheritedWidget pada langkah 1 tersebut! Mengapa yang digunakan InheritedNotifier?

<b>Jawab:</b>

Pada langkah 1, "InheritedWidget" digunakan sebagai superclass dari "PlanProvider". Alasan penggunaan InheritedNotifier adalah untuk memberikan kemampuan untuk mendengarkan perubahan nilai Plan dan membangun kembali bagian dari widget tree yang terpengaruh ketika nilai tersebut berubah. Jadi, setiap kali nilai Plan diubah, widget di seluruh bagian aplikasi yang bergantung pada nilai ini akan secara otomatis diperbarui.

3. Jelaskan maksud dari method di langkah 3 pada praktikum tersebut! Mengapa dilakukan demikian?

<b>Jawab:</b>

* Metode completedCount menyediakan informasi numerik tentang sejauh mana tugas-tugas telah diselesaikan,
* Metode completenessMessage menggabungkan informasi dari completedCount dengan pesan teks yang jelas, memberikan representasi yang lebih deskriptif tentang kemajuan daftar tugas.

4. Lakukan capture hasil dari Langkah 9 berupa GIF, kemudian jelaskan apa yang telah Anda buat!

<b>Jawab:</b>

<img src="tugas2.gif">

Pada praktikum ini, menambahkan sebuah tanda pada bagian footer yang dimana jika kita menekan tanda ceklis maka akan bertambah 1 plan yang terselesaikan.

5. Kumpulkan laporan praktikum Anda berupa link commit atau repository GitHub ke spreadsheet yang telah disediakan!

<b>Jawab:</b>

baik

## <b>Praktikum 3: Membuat State di Multiple Screens</b>

### <b>Langkah 1: Edit PlanProvider</b>

Perhatikan kode berikut, edit class PlanProvider sehingga dapat menangani List Plan.

![Alt text](image-25.png)

### <b>Langkah 2: Edit main.dart</b>

Langkah sebelumnya dapat menyebabkan error pada main.dart dan plan_screen.dart. Pada method build, gantilah menjadi kode seperti ini.

![Alt text](image-26.png)

### <b>Langkah 3: Edit plan_screen.dart</b>

Tambahkan variabel plan dan atribut pada constructor-nya seperti berikut.

![Alt text](image-27.png)

### <b>Langkah 4: Error</b>

Itu akan terjadi error setiap kali memanggil PlanProvider.of(context). Itu terjadi karena screen saat ini hanya menerima tugas-tugas untuk satu kelompok Plan, tapi sekarang PlanProvider menjadi list dari objek plan tersebut.

### <b>Langkah 5: Tambah getter Plan</b>

Tambahkan getter pada _PlanScreenState seperti kode berikut.

![Alt text](image-28.png)

### <b>Langkah 6: Method initState()</b>

Pada bagian ini kode tetap seperti berikut.

![Alt text](image-29.png)

### <b>Langkah 7: Widget build</b>

Pastikan Anda telah merubah ke List dan mengubah nilai pada currentPlan seperti kode berikut ini.

![Alt text](image-30.png)

### <b>Langkah 8: Edit _buildTaskTile</b>

Pastikan ubah ke List dan variabel planNotifier seperti kode berikut ini.

![Alt text](image-31.png)

### <b>Langkah 9: Buat screen baru</b>

Pada folder view, buatlah file baru dengan nama plan_creator_screen.dart dan deklarasikan dengan StatefulWidget bernama PlanCreatorScreen. Gantilah di main.dart pada atribut home menjadi seperti berikut.

![Alt text](image-32.png)

![Alt text](image-33.png)

### <b>Langkah 10: Pindah ke class _PlanCreatorScreenState</b>

Kita perlu tambahkan variabel TextEditingController sehingga bisa membuat TextField sederhana untuk menambah Plan baru. Jangan lupa tambahkan dispose ketika widget unmounted seperti kode berikut.

![Alt text](image-34.png)

### <b>Langkah 11: Pindah ke method build</b>

Letakkan method Widget build berikut di atas void dispose. Gantilah ‘Namaku' dengan nama panggilan Anda.

![Alt text](image-35.png)

### <b>Langkah 12: Buat widget _buildListCreator</b>

Buatlah widget berikut setelah widget build.

![Alt text](image-36.png)

### <b>Langkah 13: Buat void addPlan()</b>

Tambahkan method berikut untuk menerima inputan dari user berupa text plan.

![Alt text](image-37.png)

### <b>Langkah 14: Buat widget _buildMasterPlans()</b>

Tambahkan widget seperti kode berikut.

![Alt text](image-38.png)

Terakhir, run atau tekan F5 untuk melihat hasilnya jika memang belum running. Bisa juga lakukan hot restart jika aplikasi sudah running. Maka hasilnya akan seperti gambar berikut ini.

Penambahan import pada main.dart untuk menghilangkan error

![Alt text](image-39.png)