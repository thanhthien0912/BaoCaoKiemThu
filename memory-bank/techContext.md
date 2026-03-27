# Tech Context: Công nghệ, Thiết lập và Ràng buộc

## Stack công nghệ chính

### Backend
- **Runtime**: Node.js (v18+)
- **Framework**: Express.js (v4+)
- **Authentication**: JWT (JSON Web Tokens)
- **Database**: MongoDB (v5+)
- **ODM**: Mongoose
- **AI Integration**: Google Gemini API v1 (gemini-1.5-flash/gemini-pro)
- **Validation**: Joi
- **File Upload**: Multer
- **Email**: Nodemailer
- **Testing**: Jest, Supertest
- **Documentation**: Swagger/OpenAPI

### Frontend Web (Unified App)
- **Framework**: React.js (v18+)
- **Language**: JavaScript (ES6+)
- **State Management**: React Context API / Redux Toolkit
- **Routing**: React Router
- **UI Components**: Material-UI / Ant Design
- **HTTP Client**: Axios
- **Form Handling**: React Hook Form
- **Validation**: Yup
- **Styling**: CSS Modules / Styled Components
- **Testing**: Jest, React Testing Library
- **Build Tool**: Vite

### Mobile App (Flutter - Cross-platform)
- **Framework**: Flutter (v3.2.0+)
- **Language**: Dart (v3.0+)
- **Architecture**: Clean Architecture với MVVM pattern
- **State Management**: hooks_riverpod (v2.4.0+)
- **Routing**: go_router (v12.0+) - Declarative routing
- **HTTP Client**: Dio (v5.3+) với interceptors
- **Storage**: flutter_secure_storage (v9.0+) - Token management
- **NFC**: flutter_nfc_kit (v3.3+) - Host Card Emulation
- **Forms**: flutter_hooks + Form validation
- **Testing**: flutter_test, mockito
- **Build System**: Flutter SDK

### Database
- **Primary**: MongoDB (Atlas cloud hoặc self-hosted)
- **Caching**: Redis (cho sessions và frequent data)
- **File Storage**: AWS S3 / Local storage

### Deployment & DevOps
- **Backend Hosting**: Railway (Start Plan)
- **Frontend Hosting**: Vercel (Hobby Plan)
- **Database**: MongoDB Atlas (M0 Sandbox)
- **CI/CD**: Automatic deployments via Git integration (Railway/Vercel)
- **Automation Scripts**: PowerShell (`.ps1`) và Node.js scripts
- **Environment Management**: `.env` files và Railway/Vercel dashboard variables

### Development Tools
- **Version Control**: Git
- **Code Editor**: Visual Studio Code / Android Studio
- **API Testing**: Postman / Insomnia
- **Database Management**: MongoDB Compass
- **Package Managers**: npm, yarn, Gradle

## Thiết lập môi trường phát triển

### Prerequisites
- **Node.js**: v18.x.x trở lên
- **MongoDB**: v7.x.x trở lên
- **Flutter SDK**: v3.2.0 trở lên
- **Android Studio**: Latest version (cho Android development)
- **Xcode**: Latest version (cho iOS development - macOS only)
- **Git**: Latest version
- **VS Code**: Latest version (với Flutter extensions)

### Environment Variables
```bash
# Backend (.env)
NODE_ENV=development
PORT=3000
MONGODB_URI=mongodb://localhost:27017/student_wallet
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRES_IN=7d
REDIS_URL=redis://localhost:6379

# AI Configuration
GEMINI_API_KEY=your_gemini_api_key
GEMINI_MODEL=gemini-1.5-flash

# Email Configuration
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email@gmail.com
SMTP_PASS=your_app_password

# NFC Configuration
NFC_SECURITY_KEY=your_nfc_security_key

# MoMo Configuration (Sandbox/Production)
MOMO_PARTNER_CODE=your_partner_code
MOMO_ACCESS_KEY=your_access_key
MOMO_SECRET_KEY=your_secret_key
MOMO_REDIRECT_URL=your_redirect_url
MOMO_IPN_URL=your_ipn_url
MOMO_ENDPOINT=https://test-payment.momo.vn  # Sandbox
# MOMO_ENDPOINT=https://payment.momo.vn     # Production
```

### Project Structure
```
student-wallet-platform/
├── backend/                 # Node.js/Express backend
│   ├── src/
│   ├── tests/
│   ├── .env
│   └── package.json
├── frontend/                # React unified app (student + admin)
│   ├── src/
│   ├── public/
│   ├── assets/
│   └── package.json
├── mobile-app/              # Android app
│   ├── app/
│   ├── gradle/
│   └── build.gradle
├── memory-bank/            # Project documentation
├── .gitignore
└── README.md
```

## Dependencies và Packages

### Backend Dependencies
```json
{
  "dependencies": {
    "express": "^4.18.2",
    "mongoose": "^7.5.0",
    "jsonwebtoken": "^9.0.2",
    "bcryptjs": "^2.4.3",
    "joi": "^17.9.2",
    "cors": "^2.8.5",
    "dotenv": "^16.3.1",
    "multer": "^1.4.5-lts.1",
    "nodemailer": "^6.9.4",
    "redis": "^4.6.8",
    "helmet": "^7.0.0",
    "express-rate-limit": "^6.10.0",
    "compression": "^1.7.4",
    "morgan": "^1.10.0"
  },
  "devDependencies": {
    "nodemon": "^3.0.1",
    "jest": "^29.6.2",
    "supertest": "^6.3.3",
    "eslint": "^8.47.0",
    "prettier": "^3.0.2"
  }
}
```

### Frontend Dependencies
```json
{
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.15.0",
    "axios": "^1.4.0",
    "@mui/material": "^5.14.5",
    "@emotion/react": "^11.11.1",
    "@emotion/styled": "^11.11.0",
    "@mui/icons-material": "^5.14.3",
    "react-hook-form": "^7.45.4",
    "yup": "^1.3.0",
    "recharts": "^2.8.0",
    "date-fns": "^2.30.0",
    "react-query": "^3.39.3",
    "@hookform/resolvers": "^3.3.2"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^4.0.3",
    "vite": "^4.4.5",
    "eslint": "^8.47.0",
    "prettier": "^3.0.2"
  }
}
```

### Mobile App Dependencies (pubspec.yaml)
```yaml
dependencies:
  flutter:
    sdk: flutter
  
  # State Management
  hooks_riverpod: ^2.4.0
  flutter_hooks: ^0.20.3
  
  # Routing
  go_router: ^12.0.0
  
  # Networking
  dio: ^5.3.3
  pretty_dio_logger: ^1.3.1
  
  # Storage
  flutter_secure_storage: ^9.0.0
  shared_preferences: ^2.2.2
  
  # NFC
  flutter_nfc_kit: ^3.3.1
  ndef: ^0.3.1
  
  # UI/UX
  flutter_svg: ^2.0.9
  cached_network_image: ^3.3.0
  lottie: ^2.7.0
  
  # Forms & Validation
  formz: ^0.6.1
  
  # Utilities
  intl: ^0.18.1
  url_launcher: ^6.2.1
  
  # Development
  flutter_lints: ^3.0.0

dev_dependencies:
  flutter_test:
    sdk: flutter
  build_runner: ^2.4.6
  riverpod_generator: ^2.3.5
  mockito: ^5.4.2
```

## Ràng buộc kỹ thuật

### Performance Requirements
- **API Response Time**: < 500ms cho 90% requests
- **Mobile App Response**: < 2s cho UI interactions
- **Database Queries**: < 100ms cho common queries
- **Uptime**: 99.5% availability

### Security Requirements
- **Password Hashing**: bcrypt với salt rounds >= 10
- **JWT Expiration**: 7 days cho access tokens
- **HTTPS Required**: Tất cả environments
- **Input Validation**: Tất cả user inputs phải được validate
- **Rate Limiting**: 100 requests/minute per IP

### Data Constraints
- **File Upload Size**: Max 10MB per file
- **Database Connections**: Max 100 concurrent connections
- **API Rate Limit**: 1000 requests/hour per user
- **Transaction Amount**: Min 1,000 VND, Max 10,000,000 VND

### Platform Requirements
- **Android**: API level 24+ (Android 7.0+) - Flutter support
- **iOS**: iOS 12.0+ - Flutter support (ready for deployment)
- **Windows**: Windows 10+ - NFC support for testing
- **Browser**: Chrome 80+, Firefox 75+, Safari 13+, Edge 80+
- **Node.js**: v18.x.x trở lên

## Testing Strategy

### Backend Testing
- **Unit Tests**: Jest cho individual functions
- **Integration Tests**: Supertest cho API endpoints
- **Database Tests**: In-memory MongoDB cho testing
- **Coverage**: Minimum 80% code coverage

### Frontend Testing
- **Unit Tests**: Jest + React Testing Library
- **Component Tests**: Mounting and interaction testing
- **Integration Tests**: API integration testing
- **E2E Tests**: Cypress cho critical user flows

### Mobile Testing (Flutter)
- **Unit Tests**: flutter_test cho Dart code
- **Widget Tests**: flutter_test cho UI components
- **Integration Tests**: integration_test package
- **Mocking**: mockito cho external dependencies
- **NFC Testing**: Physical device testing (Android/iOS)
- **Coverage**: flutter test --coverage

## Deployment Considerations

### Backend Deployment
- **Platform**: Node.js trên Linux server
- **Process Manager**: PM2 cho production
- **Reverse Proxy**: Nginx cho load balancing
- **SSL**: Let's Encrypt certificates

### Database Deployment
- **MongoDB Atlas**: Recommended cho production
- **Backup Strategy**: Daily backups with retention
- **Monitoring**: MongoDB Atlas monitoring
- **Security**: Network access control và encryption

### Mobile App Deployment (Flutter)
- **Android**:
  - Play Store distribution
  - Beta testing via Google Play Beta tracks
  - Code signing với keystore (release/debug)
  - Build command: `flutter build apk --release`
- **iOS** (Future):
  - App Store distribution
  - TestFlight for beta testing
  - Code signing với Apple certificates
  - Build command: `flutter build ios --release`
- **Version Management**: Semantic versioning (pubspec.yaml)

## Monitoring và Logging

### Application Monitoring
- **Health Checks**: Endpoint /health cho monitoring
- **Error Tracking**: Error reporting dashboard
- **Performance Monitoring**: Response time tracking
- **Business Metrics**: Transaction volume tracking

### Logging Strategy
- **Structured Logging**: JSON format logs
- **Log Levels**: Error, Warn, Info, Debug
- **Log Rotation**: Daily rotation with retention
- **Centralized Logging**: ELK stack (Elasticsearch, Logstash, Kibana)

---
*Cập nhật lần cuối: 02/12/2025*