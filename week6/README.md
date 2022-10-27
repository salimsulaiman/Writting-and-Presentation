# Day 1 | Intro React JS

- React JS Merupakan Framework Library Javascript untuk membuat tampilan UI pada sebuah Website.
- React JS dapat membuat aplikasi Front End menjadi lebih cepat meski harus menghandle beberapa data.
- JSX merupakan ekstensi yang dikembangkan untuk React JS.
- React JS membagi 1 tampilan menjadi sebuah komponen-komponen kecil.
- Instalasi React
  - Step 1 - Install Node JS
  - Step 2 - Use Library `npx create-react-app app_name` untuk membuat project React.
- Untuk Start project React JS kita dapat menggunakan perintah `npm start`.
- Untuk membuat component kita dapat menggunakan function component pada React JS versi terbaru.
  ```js
  function Home() {
    return (
      <div>
        <h1>Home</h1>
      </div>
    );
  }
  export default Home;
  ```
- Setiap JSX hanya bisa memiliki dan dibungkus oleh 1 parent element saja
  ```js
  function Home() {
    return (
      <div class="parent">
        <h1>Home</h1>
        <h2>About</h2>
      </div>
    );
  }
  export default Home;
  ```
- React JS mempunyai fitur Virtual DOM yang merupakan duplikasi dari real DOM yang sebenarnya
- Kita bisa menggunakan syntax javascript di dalam Element HTML dengan menggunakan curly braces
  ```js
  function Home() {
    return (
      <div class="parent">
        <h1>{1 + 1}</h1>
      </div>
    );
  }
  export default Home;
  ```
