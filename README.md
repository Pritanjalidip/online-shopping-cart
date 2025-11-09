# 🌱 GreenDookan - Organic Grocery E-Commerce Website

A full-stack organic grocery e-commerce platform built with Java, Servlets, and modern web technologies.

## 🚀 Features

### 🛒 Shopping Experience
- **113 Products** across 6 categories
- Real-time search and filtering
- Shopping cart with quantity management
- Promo code support (FRESH10, SAVE50, ORGANIC20)
- Smooth checkout process

### 🔐 Authentication
- User registration with validation
- Secure login system
- Profile management
- Order history tracking

### 📦 Product Categories
- Fruits & Vegetables (35 items)
- Dairy & Eggs (18 items)
- Pantry & Dry Goods (25 items)
- Beverages (15 items)
- Snacks & Treats (15 items)
- Meat (2 items)

### 👨‍💼 Admin Panel
- Product management (Add/Edit/Delete)
- Order management
- Sales reports
- Customer analytics

## 🛠️ Technologies Used

### Frontend
- HTML5, CSS3, JavaScript (ES6+)
- Font Awesome 6.0 for icons
- Responsive design
- LocalStorage for data persistence

### Backend
- Java 11
- Servlets (javax.servlet 4.0.1)
- Apache Tomcat 7
- H2 In-Memory Database
- Maven for build management

## 📋 Prerequisites

- Java 11 or higher
- Maven 3.6+
- Python 3.x (for development server)
- Modern web browser

## 🚀 Getting Started

### Clone the repository
```bash
git clone https://github.com/AditiAnand082004/GreenDookan.git
cd GreenDookan
```

### Run Frontend (Development)
```bash
cd src/main/webapp
python -m http.server 3000
```
Visit: `http://localhost:3000`

### Run Backend (Production)
```bash
mvn tomcat7:run
```
Visit: `http://localhost:8082/GreenDookan`

## 🔑 Default Admin Account
- **Email**: admin@greendookan.com
- **Password**: admin123

## 📁 Project Structure
```
GreenDookan/
├── src/main/
│   ├── java/com/webapp/
│   │   ├── dao/          # Data Access Objects
│   │   ├── model/        # Entity Models
│   │   └── servlet/      # HTTP Servlets
│   └── webapp/
│       ├── css/          # Stylesheets
│       ├── js/           # JavaScript files
│       └── index.html    # Main page
├── pom.xml               # Maven configuration
└── README.md
```

## ✨ Key Features

- ✅ No seafood or ginger products (vegetarian-friendly)
- ✅ Accurate product-specific images
- ✅ Extra small notification toasts
- ✅ Professional authentication system
- ✅ Real-time form validation
- ✅ Responsive mobile design
- ✅ Order tracking system
- ✅ Admin dashboard

## 🎯 Promo Codes
- **FRESH10** - 10% discount
- **SAVE50** - ₹50 off
- **ORGANIC20** - 20% discount

## 📊 Statistics
- **Total Products**: 113
- **Categories**: 6
- **Code Lines**: 6000+
- **CSS Rules**: 4000+

## 🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License
This project is open source and available under the MIT License.

## 👩‍💻 Author
**Aditi Anand**
- GitHub: [@AditiAnand082004](https://github.com/AditiAnand082004)

## 🙏 Acknowledgments
- Font Awesome for icons
- Unsplash for product images
- Apache Tomcat team
- Maven community

---
Made with 💚 by Aditi Anand
