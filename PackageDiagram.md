# Rana Electronics System - Package Diagram

## Overview
The package diagram illustrates the logical organization of the Rana Electronics System into subsystems and packages. It shows dependencies between packages and helps organize the codebase into manageable modules.

## Architecture Layers

```
┌─────────────────────────────────────────────────────────────┐
│                   PRESENTATION LAYER                        │
│                     (Client-Side)                           │
│  HTML5, CSS3, JavaScript, Bootstrap 5, AJAX                │
└─────────────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────────┐
│                  BUSINESS LOGIC LAYER                       │
│                    (Server-Side)                            │
│             PHP 8, Service Classes, DTOs                    │
└─────────────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────────┐
│                   DATA ACCESS LAYER                         │
│              (Database Abstraction)                         │
│          PHP 8 PDO, Repository Pattern, DAOs                │
└─────────────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────────┐
│                    DATABASE LAYER                           │
│                      (MySQL 8.0+)                           │
│           Relational Database Management System             │
└─────────────────────────────────────────────────────────────┘
```

---

## Package Hierarchy

### **1. PRESENTATION LAYER**

#### Package: `UI.Web`
Main package for all web-based user interface components.

**Sub-packages:**

##### **UI.Web.Pages**
Contains all page templates and layouts.

```
UI.Web.Pages
├── HomePage.php
├── ProductListingPage.php
├── ProductDetailPage.php
├── SearchResultsPage.php
├── UserDashboard/
│   ├── ProfilePage.php
│   ├── OrderHistoryPage.php
│   ├── WishlistPage.php
│   └── LoyaltyPointsPage.php
├── Checkout/
│   ├── CartPage.php
│   ├── CheckoutPage.php
│   └── OrderConfirmationPage.php
├── Admin/
│   ├── AdminDashboard.php
│   ├── ProductManagement.php
│   ├── UserManagement.php
│   ├── OrderManagement.php
│   └── ReportsPage.php
├── Auth/
│   ├── LoginPage.php
│   ├── RegistrationPage.php
│   ├── ForgotPasswordPage.php
│   └── PasswordResetPage.php
├── Support/
│   ├── FAQPage.php
│   ├── ContactPage.php
│   └── SupportPage.php
└── Error/
    ├── 404Page.php
    └── ErrorPage.php
```

##### **UI.Web.Components**
Reusable UI components.

```
UI.Web.Components
├── Common/
│   ├── Header.php
│   ├── Footer.php
│   ├── Navbar.php
│   ├── Sidebar.php
│   └── BreadcrumbNavigation.php
├── Product/
│   ├── ProductCard.php
│   ├── ProductImage.php
│   ├── ProductSpecifications.php
│   ├── ProductReviews.php
│   └── RatingDisplay.php
├── Cart/
│   ├── CartSummary.php
│   ├── CartItemRow.php
│   └── ApplyCouponForm.php
├── Order/
│   ├── OrderSummary.php
│   ├── OrderTimeline.php
│   └── OrderStatusBadge.php
└── Form/
    ├── FormGroup.php
    ├── InputField.php
    ├── SelectField.php
    ├── TextAreaField.php
    └── SubmitButton.php
```

##### **UI.Web.Forms**
Form components and validation.

```
UI.Web.Forms
├── LoginForm.php
├── RegistrationForm.php
├── ProfileUpdateForm.php
├── ProductSearchForm.php
├── FilteringForm.php
├── ReviewSubmissionForm.php
├── ContactForm.php
├── AddressForm.php
├── CheckoutForm.php
└── CouponForm.php
```

##### **UI.Web.Assets**
Static assets (CSS, JavaScript, Images).

```
UI.Web.Assets
├── CSS/
│   ├── style.css
│   ├── responsive.css
│   ├── animations.css
│   └── admin.css
├── JavaScript/
│   ├── main.js
│   ├── cart.js
│   ├── search.js
│   ├── validation.js
│   ├── filters.js
│   └── admin.js
└── Images/
    ├── logos/
    ├── icons/
    ├── products/
    └── banners/
```

---

### **2. BUSINESS LOGIC LAYER**

#### Package: `Services`
Core business logic services.

**Sub-packages:**

##### **Services.User**
User and authentication services.

```
Services.User
├── UserAuthenticationService.php
├── UserRegistrationService.php
├── UserProfileService.php
├── PasswordResetService.php
├── UserManagementService.php
├── SessionManagementService.php
└── UserBlockService.php
```

##### **Services.Product**
Product catalog services.

```
Services.Product
├── ProductCatalogService.php
├── ProductSearchService.php
├── ProductFilteringService.php
├── ProductComparisonService.php
├── ProductManagementService.php
├── CategoryManagementService.php
├── BrandManagementService.php
└── ProductImageService.php
```

##### **Services.Order**
Order processing services.

```
Services.Order
├── OrderPlacementService.php
├── OrderTrackingService.php
├── OrderManagementService.php
├── OrderStatusUpdateService.php
├── OrderCancellationService.php
├── InvoiceGenerationService.php
└── OrderHistoryService.php
```

##### **Services.Payment**
Payment processing services.

```
Services.Payment
├── PaymentProcessingService.php
├── CODPaymentService.php
├── JazzCashPaymentService.php
├── EasyPaisaPaymentService.php
├── PaymentValidationService.php
└── RefundService.php
```

##### **Services.Cart**
Shopping cart services.

```
Services.Cart
├── CartManagementService.php
├── CartItemService.php
├── CartCalculationService.php
├── CouponApplicationService.php
├── CouponManagementService.php
└── CartPersistenceService.php
```

##### **Services.Delivery**
Delivery and shipment services.

```
Services.Delivery
├── DriverManagementService.php
├── ShipmentTrackingService.php
├── OrderAssignmentService.php
├── DeliveryStatusService.php
└── DriverLocationService.php
```

##### **Services.Review**
Review and rating services.

```
Services.Review
├── ReviewSubmissionService.php
├── RatingCalculationService.php
├── ReviewManagementService.php
└── ReviewModerationService.php
```

##### **Services.Wishlist**
Wishlist services.

```
Services.Wishlist
├── WishlistManagementService.php
├── WishlistItemService.php
└── WishlistNotificationService.php
```

##### **Services.Dealer**
Dealer management services.

```
Services.Dealer
├── DealerRegistrationService.php
├── DealerManagementService.php
├── DealerSearchService.php
└── DealerStatusService.php
```

##### **Services.Notification**
Notification services.

```
Services.Notification
├── NotificationService.php
├── EmailNotificationService.php
├── SMSNotificationService.php
├── NotificationHistoryService.php
└── NotificationScheduler.php
```

##### **Services.Loyalty**
Loyalty rewards services.

```
Services.Loyalty
├── LoyaltyPointsService.php
├── RewardsCalculationService.php
├── VoucherRedemptionService.php
└── PointsHistoryService.php
```

##### **Services.Feature**
Unique feature services.

```
Services.Feature
├── ElectricityEstimatorService.php
├── PriceAlertService.php
├── SmartBuyingGuideService.php
└── ProductComparisonService.php
```

##### **Services.Reporting**
Reporting and analytics services.

```
Services.Reporting
├── SalesReportService.php
├── ItemReportService.php
├── OrderReportService.php
├── ReportExportService.php
└── DashboardService.php
```

#### Package: `Models`
Domain models and DTOs.

**Sub-packages:**

##### **Models.Entity**
Core business entities.

```
Models.Entity
├── User.php
├── Customer.php
├── Admin.php
├── Product.php
├── Order.php
├── OrderItem.php
├── Payment.php
├── ShoppingCart.php
├── CartItem.php
├── Review.php
├── Wishlist.php
├── Driver.php
├── Dealer.php
├── Coupon.php
├── PriceAlert.php
├── Notification.php
├── LoyaltyPoints.php
├── Address.php
└── Banner.php
```

##### **Models.ValueObjects**
Immutable value objects.

```
Models.ValueObjects
├── Address.php
├── Price.php
├── EmailAddress.php
├── PhoneNumber.php
├── OrderStatus.php
├── PaymentStatus.php
├── ProductSpecifications.php
└── GeolocationCoordinates.php
```

##### **Models.DTO**
Data Transfer Objects.

```
Models.DTO
├── UserDTO.php
├── ProductDTO.php
├── OrderDTO.php
├── ReviewDTO.php
├── CartDTO.php
├── PaymentDTO.php
├── DealerDTO.php
├── DriverDTO.php
└── NotificationDTO.php
```

---

### **3. DATA ACCESS LAYER**

#### Package: `DataAccess`
Database access and persistence layer.

**Sub-packages:**

##### **DataAccess.Repository**
Repository pattern implementations.

```
DataAccess.Repository
├── UserRepository.php
├── ProductRepository.php
├── OrderRepository.php
├── PaymentRepository.php
├── CartRepository.php
├── ReviewRepository.php
├── DriverRepository.php
├── DealerRepository.php
├── CouponRepository.php
├── NotificationRepository.php
├── LoyaltyPointsRepository.php
├── WishlistRepository.php
├── CategoryRepository.php
├── BrandRepository.php
├── PriceAlertRepository.php
├── AddressRepository.php
└── BannerRepository.php
```

##### **DataAccess.Database**
Database connection and query management.

```
DataAccess.Database
├── DatabaseConnection.php
├── DatabaseQueryBuilder.php
├── TransactionManager.php
├── BackupService.php
└── ConnectionPool.php
```

##### **DataAccess.Migration**
Database schema migration.

```
DataAccess.Migration
├── SchemaMigration.php
├── DataMigration.php
└── VersionControl.php
```

---

### **4. UTILITY LAYER**

#### Package: `Utilities`
Helper and utility functions.

**Sub-packages:**

##### **Utilities.Security**
Security-related utilities.

```
Utilities.Security
├── PasswordEncryption.php
├── EncryptionService.php
├── TokenGenerator.php
├── SessionManager.php
├── AuthenticationValidator.php
├── CORSHandler.php
├── CSRFProtection.php
└── JWTHandler.php
```

##### **Utilities.Validation**
Input validation utilities.

```
Utilities.Validation
├── EmailValidator.php
├── PhoneValidator.php
├── PasswordValidator.php
├── FormValidator.php
├── ImageValidator.php
├── InputSanitizer.php
├── URLValidator.php
└── CreditCardValidator.php
```

##### **Utilities.File**
File handling utilities.

```
Utilities.File
├── ImageUploadHandler.php
├── FileProcessor.php
├── DocumentGenerator.php
├── PDFExporter.php
├── CSVExporter.php
└── ImageCompressor.php
```

##### **Utilities.Communication**
Communication utilities (Email, SMS).

```
Utilities.Communication
├── EmailSender.php
├── SMSSender.php
├── SMTPConfigurer.php
├── NotificationScheduler.php
└── MessageTemplate.php
```

##### **Utilities.Logging**
Logging and error handling.

```
Utilities.Logging
├── Logger.php
├── ErrorHandler.php
├── AuditTrail.php
├── ActivityLogger.php
└── ExceptionHandler.php
```

##### **Utilities.Config**
Configuration management.

```
Utilities.Config
├── ConfigurationManager.php
├── EnvironmentConfig.php
├── DatabaseConfig.php
├── EmailConfig.php
├── PaymentGatewayConfig.php
└── AppConfig.php
```

##### **Utilities.Constants**
Application constants.

```
Utilities.Constants
├── ApplicationConstants.php
├── ErrorMessages.php
├── SuccessMessages.php
├── StatusCodes.php
└── PermissionConstants.php
```

##### **Utilities.Helpers**
Helper functions.

```
Utilities.Helpers
├── DateTimeHelper.php
├── StringHelper.php
├── NumberHelper.php
├── ArrayHelper.php
├── CurrencyConverter.php
└── URLHelper.php
```

##### **Utilities.Cache**
Caching utilities.

```
Utilities.Cache
├── CacheManager.php
├── MemoryCache.php
├── SessionCache.php
└── FileCache.php
```

##### **Utilities.Integration**
Third-party integrations.

```
Utilities.Integration
├── JazzCashIntegration.php
├── EasyPaisaIntegration.php
├── WAPDATariffFetcher.php
└── SMSGatewayIntegration.php
```

#### Package: `Middleware`
Middleware components.

```
Middleware
├── AuthenticationMiddleware.php
├── AuthorizationMiddleware.php
├── ValidationMiddleware.php
├── LoggingMiddleware.php
├── CORSMiddleware.php
├── ErrorHandlingMiddleware.php
└── CacheMiddleware.php
```

---

## Package Dependencies

### **Dependency Matrix**

```
PresentationLayer (UI.Web)
    ↓
BusinessLogicLayer (Services, Models)
    ↓
DataAccessLayer (DataAccess)
    ↓
Utilities (Helper functions, config)
```

### **Detailed Dependency Chains**

**1. User Authentication Flow:**
```
UI.Web.Forms.LoginForm
    ↓
Services.User.UserAuthenticationService
    ↓
DataAccess.Repository.UserRepository
    ↓
Utilities.Security.PasswordEncryption
    ↓
DataAccess.Database.DatabaseConnection
```

**2. Product Search Flow:**
```
UI.Web.Pages.ProductListingPage
    ↓
Services.Product.ProductSearchService
    ↓
Services.Product.ProductFilteringService
    ↓
DataAccess.Repository.ProductRepository
    ↓
Utilities.Helpers.StringHelper
    ↓
DataAccess.Database.DatabaseQueryBuilder
```

**3. Order Placement Flow:**
```
UI.Web.Pages.Checkout.CheckoutPage
    ↓
Services.Order.OrderPlacementService
    ↓
Services.Payment.PaymentProcessingService
    ↓
Services.Loyalty.LoyaltyPointsService
    ↓
Services.Notification.EmailNotificationService
    ↓
DataAccess.Repository.OrderRepository
    ↓
Utilities.Communication.EmailSender
```

**4. Admin Report Generation Flow:**
```
UI.Web.Pages.Admin.ReportsPage
    ↓
Services.Reporting.SalesReportService
    ↓
Services.Reporting.ReportExportService
    ↓
DataAccess.Repository.OrderRepository
    ↓
Utilities.File.PDFExporter
    ↓
Utilities.Helpers.DateTimeHelper
```

---

## Cross-Cutting Concerns

### **1. Authentication & Authorization**
```
Middleware.AuthenticationMiddleware
    ↓
Utilities.Security.SessionManager
    ↓
Services.User.UserAuthenticationService
    ↓
Utilities.Security.PasswordEncryption
```

### **2. Validation**
```
UI.Web.Forms.* (Client-side validation via JavaScript)
    ↓
Middleware.ValidationMiddleware
    ↓
Utilities.Validation.*
    ↓
Services.* (Business logic validation)
```

### **3. Error Handling & Logging**
```
Middleware.ErrorHandlingMiddleware
    ↓
Utilities.Logging.ErrorHandler
    ↓
Utilities.Logging.AuditTrail
    ↓
Utilities.Logging.Logger
```

### **4. Notifications**
```
Services.*.* (Any service that triggers notifications)
    ↓
Services.Notification.NotificationService
    ↓
Utilities.Communication.EmailSender
    ↓
Utilities.Communication.SMSSender
```

---

## Package Design Patterns

### **1. Repository Pattern**
Located in: `DataAccess.Repository`
- Abstracts database access
- Enables testing with mock repositories
- Centralizes query logic

### **2. Service Pattern**
Located in: `Services.*`
- Encapsulates business logic
- Reusable across multiple controllers
- Single Responsibility Principle

### **3. Data Transfer Object (DTO)**
Located in: `Models.DTO`
- Decouples API responses from entities
- Reduces over-posting vulnerabilities
- Enables versioning

### **4. Value Object**
Located in: `Models.ValueObjects`
- Immutable objects
- Encapsulates validation logic
- Type safety

### **5. Middleware Pattern**
Located in: `Middleware`
- Cross-cutting concerns
- Pipeline architecture
- Separation of concerns

---

## Technology Stack by Package

| Package | Technology | Purpose |
|---------|-----------|---------|
| UI.Web | HTML5, CSS3, JS, Bootstrap 5 | User interface |
| Services | PHP 8, OOP | Business logic |
| Models | PHP 8 Classes | Domain entities |
| DataAccess | PHP 8 PDO | Database operations |
| Utilities | PHP 8 Libraries | Helper functions |
| Middleware | PHP 8 | Request processing |

---

## File Organization on Disk

```
rana-electronics/
├── public/
│   ├── index.php (Router entry point)
│   ├── assets/
│   │   ├── css/
│   │   ├── js/
│   │   └── images/
│   └── uploads/
│
├── app/
│   ├── Controllers/ (Routes handler)
│   ├── Services/
│   ├── Models/
│   ├── Middleware/
│   └── Utilities/
│
├── src/
│   ├── DataAccess/
│   ├── Database/
│   ├── Views/ (Templates from UI.Web)
│   └── Components/
│
├── config/
│   ├── database.php
│   ├── mail.php
│   ├── app.php
│   └── payment.php
│
├── resources/
│   ├── views/ (UI templates)
│   └── assets/
│
├── storage/
│   ├── logs/
│   ├── cache/
│   └── uploads/
│
├── tests/
│   ├── Unit/
│   ├── Feature/
│   └── Integration/
│
└── vendor/ (Third-party libraries)
```

---

## Integration Points

### **External Systems**

```
┌──────────────────────────────────────────────────────┐
│         Rana Electronics System                      │
│  ┌────────────────────────────────────────────────┐  │
│  │  Utilities.Integration                         │  │
│  └────────────────────────────────────────────────┘  │
└──────────────────┬───────────────────────────────────┘
                   │
     ┌─────────────┼─────────────┬──────────────┐
     ↓             ↓             ↓              ↓
┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐
│JazzCash  │ │EasyPaisa │ │ WAPDA    │ │   SMS    │
│ Payment  │ │ Payment  │ │ Tariff   │ │ Gateway  │
│ Gateway  │ │ Gateway  │ │ Rates    │ │          │
└──────────┘ └──────────┘ └──────────┘ └──────────┘
```

---

