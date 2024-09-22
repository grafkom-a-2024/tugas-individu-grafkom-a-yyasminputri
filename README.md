## Tugas Individu
### Nama : Yasmin Putri <br> NRP : 5025221273

### Tugas 1 
Membuat Program Sederhana dengan WebGL, saya berhasil menggambar segitiga berwarna pink dengan latar belakang abu-abu `gl.clearColor(0.5, 0.5, 0.5, 1.0);`.
Membuat segitiga pink dengan 3 vertex dan 3 buah segitiga. 
```
var triangleVertices = 
    [ // X, Y,    -  R, G, B
    //untuk besar/kecil - untuk warna
        0.0, 0.3,       1.0, 0.7, 1.0, // Vertex 1 (light pink) // atas
        -0.3, -0.3,     1.0, 0.5, 0.8, // Vertex 2 (darker pink) //kiri bawah
        0.3, -0.3,      1.0, 0.8, 1.0  // Vertex 3 (light pink with different shade) // kanan bawah
    ];
```
Dalam membuat segitiga ini, hanya memerlukan 2 file, yaitu js dan html
- js : Kode JavaScript ini berhasil menginisialisasi dan menggambar segitiga menggunakan WebGL dengan memanfaatkan shader untuk mengatur warna dan posisi vertex. 
Proses ini mencakup pembuatan shader, buffer vertex, serta pengaturan atribut yang diperlukan untuk rendering. 
secara keseluruhan, kode ini memberikan dasar yang kuat untuk memahami penggunaan WebGL dalam menggambar grafik 2D dan 3D. <br>
  - Langkah :
Kode dimulai dengan mendefinisikan shader vertex dan fragment untuk menggambar segitiga, kemudian inisialisasi konteks WebGL dan membuat buffer untuk menyimpan data vertex segitiga. Lalu, Shader disusun dan dikompilasi, program kemudian dilink dan divalidasi untuk memastikan tidak ada kesalahan. Akhirnya, atribut posisi dan warna diatur, dan segitiga digambar menggunakan gl.drawArrays dalam loop render utama.
- html : Halaman HTML ini digunakan untuk menampilkan aplikasi WebGL, dengan elemen <canvas> yang berfungsi sebagai area menggambar grafik secara dinamis.
Fungsi InitDemo() dipanggil saat halaman dimuat, untuk menginisialisasi aplikasi WebGL.
File JavaScript eksternal bernama app.js diimpor untuk mengatur dan menggambar grafik, seperti segitiga sederhana, pada canvas. 
  - Langkah :
    Pertama, membuat dokumen HTML dengan judul "WebGL - Simple triangle" dan sertakan elemen <canvas> untuk menampilkan grafik WebGL. Lalu, Atur atribut onload pada elemen <body> untuk memanggil fungsi InitDemo() saat halaman dimuat dan Sertakan file JavaScript eksternal bernama app.js untuk menangani logika WebGL dan menggambar segitiga.
- Output Result
  <img width="789" alt="Screenshot 2024-09-22 at 11 33 36" src="https://github.com/user-attachments/assets/c20d05af-d2f4-43cd-a3d5-52a455f814ea">

### Tugas 2
 Implementasi 2D Rotating, Translation, Scaling, Matrices dalam WebGL, saya berhasil mengimplemntasikan dengan letter 'L', dimana bentuk tersebut berwarna pink. 
 ```
function setL(gl){
    gl.bufferData(
        gl.ARRAY_BUFFER,
        new Float32Array([
             // Left part of L
             0, 0, 
             30, 0,
             0, 120,
             0, 120,
             30, 0,
             30, 120,
 
             // Bottom part of L
             0, 120,
             80, 120,
             80, 80,
             0, 120,
             80, 80,
             0, 80,
        ]),
        gl.STATIC_DRAW
    );
}
```
- Rotating
