# E-Commerce Product Recommendation System using Content-Based Filtering

## Project 3 — Industrial Training Kit (DecodeLabs)

### Overview
This project is a simple AI-powered recommendation system that suggests the
**Top 3 most suitable products** for a customer based on shopping
preferences they select (e.g. preferred payment method, referral source,
coupon usage). It uses **Content-Based Filtering**, matching a user's
preference profile against product profiles built from real order data,
using **TF-IDF vectorization** and **Cosine Similarity** — no machine
learning models, collaborative filtering, or neural networks are used.

### Goal
Create a simple recommendation system based on user preferences by:
- Taking user input (shopping preferences)
- Matching preferences using similarity logic
- Displaying the recommended items (products)

### Methodology (IPO Model)
| Stage | Description |
|-------|-------------|
| **Input** | User selects at least 3 shopping preferences |
| **Process** | TF-IDF Vectorization -> Cosine Similarity -> Ranking -> Filtering |
| **Output** | Top 3 recommended products |

### How It Works
1. **Load Dataset** — Reads `ecommerce_orders.csv`, which contains order-level
   e-commerce data (product purchased, payment method, order status,
   referral source, coupon code, etc.).
2. **Build Product Profiles** — For every unique `Product`, all of its
   related order attributes (`PaymentMethod`, `OrderStatus`,
   `ReferralSource`, `CouponCode`) are combined into a single text profile.
   This turns each product into a "document" describing the kinds of
   purchase behavior associated with it.
3. **User Input** — The user provides at least three shopping preferences
   (e.g. Debit Card, Instagram, SAVE10).
4. **TF-IDF Vectorization** — Both the product profiles and the user's
   preferences are converted into numerical TF-IDF vectors using the same
   fitted `TfidfVectorizer`, ensuring they share the same vocabulary space.
5. **Cosine Similarity** — The angle between the user's preference vector
   and each product's profile vector is measured. A higher score means a
   closer match.
6. **Sorting & Filtering** — Products are sorted by similarity score in
   descending order, and only the Top 3 are kept.
7. **Output** — The Top 3 products are displayed along with their
   similarity score.

### Dataset
The dataset (`ecommerce_orders.csv`) is a real order-level dataset with the
following columns (1,200 rows):

| Column | Description |
|--------|-------------|
| `OrderID` | Unique order identifier |
| `Date` | Order date |
| `CustomerID` | Unique customer identifier |
| `Product` | Product purchased (Monitor, Phone, Tablet, Chair, Printer, Laptop, Desk) |
| `Quantity` | Number of units ordered |
| `UnitPrice` | Price per unit |
| `ShippingAddress` | Shipping address |
| `PaymentMethod` | Payment method used (Debit Card, Online, Credit Card, Gift Card, Cash) |
| `OrderStatus` | Order status (Shipped, Cancelled, Returned, Delivered, Pending) |
| `TrackingNumber` | Shipment tracking number |
| `ItemsInCart` | Number of items in the cart |
| `CouponCode` | Coupon code used, if any (SAVE10, FREESHIP, WINTER15) |
| `ReferralSource` | How the customer found the store (Instagram, Referral, Email, Facebook, Google) |
| `TotalPrice` | Total order price |

Only `Product`, `PaymentMethod`, `OrderStatus`, `ReferralSource`, and
`CouponCode` are used to build the content-based product profiles.

> Upload `ecommerce_orders.csv` to your Google Colab session (or mount
> Google Drive and update the file path) before running the notebook.


Logic building, pattern matching, and content-based recommendation concepts
using the IPO (Input-Process-Output) architecture.
