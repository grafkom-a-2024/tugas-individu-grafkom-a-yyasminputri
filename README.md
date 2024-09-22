# Tugas Individu Grafkom A
### Nama : Yasmin Putri <br> NRP : 5025221273

## Tugas 1 - Program Sederhana (2D)
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

## Tugas 2 - Rotating, Translation, Scaling,
 Implementasi 2D Rotating, Translation, Scaling Matrix dalam WebGL, saya berhasil mengimplemntasikan dengan letter 'L', dimana bentuk tersebut berwarna pink. 
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
Dalam pembuatan kode ini, saya memerlukan 3 file, yaitu css, js dan html
- css : Kode CSS ini mendefinisikan gaya untuk elemen HTML dalam aplikasi WebGL, dengan fokus pada tampilan dan interaksi antarmuka pengguna. Ia mengatur tata letak responsif untuk berbagai ukuran layar dan mendukung mode gelap, meningkatkan keterbacaan dan aksesibilitas. Selain itu, pengaturan khusus untuk elemen canvas memastikan tampilan yang konsisten dan menarik, baik dalam tampilan biasa maupun dalam iframe.
- js : Kode ini menginisialisasi aplikasi WebGL untuk menggambar bentuk huruf "L" yang dapat diputar, diubah bentuk dan dipindahkan di canvas. Shader vertex dan fragment diproses dan dihubungkan ke program GLSL, sementara antarmuka pengguna memungkinkan pengguna untuk mengubah posisi rotasi melalui slider. Fungsi drawScene bertanggung jawab untuk memperbarui dan menggambar ulang objek di canvas setiap kali ada perubahan input.
    ```
    var rotationLocation = gl.getUniformLocation(program, "u_rotation");
    var translationLocation = gl.getUniformLocation(program, "u_translation");
    var scaleLocation = gl.getUniformLocation(program, "u_scale");

    ...

    var translation = [100, 0];
    var rotation = [0, 1];
    var scale = [1, 1];

    ...
    
    webglLessonsUI.setupSlider("#x", {value: rotation[0], slide: updatePosition(0), max: gl.canvas.width });
    webglLessonsUI.setupSlider("#y", {value: rotation[1], slide: updatePosition(1), max: gl.canvas.height});
    webglLessonsUI.setupSlider("#angle", {slide: updateAngle, max: 360});
    
    webglLessonsUI.setupSlider("#scaleX", {value: scale[0], slide: updateScale(0), min: 0, max: 10, step: 0.01, precision: 2});
    webglLessonsUI.setupSlider("#scaleY", {value: scale[1], slide: updateScale(1), min: 0, max: 10, step: 0.01, precision: 2});

    webglLessonsUI.setupSlider("#x", {value: translation[0], slide: updatePosition(0), max: gl.canvas.width });
    webglLessonsUI.setupSlider("#y", {value: translation[1], slide: updatePosition(1), max: gl.canvas.height});
    ```
- html : Kode ini mengatur elemen canvas dan antarmuka pengguna untuk aplikasi WebGL yang menampilkan objek yang dapat diputar, diubah, dan dipindahkan. Shader vertex mengelola rotasi, skala, dan translasi posisi titik sebelum menggambar, sementara shader fragment menetapkan warna objek. Dengan menggunakan dua skrip eksternal, webgl-lessons-ui.js dan rotating.js, aplikasi ini berinteraksi dengan antarmuka pengguna untuk mengubah parameter rotasi secara dinamis.

- Output Result Rotating
  <img width="1440" alt="Screenshot 2024-09-22 at 11 54 24" src="https://github.com/user-attachments/assets/17ad3a36-3ca6-49b8-94ff-1eee1761affc">
- Output Result Translating
  <img width="1440" alt="Screenshot 2024-09-22 at 11 54 41" src="https://github.com/user-attachments/assets/cba5a5bf-709d-4215-9dee-6223267fb078">
- Output Result Scaling
<img width="1440" alt="Screenshot 2024-09-22 at 11 54 33" src="https://github.com/user-attachments/assets/00dac464-a999-4f96-8f22-6dc22769eae4">

## Tugas 3
### 1. 3D Animation
Saya membuat animasi 3d dengan bentuk cube, bola, cone, dan ring. Pembuatan ini hanya memerlukan 1 file yang bernama html. 
- Cube : Kode HTML ini membuat aplikasi WebGL yang menggambar kubus 3D dengan enam wajah berwarna pastel yang berbeda. Kubus dirender menggunakan buffer untuk menyimpan vertex dan warna, serta shader untuk mengatur tampilan objek. Animasi rotasi diterapkan untuk memberikan efek dinamis saat kubus ditampilkan.
```
// Define vertices for a cube
var vertices = [
    -0.5, -0.5, -0.5,   0.5, -0.5, -0.5,   0.5, 0.5, -0.5,   -0.5, 0.5, -0.5,  // Front face
    -0.5, -0.5, 0.5,    0.5, -0.5, 0.5,    0.5, 0.5, 0.5,    -0.5, 0.5, 0.5,   // Back face
    -0.5, 0.5, -0.5,    -0.5, 0.5, 0.5,    -0.5, -0.5, 0.5,   -0.5, -0.5, -0.5, // Left face
    0.5, 0.5, -0.5,     0.5, 0.5, 0.5,     0.5, -0.5, 0.5,    0.5, -0.5, -0.5,  // Right face
    -0.5, -0.5, 0.5,    0.5, -0.5, 0.5,    0.5, -0.5, -0.5,   -0.5, -0.5, -0.5, // Bottom face
    -0.5, 0.5, 0.5,     0.5, 0.5, 0.5,     0.5, 0.5, -0.5,    -0.5, 0.5, -0.5   // Top face
];

// Define colors for each face
var colors = [
    // Front face: Baby Pink
    1.0, 0.75, 0.8,  1.0, 0.75, 0.8,  1.0, 0.75, 0.8,  1.0, 0.75, 0.8,
    // Back face: Soft Pink
    0.8, 0.6, 0.9,  0.8, 0.6, 0.9,  0.8, 0.6, 0.9,  0.8, 0.6, 0.9,
    // Left face: Pastel Blue
    0.6, 0.8, 1.0,  0.6, 0.8, 1.0,  0.6, 0.8, 1.0,  0.6, 0.8, 1.0,
    // Right face: Pastel Yellow
    1.0, 1.0, 0.6,  1.0, 1.0, 0.6,  1.0, 1.0, 0.6,  1.0, 1.0, 0.6,
    // Bottom face: Baby Pink
    1.0, 0.75, 0.8,  1.0, 0.75, 0.8,  1.0, 0.75, 0.8,  1.0, 0.75, 0.8,
    // Top face: Soft Pink
    1.0, 0.5, 0.7,  1.0, 0.5, 0.7,  1.0, 0.5, 0.7,  1.0, 0.5, 0.7
];

// Define indices for the cube's faces
var indices = [
    0, 1, 2, 0, 2, 3,  // Front face
    4, 5, 6, 4, 6, 7,  // Back face
    8, 9, 10, 8, 10, 11,// Left face
    12, 13, 14, 12, 14, 15, // Right face
    16, 17, 18, 16, 18, 19, // Bottom face
    20, 21, 22, 20, 22, 23  // Top face
];
```
<br>
Output Result Cube
<img width="1440" alt="Screenshot 2024-09-22 at 12 03 31" src="https://github.com/user-attachments/assets/8440e533-937c-4572-8253-7bc4daf701b5"> <br>
- Ball : Kode HTML ini membuat aplikasi WebGL yang menggambar bola 3D dengan efek warna gradasi, menggunakan vertex dan fragment shaders untuk mengatur tampilan objek. Selain itu, kode ini menerapkan transformasi matriks dan animasi rotasi untuk memberikan efek dinamis pada bola saat ditampilkan. Dengan menggunakan buffer untuk menyimpan vertex, warna, dan indeks, objek 3D dapat dirender secara efisien.

```
var radius = 1.0;
var latBands = 25;
var longBands = 25;
var vertices = [];
var colors = [];
var indices = [];

for (var latNumber = 0; latNumber <= latBands; latNumber++) {
    var theta = latNumber * Math.PI / latBands;
    var sinTheta = Math.sin(theta);
    var cosTheta = Math.cos(theta);

    ...

        vertices.push(radius * x, radius * y, radius * z);
        
        // Warna gradasi
        var gradientRatio = latNumber / latBands;
        var color;

...
```
<br> 
Output Result Ball
<img width="1440" alt="Screenshot 2024-09-22 at 12 03 15" src="https://github.com/user-attachments/assets/a7708c8b-133e-470b-b6ca-66cd80c498cc"> <br>

- Cone : Kode ini untuk membuat tampilan 3D sebuah kerucut/cone menggunakan WebGL. Kerucut ini memiliki warna gradasi yang berbeda di bagian alas dan ujungnya, serta dapat berputar secara dinamis. Kode ini mencakup pembuatan buffer untuk geometri, warna, dan pengaturan shader untuk merender kerucut/cone.
```
// Vertices 
var vertices = [
    // Titik pusat dan titik-titik di tepi lingkaran
    0, 0, -1, // Pusat alas
    1, 0, -1,
    0.707, 0.707, -1,
    0, 1, -1,
    -0.707, 0.707, -1,
    -1, 0, -1,
    -0.707, -0.707, -1,
    0, -1, -1,
    0.707, -0.707, -1,
    // Titik puncak kerucut 
    0, 0, 1  // Titik puncak
];

// Indices untuk menggambar kerucut
var indices = [
    // Segitiga alas
    0, 1, 2,
    0, 2, 3,
    0, 3, 4,
    0, 4, 5,
    0, 5, 6,
    0, 6, 7,
    0, 7, 8,
    0, 8, 1,
    // Segitiga sisi
    9, 1, 2,
    9, 2, 3,
    9, 3, 4,
    9, 4, 5,
    9, 5, 6,
    9, 6, 7,
    9, 7, 8,
    9, 8, 1
];
```
<br> 
Output Result Cone 
<img width="1440" alt="Screenshot 2024-09-22 at 12 03 01" src="https://github.com/user-attachments/assets/b2ed6b90-71a7-40c7-8214-2f06f9d944a5"> <br>

- Ring : Kode HTML ini menghasilkan bentuk ring 3D menggunakan WebGL. Dengan menggunakan dua jari-jari (inner dan outer), program ini membangun geometri ring dan memberikan warna yang bervariasi untuk setiap vertex. Efek rotasi ditambahkan untuk membuat tampilan lebih dinamis.
```
// Vertices for the cone
        var vertices = [];
        var colors = [];
        var indices = [];
        var radius = 1;
        var height = 2;
        var radialSegments = 30;

        // Base circle vertices
        vertices.push(0, 0, 0); // Center of base
        colors.push(1, 0, 0); // Red for center

...

// Tip of the cone
        vertices.push(0, 0, height);
        colors.push(0, 0, 1); // Blue for tip

        // Side triangles
        for (var i = 1; i < radialSegments; i++) {
            indices.push(i, i + 1, radialSegments + 1);
        }
```
Output Result Ring
<img width="1312" alt="Screenshot 2024-09-22 at 12 02 49" src="https://github.com/user-attachments/assets/2a0a994b-4b24-4db9-801c-ca2673df03d8"> <br>

### 2. Animation
Dalam mengaplikasikan animation (Rotating, Scaling dan Translating) hanya memerlukan 3 file, yaitu js, css, dan html. 
Pembuatan Cubenya sebagai bentuk utama 
```
function setGeometry(gl) {
    gl.bufferData(
        gl.ARRAY_BUFFER,
        new Float32Array([
            // Front face
            -1, -1,  1,
             1, -1,  1,
             1,  1,  1,
            -1, -1,  1,
             1,  1,  1,
            -1,  1,  1,
            // Back face
            -1, -1, -1,
             1, -1, -1,
             1,  1, -1,
            -1, -1, -1,
             1,  1, -1,
            -1,  1, -1,
            // ... (other faces)
        ]),
        gl.STATIC_DRAW
    );
}
```
- js : Kode ini menginisialisasi konteks WebGL, membuat program shader, dan mengatur data geometri serta warna untuk menggambar kubus berwarna-warni. Fungsi drawScene digunakan untuk menggambar kubus dengan transformasi translasi, rotasi, dan skala yang dapat disesuaikan menggunakan slider. Shader vertex dan fragment ditentukan dalam elemen <script> di HTML untuk mengontrol tampilan kubus di kanvas.
  - Langkah : Buat elemen <canvas> di HTML dan ambil konteks WebGL menggunakan getContext("webgl"). Menulis shader vertex dan fragment untuk mendefinisikan geometri dan warna, lalu siapkan buffer untuk posisi dan warna kubus. Implementasikan fungsi drawScene untuk menggambar kubus dengan transformasi yang diatur oleh kontrol UI, dan panggil fungsi ini saat halaman dimuat.
- css : CSS ini mengatur tampilan aplikasi WebGL dengan latar belakang pink muda dan memastikan kanvas mengisi seluruh layar. UI slider ditempatkan di sudut kanan atas dan disusun secara vertikal untuk kemudahan penggunaan. Font yang digunakan memberikan sentuhan klasik pada antarmuka.
    - Langkah : Siapkan elemen HTML yang mencakup kanvas dan kontainer UI untuk slider. Lalu, membuat file CSS untuk mengatur gaya tampilan, termasuk latar belakang, ukuran kanvas, dan penataan slider. Serta, Implementasikan JavaScript untuk menghubungkan slider dengan rotasi, skala, dan translasi objek 3D.
- html : Dokumen HTML ini membuat halaman dengan judul "Rainbow Cube" dan menampilkan kanvas WebGL berukuran 400x400 piksel. Terdapat juga elemen untuk mengontrol rotasi kubus dalam tiga sumbu. Vertex dan fragment shader ditulis dalam elemen <script> terpisah, dan skrip tambahan dimuat dari sumber eksternal untuk mendukung fungsi WebGL.
  - Langkah : Dokumen HTML dimulai dengan deklarasi tipe dan struktur dasar, termasuk elemen <head> untuk metadata dan judul, serta elemen <body> yang memuat kanvas WebGL. Di dalam <body>, terdapat elemen kanvas untuk menggambar kubus, dan skrip shader ditulis dalam elemen <script> terpisah. Skrip JavaScript eksternal diimpor untuk mendukung fungsi WebGL dan logika aplikasi.

- Rotating
```
var rotation = [degToRad(40), degToRad(25), degToRad(325)];
function updateRotation(index) {
    return function(event, ui) {
        var angleInDegrees = ui.value;
        var angleInRadians = angleInDegrees * Math.PI / 180;
        rotation[index] = angleInRadians;
        drawScene();
    };
}

// Dalam fungsi drawScene
matrix = m4.xRotate(matrix, rotation[0]);
matrix = m4.yRotate(matrix, rotation[1]);
matrix = m4.zRotate(matrix, rotation[2]);
```
Output Result Rotating
<img width="1440" alt="Screenshot 2024-09-22 at 12 21 43" src="https://github.com/user-attachments/assets/82018324-dd39-4652-a7ab-54ee9bb942a7">

- Scaling
```
var scale = [100, 100, 100];

function updateScale(index) {
    return function(event, ui) {
        scale[index] = ui.value;
        drawScene();
    };
}

// Dalam fungsi drawScene
matrix = m4.scale(matrix, scale[0], scale[1], scale[2]);
```
Output Result Scaling
<img width="1440" alt="Screenshot 2024-09-22 at 12 21 58" src="https://github.com/user-attachments/assets/f86e8a13-2544-4625-a18a-845c085e80cd">

- Translating
```
var translation = [300, 300, 100];

function updatePosition(index) {
    return function(event, ui) {
        translation[index] = ui.value;

        drawScene();
    };
}

// Dalam fungsi drawScene
matrix = m4.translate(matrix, translation[0], translation[1], translation[2]);
```
Output Result Translating
<img width="1440" alt="Screenshot 2024-09-22 at 12 21 21" src="https://github.com/user-attachments/assets/ad1daf0e-937e-4593-9f8e-cb22a1170251">
