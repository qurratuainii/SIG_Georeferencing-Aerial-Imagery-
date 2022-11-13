# SIG_Georeferencing-Aerial-Imagery-

*Tutorial Georeferencing Aerial Imagery 

1. Download file newyorkcity-washingtonsquarepark.jpg terlebih dahulu 

2. Kita akan menggunakan peta dasar dari OpenStreetMap untuk menangkap koordinat georeferensi. QGIS3 hadir dengan dukungan built-in untuk lapisan petak. Ini umumnya dikenal sebagai lapisan 'XYZ' karena dibuat menggunakan petak peta individual untuk setiap tingkat zoom (z) pada kisi x,y. Kita dapat menemukan layer OpenStreetMap di bawah XYZ Tiles di Panel Browser. Seret layer ke kanvas utama. Setelah dimuat, catat sistem referensi koordinat (CRS) untuk lapisan ini di corder kanan bawah. Ini diatur sebagai EPSG 3857 Pseudo Mercator. Ini penting karena koordinat yang kami simpulkan dari lapisan ini selama georeferensi akan berada di CRS ini (*Gambar 1*)

3. Gambar yang kita georeferensi adalah untuk Washington Square Park, New Yorl. Kita dapat memperbesar/menggeser untuk menemukan taman ini di peta. Tapi itu rumit dan tidak praktis dari QGIS versi 3.20 dan seterusnya, ada dukungan bawaan untuk Nominatim Geocoder berbasis OpenStreetMap. Klik bilah encarian di kiri bawah jendela QGIS. Untuk menggunakan ini sebagai awalan geocoder, tempat pencarian dengan >. MEncari >Washington Square Park akan memunculkan daftar alamat untuk dipilih. Klik alamat pertama (*Gambar 2*)

4. Kanvas peta akan dipusatkan ke Square Park. Sekarang mari kita mulai georeferensi. Luncurkan Georeferensi dari Layer pilih Georeferencer (*Gambar 3*)

5. Untuk melakukan georeferensi pada citra udara, kita harus memilih titik koordinat dari OpenStreetMap, jadi pertama-tama mari pasangkan alat Georeferensi ke jendela utama QGIS. Pilih Configure Georeferencer dari bilah Settings (*Gambar 4*)

6. Centang Show georeferencer window doscked dan klik OK (*Gambar 5*)

7. Pada jendela Georeferencer akan diletakkan di bagian bawah jendela utama QGIS. Mari memuat file gambar dengan mengklik ikon Open Raster di jendela Georeferencer dan menavigasi ke file JPG yang diunduh lalu klik Open (*Gambar 6*)

8. Sebelum menambahkan Titik KOntrol Tanah (GCP), kita perlu menentukan Pengaturan Transformasi. Klik ikon Transformation Settings untuk membuka dialog Transformation Settings. Pilih tipe Transformation sebagai Polynomial 2. Lihat dokumentasi QGIS untuk mempelajari berbagai tipe transformsi dan penggunaannya. Seperti disebutkan sebelumnya, peta dasar kita ada di EPSG 3857 Pseudo Mercator CRS, jadi tetapkan itu sebagai Target CRS. Kita dapat membiarkan nama output raster ke dafault dan memilih LZW sebagai Compression. Periksa gunakan 0 untuk transparansi bila diperlukan. Periksa Simpan Poin GCP untuk menyimpan poin sebagai file terpisah untuk keperluan di masa mendatang. Pastikan opsi Muat di QGIS saat selesai dicentang. Lalu klik OK (*Gambar 7*)

9. Sekarang klik tombol Add Point pada toolbar dan pilih lokasi yang mudah diidentifikasi pada gambar. Sudut, persimpangan, tiang, dll, membuat titik kontrol yang baik. Setelah kita mengklik gambar di lokasi titik kontrol, kita akan melihat pop-up yang meminta kita untuk memasukkan koordinat peta. Klik tombol dari kanvas peta (*Gambar 8*)

10. Di lapisan OpenStreetMap, klik lokasi yang tepat di lapisan referensi. Koordinat akan diisi secara otomatis dari klik kita pada kanvas peta, klik OK (*Gambar 9*)

11. Demikian pula, pilih setidaknya 6 titik pada gambar dan tambahkan koordinatnya dari lapisan referensi. Setelah kita menambahkan jumlah poin minimum yang diperlukan untuk transformasi, kita akan melihat bahwa GCP sekarang memiliki nilai kesalahan dX, dY, dan Residual bukan nol. Jika GCP tertentu memiliki nilai error yang luar biasa tinggi, hal itu biasanya berarti kesalahan manusia dalam memasukkan nilai koordinat. Jadi kita dapat menghapus GCP itu dan menangkapnya lagi (*Gambar 10*)

12. Setelah kita puas dengan GCP, klik mulai georeferensi. Ini akan memulai proses membengkokkan gambar menggunakan GCP dan membuat raster target. Setelah proses selesai, kita akan melihat layer dimuat di QGIS. Tutup jendela Georeferencer (*Gambar 11*)

13. Sekarang klik pada ikon panel Open layer styling dan beralih ke tab Transparancy. Tambahkan 255 sebagai nilai Additional no data value. Ini akan menghapus batas putih di sekitar gambar. Sekarang kita akan melihat gambar georeferensi kita terhampar dengan baik di lapisan dasar (*Gambar 12* , *Gambar 13* , *Gambar 14*)
