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

## Complete Package Structure

### **Layer 1: PRESENTATION (UI.Web)**
- **Pages** (28 files): All page templates
- **Components** (15 files): Reusable UI components
- **Forms** (10 files): Form implementations
- **Assets** (CSS, JS, Images)

### **Layer 2: BUSINESS LOGIC (Services & Models)**
- **Services** (16 sub-packages, 80+ files): All business services
- **Models.Entity** (24 entity classes)
- **Models.DTO** (9 data transfer objects)
- **Models.ValueObjects** (8 value object classes)

### **Layer 3: DATA ACCESS (DataAccess)**
- **Repository** (16 repository classes)
- **Database** (5 connection manager classes)
- **Migration** (3 migration classes)

### **Layer 4: UTILITIES**
- **Security** (8 security classes)
- **Validation** (8 validation classes)
- **File** (6 file handling classes)
- **Communication** (5 communication classes)
- **Logging** (5 logging classes)
- **Config** (6 configuration classes)
- **Constants** (5 constant files)
- **Helpers** (6 helper classes)
- **Cache** (4 cache classes)
- **Integration** (4 integration classes)
- **Middleware** (7 middleware classes)

---

## Dependency Flow

```
UI.Web (Presentation)
    ↓ depends on
Services.* (Business Logic)
    ↓ depends on
DataAccess.Repository (Data Access)
    ↓ depends on
Utilities.* (Helper Layer)

All Layers depend on:
- Utilities.Security (Authentication, Encryption)
- Utilities.Validation (Input validation)
- Utilities.Logging (Error handling)
```

---

## Key Service Dependencies

### **User Authentication:**
```
LoginForm → UserAuthenticationService → UserRepository
         → PasswordEncryption (Utilities.Security)
         → SessionManager (Utilities.Security)
```

### **Product Search:**
```
ProductListingPage → ProductSearchService → ProductRepository
                  → ProductFilteringService
                  → StringHelper (Utilities.Helpers)
```

### **Order Processing:**
```
CheckoutPage → OrderPlacementService → OrderRepository
            → PaymentProcessingService → PaymentRepository
            → LoyaltyPointsService
            → NotificationService → EmailSender (Utilities.Communication)
            → InvoiceGenerationService → PDFExporter (Utilities.File)
```

### **Report Generation:**
```
ReportsPage → SalesReportService → OrderRepository
           → ReportExportService → PDFExporter
           → DateTimeHelper (Utilities.Helpers)
```

---

## Cross-Cutting Concerns

1. **Authentication & Authorization:**
   - Middleware.AuthenticationMiddleware
   - Utilities.Security.SessionManager
   - Services.User.UserAuthenticationService

2. **Validation:**
   - UI.Web.Forms (Client-side via JavaScript)
   - Middleware.ValidationMiddleware
   - Utilities.Validation.*
   - Services.* (Business logic validation)

3. **Error Handling & Logging:**
   - Middleware.ErrorHandlingMiddleware
   - Utilities.Logging.ErrorHandler
   - Utilities.Logging.AuditTrail

4. **Notifications:**
   - Services.Notification.NotificationService
   - Utilities.Communication.EmailSender
   - Utilities.Communication.SMSSender

---

## Technology Stack Summary

| Layer | Technology | Count |
|-------|-----------|-------|
| Presentation | HTML5, CSS3, JavaScript, Bootstrap 5 | 53 files |
| Business Logic | PHP 8 Services & Models | 111 files |
| Data Access | PHP 8 PDO, Repository Pattern | 24 files |
| Utilities | PHP 8 Helpers & Libraries | 68 files |
| Middleware | PHP 8 Pipeline Processing | 7 files |
| **TOTAL** | | **~263 files** |

---

## Integration Points

```
┌─────────────────────────────────────────────────────┐
│    Rana Electronics System                          │
│    ┌─────────────────────────────────────────────┐  │
│    │ Utilities.Integration                       │  │
│    └─────────────────────────────────────────────┘  │
└──────────────────┬────────────────────────────────┬─┘
                   │                                │
        ┌──────────┼──────────────┬──────────────┐ │
        ↓          ↓              ↓              ↓ ↓
    ┌────────┐ ┌────────┐ ┌────────┐ ┌──────────┐
    │JazzCash│ │EasyPaisa Payment  │ WAPDA    │ SMS Gateway
    │        │ │Gateway             │ Tariff   │ (Twilio/etc)
    └────────┘ └────────┘ └────────┘ └──────────┘
```

---