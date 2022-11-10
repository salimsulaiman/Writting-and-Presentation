# React Context

- Context merupakan sebuah library yang dimiliki react untuk pass data melalui component tanpa harus pass props setiap saat
- Context dirancang untuk berbagi data yang dapat dianggap global untuk komponen
- Data yang dapat dioper berupa theme, bahasa, dan yang lainnya.
- Untuk membuat context kita dapat menggunakan `createContext()`

  ```js
  // file UserProvide.jsx
  import React, { createContext } from "react";
  import { useState } from "react";

  export const UserContext = createContext();

  function UserProvider({ children }) {
    const [user, setUser] = useState({
      name: "Salim",
      email: "salimsulaiman@gmail.com",
    });
    return <UserContext.Provider value={{ user, setUser }}>{children}</UserContext.Provider>;
  }

  export default UserProvider;
  ```

  Pada code diatas kita akan mengoper variabel user dan juga setUser

- Sebelum mengambil variabel global tersebut kita harus membungkus komponen root dengan komponen Provider tersebut

  ```js
  // main.jsx
  import React from "react";
  import ReactDOM from "react-dom/client";
  import App from "./App";
  import "./index.css";
  import KeranjangCountProvider from "./KeranjangCountProvider";
  import UserProvider from "./UserProvider";

  ReactDOM.createRoot(document.getElementById("root")).render(
    <UserProvider>
      <KeranjangCountProvider>
        <App />
      </KeranjangCountProvider>
    </UserProvider>
  );
  ```

- Untuk mengambil variabel global dari context kita cukup menggunakan `useContext()`

  ```js
  // App.jsx
  import { useContext, useState } from "react";
  import "./App.css";
  import Keranjang from "./components/Keranjang";
  import ListProduk from "./components/ListProduk";
  import SummaryPembelian from "./components/SummaryPembelian";
  import { UserContext } from "./UserProvider";

  function App() {
    const { user } = useContext(UserContext);

    return (
      <div className="App">
        <h2>{user.name}</h2>
        <h4>{user.email}</h4>
        <Keranjang />
        <ListProduk />
        <SummaryPembelian />
      </div>
    );
  }

  export default App;
  ```
