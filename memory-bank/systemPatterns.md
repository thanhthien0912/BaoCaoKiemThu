# System Patterns: Kiến trúc và Mẫu thiết kế

## Kiến trúc hệ thống tổng thể

### High-level Architecture
```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Android App   │    │   Web Frontend  │    │   NFC Reader    │
│   (Kotlin)      │    │   (React)       │    │   (Hardware)    │
└─────────┬───────┘    └─────────┬───────┘    └─────────┬───────┘
          │           (Student & Admin)                 │                      
          │                      │                      │
          └──────────────────────┼──────────────────────┘
                                 │
                    ┌─────────────▼─────────────┐
                    │      Backend API          │
                    │     (Node.js/Express)     │
                    └─────────────┬─────────────┘
                                 │
                    ┌─────────────▼─────────────┐
                    │      Database             │
                    │       (MongoDB)           │
                    └───────────────────────────┘
```

### Components Architecture

#### Backend Layer
```
Backend/
├── Controllers/          # Xử lý request logic
│   ├── authController.js
│   ├── transactionController.js
│   ├── studentController.js
│   └── adminController.js
├── Models/              # Database schemas
│   ├── User.js
│   ├── Transaction.js
│   ├── Wallet.js
│   └── Session.js
├── Services/            # Business logic
│   ├── authService.js
│   ├── paymentService.js
│   ├── nfcService.js
│   └── emailService.js
├── Middlewares/         # Authentication & validation
│   ├── auth.js
│   ├── validation.js
│   └── errorHandler.js
├── Routes/              # API endpoints
│   ├── authRoutes.js
│   ├── transactionRoutes.js
│   ├── studentRoutes.js
│   └── adminRoutes.js
└── Utils/               # Helper functions
    ├── crypto.js
    ├── logger.js
    └── constants.js
```

#### Mobile App Architecture (Android)
```
Android App/
├── Presentation/
│   ├── Activities/      # Main screens
│   ├── Fragments/       # UI components
│   ├── ViewModels/      # MVVM pattern
│   └── Adapters/        # RecyclerView adapters
├── Domain/
│   ├── UseCases/        # Business logic
│   ├── Models/          # Data models
│   └── Repositories/    # Repository interfaces
├── Data/
│   ├── Repositories/    # Repository implementations
│   ├── DataSource/      # API/Local data sources
│   └── Database/        # Local storage
└── Core/
    ├── Network/         # Retrofit/OkHttp
    ├── NFC/            # NFC handling
    └── Utils/          # Shared utilities
```

#### Web Frontend Architecture (React)
```
Frontend/
├── Components/
│   ├── Common/         # Reusable components
│   ├── Student/        # Student-facing components
│   │   ├── Wallet/
│   │   ├── Transactions/
│   │   └── Profile/
│   ├── Admin/          # Admin components
│   │   ├── Dashboard/
│   │   ├── StudentManagement/
│   │   └── TransactionManagement/
│   └── Auth/           # Authentication components
├── Pages/
│   ├── Student/        # Student pages
│   ├── Admin/          # Admin pages
│   └── Shared/         # Shared pages (Login, etc.)
├── Services/           # API services
├── Store/              # State management (Context/Redux)
├── Hooks/              # Custom hooks
├── Utils/              # Helper functions
└── Assets/             # Static files
```

## Deployment Architecture Patterns (New)

### Cloud Infrastructure
```
User Devices                    Cloud Services
┌─────────────┐              ┌──────────────────┐
│ Web Browser │ ───────────► │ Vercel (Frontend)│
└─────────────┘    HTTPS     │ • React SPA      │
                             │ • Static Assets  │
┌─────────────┐              └─────────┬────────┘
│ Mobile App  │                        │ API Calls
│ (Android)   │ ───────────┐           │ (HTTPS)
└─────────────┘            │           ▼
                           │ ┌──────────────────┐
                           └►│ Railway (Backend)│
                             │ • Node.js API    │
                             │ • Background Jobs│
                             │ • Environment Var│
                             └─────────┬────────┘
                                       │ DB Connection
                                       │ (Secure)
                                       ▼
                             ┌──────────────────┐
                             │ MongoDB Atlas    │
                             │ • Database       │
                             │ • Vector Search  │
                             │ • Backups        │
                             └──────────────────┘
```

### Deployment Automation Patterns
- **Secrets Management**: Sử dụng script `generate-secrets.js` để tạo cryptographically strong keys cho JWT và NFC security.
- **Environment Validation**: Script `check-env.js` tự động kiểm tra sự tồn tại của các biến môi trường bắt buộc trước khi start server.
- **Setup Automation**: `setup-railway.ps1` cung cấp menu interactive để hỗ trợ developers setup môi trường deployment nhanh chóng trên Windows.
- **Git Integration**:
  - Push to `main` triggers Railway deployment (Backend).
  - Push to `main` triggers Vercel deployment (Frontend).

### Production Configuration Patterns
- **CORS Handling**: Strict whitelist cho domain Vercel (`CORS_ORIGIN` env var).
- **HTTPS Enforcement**: Bắt buộc HTTPS cho mọi kết nối API.
- **Secure Cookies**: HttpOnly, Secure flags cho cookies trên production.
- **Error Exposure**: Ẩn stack traces trên production (`NODE_ENV=production`).
- **Health Checks**: `/api/health` endpoint cho monitoring service status.

## Data Flow Patterns

### Authentication Flow
1. **Login**: Client → API → Database → JWT Token
2. **Authorization**: Middleware → Token Validation → Route Access
3. **Session Management**: Token refresh → Logout → Session cleanup

### Payment Flow (NFC)
1. **Initiation**: App → NFC Controller → Backend Validation
2. **Processing**: Payment Service → Database Update → Transaction Record
3. **Confirmation**: Response → App UI → Receipt Generation

### Data Synchronization
- **Real-time updates**: WebSocket connection for live dashboard
- **Offline support**: Local storage with sync when online
- **Conflict resolution**: Last-write-wins strategy

## Security Patterns

### Authentication & Authorization
- **JWT Tokens**: Stateless authentication
- **Role-based Access**: Student vs Admin permissions
- **Session Management**: Token expiration and refresh

### Data Protection
- **Encryption**: Sensitive data encryption at rest
- **HTTPS**: All communications encrypted
- **Input Validation**: Sanitize all user inputs

### API Security
- **Rate Limiting**: Prevent abuse
- **CORS**: Cross-origin restrictions
- **Headers**: Security headers implementation

## Database Patterns

### Schema Design
```
User Collection
- _id: ObjectId
- studentId: String (unique)
- email: String (unique)
- password: String (hashed)
- role: Enum ['student', 'admin']
- profile: Object
- createdAt: Date
- updatedAt: Date

Wallet Collection
- _id: ObjectId
- userId: ObjectId (ref: User)
- balance: Number
- currency: String
- isActive: Boolean
- createdAt: Date
- updatedAt: Date

Transaction Collection
- _id: ObjectId
- userId: ObjectId (ref: User)
- walletId: ObjectId (ref: Wallet)
- type: Enum ['topup', 'payment', 'refund']
- amount: Number
- status: Enum ['pending', 'completed', 'failed']
- description: String
- nfcData: Object (optional)
- createdAt: Date
- updatedAt: Date
```

### Indexing Strategy
- **User**: email (unique), studentId (unique)
- **Wallet**: userId (unique)
- **Transaction**: userId, createdAt, status

## Error Handling Patterns

### Standardized Error Response
```javascript
{
  success: false,
  error: {
    code: "ERROR_CODE",
    message: "Human readable error",
    details: {} // Optional additional context
  }
}
```

### Error Types
- **Validation Errors**: 400 Bad Request
- **Authentication Errors**: 401 Unauthorized
- **Authorization Errors**: 403 Forbidden
- **Not Found Errors**: 404 Not Found
- **Server Errors**: 500 Internal Server Error

## Performance Patterns

### Caching Strategy
- **Redis**: Session storage and frequent data
- **In-memory cache**: Application-level caching
- **Database indexing**: Optimized queries

### API Optimization
- **Pagination**: Large dataset responses
- **Lazy loading**: On-demand data loading
- **Compression**: Response compression

## Monitoring & Logging

### Logging Strategy
- **Structured logging**: JSON format for easy parsing
- **Log levels**: Error, Warn, Info, Debug
- **Request tracing**: Correlation IDs for debugging

### Monitoring
- **Health checks**: Service status monitoring
- **Performance metrics**: Response times, error rates
- **Business metrics**: Transaction volume, success rates

## Extended System Patterns (Updated 26/11/2025)

### POS System Architecture
```
POS System/
├── Models/
│   ├── POSCategory       # 3 categories: BUS, CANTEEN, VENDING_MACHINE
│   ├── POSItem           # Products/services với pricing
│   └── FavoriteTransaction # Quick purchase shortcuts
├── Controllers/
│   └── posController     # CRUD operations và transaction processing
├── Routes/
│   └── /api/pos/*        # RESTful endpoints
└── Mobile UI/
    ├── POSScreen         # Main POS interface
    ├── CategoryScreen    # Category selection
    ├── ConfirmationScreen # Transaction confirmation
    └── FavoritesScreen   # Manage favorites
```

**Data Flow**: Category Selection → Item Selection → Add to Favorites (optional) → Process Transaction → NFC Payment → Confirmation

### Personal Expense System Architecture
```
Personal Expense/
├── Models/
│   ├── PersonalExpense    # INCOME/EXPENSE transactions
│   ├── ExpenseCategory    # 4 categories với icons/colors
│   └── DailyExpenseSummary # Aggregated daily stats
├── Controllers/
│   └── personalExpenseController # Dashboard, stats, calendar
├── Repositories/
│   └── personalExpenseRepository # Complex queries
└── Frontend/
    └── ExpenseTab        # Integrated trong Student Dashboard
        ├── Calendar View
        ├── Statistics Charts
        └── Category Breakdown
```

**Features**:
- Reference number generation (EXP{timestamp}{random})
- Recurring expense support (DAILY, WEEKLY, MONTHLY, YEARLY)
- Location tracking với coordinates
- File attachments support
- Monthly comparison analytics

### AI Chat System Architecture
```
AI Chat/
├── Models/
│   ├── ChatMessage       # Conversation history
│   └── UserSpendingStats # Aggregated data for AI
├── Services/
│   └── aiChatService     # Google Gemini integration
│       ├── Context gathering (User, Wallet, Transactions)
│       ├── Spending analysis
│       ├── Smart recommendations
│       └── Vietnamese conversation
├── Controllers/
│   └── aiChatController  # Message handling với rate limit
└── Frontend/
    └── ChatTab           # Chat interface trong Dashboard
```

**AI Context**:
- Full user profile và wallet info
- Last 30 days transactions
- Category spending breakdown
- Monthly comparisons
- Recent personal expenses

**Rate Limiting**: 20 messages/minute per user

### MoMo Payment Gateway Integration
```
MoMo Integration/
├── Services/
│   ├── momoService           # API calls (create, status)
│   ├── momoWebhookService    # IPN handling
│   └── momoSecurity         # HMAC-SHA256 signature
├── Models/
│   ├── TopupRequest         # Payment requests
│   └── MomoTransactionLog   # Complete audit trail
├── Controllers/
│   └── momoController       # Init payment, check status
└── Webhooks/
    └── /api/webhooks/momo/ipn # Async payment confirmation
```

**Security Patterns**:
- HMAC-SHA256 signature verification
- Idempotency handling via requestId
- Amount normalization (handle VND formats)
- Retry logic with exponential backoff
- Error code mapping

**Payment Flow**:
1. Mobile app → Init payment (POST /api/momo/init)
2. Backend → MoMo API (createPayment)
3. User → MoMo app/web (complete payment)
4. MoMo → Backend webhook (IPN notification)
5. Backend → Update TopupRequest & Wallet
6. Backend → Create Transaction record
7. Mobile → Poll status (GET /api/momo/status/:requestId)

### NFC Card System Patterns
```
Card System/
├── Models/
│   └── Card              # NFC card info
├── Services/
│   └── cardService       # Generate write data với signature
└── Mobile/
    └── WriteCardScreen   # Auto-write flow
        ├── Load user info
        ├── Generate card data (HMAC-SHA256)
        ├── Write NDEF record
        └── Auto-link to account
```

**Security**: HMAC-SHA256 signature với server secret để prevent card forgery

---
*Cập nhật lần cuối: 02/12/2025*