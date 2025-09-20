# AI-Powered Marketplace Assistant - Setup Guide

This guide will help you set up the complete AI-Powered Marketplace Assistant for Local Artisans.

## Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- Google Cloud Platform account
- Firebase project
- Razorpay account (for payments)

## Quick Start

### 1. Clone and Install Dependencies

```bash
# Install root dependencies
npm install

# Install all project dependencies
npm run install:all
```

### 2. Environment Setup

#### Backend Environment Variables

Copy `backend/env.example` to `backend/.env` and fill in your credentials:

```bash
cp backend/env.example backend/.env
```

Required environment variables:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Firebase Configuration
FIREBASE_PROJECT_ID=your-project-id
FIREBASE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\nYOUR_PRIVATE_KEY_HERE\n-----END PRIVATE KEY-----\n"
FIREBASE_CLIENT_EMAIL=your-service-account@your-project-id.iam.gserviceaccount.com

# Google Cloud Vertex AI
GOOGLE_CLOUD_PROJECT_ID=your-project-id
GOOGLE_APPLICATION_CREDENTIALS=path/to/service-account-key.json

# Razorpay Configuration
RAZORPAY_KEY_ID=rzp_test_your_key_id
RAZORPAY_KEY_SECRET=your_key_secret

# JWT Secret
JWT_SECRET=your-super-secret-jwt-key

# CORS Origins
FRONTEND_URL=http://localhost:3000
```

#### Frontend Environment Variables

Copy `frontend/env.local.example` to `frontend/.env.local`:

```bash
cp frontend/env.local.example frontend/.env.local
```

```env
NEXT_PUBLIC_API_URL=http://localhost:5000/api
NEXT_PUBLIC_RAZORPAY_KEY=rzp_test_your_key_id
```

### 3. Google Cloud Setup

1. **Create a Google Cloud Project**
   - Go to [Google Cloud Console](https://console.cloud.google.com/)
   - Create a new project or select existing one

2. **Enable Vertex AI API**
   - Navigate to APIs & Services > Library
   - Search for "Vertex AI API" and enable it

3. **Create Service Account**
   - Go to IAM & Admin > Service Accounts
   - Create a new service account
   - Download the JSON key file
   - Set the path in `GOOGLE_APPLICATION_CREDENTIALS`

4. **Set up Authentication**
   ```bash
   export GOOGLE_APPLICATION_CREDENTIALS="path/to/your/service-account-key.json"
   ```

### 4. Firebase Setup

1. **Create Firebase Project**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Create a new project

2. **Enable Firestore**
   - Go to Firestore Database
   - Create database in production mode
   - Set up security rules (for development, allow all reads/writes)

3. **Get Service Account Key**
   - Go to Project Settings > Service Accounts
   - Generate new private key
   - Use the credentials in your `.env` file

### 5. Razorpay Setup

1. **Create Razorpay Account**
   - Sign up at [Razorpay](https://razorpay.com/)
   - Complete KYC verification

2. **Get API Keys**
   - Go to Settings > API Keys
   - Copy Test Key ID and Secret
   - Add to your `.env` file

### 6. Database Setup

Run the database setup script to create sample data:

```bash
cd backend
node scripts/setup-database.js
```

This will create:
- Sample users (artisans and customers)
- Sample products with AI-generated content
- Sample categories
- Sample orders

### 7. Start the Application

```bash
# Start both frontend and backend
npm run dev
```

Or start them separately:

```bash
# Terminal 1 - Backend
npm run dev:backend

# Terminal 2 - Frontend  
npm run dev:frontend
```

### 8. Access the Application

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:5000
- **API Health Check**: http://localhost:5000/api/health

## Demo Credentials

The setup script creates test users:

### Artisans
- **Email**: priya@example.com
- **Password**: password123
- **Specialty**: Pottery & Ceramics

- **Email**: rajesh@example.com  
- **Password**: password123
- **Specialty**: Textiles & Silk Weaving

### Customers
- **Email**: amit@example.com
- **Password**: password123

- **Email**: sneha@example.com
- **Password**: password123

## Features Overview

### 🎨 Artisan Portal
- Product upload with image support
- AI-generated product descriptions and titles
- Social media content generation
- Order management and tracking
- Sales analytics

### 🛍️ Customer Portal
- Browse products by category
- AI-powered product recommendations
- Shopping cart and checkout
- Order tracking with progress visualization
- Artisan profiles and stories

### 🤖 AI Integration
- Google Cloud Vertex AI for content generation
- Product descriptions in English and Hindi
- Social media captions and hashtags
- Artisan storytelling and biographies
- Customer Q&A chatbot

### 💳 Payment & Delivery
- Razorpay sandbox integration
- Simulated delivery tracking
- Order status updates
- Payment verification

## Project Structure

```
├── backend/                 # Node.js API server
│   ├── routes/             # API endpoints
│   ├── models/             # Database models
│   ├── services/           # Business logic
│   ├── config/            # Configuration files
│   └── scripts/           # Setup and utility scripts
├── frontend/              # Next.js React application
│   ├── app/               # App router pages
│   ├── components/        # Reusable components
│   ├── contexts/          # React contexts
│   └── lib/               # Utilities and API client
└── docs/                  # Documentation
```

## API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/profile` - Get user profile
- `PUT /api/auth/profile` - Update profile

### Products
- `GET /api/products` - Get all products
- `GET /api/products/search` - Search products
- `POST /api/products` - Create product (artisan only)
- `GET /api/products/:id` - Get product details

### Orders
- `GET /api/orders/my-orders` - Get user's orders
- `POST /api/payment/create-order` - Create payment order
- `POST /api/payment/verify-payment` - Verify payment

### AI Services
- `POST /api/ai/generate-product-content` - Generate product content
- `POST /api/ai/generate-artisan-story` - Generate artisan biography
- `POST /api/ai/recommendations` - Get product recommendations

## Troubleshooting

### Common Issues

1. **Firebase Connection Error**
   - Check your Firebase project ID and credentials
   - Ensure Firestore is enabled
   - Verify service account permissions

2. **Google Cloud AI Error**
   - Verify Vertex AI API is enabled
   - Check service account key path
   - Ensure proper authentication

3. **Razorpay Payment Issues**
   - Verify test API keys
   - Check webhook configuration
   - Ensure proper CORS settings

4. **Frontend Build Errors**
   - Clear Next.js cache: `rm -rf .next`
   - Reinstall dependencies: `npm install`
   - Check environment variables

### Development Tips

- Use browser dev tools to inspect API calls
- Check backend logs for detailed error messages
- Use Postman or similar tools to test API endpoints
- Monitor Firebase console for database operations

## Production Deployment

For production deployment:

1. **Environment Variables**
   - Use production Firebase project
   - Set up production Razorpay account
   - Use production Google Cloud credentials

2. **Security**
   - Implement proper Firestore security rules
   - Use environment-specific CORS settings
   - Enable rate limiting and security headers

3. **Performance**
   - Enable image optimization
   - Implement caching strategies
   - Use CDN for static assets

## Support

For issues and questions:
- Check the troubleshooting section
- Review API documentation
- Check Firebase and Google Cloud console logs

## License

This project is created for hackathon purposes. Feel free to use and modify as needed.



