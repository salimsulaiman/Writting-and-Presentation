# Day 1 | Array

## **Pengertian**

Array adalah tipe data list order yang dapat menyimpen berbagai jenis tipe data di dalamnya seperti String, Number, Boolean, dan lainnya.

## **Contoh Array**

```js
let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];
console.log(arrBuah);
```

```js
let arr = ["hello", 1, true];

console.log(arr);
```

## **Mengakses element array**

Array pada javascript dihitung dari index data ke-0, jadi data pertama adalah index ke-0

```js
let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];
console.log(arrBuah[1]); // output : semangka
```

## **Update Array**

Seperti tipe data lainnya, kita juga dapat mengupdate data pada array

```js
let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];
console.log(arrBuah[1]); // output : semangka

arrBuah[1] = "jambu";
console.log(arrBuah[1]); // output : jambu
```

## **Mengetahui Panjang Array**

Untuk mengetahui jumlah panjang data suatu array kita dapat menggunakan property length

```js
let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];
console.log(arrBuah.length); // output : 4
```

## **Menambahkan data array paling belakang**

Kita dapat menambahkan data array dengan menggunakan built-in method .push().  
push() digunakan untuk menambahkan data array di posisi paling belakang.

```js
let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];

arrBuah.push("duku");
console.log(arrBuah);
```

## **Menambahkan data array paling depan**

Kita dapat menambahkan data array di posisi paling depan dengan menggunakan unshift().

```js
let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];

arrBuah.unshift("anggur");
console.log(arrBuah);
```

## **Menghapus data array paling belakang**

Untuk menghapus data array di posisi paling belakang kita dapat menggunakan method pop()

```js
let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];

arrBuah.pop();
console.log(arrBuah);
```

## **Menghapus data array paling depan**

Untuk menghapus data array di posisi paling depan kita dapat menggunakan method shift()

```js
let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];

arrBuah.shift();
console.log(arrBuah);
```

## **Menghapus, Mengubah, dan Menambahkan data dari tengah**

Dengan menggunakan method splice() kita dapat menghapus, mengubah, maupun menambahkan data dari manapun, terutama pada data yang memiliki posisi di tengah

- Menghapus data array

  ```js
  let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];

  arrBuah.splice(2, 1); // splice(startIndex, deleteCount)
  console.log(arrBuah);
  ```

  - Mengubah data array

  ```js
  let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];

  arrBuah.splice(3, 1, "dukuh"); // splice(startIndex, deleteCount, item)
  // mengubah 1 element pada index 3 menjadi "dukuh"
  console.log(arrBuah);
  ```

  - Menambah data array

  ```js
  let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];

  arrBuah.splice(3, 0, "dukuh", "durian"); // splice(startIndex, deleteCount, item1, item2)
  // menambahkan 2 data yang dimulai dari index ke 3
  console.log(arrBuah);
  ```

## **Mengambil dengan cara mengcopy datanya**

Untuk mengambil dengan cara mengcopy data array dapat menggunakan method slice()

```js
let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];
console.log(arrBuah.slice(1, 4)); // value kedua merupakan batas datanya
```

## **Looping**

Terdapat berbagai cara untuk melakukan looping pada array.

- for

  ```js
  let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];

  for (let i = 0; i < arrBuah.length; i++) {
    console.log(arrBuah[i]);
  }
  ```

- for of

  ```js
  let arrBuah = ["jeruk", "semangka", "pepaya", "rambutan"];
  for (let buah of arrBuah) {
    console.log(buah);
  }
  ```

- forEach
  ```js
  arrBuah.forEach((item, index) => {
    //menampilkan data denga index ganjil
    if (index % 2 == 1) {
      console.log(index, item);
    }
  });
  ```
- map
  ```js
  arrBuah.forEach((item, index) => {
    //menampilkan data denga index ganjil
    if (index % 2 == 1) {
      console.log(index, item);
    }
  });
  ```

## **Array Multidimension**

Multidimensional Array dapat diartikan sebagai array of array, atau ada array di dalam array

```js
let shop = [
  ["kaos", 20],
  ["jaket", 12],
  ["topi", 35],
  ["celana", 10],
];

console.log(shop);
```

## **Mengakses index Array Multidimension**

```js
let shop = [
  ["kaos", 20],
  ["jaket", 12],
  ["topi", 35],
  ["celana", 10],
];

console.log(shop[2][0]); // output : topi
```

# Day 2 | Object

## **Pengertian Object**

**Object** merupakan sebuah tipe data pada variabel yang menyimpan properti dan fungsi.  
**Property** adalah data lengkap dari sebuah object.  
**Method** adalah action dari sebuah object

## **Membuat object**

Object memiliki sebuah key dan juga value.

```js
let namaObject = {
  key: value,
};
```

contoh untuk membuat object person

```js
let person = {
  nama: "Salim Sulaiman",
  umur: 20,
  gender: "Laki-laki",
};

console.log(person);
```

## **Mengakses Object**

Untuk mmengakses object kita bisa menggunakan 2 cara

**1. Dot Notation**

```js
let person = {
  nama: "Salim Sulaiman",
  umur: 20,
  gender: "Laki-laki",
};

console.log(person.nama); // output : Salim Sulaiman
```

**2. Bracket**

```js
let person = {
  nama: "Salim Sulaiman",
  umur: 20,
  gender: "Laki-laki",
};

console.log(person[umur]); // output : 20
```

## **Update data pada Object**

Kita dapat melakukan update pada variabel dengan tipe data object.  
Object dapat mengupdate value key yang sudah tersedia serta object dapat menambahkan key dan value baru

```js
let person = {
  nama: "Salim Sulaiman",
  umur: 20,
  gender: "Laki-laki",
};

// mengupdate value dari key yang sudah tersedia
person.umur = 21;

// menambah key dan value baru
person.address = "Tegal, Jawa Tengah";

console.log(person);
```

## **Menghapus Property Object**

Kita dapat menghapus property dari object menggunakna delete operator

```js
let person = {
  nama: "Salim Sulaiman",
  umur: 20,
  gender: "Laki-laki",
};

delete person.gender;

console.log(person);
```

## **Method pada Object**

Jika value yang kita masukan pada property berupa function, maka hal itu disebut method.

```js
const greeting = {
  welcome: function () {
    return "Halo selamat datang";
  },
  afterPay: function () {
    return "Terimakasih sudah membeli produk kami";
  },
};

console.log(greeting.afterPay()); // output : Terimakasih sudah membeli produk kami
```

## **Nested Object**

```js
let buku = {
  judul: "tips jago javascript",
  tahun: 2022,
  penulis: {
    penulis1: {
      nama: "Reyhan",
      umur: 28,
      kota: "Jakarta",
    },
    penulis2: {
      nama: "Aby",
      umur: 25,
      kota: "Bandung",
    },
  },
};

console.log(buku);
console.log(buku.penulis.penulis1.nama); // output Reyhan
```

## **Looping Object**

```js
// for in
let siswa = {
  nama: "Salim Sulaiman",
  umur: 20,
  asal: "Tegal",
};

console.log(siswa);

for (let key in siswa) {
  console.log(siswa[key]);
}
```

Output  
 ![forin!](for-in.png)

## **Array of Object**

Kita dapat menggunakan array of object untuk data yang lebih dari satu.

```js
let users = [
  {
    nama: "Reyhan",
    umur: 17,
    alamat: "Tegal",
  },
  {
    nama: "Wahyu",
    umur: 20,
    alamat: "Tegal",
  },
  {
    nama: "Aby",
    umur: 21,
    alamat: "Tegal",
  },
];

// menampilkan seluruh user
console.log(users);

// mengambil data dengan index 1
console.log(users[1]);

// melakukan looping
// parameter el dalam map berfungsi menggantikan nama dari object
let data = users.map((el) => {
  //   console.log(el.nama);
  // menambahkan property status disetiap object
  el.status = "aktif";
  return el;
});

console.log(data);
```

# Day 3 | Module & Recursive

## **Module**

### **Pengertian**

Modules adalah reusable code yang dapat di export dari suatu file javascript dan di import ke file javascript yang lain.  
Reusable code disini merupakan data yang dapat digunakan berkali kali

### **Alasan membuat program menjadi module**

Alasan membuat program menjadi module adalah sebagai berikut :

- Mudah untuk menemukan dan mengatasi debug pada sebuah program.
- Code lebih mudah dibaca dan mudah dimengerti karena program diubah menjadi componet-component yang kecil.
- Reusable code, cukup membuat logic method pada suatu file lalu dapat digunakan pada pada file lainnya.

### **Membuat Module**

- Pada file index.html kita harus menambahkan script attribute type untuk modules.

  ```html
  <script src="indonesia.js" type="module"></script>
  ```

  File indonesia.js merupakan file javascript utama/main yang dipanggil pada file html.

- Kemudian buatlah file javascript dengan nama jepang.js. Di dalamnya berisi array berisi data motor yang nantinya akan dipanggil pada file Indonesia.js

  ```js
  let motor = ["Suzuki", "Yamaha", "Honda", "Kawasaki"];

  export { motor };
  ```

  Seperti yang dilihat pada kode diatas, setelah membuat array motor, selanjutnya kita melakukan export array motor tersebut.

- Kemudian pada file indonesia.js kita akan mengimport file javascript.js agar datanya dapat kita gunakan pada file main/utama (indonesia.js)
  ```js
  import { motor } from "./jepang.js";
  console.log(motor);
  console.log(motor[2]);
  ```
  Pada code diatas kita melakukan import file jepang.js, kemudian kita mengambil variabel motor yang ada pada file jepang.js tersebut.  
  ![module!](module.png).

Jadi untuk segala variabel, function, dll kita letakan pada file jepang.js, sedangkan pada file indonesia.js kita hanya tinggal memanggil saja data-data yang ada pada jepang.js. Dengan begini code akan lebih tertata, mudah dibaca, dan juga mudah dimengerti.

## **Recursive**

### **Pengertian**

Recursive merupakan function yang memanggil dirinya sendiri sampai kondisi tertentu. Recursive merupakan salah satu paradigma pemrograman.
Recursive kebanyakan digunakan untuk case matematika, fisika, kimia, dan yang berhubungan dengan calculation.

```js
function recursive() {
  if (condition) {
    // stop calling itself
    // ...
  } else {
    recursive();
  }
}
```

### **Ciri-ciri Rekursif**

- Fungsi rekursif selalu memiliki kondisi yang menyatakan kapan fungsi tersebut berhenti.
- Fungsi rekursif selalu memanggil dirinya sendiri sambil mengurangi atau memecahkan data masukan setiap panggilannya.

### **Contoh sederhana kasus rekursif**

Contoh sederhananya saat kita ingin membuat sebuah deret angka

```js
function deretAngka(n) {
  if (n == 1) {
    console.log(n);
  } else {
    deretAngka(n - 1);
    console.log(n);
  }
}

deretAngka(3); // output 1 2 3
```

- Function diatas memiliki sebuah parameter (n)
- Program akan melakukan perkondisian, jika n == 1 maka tampilkan n.
- Jika else maka akan memanggil kembali function deretAngka dengan parameter (n-1), kemudian tampilkan.
- Dari program diatas, function deretAngka akan terpanggil terus menerus hingga memenuhi kondisi, yaitu ketika n==1

# Day 4 | Asynchronus & Promise

## **Asynchronus**

Asyncronus Programming merupakan teknik yang memungkinkan program untuk memulai task yang berjalan lama agar dapat disela oleh task yang membutuhkan waktu sebentar, setelah task selesai, maka akan melanjutkan task yang sebelumnya masih berjalan.

Asynchronus dibutuhkan ketika ada suatu proses yang membutuhkan waktu lama, jadi daripada menunggu proses itu selesai dikerjakan kita dapat mengerjakan task yang lainnya.

## **Proses Asynchronus**

Sebagai contoh :

```js
console.log("A");

console.log("B");

console.log("C");
```

Ketika program diatas dijalankan maka akan menghasilkan output  
![asyncronus!](<asyncronus(1).png>).

Namun apa yang terjadi jika kita menambahkan setTimeout pada salah satu proses.

```js
console.log("A");

setTimeout(() => {
  console.log("B");
}, 1000);

console.log("C");
``;
```

maka yang terjadi adalah "C" akan lebih dahulu diproses sebelum "B".  
![asyncronus!](<asyncronus(2).png>).

## **Callback Function**

Callback merupakan function yang dijadikan sebagai argumen

```js
setTimeout(() => {
  console.log("Contoh Callback");
}, 2000);
```

## **Promise**

Promise merepresentasikan dari suatu kejadian, apakah kejadian itu berhasil atau gagal dari proses asynchronus.

Promise memiliki 2 parameter callback, yaitu resolve dan juga reject.

Resolve ketika sebuah promise terpenuhi, sedangkan Reject ketika sebuah promise gagal terpenuhi

```js
let nonton = (kondisi) => {
  return new Promise((resolve, reject) => {
    if (kondisi == "jalan") {
      resolve("Nonton Terpenuhi");
    } else {
      reject("Batal nonton");
    }
  });
};

nonton("jalan")
  .then((result) => {
    console.log(result);
  })
  .catch((err) => {
    console.log(err);
  });
```

# Day 5 | Web Storage

## **Pengertian**

Web Storage merupakan sebuah penyimpanan atau ruang yang digunakan untuk menyimpan suatu data pada browser

## **Contoh Data Yang disimpan**

- Preferensi User
- Setting
- Score pada Game
- Darkmode / Lightmode
- Dll

## **Jenis Penyimpanan**

Web Storage menyediakan dua object untuk menyimpan sebuah data.

- localStorage = Menyimpan data tanpa expiration date.
- sessionStorage = Menyimpan data untuk one session (data akan hilang ketika browser ditutup)

## **Menyimpan data dengan Local Storage**

Untuk menyimpan sebuah data kita dapat menggunakan setItem("key", "value")

```js
let theme = "darkMode";
localStorage.setItem("theme", theme);
```

## **Mengambil data dari Local Storage**

Untuk mengambil sebuah data kita dapat menggunakan getItem("key")

```js
console.log(localStorage.getItem("theme"));
```

## **Menghapus data dari Local Storage**

Untuk menghapus sebuah data pada local storage kita dapat menggunakan fungsi removeItem("key")

```js
localStorage.removeItem("theme");
```
