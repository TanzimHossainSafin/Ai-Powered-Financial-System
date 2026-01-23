# AI-Powered Financial System

Welcome to the **AI-Powered Financial System**! A comprehensive full-stack financial management platform that combines real-time cryptocurrency tracking, live stock market monitoring, AI-powered financial advisory, and Solana blockchain integration to provide users with intelligent financial insights and management tools.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Configuration](#configuration)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview

The AI-Powered Financial System is a modern web application that empowers users to make informed financial decisions through:

- **Real-time Market Data**: Track cryptocurrency prices and live stock market updates
- **AI Financial Advisor**: Get intelligent financial advice through an AI-powered chatbot
- **Blockchain Integration**: Connect with Solana wallets for cryptocurrency operations
- **Secure Authentication**: JWT-based authentication with password recovery
- **User Profile Management**: Personalized user dashboard and profile settings

This project demonstrates the integration of traditional finance (stocks) with modern cryptocurrency markets, enhanced by artificial intelligence to provide actionable insights.

## Features

### 🔐 Authentication & User Management
- Secure user registration and login with JWT tokens
- Password recovery and reset functionality
- Protected routes and middleware for secure API access
- User profile viewing and updating

### 💰 Cryptocurrency Features
- Real-time cryptocurrency price tracking via CoinRanking API
- Top cryptocurrency identification and monitoring
- Email notifications for cryptocurrency updates
- Solana wallet integration for blockchain transactions
- Airdrop functionality for Solana tokens

### 📈 Stock Market Integration
- Live stock price tracking via WebSocket connection
- Real-time updates for major stocks (AAPL, TSLA, AMZN, MSFT, etc.)
- Market status and volume tracking
- Dynamic stock dashboard with live data visualization

### 🤖 AI-Powered Financial Advisor
- Interactive AI chatbot for financial queries
- Powered by EdenAI workflow integration
- Real-time responses to financial questions
- Contextual financial advice and guidance

### 🎨 Modern User Interface
- Responsive React frontend with Tailwind CSS
- Bootstrap integration for enhanced styling
- Interactive dashboards and data visualization
- Real-time data updates without page refresh

## Technologies Used

### Backend
- **Node.js & Express**: RESTful API server
- **MongoDB & Mongoose**: Database and ODM
- **JWT (jsonwebtoken)**: Authentication tokens
- **bcrypt**: Password hashing and security
- **Zod**: Schema validation
- **Axios**: HTTP client for external APIs
- **Nodemailer**: Email functionality
- **CORS**: Cross-origin resource sharing

### Frontend
- **React 18**: Modern UI library
- **Vite**: Fast build tool and dev server
- **React Router DOM**: Client-side routing
- **Tailwind CSS**: Utility-first CSS framework
- **Bootstrap**: Component styling
- **React Icons**: Icon library
- **Solana Wallet Adapter**: Blockchain wallet integration

### External APIs & Services
- **CoinRanking API**: Cryptocurrency data
- **EOD Historical Data**: Live stock market data via WebSocket
- **EdenAI**: AI-powered chat responses
- **Solana Blockchain**: Cryptocurrency wallet and transactions

## Architecture

```
├── backend/                 # Node.js/Express backend
│   ├── app.js              # Main application entry
│   ├── server.js           # Server configuration
│   ├── config.js           # Configuration management
│   ├── schema.js           # MongoDB schemas
│   ├── router/
│   │   └── userRouter.js   # User API routes
│   └── middleware/
│       └── userMiddleware.js # Authentication middleware
│
└── client/                  # React frontend
    ├── src/
    │   ├── App.jsx         # Main app component
    │   ├── main.jsx        # Application entry point
    │   ├── component/      # React components
    │   │   ├── Home.jsx
    │   │   ├── Login.jsx
    │   │   ├── signup.jsx
    │   │   ├── Chat.jsx    # AI chatbot
    │   │   ├── live-stock.jsx # Stock dashboard
    │   │   ├── userProfile.jsx
    │   │   └── Crypto/     # Cryptocurrency components
    │   │       ├── CoinData.jsx
    │   │       ├── AirDrop.jsx
    │   │       └── solana_Adapter.jsx
    │   └── DashBord/
    │       └── NavBar.jsx
    └── public/             # Static assets
```

## Getting Started

### Prerequisites

Ensure you have the following installed:

- **Node.js** (v16 or higher) - [Download](https://nodejs.org/)
- **npm** or **yarn** package manager
- **MongoDB** (local or Atlas cloud) - [Download](https://www.mongodb.com/)
- **Git** - [Download](https://git-scm.com/)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/TanzimHossainSafin/Ai-Powered-Financial-System.git
   cd Ai-Powered-Financial-System
   ```

2. **Install backend dependencies**
   ```bash
   cd backend
   npm install
   ```

3. **Install frontend dependencies**
   ```bash
   cd ../client
   npm install
   ```

### Configuration

1. **Backend Environment Variables**
   
   Create a `.env` file in the `backend` directory:
   ```env
   MONGO_URL=your_mongodb_connection_string
   JWT_SECRET_User=your_jwt_secret_key
   PORT=8080
   ```

2. **Frontend Environment Variables**
   
   Create a `.env` file in the `client` directory (if needed for additional configurations):
   ```env
   VITE_API_URL=http://localhost:8080
   ```

3. **API Keys Configuration**
   
   Update the following in the respective files:
   - **CoinRanking API**: In `client/src/component/Crypto/CoinData.jsx`
   - **EOD Historical Data**: In `client/src/component/live-stock.jsx`
   - **EdenAI**: In `client/src/component/Chat.jsx`

## Usage

### Starting the Development Servers

1. **Start the backend server**
   ```bash
   cd backend
   npm start
   # or for development with nodemon
   npm run dev
   ```
   Backend will run on `http://localhost:8080`

2. **Start the frontend development server**
   ```bash
   cd client
   npm run dev
   ```
   Frontend will run on `http://localhost:5173` (default Vite port)

3. **Access the application**
   
   Open your browser and navigate to `http://localhost:5173`

### Building for Production

```bash
cd client
npm run build
```

The optimized production build will be in the `client/dist` directory.

## API Endpoints

### Authentication
- `POST /app/v1/user/signup` - Register a new user
- `POST /app/v1/user/signin` - Login user
- `POST /app/v1/user/forgetPassword` - Verify email for password reset
- `PUT /app/v1/user/forgetPassword` - Update password

### User Profile (Protected Routes)
- `GET /app/v1/user/profile` - Get user profile
- `PUT /app/v1/user/profile` - Update user profile

### Cryptocurrency
- `GET /app/v1/user/crypto` - Get top cryptocurrency data (Protected)

### Request/Response Examples

**Sign Up**
```json
POST /app/v1/user/signup
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "SecurePass123!",
  "dateOfBirth": "1990-01-01"
}
```

**Sign In**
```json
POST /app/v1/user/signin
{
  "email": "john@example.com",
  "Password": "SecurePass123!"
}

Response:
{
  "message": "User is SignedIn",
  "auth": true,
  "token": "jwt_token_here"
}
```

## Contributing

Contributions are welcome! If you'd like to contribute to this project, please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/YourFeatureName`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/YourFeatureName`)
5. Open a pull request

Please ensure your code follows the existing code style and includes appropriate tests.

## License

This project is licensed under the [MIT License](LICENSE).

## Contact

For questions, support, or collaboration opportunities, please reach out to:

- **Author**: Tanzim Hossain Safin
- **GitHub**: [TanzimHossainSafin](https://github.com/TanzimHossainSafin)
- **Repository**: [Ai-Powered-Financial-System](https://github.com/TanzimHossainSafin/Ai-Powered-Financial-System)

---

## Acknowledgments

- **CoinRanking** for cryptocurrency data API
- **EOD Historical Data** for real-time stock market data
- **EdenAI** for AI-powered chat functionality
- **Solana Foundation** for blockchain integration capabilities

---

Thank you for using the AI-Powered Financial System! If you find this project helpful, consider giving it a ⭐ on [GitHub](https://github.com/TanzimHossainSafin/Ai-Powered-Financial-System).
