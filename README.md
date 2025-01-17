# Marketplace Technical Foundation - [Ecommerce]


## 📌 Project Overview  
The **Marketplace Builder** is a web application built using **Next.js** and integrated with **Sanity CMS** for managing products and orders. This application allows users to browse products, add them to the cart, and complete purchases securely via **Stripe**. It also integrates with **ShipEngine** for generating shipping labels and tracking orders.

---

## 🌟 Features  
- **Product Listing Page**: Display products available for purchase.
- **Cart Page**: Allow users to add products to their cart and view the total.
- **Checkout Page**: Complete the purchase securely using Stripe.
- **Payment Integration with Stripe**: Secure payment processing for orders.
- **Shipping Label Generation & Order Tracking via ShipEngine**: Generate shipping labels and track orders.
- **Product & Order Management via Sanity CMS**: Easily manage products and orders.

---

## 🏗️ System Architecture  

### Frontend  
- Built with **Next.js** to render pages and fetch data from APIs.

### CMS  
- **Sanity CMS** is used to manage product and order data.

### APIs  
- **Products API**: Fetch product data from **Sanity CMS**.
- **Shipping API**: Generate and track shipping labels using **ShipEngine**.
- **Payments API**: Process payments securely via **Stripe**.

### Architecture Diagram  
```css
[Frontend (Next.js)]
    |
[Sanity CMS] --> [Product Data API]
    |
[Third-Party API] --> [Shipment Tracking API]
    |
[Payment Gateway]

🛠️ Technical Requirements
Frontend
Next.js will be used to build the user interface with the following pages:
Homepage
Product Listing Page
Cart Page
Checkout Page
CMS
Sanity CMS will be used for managing products and orders.
Define schemas for Products and Orders in Sanity.
Third-Party APIs
Payment Gateway: Integrate Stripe for secure payment processing.
Shipping API: Use ShipEngine for order tracking and shipping label generation.

📡 API Endpoints
1️⃣ /api/products (GET)
Fetches product data from Sanity CMS.
Example Response:

[
  {
    "id": "1",
    "name": "Product A",
    "price": 100,
    "description": "A great product."
  }
]
2️⃣ /api/shipping-label (POST)
Generates a shipping label using ShipEngine.
Example Request:

{
  "orderId": "12345",
  "address": {
    "line1": "123 Main St",
    "city": "New York",
    "state": "NY",
    "zip": "10001"
  }
}
3️⃣ /api/checkout (POST)
Processes payments via Stripe.
Example Request:

{
  "amount": 200,
  "currency": "USD",
  "paymentMethodId": "pm_1GqIC8AHEMiO6EgC2LkU5bXE"
}
📝 Sanity Schema Documentation

1️⃣ Products Schema

export default {
  name: "product",
  type: "document",
  title: "Product",
  fields: [
    { name: "name", type: "string", title: "Product Name" },
    { name: "price", type: "number", title: "Price" },
    { name: "description", type: "text", title: "Description" },
    { name: "image", type: "image", title: "Product Image" },
    { name: "category", type: "string", title: "Category" }
  ]
};
2️⃣ Orders Schema

export default {
  name: "order",
  type: "document",
  title: "Order",
  fields: [
    { name: "user", type: "string", title: "User" },
    { name: "productIds", type: "array", of: [{ type: "reference", to: [{ type: "product" }] }] },
    { name: "totalPrice", type: "number", title: "Total Price" },
    { name: "status", type: "string", title: "Order Status" }
  ]
};

