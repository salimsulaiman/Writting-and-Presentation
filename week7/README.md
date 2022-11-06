# Day 1 | Proptypes

- Proptypes merupakan sebuah library yang dapat membantu kita dalam memeriksa data props yang kita kirim agar sesuai ekspetasi
- Untuk menginstal PropTypes kita dapat menggunakan perintah `npm install prop-types`
- Sebelum menggunakan lib PropTypes kita harus mengimport
  ```js
  import PropTypes from `prop-types`
  ```
- Penggunaan PropTypes

  ```js
  import PropTypes, { string } from "prop-types";

  function StudentInfo({ name, age }) {
    return (
      <>
        <h1>PropTypes</h1>
        <h2>{name}</h2>
        <h2>{age + 5}</h2>
      </>
    );
  }

  StudentInfo.propTypes = {
    // type data string
    name: PropTypes.string,

    // type data number
    age: PropTypes.number,

    // type data bebas
    name: PropTypes.any.isRequired, // is required, data harus ada

    // memberikan opsi untuk type data
    age: PropTypes.oneOfType([PropTypes.string, PropTypes.number]),

    // type data array
    data: PropTypes.array,

    // Mengecek value dari array
    data: PropTypes.arrayOf(PropTypes.number),

    // array dengan berbagai type data
    data: PropTypes.arrayOf(PropTypes.oneOfType([PropTypes.string, PropTypes.number])),

    // type data object
    info: PropTypes.object,

    // mengecek nilai dari object
    info: PropTypes.shape({
      hoby: PropTypes.string,
      class: PropTypes.number,
    }),

    // mengecek nilai dan key dari object
    info: PropTypes.exact({
      hoby: PropTypes.string,
      class: PropTypes.number,
      address: PropTypes.string,
    }).isRequired,
  };
  export default StudentInfo;
  ```

# Day 2 | React Router

- React Router merupakan library dengan fitur client lengkap untuk React.
- Pada intinya React Router dapat diartikan sebagai jalur halaman yang dituju ketika sebuah element di click sesuai dengan URL yang diterapkan
- React Router digunakank pada aplikasi single page yaitu React JS.
- untuk menginstal library React Router kita dapat menggunakan perintah `npm install react-router-dom`
- untuk membungkus root dari component pada React kita dapat menggunakan component `<BrowserRouter>`

  ```js
  import React from "react";
  import ReactDOM from "react-dom/client";
  import App from "./App";
  import "bootstrap/dist/css/bootstrap.min.css";
  import { BrowserRouter } from "react-router-dom";

  ReactDOM.createRoot(document.getElementById("root")).render(
    <React.StrictMode>
      <BrowserRouter>
        <App />
      </BrowserRouter>
    </React.StrictMode>
  );
  ```

- Setiap list Route yang ingin kita dartarkan atau gunakan harus dibungkus dengan sebuah component `<Routes>`

  ```js
  import "./App.css";
  import { Routes, Route, Link } from "react-router-dom";
  import HomePage from "./pages/HomePage";
  import AboutPage from "./pages/AboutPage";
  import Page404 from "./pages/Page404";
  import DetailPage from "./pages/DetailPage";
  import AboutStudent from "./pages/AboutStudent";
  import AboutTeacher from "./pages/AboutTeacher";
  import AboutSchool from "./pages/AboutSchool";
  function App() {
    return (
      <>
        <div className="App">
          <Link to={"/"}>Home | </Link>
          <Link to={"about"}>About </Link>
          <Routes>
            <Route path="/" element={<HomePage />} />
            <Route path="/detail/:id" element={<DetailPage />} />
            <Route path="/about" element={<AboutPage />} />
            <Route path="/about" element={<AboutPage />}>
              <Route path="student" element={<AboutStudent />} />
              <Route path="teacher" element={<AboutTeacher />} />
              <Route index element={<AboutSchool />} />
            </Route>
            <Route path="*" element={<Page404 />} />
          </Routes>
        </div>
      </>
    );
  }

  export default App;
  ```

- Untuk mengatur Route dari halaman web kita dapat menggunakan sebuah component `<Route>` yang telah dibungkus pada component `<Routes>`. path pada `<Route>` digunakan sebagai jalur halaman yang dituju ketika url yang dituju sesuai dengan path yang didaftarkan, element pada `<Route>` merupakan component yang akan ditampilkan ketika sebuah path tertuju
- Untuk berpindah halaman kita dapat menggunakan component `<Link>` sebagai pengganti tag `<a>`

  ```js
  import { Outlet, Link } from "react-router-dom";

  function AboutPage() {
    return (
      <>
        <h1>About</h1>
        <Link to={"student"}>About Student | </Link>
        <Link to={"teacher"}>About Teacher</Link>
        <Outlet />
      </>
    );
  }

  export default AboutPage;
  ```

# Day 3 | Redux

- Redux merupakan sebuah library react untuk mengelola state management
- Pada redux, state akan disimpan pada tempat tertentu sehingga akan lebih mudah dalam memanagenya.
- Terdapat 3 component utama dalam Redux
  - Store : Berfungsi untuk menampung sebuah state yang nantinya akan digunakan.
  - Reducer : Berfungsi untuk mengelola sebuah state yang ada pada store.
  - Action : Berisi function yang mereturn sebuah object yang nantinya dapat dipanggill.
- Untuk menginstal Redux kita dapat menggunakan perintah `npm install redux react-redux`
- Melakukan setup redux

  - Membuat store

    ```js
    import { createStore } from "redux";
    import keranjangReducer from "../reducer/keranjangReducer";

    const store = createStore(keranjangReducer);

    export default store;
    ```

  - Setup store pada main.jsx

    ```js
    import React from "react";
    import ReactDOM from "react-dom/client";
    import App from "./App";
    import "./index.css";
    import { Provider } from "react-redux";
    import store from "./redux/store";

    ReactDOM.createRoot(document.getElementById("root")).render(
      <Provider store={store}>
        <App />
      </Provider>
    );
    ```

  - Membuat Reducer

    ```js
    import { INCREMENT_KERANJANG, DECREMENT_KERANJANG } from "../action/keranjangAction";

    const initialState = {
      totalKeranjang: 0,
    };

    function keranjangReducer(state = initialState, action) {
      switch (action.type) {
        case INCREMENT_KERANJANG:
          return {
            totalKeranjang: state.totalKeranjang + 1,
          };
        case DECREMENT_KERANJANG:
          return {
            totalKeranjang: state.totalKeranjang - 1,
          };
        default:
          return state;
          break;
      }
    }

    export default keranjangReducer;
    ```

  - Membuat action

    ```js
    export const INCREMENT_KERANJANG = "INCREMENT_KERANJANG";
    export const DECREMENT_KERANJANG = "DECREMENTa_KERANJANG";

    export function incrementKeranjang() {
      return {
        type: INCREMENT_KERANJANG,
      };
    }
    export function decrementKeranjang() {
      return {
        type: DECREMENT_KERANJANG,
      };
    }
    ```
