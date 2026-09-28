## 🛒 OneCart: Full-Stack E-Commerce Platform with Admin Panel

## 📌 Overview

OneCart is a full-stack MERN e-commerce platform for fashion shopping. Customers can sign up with email or Google, browse and filter products, manage a cart with sizes, and pay by Cash on Delivery or Razorpay. A separate admin panel lets the store owner add products with four images, manage the product list, and update order status. A built-in voice assistant lets shoppers navigate the store by speaking.

## 🚀 Why It Matters

🛍️ **Complete Shopping Flow in One Project**
→ Product browsing, cart, checkout, online payments, and order tracking work together like a real online store.

🧑‍💼 **Separate Admin Panel**
→ Store owners manage products and orders from a dedicated dashboard, kept apart from the customer app.

🎙️ **Voice Navigation Improves Accessibility**
→ Shoppers can open pages, search, and go to their cart just by speaking.

## 🏗 Project Structure

```text
📂 One-cart
├── 📂 backend  (Node.js, Express & MongoDB API)
│   ├── index.js  (Express server entry point & route setup)
│   ├── package.json  (Backend dependencies)
│   ├── .gitignore
│   ├── 📂 config
│   │   ├── db.js  (MongoDB connection)
│   │   ├── cloudinary.js  (Cloudinary image upload)
│   │   ├── token.js  (JWT token generation)
│   ├── 📂 controller
│   │   ├── authController.js  (Registration, login, Google login, admin login, logout)
│   │   ├── userController.js  (Current user & admin info)
│   │   ├── productController.js  (Add, list & remove products)
│   │   ├── cartController.js  (Get, add & update cart)
│   │   ├── orderController.js  (COD, Razorpay, user orders & admin order management)
│   ├── 📂 middleware
│   │   ├── isAuth.js  (User JWT cookie authentication)
│   │   ├── adminAuth.js  (Admin JWT cookie authentication)
│   │   ├── multer.js  (Image upload handling)
│   ├── 📂 model
│   │   ├── userModel.js  (User schema: profile & cart data)
│   │   ├── productModel.js  (Product schema: images, price, sizes, category)
│   │   ├── orderModel.js  (Order schema: items, address, payment & status)
│   ├── 📂 routes
│   │   ├── authRoutes.js  (Auth endpoints)
│   │   ├── userRoutes.js  (User endpoints)
│   │   ├── productRoutes.js  (Product endpoints)
│   │   ├── cartRoutes.js  (Cart endpoints)
│   │   ├── orderRoutes.js  (Order endpoints)
│   ├── 📂 public
│   │   ├── .gitkeep  (Temporary upload folder placeholder)
│
├── 📂 frontend  (Customer app: React.js + TailwindCSS + Vite)
│   ├── index.html  (Base HTML file)
│   ├── package.json  (Frontend dependencies)
│   ├── vite.config.js  (Vite & Tailwind configuration)
│   ├── eslint.config.js  (ESLint configuration)
│   ├── README.md  (Default Vite readme)
│   ├── .gitignore
│   ├── 📂 utils
│   │   ├── Firebase.js  (Firebase Google Auth config)
│   ├── 📂 src
│   │   ├── App.jsx  (Main component & routing)
│   │   ├── main.jsx  (React entry point)
│   │   ├── App.css  (Component styling)
│   │   ├── index.css  (Global TailwindCSS styling)
│   │   ├── vcart logo.png  (Brand logo)
│   │   ├── 📂 assets  (Images, banners, payment logo & voice assistant sounds)
│   │   ├── 📂 context
│   │   │   ├── AuthContext.jsx  (Server URL provider)
│   │   │   ├── UserContext.jsx  (Logged-in user state)
│   │   │   ├── ShopContext.jsx  (Products, cart, search & delivery fee)
│   │   ├── 📂 component
│   │   │   ├── Nav.jsx  (Navigation bar & search)
│   │   │   ├── Hero.jsx  (Homepage hero slider)
│   │   │   ├── Backgound.jsx  (Hero background images)
│   │   │   ├── LatestCollection.jsx  (Latest products section)
│   │   │   ├── BestSeller.jsx  (Best selling products section)
│   │   │   ├── Card.jsx  (Product card)
│   │   │   ├── RelatedProduct.jsx  (Related products on detail page)
│   │   │   ├── CartTotal.jsx  (Cart totals & delivery fee)
│   │   │   ├── OurPolicy.jsx  (Store policies section)
│   │   │   ├── NewLetterBox.jsx  (Newsletter subscription box)
│   │   │   ├── Title.jsx  (Section title)
│   │   │   ├── Loading.jsx  (Loading spinner)
│   │   │   ├── Footer.jsx  (Footer)
│   │   │   ├── Ai.jsx  (Voice assistant using Web Speech API)
│   │   ├── 📂 pages
│   │   │   ├── Registration.jsx  (Signup page)
│   │   │   ├── Login.jsx  (Login page with Google sign-in)
│   │   │   ├── Home.jsx  (Landing page)
│   │   │   ├── About.jsx  (About page)
│   │   │   ├── Contact.jsx  (Contact page)
│   │   │   ├── Collections.jsx  (Product listing with filters & sorting)
│   │   │   ├── Product.jsx  (Products page)
│   │   │   ├── ProductDetail.jsx  (Single product page)
│   │   │   ├── Cart.jsx  (Shopping cart)
│   │   │   ├── PlaceOrder.jsx  (Checkout & payment)
│   │   │   ├── Order.jsx  (Order history)
│   │   │   ├── NotFound.jsx  (404 page)
│
├── 📂 admin  (Admin panel: React.js + TailwindCSS + Vite)
│   ├── index.html  (Base HTML file)
│   ├── package.json  (Admin dependencies)
│   ├── vite.config.js  (Vite & Tailwind configuration)
│   ├── eslint.config.js  (ESLint configuration)
│   ├── logo.png  (Admin logo)
│   ├── README.md  (Default Vite readme)
│   ├── .gitignore
│   ├── 📂 src
│   │   ├── App.jsx  (Main component & routing)
│   │   ├── main.jsx  (React entry point)
│   │   ├── App.css  (Component styling)
│   │   ├── index.css  (Global TailwindCSS styling)
│   │   ├── 📂 assets  (Logo & upload placeholder image)
│   │   ├── 📂 context
│   │   │   ├── AuthContext.jsx  (Server URL provider)
│   │   │   ├── AdminContext.jsx  (Logged-in admin state)
│   │   ├── 📂 component
│   │   │   ├── Nav.jsx  (Admin top bar & logout)
│   │   │   ├── Sidebar.jsx  (Admin sidebar navigation)
│   │   │   ├── Loading.jsx  (Loading spinner)
│   │   ├── 📂 pages
│   │   │   ├── Login.jsx  (Admin login)
│   │   │   ├── Home.jsx  (Admin home)
│   │   │   ├── Add.jsx  (Add new product)
│   │   │   ├── Lists.jsx  (View & remove products)
│   │   │   ├── Orders.jsx  (View orders & update status)
│
└── 📖 README.md  (Project documentation)
```

## 🚀 Features

- ✅ **Authentication:** Email signup with validation (valid email and password of 8+ characters), login, and Google sign-in through Firebase, with JWT cookie sessions.
- ✅ **Product Browsing:** Latest Collection, Best Sellers, and Related Products sections.
- ✅ **Filters, Search & Sorting:** Filter by Men, Women, or Kids and by TopWear, BottomWear, or WinterWear, search products, and sort by price.
- ✅ **Product Details:** Four product images, description, and size selection.
- ✅ **Cart:** Add items with sizes, update quantities, and see totals with a ₹40 delivery fee.
- ✅ **Checkout & Payments:** Cash on Delivery or online payment with Razorpay, verified on the server.
- ✅ **Order History:** Customers can view their past orders and status.
- ✅ **Admin Panel:** Separate login, add products with four images, list and remove products, and update order status.
- ✅ **Voice Assistant:** Navigate to pages, open or close search, and open the cart by speaking.
- ✅ **Image Hosting:** Product images are uploaded to Cloudinary.

## 🔧 Tech Stack

- **Frontend & Admin:** React.js, React Router, TailwindCSS, Vite, React Toastify, React Icons
- **Backend:** Node.js, Express.js
- **Database:** MongoDB with Mongoose
- **Authentication:** JWT, bcrypt.js, Firebase (Google Auth), cookie-parser
- **Payments:** Razorpay
- **Media Storage:** Cloudinary, Multer
- **Voice Assistant:** Web Speech API (speech recognition & synthesis)
- **HTTP Client:** Axios

## 📥 Installation & Setup

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/ravisainii701/One-cart.git
cd One-cart
```

### 2️⃣ Backend Setup

```bash
cd backend
npm install
```

### 3️⃣ Frontend Setup

```bash
cd frontend
npm install
```

### 4️⃣ Admin Panel Setup

```bash
cd admin
npm install
```

### 5️⃣ Set Environment Variables

Create a `.env` file in the `backend` directory:

```env
PORT=8000
MONGODB_URL=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
CLOUDINARY_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret
ADMIN_EMAIL=your_admin_email
ADMIN_PASSWORD=your_admin_password
```

Create a `.env` file in the `frontend` directory:

```env
VITE_FIREBASE_APIKEY=your_firebase_api_key
VITE_RAZORPAY_KEY_ID=your_razorpay_key_id
```

> ⚠️ Keep `PORT=8000`. Both the frontend and the admin panel call the API at `http://localhost:8000` (set in their `AuthContext.jsx` files), and the backend defaults to 6000 if `PORT` is not set.

## 📌 Steps to Run the Project

### 6️⃣ Run the Backend Server

```bash
cd backend
npm run dev
```

The API will be available at: http://localhost:8000

### 7️⃣ Run the Frontend (Customer App)

```bash
cd frontend
npm run dev
```

Frontend will be available at: http://localhost:5173

### 8️⃣ Run the Admin Panel

```bash
cd admin
npm run dev
```

Admin panel will be available at: http://localhost:5174 (Vite picks the next free port if 5173 is taken)

## 📡 API Endpoints

**Auth** (`/api/auth`)

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/registration` | Register a new user |
| POST | `/login` | Log in a user |
| GET | `/logout` | Log out |
| POST | `/googlelogin` | Google sign-in |
| POST | `/adminlogin` | Admin login |

**User** (`/api/user`)

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/getcurrentuser` | Get current logged-in user |
| GET | `/getadmin` | Get current admin (admin only) |

**Product** (`/api/product`)

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/addproduct` | Add a product with up to 4 images |
| GET | `/list` | Get all products |
| POST | `/remove/:id` | Remove a product (admin only) |

**Cart** (`/api/cart`)

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/get` | Get the user's cart |
| POST | `/add` | Add an item to the cart |
| POST | `/update` | Update item quantity |

**Order** (`/api/order`)

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/placeorder` | Place a Cash on Delivery order |
| POST | `/razorpay` | Create a Razorpay order |
| POST | `/verifyrazorpay` | Verify Razorpay payment |
| POST | `/userorder` | Get the user's orders |
| POST | `/list` | Get all orders (admin only) |
| POST | `/status` | Update order status (admin only) |

## 🚀 Deployment

### 🌍 Backend Deployment (Node.js/Express)

- Use Render, Railway, AWS EC2, or DigitalOcean to host the backend.
- Add a `"start": "node index.js"` script to `backend/package.json` (only `dev` exists right now).
- Set all environment variables in your hosting provider's dashboard.
- Replace the hardcoded `http://localhost:5173` and `http://localhost:5174` in the CORS setup of `backend/index.js` with your deployed frontend and admin URLs.
- Ensure MongoDB Atlas allows connections from your server's IP.

### 🖥 Frontend & Admin Deployment (React + Vite)

- Replace `serverUrl` in `frontend/src/context/AuthContext.jsx` and `admin/src/context/AuthContext.jsx` with your deployed backend URL.

**Deploy on Vercel**

```bash
cd frontend
npm install -g vercel
vercel login
vercel deploy
```

Repeat the same steps inside the `admin` folder for the admin panel.

**Deploy on Netlify**

```bash
cd frontend
npm install -g netlify-cli
netlify login
netlify deploy --prod
```

## 🌱 How It Works

1️⃣ A customer signs up with email or Google and logs in.
2️⃣ They browse products, filter and search, and add items to the cart with sizes.
3️⃣ At checkout they enter an address and pay by Cash on Delivery or Razorpay.
4️⃣ The admin adds products, views incoming orders, and updates order status.
5️⃣ The customer checks their order history for the latest status.

## 🛠 Future Roadmap

- ⭐ Product reviews and ratings
- ❤️ Wishlist and saved items
- 🎟️ Coupons and discount codes
- 📊 Sales analytics dashboard for admins
- 📱 Mobile app (React Native)

## 🤝 Real-World Use Cases

- 🏬 **Small Fashion Businesses:** Launch an online store with product and order management.
- 🛒 **Shoppers:** Browse, filter, and buy clothing with easy payments.
- 🎓 **Developers & Students:** A full-stack reference project covering auth, payments, image uploads, and admin dashboards.

## 🤝 Contributing

We welcome contributions from the community! Feel free to:

- Fork the repository
- Create a pull request with your changes
- Report issues or suggest improvements

**🛒 Shop smart, manage easily with OneCart! 🚀**
