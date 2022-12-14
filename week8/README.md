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

# Context useReducer

- Sama seperti Redux, react memiliki state management context useReducer
- Penggunaan useReducer juga hampir sama seperti Redux
- Untuk membuat reducer kita memerlukan initialstate dan juga function reducer

  ```js
  // TodoProvider.jsx
  import React, { createContext, useReducer } from "react";
  export const TodoContext = createContext();
  const initialState = {
    todos: ["belajar react", "belajar redux", "belajar context"],
  };

  function reducer(state, action) {
    switch (action.type) {
      default:
        return state;
    }
  }
  ```

- Untuk menggunakan useReducer kita menggunakan
  `const [state, dispatch] = useReducer(reducer, initialState);`
  Sehingga code keseluruhan menjadi

  ```js
  import React, { createContext, useReducer } from "react";

  export const TodoContext = createContext();

  const initialState = {
    todos: ["belajar react", "belajar redux", "belajar context"],
  };

  function reducer(state, action) {
    switch (action.type) {
      default:
        return state;
    }
  }
  function TodoProvider({ children }) {
    const [state, dispatch] = useReducer(reducer, initialState);

    return <TodoContext.Provider value={{ state, deleteTodo }}>{children}</TodoContext.Provider>;
  }

  export default TodoProvider;
  ```

- Untuk memanggil state pada reducer tersebut kita cukup menggunakan useContext pada komponen yang memerlukan data dari reducer

  ```js
  import React, { useContext } from "react";
  import { TodoContext } from "../TodoProvider";

  function TodoList() {
    const { state, deleteTodo } = useContext(TodoContext);
    return (
      <div>
        <h1>Todo</h1>
        <form action="">
          <input type="text" name="" id="" />
          <button>add</button>
        </form>
        <ul>
          {state.todos.map((item, index) => {
            return (
              <li key={index}>
                <span>{item}</span>
              </li>
            );
          })}
        </ul>
      </div>
    );
  }

  export default TodoList;
  ```

# React Testing

- Testing adalah memeriksa atau menguji suatu code apakah berjalan sesuai dengan expect result atau hasil yang diharapkan.
- Terdapat 3 automation testing

  - Unit testing
  - Integration testing
  - End to End Testing

- Unit Test melakukan pengujian pada bagian yang paling kecil, sebagai contoh adalah function
- Untuk menginstal jest dapat menggunakann perintah `npm install -D jest`
- Untuk melakukan testing menggunakan jest

  ```js
  // Soal | buat fungsi penju
  function sum(x, y) {
    return x + y;
  }
  module.exports = sum;
  ```

  ```js
  const sum = require("./ app");

  test("menjumlahkan angka pada sum()", () => {
    expect(sum(0, 0)).toBe(0);
    expect(sum(0, 1)).toBe(1);
    expect(sum(1, 1)).toBe(2);
    expect(sum(2, 2)).toBe(4);
  });
  ```

- React memiliki fitur untuk melakukan testing bernama RTL (React Testing Library)
- Untuk melakukan testing menggunakan RTL

  ```js
  import { render, screen } from "@testing-library/react";
  import App from "./App";

  test("renders learn react link", () => {
    render(<App />);
    const linkElement = screen.getByText(/learn react/i);
    expect(linkElement).toBeInTheDocument();
  });
  ```

- Untuk menjalankan perintah testing dapat menggunakan `npm run test`
