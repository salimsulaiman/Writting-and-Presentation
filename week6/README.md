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

# Day 2 | Styling React JS

- Untuk membuat sebuah component tidak akan jauh dengan namanya state dan juga props
  - State digunakan untuk menghandle sebuah data yang bersifat private
  - Props digunakan untuk mengirimkan data dari satu komponen kek komponen lain
- Pada React kita akan bertemu dengan namanya stateless dan juga statefull
  - Stateless artinya tidak memiliki state, hanya memiliki props
  - Statefull artinya memiliki state dan bisa mengirimkan state tersebut ke component
- Pengiriman data pada komponen lain

  - MemberInfo.jsx

    ```js
    const MemberInfo = ({ name, age, info, imgUrl, ageColor, infoColor }) => {
      return (
        <div className="profile-container container">
          <img src={imgUrl} alt="" className="profile-img" />
          <div className="profile-info">
            <h2>{name}</h2>
            <h3 style={{ color: ageColor }}>{age} Tahun</h3>
            <p style={{ color: infoColor }}>{info}</p>
          </div>
        </div>
      );
    };

    export default MemberInfo;
    ```

  - App.js

    ```js
    import { useState } from "react";
    import "./App.css";
    import "./components/MemberInfo";
    import MemberInfo from "./components/MemberInfo";
    import Navbar from "./components/Navbar";
    function App() {
      return (
        <>
          <MemberInfo
            name={"Salim Sulaiman"}
            age={20}
            info={"Peserta Bootcamp Skilvul 2022"}
            imgUrl={
              "https://scontent-sin6-2.xx.fbcdn.net/v/t1.6435-9/96354925_1375731682637176_509494481217650688_n.jpg?_nc_cat=102&ccb=1-7&_nc_sid=09cbfe&_nc_eui2=AeHWFNh-1Fj39Kx7444-Shkn0Uri3GKGflzRSuLcYoZ-XLeA1aTuyYfBB9kR6XVf9ebpsEezOz9e_UI50svHxF39&_nc_ohc=j2jEwoCHB5EAX-x0pqF&_nc_ht=scontent-sin6-2.xx&oh=00_AT-lU8QJQXWeiCHsXQqVEBd_rhj5JqB8yUPflZxsoy0EOQ&oe=637EC9B4"
            }
            ageColor={"#666"}
            infoColor={"#999"}
          />
        </>
      );
    }
    export default App;
    ```

- Untuk melakukan styling pada element kita dapat menggunakan `style = {{property : "value"}}`

```html
 <div className="profile-container container">
  <img src={imgUrl} alt="" className="profile-img" />
  <div className="profile-info">
    <h2>{name}</h2>
    <h3 style={{ color: "Red" }}>{age} Tahun</h3>
    <p style={{ color: "Blue" }}>{info}</p>
  </div>
</div>
```

- Untuk memberikan class pada React kita dapat menggunakan `className`
  ```html
  <div className="profile-container container">...</div>
  ```
- Untuk menggunakan CSS external kita dapat memanggilnya menggunakan perintah
  ```js
  import "./style.css";
  ```
  Perintah import tersebut diketikan pada component yang ingin kita berikan css
