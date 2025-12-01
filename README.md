A full-stack e-commerce application for buying flowers online with an admin dashboard.

## Project Structure

```
flowers-shop/
├── backend/                 # Spring Boot backend
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/flowershop/
│   │   │   │   ├── controller/      # REST API controllers
│   │   │   │   ├── model/           # JPA entities
│   │   │   │   ├── repository/      # Data repositories
│   │   │   │   ├── service/         # Business logic
│   │   │   │   └── FlowersShopApplication.java
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   └── pom.xml
│   └── README.md
│
└── frontend/                # Vite frontend
    ├── admin/               # Admin dashboard
    │   └── index.html
    ├── js/                  # JavaScript files
    │   ├── main.js
    │   ├── products.js
    │   ├── cart.js
    │   ├── checkout.js
    │   └── admin.js
    ├── styles/              # CSS files
    │   ├── main.css
    │   └── admin.css
    ├── index.html           # Home page
    ├── products.html        # Product listing
    ├── cart.html            # Shopping cart
    ├── checkout.html        # Checkout page
    ├── package.json
    └── vite.config.js
```

## Features

### Customer Features

- Browse flowers by category
- Add products to cart
- Shopping cart management
- Checkout and order placement
- Responsive design

### Admin Features

- Dashboard with statistics
- Product management (CRUD operations)
- Order management with status updates
- User management
- Real-time data updates

## Technologies Used

### Backend

- **Spring Boot 3.2.0** - Java framework
- **Spring Data JPA** - Database interaction
- **MySQL** - Database
- **Swagger/OpenAPI** - API documentation
- **Lombok** - Reduce boilerplate code
- **Maven** - Build tool
- **Docker** - Containerization

### Frontend

- **Vite** - Build tool and dev server
- **HTML5** - Structure
- **CSS3** - Styling with gradients and animations
- **Vanilla JavaScript** - Client-side logic
- **Fetch API** - HTTP requests
- **Nginx** - Web server (for Docker)
- **Docker** - Containerization

## Setup Instructions

### Option 1: Run with Docker (Recommended)

**Prerequisites:**

- Docker Desktop installed

**Steps:**

1. **Start all services with Docker Compose:**

   ```bash
   cd flowers-shop
   docker-compose up -d
   ```

2. **Access the application:**

   - Frontend: `http://localhost`
   - Backend API: `http://localhost:8080`
   - Swagger UI: `http://localhost:8080/swagger-ui/index.html`
   - API Docs: `http://localhost:8080/v3/api-docs`

3. **Stop the services:**

   ```bash
   docker-compose down
   ```

4. **View logs:**
   ```bash
   docker-compose logs -f
   ```

### Option 2: Run Locally (Development)

### Prerequisites

- Java 17 or higher
- Maven 3.6+
- MySQL 8.0+
- Node.js 16+ and npm

### Backend Setup

1. **Install MySQL** and create a database:

   ```sql
   CREATE DATABASE flowers_shop;
   ```

   Or let the application create it automatically.

2. **Configure database** (if needed):
   Edit `backend/src/main/resources/application.properties`:

   ```properties
   spring.datasource.username=root
   spring.datasource.password=your_password
   ```

3. **Run the backend**:

   ```bash
   cd backend
   mvnw spring-boot:run
   ```

   The API will be available at `http://localhost:8080`

   **Swagger UI:** `http://localhost:8080/swagger-ui/index.html`

### Frontend Setup

1. **Install dependencies**:

   ```bash
   cd frontend
   npm install
   ```

2. **Run the development server**:

   ```bash
   npm run dev
   ```

   The application will be available at `http://localhost:3000`

## API Endpoints

All endpoints are documented in Swagger UI at `http://localhost:8080/swagger-ui/index.html`

### Products

- `GET /api/products` - Get all products
- `GET /api/products/{id}` - Get product by ID
- `GET /api/products/category/{category}` - Get products by category
- `POST /api/products` - Create product
- `PUT /api/products/{id}` - Update product
- `DELETE /api/products/{id}` - Delete product

### Orders

- `GET /api/orders` - Get all orders
- `GET /api/orders/{id}` - Get order by ID
- `GET /api/orders/user/{userId}` - Get orders by user
- `GET /api/orders/status/{status}` - Get orders by status
- `POST /api/orders` - Create order
- `PATCH /api/orders/{id}/status` - Update order status
- `DELETE /api/orders/{id}` - Delete order

### Users

- `GET /api/users` - Get all users
- `GET /api/users/{id}` - Get user by ID
- `POST /api/users` - Create user
- `PUT /api/users/{id}` - Update user
- `DELETE /api/users/{id}` - Delete user

## Usage

### For Customers

1. Visit `http://localhost:3000`
2. Browse flowers on the home page or product page
3. Add items to cart
4. Proceed to checkout
5. Fill in shipping information
6. Place order

### For Admins

1. Visit `http://localhost:3000/admin/`
2. Manage products, orders, and users from the dashboard
3. Add new products using the "Add Product" button
4. Update order status from the orders section
5. View statistics on the dashboard

## Database Schema

### Users Table

- id, name, email, password, phone, address, role, created_at

### Products Table

- id, name, description, price, stock, category, image_url, created_at

### Orders Table

- id, user_id, total_amount, status, shipping_address, phone, created_at, updated_at

### Order Items Table

- id, order_id, product_id, quantity, price

## Development

### Adding Sample Data

Use the admin panel to add products, or insert directly into MySQL:

```sql
INSERT INTO products (name, description, price, stock, category) VALUES
('Red Roses', 'Beautiful red roses', 29.99, 50, 'Roses'),
('White Tulips', 'Fresh white tulips', 24.99, 30, 'Tulips'),
('Pink Lilies', 'Elegant pink lilies', 34.99, 25, 'Lilies'),
('Mixed Bouquet', 'Colorful mixed bouquet', 39.99, 20, 'Bouquets');
```

## Build for Production

### Backend

```bash
cd backend
mvnw clean package
java -jar target/flowers-shop-backend-1.0.0.jar
```

### Frontend

```bash
cd frontend
npm run build
```

The production files will be in the `dist/` folder.

## License

MIT License

## Support

For issues or questions, please create an issue in the repository.
