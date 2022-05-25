1. Membuat package json di /backend
    npm init -y
2. Install package
    npm install express mysql2 sequalize cors
3. Install nodemon
    npm install --save-dev nodemon
4. Menambahkan module di package.json
    "name": "backend",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "type": "module",
5. Membuat index.js
6. Menjalankan index.js di terminal
    nodemon index.js
7. Membuat database : mern_db, table : products
    CREATE TABLE products(
    id INT(11) PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(200),
    price DOUBLE,
    createdAt DATE,
    updatedAt DATE
    )ENGINE=INNODB;
8. Memindahkan route dari backend/index.js ke routes/index.js
9. Import product route to backend/index.js import productRoutes from "./routes/index.js"
10. Membuat controller di backend/controller/Products.js
    Untuk mendapatkan All Products
    export const getAllProducts = (req, res) => {
    res.send('welcome this is awes react');
    }
11. Membuat Product Model di backend/models/productModel.js
    import { Sequelize } from "sequelize";
    import db from "../config/database.js";

    const { DataType } = Sequelize;

    const Product = db.define('products', {
        title:{
            type: DataType.STRING
        },
        price:{
            type: DataType.DOUBLE
        }
    }, {
        freezeTableName: true
    });

    export default Product;
12. Membuat controller get all product
    export const getAllProducts = async (req, res) => {
    try {
        const products = await Product.findAll();
        res.json(products);    
    } catch (error) {
        res.json({ message: error.message })
    }
    
    }
13. Membuat controller create product di backend/controller/Products.js
    export di route backend/routes/index.js 
    kemudian test di api POST backend/request.rest
14. Membuat controller get product by id di backend/controller/Products.js
    export di route backend/routes/index.js 
    kemudian test di api GET backend/request.rest
15. Membuat controller update product di backend/controller/Products.js
    export di route backend/routes/index.js 
    kemudian test di api PATCH backend/request.rest
16. Membuat controller delete product di backend/controller/Products.js
    export di route backend/routes/index.js 
    kemudian test di api DELETE backend/request.rest
17. Import cors agar data api terkoneksi dengan front end di backend/index.js
    import cors from "cors";
    app.use(cors());

(Backend telah selesai dibuat)

