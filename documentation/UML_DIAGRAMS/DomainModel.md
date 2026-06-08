# Rana Electronics System - Domain Model

## Overview
The domain model represents the core business entities and their relationships in the Rana Electronics System. This document describes the key domain classes and their associations.

## Domain Model Entities

### 1. **User** (Abstract Base Class)
Represents a person interacting with the system.

**Attributes:**
- userId: String (PK)
- fullName: String
- email: String (Unique)
- phoneNumber: String
- password: String (Encrypted)
- createdDate: DateTime
- accountStatus: Enum {Active, Blocked, Inactive}
- lastLoginDate: DateTime

**Operations:**
- login()
- logout()
- changePassword()
- updateProfile()

---

### 2. **Customer** (Specialization of User)
Represents registered customers who can purchase products.

**Additional Attributes:**
- loyaltyPoints: Integer
- totalOrders: Integer
- deliveryAddress: String
- wishlist: List<Product>
- addressBook: List<Address>

**Additional Operations:**
- addToCart()
- placeOrder()
- viewOrderHistory()
- addToWishlist()
- submitReview()
- setpriceAlert()
- viewLoyaltyPoints()

---

### 3. **Admin** (Specialization of User)
Represents administrators managing the platform.

**Additional Attributes:**
- role: String
- permissions: List<String>
- departmentAssignment: String

**Additional Operations:**
- manageProducts()
- manageUsers()
- manageOrders()
- manageDealers()
- viewReports()
- updateSettings()

---

### 4. **GuestUser**
Represents unregistered visitors.

**Attributes:**
- sessionId: String
- browsedProducts: List<Product>
- sessionStartTime: DateTime

**Operations:**
- browseProducts()
- searchProduct()
- viewProductDetail()
- register()

---

### 5. **Product**
Represents an electronic appliance available for sale.

**Attributes:**
- productId: String (PK)
- name: String
- brand: Brand
- category: Category
- description: String
- price: Decimal
- wattage: Integer (for electricity estimators)
- specifications: Map<String, String>
- images: List<String>
- stockQuantity: Integer
- status: Enum {InStock, OutOfStock, Discontinued}
- averageRating: Decimal
- dealer: Dealer
- createdDate: DateTime
- lastUpdatedDate: DateTime

**Operations:**
- updatePrice()
- updateStock()
- getReviews()
- calculateAverageRating()
- getRelatedProducts()

---

### 6. **Category**
Groups products by type.

**Attributes:**
- categoryId: String (PK)
- categoryName: String
- description: String
- icon: String

**Operations:**
- getProducts()
- addProduct()

---

### 7. **Brand**
Represents product manufacturers.

**Attributes:**
- brandId: String (PK)
- brandName: String
- logo: String
- dealersList: List<Dealer>

**Operations:**
- getProducts()
- getDealers()

---

### 8. **Dealer**
Represents suppliers/dealers providing products.

**Attributes:**
- dealerId: String (PK)
- dealerName: String
- companyName: String
- contactNumber: String
- email: String
- city: String
- address: String
- brands: List<Brand>
- status: Enum {Active, Inactive}
- createdDate: DateTime

**Operations:**
- updateContactInfo()
- updateStatus()
- getProductsList()
- addProduct()

---

### 9. **ShoppingCart**
Represents the customer's temporary shopping collection.

**Attributes:**
- cartId: String (PK)
- customer: Customer
- items: List<CartItem>
- createdDate: DateTime
- lastUpdatedDate: DateTime
- subtotal: Decimal
- discountAmount: Decimal
- totalAmount: Decimal

**Operations:**
- addItem()
- removeItem()
- updateQuantity()
- applyCoupon()
- calculateTotal()
- clearCart()
- getCartItems()

---

### 10. **CartItem**
Represents individual items in a shopping cart.

**Attributes:**
- cartItemId: String (PK)
- cart: ShoppingCart
- product: Product
- quantity: Integer
- unitPrice: Decimal
- totalPrice: Decimal
- addedDate: DateTime

**Operations:**
- updateQuantity()
- calculateTotal()
- remove()

---

### 11. **Order**
Represents a customer's purchase transaction.

**Attributes:**
- orderId: String (PK)
- customer: Customer
- orderDate: DateTime
- items: List<OrderItem>
- deliveryAddress: String
- shippingCost: Decimal
- subtotal: Decimal
- discountAmount: Decimal
- totalAmount: Decimal
- status: Enum {Pending, Processing, Shipped, OutForDelivery, Delivered, Cancelled}
- paymentMethod: PaymentMethod
- payment: Payment
- driver: Driver
- estimatedDeliveryDate: DateTime
- actualDeliveryDate: DateTime

**Operations:**
- updateStatus()
- cancelOrder()
- trackOrder()
- assignDriver()
- generateInvoice()
- calculateLoyaltyPoints()

---

### 12. **OrderItem**
Represents individual products within an order.

**Attributes:**
- orderItemId: String (PK)
- order: Order
- product: Product
- quantity: Integer
- unitPrice: Decimal
- totalPrice: Decimal

**Operations:**
- getDetails()

---

### 13. **Payment**
Represents payment transaction details.

**Attributes:**
- paymentId: String (PK)
- order: Order
- paymentMethod: Enum {COD, JazzCash, EasyPaisa}
- amount: Decimal
- status: Enum {Pending, Completed, Failed, Refunded}
- transactionId: String
- paymentDate: DateTime
- invoiceNumber: String

**Operations:**
- processPayment()
- generateInvoice()
- refundPayment()
- getPaymentStatus()

---

### 14. **Coupon**
Represents discount vouchers.

**Attributes:**
- couponId: String (PK)
- couponCode: String (Unique)
- discountPercentage: Decimal
- discountAmount: Decimal
- minimumOrderAmount: Decimal
- expiryDate: DateTime
- usageLimit: Integer
- currentUsageCount: Integer
- status: Enum {Active, Expired, Inactive}
- createdDate: DateTime

**Operations:**
- validate()
- applyCoupon()
- getDiscount()
- isExpired()
- incrementUsage()

---

### 15. **Review**
Represents customer product reviews and ratings.

**Attributes:**
- reviewId: String (PK)
- product: Product
- customer: Customer
- rating: Integer (1-5)
- comment: String
- isVerifiedBuyer: Boolean
- helpfulCount: Integer
- createdDate: DateTime

**Operations:**
- updateReview()
- deleteReview()
- markAsHelpful()

---

### 16. **Wishlist**
Represents customer's saved products for future purchase.

**Attributes:**
- wishlistId: String (PK)
- customer: Customer
- products: List<Product>
- createdDate: DateTime
- lastUpdatedDate: DateTime

**Operations:**
- addProduct()
- removeProduct()
- moveToCart()
- getProducts()

---

### 17. **Driver**
Represents delivery drivers for order shipment.

**Attributes:**
- driverId: String (PK)
- name: String
- phoneNumber: String
- cnic: String (Unique)
- vehicleNumber: String
- city: String
- status: Enum {Available, OnDelivery, OffDuty}
- registrationDate: DateTime

**Operations:**
- updateStatus()
- assignOrder()
- completeDelivery()
- getAssignedOrders()

---

### 18. **PriceAlert**
Represents customer price drop alerts.

**Attributes:**
- alertId: String (PK)
- customer: Customer
- product: Product
- targetPrice: Decimal
- currentPrice: Decimal
- status: Enum {Active, Notified, Expired}
- createdDate: DateTime
- notifiedDate: DateTime

**Operations:**
- checkPrice()
- notifyCustomer()
- deactivateAlert()

---

### 19. **Notification**
Represents system notifications sent to customers.

**Attributes:**
- notificationId: String (PK)
- recipient: User
- type: Enum {OrderConfirmation, OrderStatusUpdate, DeliveryAlert, PriceAlert, PromoAlert}
- title: String
- message: String
- channel: Enum {Email, SMS, InApp}
- status: Enum {Sent, Pending, Failed}
- sentDate: DateTime

**Operations:**
- send()
- markAsRead()
- retry()

---

### 20. **ElectricityEstimate**
Represents electricity consumption calculations.

**Attributes:**
- estimateId: String (PK)
- product: Product
- dailyUsageHours: Decimal
- wattage: Integer
- estimatedMonthlyConsumption: Decimal
- estimatedMonthlyCost: Decimal
- tariffRate: Decimal
- calculationDate: DateTime

**Operations:**
- calculate()
- getTariffRate()
- getMonthlyConsumption()

---

### 21. **Banner**
Represents promotional banners on homepage.

**Attributes:**
- bannerId: String (PK)
- title: String
- imageUrl: String
- redirectUrl: String
- displayOrder: Integer
- isActive: Boolean
- createdDate: DateTime
- expiryDate: DateTime

**Operations:**
- activate()
- deactivate()
- updateDisplayOrder()

---

### 22. **FAQ**
Represents frequently asked questions.

**Attributes:**
- faqId: String (PK)
- question: String
- answer: String
- category: String
- isActive: Boolean
- viewCount: Integer
- createdDate: DateTime
- lastUpdatedDate: DateTime

**Operations:**
- updateFAQ()
- incrementViewCount()

---

### 23. **LoyaltyPoints**
Represents customer loyalty reward system.

**Attributes:**
- loyaltyId: String (PK)
- customer: Customer
- totalPoints: Integer
- usedPoints: Integer
- availablePoints: Integer
- lastUpdatedDate: DateTime

**Operations:**
- addPoints()
- deductPoints()
- redeemVoucher()
- getAvailablePoints()

---

### 24. **Address**
Represents customer delivery addresses.

**Attributes:**
- addressId: String (PK)
- customer: Customer
- addressType: Enum {Home, Office, Other}
- city: String
- area: String
- fullAddress: String
- zipCode: String
- isDefault: Boolean
- createdDate: DateTime

**Operations:**
- updateAddress()
- setAsDefault()

---

## Key Relationships

### 1. **One-to-Many Relationships:**
- `Customer` has many `Orders`
- `Customer` has many `Reviews`
- `Customer` has one `ShoppingCart`
- `Customer` has many `PriceAlerts`
- `Customer` has one `Wishlist`
- `Customer` has one `LoyaltyPoints`
- `Product` has many `Reviews`
- `Product` has many `Orders` (through OrderItem)
- `Order` has many `OrderItems`
- `Brand` has many `Products`
- `Category` has many `Products`
- `Dealer` has many `Products`
- `Driver` has many `Orders`
- `Coupon` has many `Orders` (through Application)
- `ShoppingCart` has many `CartItems`

### 2. **Many-to-Many Relationships:**
- `Dealer` ↔ `Brand` (Many dealers supply many brands)
- `Customer` ↔ `Product` (Wishlist association)

### 3. **Inheritance Hierarchy:**
- `User` (Parent)
  - `Customer` (Child)
  - `Admin` (Child)
  - `GuestUser` (Child)

### 4. **Composition/Aggregation:**
- `ShoppingCart` contains multiple `CartItems`
- `Order` contains multiple `OrderItems`
- `Wishlist` contains multiple `Products`

---

## Cardinality Notation

```
Customer (1) ──── (M) Order
Customer (1) ──── (1) ShoppingCart
Customer (1) ──── (M) Review
Customer (1) ──── (M) PriceAlert
Customer (1) ──── (1) Wishlist
Customer (1) ──── (1) LoyaltyPoints
Customer (1) ──── (M) Address

Product (1) ──── (M) Review
Product (1) ──── (M) CartItem
Product (1) ──── (M) OrderItem

Category (1) ──── (M) Product
Brand (1) ──── (M) Product
Dealer (1) ──── (M) Product

Order (1) ──── (M) OrderItem
ShoppingCart (1) ──── (M) CartItem
Wishlist (1) ──── (M) Product

Driver (1) ──── (M) Order
Payment (1) ──── (1) Order
Coupon (M) ──── (M) Order

Brand (M) ──── (M) Dealer
```

---

## Domain Constraints

1. **Email Uniqueness:** Each user email must be unique in the system
2. **Stock Validation:** Product stock cannot be negative
3. **Price Validation:** Product price must be greater than zero
4. **Rating Range:** Review ratings must be between 1 and 5
5. **Coupon Validity:** Coupon expiry date must be in the future
6. **Order Status Flow:** Status can only progress: Pending → Processing → Shipped → OutForDelivery → Delivered
7. **Payment Amount:** Payment amount must equal order total
8. **Loyalty Points:** Points cannot go below zero
9. **Cart Quantity:** Cart item quantity must be greater than zero
10. **Driver Uniqueness:** Driver CNIC must be unique

---