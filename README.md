# Marketplace Builder Hackathon - Day 2

## Project Overview

This project forms the backbone of a dynamic and scalable e-commerce platform, developed as part of the **Marketplace Builder Hackathon 2025**. By leveraging cutting-edge technologies, the platform aims to deliver a smooth and engaging shopping experience for users.

---

## Features

### System Architecture
- **Comprehensive Design**: A robust architecture connecting the frontend, backend, and external services.
- **Interactive Workflows**: Detailed processes for seamless user interactions and system operations.

### API Endpoints
- Clear and structured documentation for API methods, payload requirements, and example responses.

### Sanity CMS Integration
- Tailored schemas for managing essential data, including products, customers, and orders.

---

## System Architecture Diagram

### Components:
1. **Frontend (Next.js)**: A responsive user interface with dynamic functionality.
2. **Sanity CMS**: A powerful backend for organizing and managing data.
3. **Third-Party Services**: Payment processing via Stripe and shipping/tracking integration.

### Workflow Overview:
1. Users explore the platform, add products to their cart, and place orders via the frontend.
2. The frontend retrieves and updates data stored in Sanity CMS.
3. Payment and shipping details are securely managed through third-party APIs.

---

## API Endpoints

| Endpoint      | Method | Purpose               | Payload                                | Response Example                              |
|---------------|--------|-----------------------|----------------------------------------|----------------------------------------------|
| `/products`   | GET    | Retrieve product list | N/A                                    | `{ "id": 1, "name": "Sofa", "price": 1000 }` |
| `/cart`       | POST   | Add item to cart      | `{ "productId": 1, "quantity": 2 }` | `{ "cartId": 123, "status": "Added" }`      |
| `/checkout`   | POST   | Finalize purchase     | `{ "cartId": 123, "paymentInfo": {...}}` | `{ "orderId": 456, "status": "Confirmed" }` |

---

## Sanity CMS Schemas

### Product Schema:
```javascript
export default {
  name: 'product',
  type: 'document',
  fields: [
    { name: 'name', type: 'string', title: 'Product Name' },
    { name: 'price', type: 'number', title: 'Price' },
    { name: 'stock', type: 'number', title: 'Stock Level' },
    { name: 'image', type: 'image', title: 'Product Image' }
  ]
};
```

### Order Schema:
```javascript
export default {
  name: 'order',
  type: 'document',
  fields: [
    { name: 'customer', type: 'reference', to: [{ type: 'customer' }] },
    { name: 'products', type: 'array', of: [{ type: 'product' }] },
    { name: 'status', type: 'string', title: 'Order Status' }
  ]
};
```

---

## Workflows

### User Journey

1. **User Authentication:**
   - New users can sign up or log in.
   - User credentials are securely stored and managed in Sanity CMS.

2. **Cart Operations:**
   - Users can add products to their cart and update quantities.
   - Cart data is processed through dedicated APIs.

3. **Order Management:**
   - Orders are created upon checkout and stored in the CMS.
   - Payments are securely processed via Stripe.

---

## Repository

The complete source code, along with diagrams and API references, is available here: [GitHub Repository](#).

---

## Next Steps

- Build and test the documented workflows.
- Expand features, including real-time order tracking and inventory management.
- Optimize the platform for performance and scalability.

---

## Feedback

We value your input! Feel free to open issues or contribute suggestions to improve the project.

