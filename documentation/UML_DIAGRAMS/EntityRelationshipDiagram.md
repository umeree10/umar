# Rana Electronics System - Entity Relationship Diagram (ERD)

## Overview
This document provides a comprehensive Entity Relationship Diagram (ERD) for the Rana Electronics System, showing all entities, their attributes, and relationships in a visual format similar to professional database design standards.

---

## ERD Visual Structure

```
                        RANA ELECTRONICS SYSTEM - ENTITY RELATIONSHIP DIAGRAM

┌──────────────────┐
│      User        │
│ (PK)userId      │─────────┐
│ fullName        │         │
│ email           │         │
│ phoneNumber     │         │
│ password        │         │
│ accountStatus   │         │
│ createdDate     │         │
└──────────────────┘         │
         │                   │
         │                   │
    ┌────┴─────┐             │
    │           │            │
    ▼           ▼            │
┌──────────┐ ┌────────┐     │
│Customer  │ │ Admin  │     │
│(PK)cust- │ │(PK)adm-│     │
│ omerId   │ │ inId   │     │
│loyaltyP- │ │ role   │     │
│oints     │ │permiss-│     │
│totalOrde-│ │ions    │     │
│rs        │ │depart- │     │
│address-  │ │ment    │     │
│Book      │ └────────┘     │
└──┬───────┘                │
   │                        │
   │ 1                      │
   │◄─────────────┐         │
   │              │         │
   │         ┌────┴──────────┤
   │         │                │
   ▼         │ 1              │
┌──────────────┐              │
│ ShoppingCart │              │
│ (PK)cartId  │              │
│ customer(FK)├──────────────┤
│ subtotal    │              │
│ discount    │              │
│ totalAmount │              │
│ createdDate │              │
└──┬───────────┘              │
   │                          │
   │ 1          ┌─────────────┤
   │            │              │
   ▼            │ 1            │
┌──────────────────┐           │
│   CartItem       │           │
│ (PK)cartItemId  │           │
│ cart(FK)        │           │
│ product(FK)     │           │
│ quantity        │           │
│ unitPrice       │           │
│ totalPrice      │           │
└────────┬─────────┘           │
         │                     │
         │ M                   │
         │                     │
         ▼                     │
    ┌─────────────┐            │
    │  Product    │            │
    │(PK)product- │            │
    │Id           │            │
    │ name        │            │
    │ brand(FK)   │            │
    │ category(FK)│            │
    │ price       │            │
    │ wattage     │            │
    │ stock       │            │
    │ status      │            │
    │ avgRating   │            │
    │ dealer(FK)  │            │
    └─┬──┬────┬───┘            │
      │  │    │                │
      │  │    └──────────┐     │
      │  │               │     │
   M  │  │ M          M  │     │
      │  │               │     │
      ▼  ▼               ▼     │
   ┌──────┐         ┌────────┐ │
   │Brand │         │Category│ │
   │(PK)b-│         │(PK)cat-│ │
   │randId│         │egoryId │ │
   │brand-│         │category│ │
   │Name  │         │Name    │ │
   │ logo │         │descrip-│ │
   │deal- │         │tion    │ │
   │ers   │         │ icon   │ │
   └──┬───┘         └────────┘ │
      │                        │
      │ M                      │
      │                        │
      ▼                        │
   ┌──────────┐                │
   │ Dealer   │                │
   │(PK)deal- │                │
   │erId      │                │
   │dealerName│                │
   │companyNa-│                │
   │me        │                │
   │contact#  │                │
   │email     │                │
   │city      │                │
   │address   │                │
   │status    │                │
   └──────────┘                │
                               │
                               │ 1
                               │
                               └──┐
                                  │
                                  ▼
┌──────────────────┐    ┌─────────────────┐
│     Order        │───M│   OrderItem     │
│ (PK)orderId     │    │ (PK)orderItemId │
│ customer(FK)    │    │ order(FK)       │
│ orderDate       │    │ product(FK)     │
│ deliveryAddress │    │ quantity        │
│ shipping Cost   │    │ unitPrice       │
│ subtotal        │    │ totalPrice      │
│ discount        │    └─────────────────┘
│ totalAmount     │
│ status          │
│ paymentMethod   │    ┌──────────────────┐
│ payment(FK)  ├──────M│    Payment       │
│ driver(FK)      │    │ (PK)paymentId    │
│ estDelivery     │    │ order(FK)        │
│ actualDelivery  │    │ method           │
│ createdDate     │    │ amount           │
└─────────────────┘    │ status           │
   │                   │ transactionId    │
   │ 1                 │ paymentDate      │
   │                   │ invoiceNumber    │
   │                   └──────────────────┘
   │
   │ M
   │
   ▼
┌──────────────────┐
│     Driver       │
│ (PK)driverId     │
│ name             │
│ phoneNumber      │
│ cnic             │
│ vehicleNumber    │
│ city             │
│ status           │
│ registrationDate │
└──────────────────┘


┌────────────────────────────────────────────────────────────────────────────┐
│ Additional Entities & Relationships (Detailed View)                        │
└────────────────────────────────────────────────────────────────────────────┘

   ┌──────────────┐
   │   Product    │
   │ (PK)product- │──M──┐
   │   Id         │     │
   └──────────────┘     │
         │              │
         │ 1            │
         │              ▼
         │         ┌──────────────┐
         │         │   Review     │
         │         │(PK)reviewId  │
         │         │product(FK)   │
         │         │customer(FK)  │
         │         │ rating       │
         │         │ comment      │
         │         │isVerified    │
         │         │helpfulCount  │
         │         │createdDate   │
         │         └──────────────┘
         │
         │ 1        ┌──────────────┐
         └────M────│  Wishlist    │
                   │(PK)wishlist- │
                   │   Id         │
                   │customer(FK)  │
                   │product(FK) M │
                   │createdDate   │
                   └──────────────┘


   ┌──────────────┐
   │  Customer    │
   │(PK)cust-     │
   │ omerId       │──M──┐
   └──────────────┘     │
         │              │
         │ 1            │
         │              ▼
         │         ┌──────────────┐
         │         │ PriceAlert   │
         │         │(PK)alertId   │
         │         │customer(FK)  │
         │         │product(FK)   │
         │         │targetPrice   │
         │         │currentPrice  │
         │         │status        │
         │         │createdDate   │
         │         │notifiedDate  │
         │         └──────────────┘
         │
         │ 1        ┌──────────────┐
         └────M────│  Address     │
                   │(PK)address-  │
                   │   Id         │
                   │customer(FK)  │
                   │addressType   │
                   │city          │
                   │area          │
                   │fullAddress   │
                   │zipCode       │
                   │isDefault     │
                   │createdDate   │
                   └──────────────┘


   ┌──────────────┐
   │  Customer    │
   │(PK)cust-     │──1──┐
   │ omerId       │     │
   └──────────────┘     │
                        ▼
                   ┌──────────────────┐
                   │ LoyaltyPoints    │
                   │(PK)loyaltyId     │
                   │customer(FK)      │
                   │totalPoints       │
                   │usedPoints        │
                   │availablePoints   │
                   │lastUpdatedDate   │
                   └──────────────────┘


   ┌──────────────┐
   │   Order      │──M──┐
   │(PK)orderId   │     │
   └──────────────┘     │
                        ▼
                   ┌──────────────┐
                   │ Notification │
                   │(PK)notif-    │
                   │   Id         │
                   │recipient(FK) │
                   │type          │
                   │title         │
                   │message       │
                   │channel       │
                   │status        │
                   │sentDate      │
                   └──────────────┘


   ┌──────────────┐
   │   Order      │──M──┐
   │(PK)orderId   │     │
   └──────────────┘     │
                        ▼
                   ┌──────────────┐
                   │   Coupon     │
                   │(PK)couponId  │
                   │couponCode    │
                   │discountPct   │
                   │discountAmt   │
                   │minOrderAmt   │
                   │expiryDate    │
                   │usageLimit    │
                   │usageCount    │
                   │status        │
                   │createdDate   │
                   └──────────────┘

```

---

## Complete Entity Definitions

### **CORE USER ENTITIES**

#### **1. User (Base Entity)**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| userId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| fullName | VARCHAR(100) | - | NOT NULL |
| email | VARCHAR(100) | - | NOT NULL, UNIQUE |
| phoneNumber | VARCHAR(15) | - | NOT NULL |
| password | VARCHAR(255) | - | NOT NULL, ENCRYPTED |
| accountStatus | ENUM | - | {Active, Blocked, Inactive} |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |
| lastLoginDate | DATETIME | - | NULL |

#### **2. Customer**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| customerId | VARCHAR(50) | PK | Foreign Key from User |
| loyaltyPoints | INT | - | DEFAULT 0, >= 0 |
| totalOrders | INT | - | DEFAULT 0 |
| lastOrderDate | DATETIME | - | NULL |

#### **3. Admin**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| adminId | VARCHAR(50) | PK | Foreign Key from User |
| role | VARCHAR(50) | - | NOT NULL |
| permissions | JSON | - | Array of permission strings |
| department | VARCHAR(50) | - | NULL |

---

### **PRODUCT CATALOG ENTITIES**

#### **4. Product**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| productId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| name | VARCHAR(255) | - | NOT NULL |
| description | TEXT | - | NULL |
| price | DECIMAL(10,2) | - | NOT NULL, > 0 |
| wattage | INT | - | NULL (for electricity estimate) |
| specifications | JSON | - | Product specifications |
| stockQuantity | INT | - | NOT NULL, >= 0 |
| status | ENUM | - | {InStock, OutOfStock, Discontinued} |
| averageRating | DECIMAL(3,2) | - | DEFAULT 0, RANGE 0-5 |
| brandId | VARCHAR(50) | FK | References Brand |
| categoryId | VARCHAR(50) | FK | References Category |
| dealerId | VARCHAR(50) | FK | References Dealer |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |
| lastUpdatedDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

#### **5. Brand**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| brandId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| brandName | VARCHAR(100) | - | NOT NULL, UNIQUE |
| logo | VARCHAR(255) | - | NULL (image URL) |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

#### **6. Category**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| categoryId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| categoryName | VARCHAR(100) | - | NOT NULL, UNIQUE |
| description | TEXT | - | NULL |
| icon | VARCHAR(255) | - | NULL (image URL) |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

#### **7. Dealer**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| dealerId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| dealerName | VARCHAR(100) | - | NOT NULL |
| companyName | VARCHAR(100) | - | NULL |
| contactNumber | VARCHAR(15) | - | NOT NULL |
| email | VARCHAR(100) | - | NOT NULL |
| city | VARCHAR(50) | - | NOT NULL |
| address | TEXT | - | NOT NULL |
| status | ENUM | - | {Active, Inactive} |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

---

### **SHOPPING & CHECKOUT ENTITIES**

#### **8. ShoppingCart**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| cartId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| customerId | VARCHAR(50) | FK | References Customer |
| subtotal | DECIMAL(10,2) | - | DEFAULT 0 |
| discountAmount | DECIMAL(10,2) | - | DEFAULT 0 |
| totalAmount | DECIMAL(10,2) | - | DEFAULT 0 |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |
| lastUpdatedDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

#### **9. CartItem**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| cartItemId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| cartId | VARCHAR(50) | FK | References ShoppingCart |
| productId | VARCHAR(50) | FK | References Product |
| quantity | INT | - | NOT NULL, > 0 |
| unitPrice | DECIMAL(10,2) | - | NOT NULL |
| totalPrice | DECIMAL(10,2) | - | NOT NULL |
| addedDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

---

### **ORDER & PAYMENT ENTITIES**

#### **10. Order**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| orderId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| customerId | VARCHAR(50) | FK | References Customer |
| orderDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |
| deliveryAddress | TEXT | - | NOT NULL |
| shippingCost | DECIMAL(10,2) | - | DEFAULT 0 |
| subtotal | DECIMAL(10,2) | - | NOT NULL |
| discountAmount | DECIMAL(10,2) | - | DEFAULT 0 |
| totalAmount | DECIMAL(10,2) | - | NOT NULL |
| status | ENUM | - | {Pending, Processing, Shipped, OutForDelivery, Delivered, Cancelled} |
| paymentId | VARCHAR(50) | FK | References Payment |
| driverId | VARCHAR(50) | FK | References Driver (NULL if not assigned) |
| estimatedDeliveryDate | DATE | - | NULL |
| actualDeliveryDate | DATE | - | NULL |

#### **11. OrderItem**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| orderItemId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| orderId | VARCHAR(50) | FK | References Order |
| productId | VARCHAR(50) | FK | References Product |
| quantity | INT | - | NOT NULL, > 0 |
| unitPrice | DECIMAL(10,2) | - | NOT NULL |
| totalPrice | DECIMAL(10,2) | - | NOT NULL |

#### **12. Payment**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| paymentId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| orderId | VARCHAR(50) | FK | References Order |
| paymentMethod | ENUM | - | {COD, JazzCash, EasyPaisa} |
| amount | DECIMAL(10,2) | - | NOT NULL |
| status | ENUM | - | {Pending, Completed, Failed, Refunded} |
| transactionId | VARCHAR(100) | - | NULL (for online payments) |
| paymentDate | DATETIME | - | NULL |
| invoiceNumber | VARCHAR(50) | - | NULL |

---

### **DELIVERY ENTITY**

#### **13. Driver**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| driverId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| name | VARCHAR(100) | - | NOT NULL |
| phoneNumber | VARCHAR(15) | - | NOT NULL |
| cnic | VARCHAR(20) | - | NOT NULL, UNIQUE |
| vehicleNumber | VARCHAR(20) | - | NOT NULL, UNIQUE |
| city | VARCHAR(50) | - | NOT NULL |
| status | ENUM | - | {Available, OnDelivery, OffDuty} |
| registrationDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

---

### **REVIEW & RATING ENTITIES**

#### **14. Review**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| reviewId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| productId | VARCHAR(50) | FK | References Product |
| customerId | VARCHAR(50) | FK | References Customer |
| rating | INT | - | NOT NULL, RANGE 1-5 |
| comment | TEXT | - | NULL |
| isVerifiedBuyer | BOOLEAN | - | DEFAULT FALSE |
| helpfulCount | INT | - | DEFAULT 0 |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

---

### **WISHLIST ENTITY**

#### **15. Wishlist**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| wishlistId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| customerId | VARCHAR(50) | FK | References Customer |
| productId | VARCHAR(50) | FK | References Product |
| addedDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

---

### **PRICING & ALERTS**

#### **16. Coupon**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| couponId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| couponCode | VARCHAR(50) | - | NOT NULL, UNIQUE |
| discountPercentage | DECIMAL(5,2) | - | NULL |
| discountAmount | DECIMAL(10,2) | - | NULL |
| minimumOrderAmount | DECIMAL(10,2) | - | DEFAULT 0 |
| expiryDate | DATE | - | NOT NULL |
| usageLimit | INT | - | NULL |
| currentUsageCount | INT | - | DEFAULT 0 |
| status | ENUM | - | {Active, Expired, Inactive} |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

#### **17. PriceAlert**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| alertId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| customerId | VARCHAR(50) | FK | References Customer |
| productId | VARCHAR(50) | FK | References Product |
| targetPrice | DECIMAL(10,2) | - | NOT NULL |
| currentPrice | DECIMAL(10,2) | - | NOT NULL |
| status | ENUM | - | {Active, Notified, Expired} |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |
| notifiedDate | DATETIME | - | NULL |

---

### **CUSTOMER SUPPORT ENTITIES**

#### **18. Address**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| addressId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| customerId | VARCHAR(50) | FK | References Customer |
| addressType | ENUM | - | {Home, Office, Other} |
| city | VARCHAR(50) | - | NOT NULL |
| area | VARCHAR(100) | - | NOT NULL |
| fullAddress | TEXT | - | NOT NULL |
| zipCode | VARCHAR(10) | - | NULL |
| isDefault | BOOLEAN | - | DEFAULT FALSE |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

#### **19. LoyaltyPoints**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| loyaltyId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| customerId | VARCHAR(50) | FK | References Customer |
| totalPoints | INT | - | DEFAULT 0, >= 0 |
| usedPoints | INT | - | DEFAULT 0, >= 0 |
| availablePoints | INT | - | DEFAULT 0, >= 0 |
| lastUpdatedDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

#### **20. Notification**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| notificationId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| recipientId | VARCHAR(50) | FK | References User |
| type | ENUM | - | {OrderConfirmation, OrderStatusUpdate, DeliveryAlert, PriceAlert} |
| title | VARCHAR(255) | - | NOT NULL |
| message | TEXT | - | NOT NULL |
| channel | ENUM | - | {Email, SMS, InApp} |
| status | ENUM | - | {Sent, Pending, Failed} |
| sentDate | DATETIME | - | NULL |

#### **21. ElectricityEstimate**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| estimateId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| productId | VARCHAR(50) | FK | References Product |
| dailyUsageHours | DECIMAL(5,2) | - | NOT NULL |
| wattage | INT | - | NOT NULL |
| estimatedMonthlyConsumption | DECIMAL(10,2) | - | CALCULATED |
| estimatedMonthlyCost | DECIMAL(10,2) | - | CALCULATED |
| tariffRate | DECIMAL(10,4) | - | NOT NULL |
| calculationDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

#### **22. Banner**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| bannerId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| title | VARCHAR(255) | - | NOT NULL |
| imageUrl | VARCHAR(255) | - | NOT NULL |
| redirectUrl | VARCHAR(255) | - | NULL |
| displayOrder | INT | - | DEFAULT 0 |
| isActive | BOOLEAN | - | DEFAULT TRUE |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |
| expiryDate | DATE | - | NULL |

#### **23. FAQ**
| Attribute | Type | PK/FK | Constraints |
|-----------|------|-------|-------------|
| faqId | VARCHAR(50) | PK | NOT NULL, UNIQUE |
| question | VARCHAR(500) | - | NOT NULL |
| answer | TEXT | - | NOT NULL |
| category | VARCHAR(100) | - | NULL |
| isActive | BOOLEAN | - | DEFAULT TRUE |
| viewCount | INT | - | DEFAULT 0 |
| createdDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |
| lastUpdatedDate | DATETIME | - | DEFAULT CURRENT_TIMESTAMP |

---

## Relationship Summary

| Relationship | Type | Cardinality | Description |
|--------------|------|-------------|-------------|
| User → Customer | Inheritance | 1:1 | Customer extends User |
| User → Admin | Inheritance | 1:1 | Admin extends User |
| Customer → ShoppingCart | Association | 1:1 | Each customer has one cart |
| Customer → Order | Association | 1:M | Customer can have many orders |
| Customer → Review | Association | 1:M | Customer can write many reviews |
| Customer → Address | Association | 1:M | Customer has multiple addresses |
| Customer → LoyaltyPoints | Association | 1:1 | Each customer has loyalty points |
| Customer → PriceAlert | Association | 1:M | Customer can set multiple price alerts |
| Customer → Wishlist | Association | 1:M | Customer can add items to wishlist |
| ShoppingCart → CartItem | Aggregation | 1:M | Cart contains multiple items |
| Product → CartItem | Association | 1:M | Product can be in many carts |
| Product → OrderItem | Association | 1:M | Product can be in many orders |
| Product → Review | Association | 1:M | Product can have many reviews |
| Product → Brand | Association | M:1 | Many products per brand |
| Product → Category | Association | M:1 | Many products per category |
| Product → Dealer | Association | M:1 | Many products per dealer |
| Order → OrderItem | Aggregation | 1:M | Order contains multiple items |
| Order → Payment | Association | 1:1 | Each order has one payment |
| Order → Driver | Association | M:1 | Many orders assigned to driver |
| Payment → Order | Association | 1:1 | Payment linked to order |
| Brand ↔ Dealer | Association | M:M | Many brands from many dealers |
| Coupon → Order | Association | M:M | Coupon applied to many orders |

---

## Normalization Status

All entities are in **Third Normal Form (3NF)**:

✅ **1NF:** All attributes contain atomic values
✅ **2NF:** No partial dependencies
✅ **3NF:** No transitive dependencies

---

## Key Constraints & Rules

1. **Unique Constraints:**
   - User.email
   - Product.productId
   - Brand.brandName
   - Category.categoryName
   - Dealer.dealerId
   - Driver.cnic, vehicleNumber
   - Coupon.couponCode

2. **Not Null Constraints:**
   - All primary keys
   - User: fullName, email, phoneNumber, password
   - Product: name, price, stockQuantity, categoryId, brandId, dealerId
   - Order: customerId, deliveryAddress, totalAmount, status
   - Payment: orderId, paymentMethod, amount

3. **Check Constraints:**
   - Product.price > 0
   - Product.stockQuantity >= 0
   - Review.rating BETWEEN 1 AND 5
   - Coupon.expiryDate >= CURRENT_DATE
   - LoyaltyPoints: totalPoints, usedPoints, availablePoints >= 0

4. **Foreign Key Constraints:**
   - All FK relationships ON DELETE RESTRICT
   - Soft deletes for Product (hide from storefront, retain in database)

---
