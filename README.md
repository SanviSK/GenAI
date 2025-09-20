# AI-Powered Marketplace Assistant for Local Artisans

A hackathon-ready MVP web-based marketplace that empowers Indian artisans to showcase their crafts, tell their stories, and sell products online with AI-powered content generation.

## Features

- **Artisan Portal**: Upload products, AI-generated descriptions and storytelling
- **Customer Portal**: Browse products, AI-powered recommendations, order tracking
- **AI Integration**: Google Cloud Vertex AI for content generation in English and Hindi
- **Payment Simulation**: Razorpay sandbox integration
- **Delivery Tracking**: Simulated order progress visualization

## Tech Stack

- **Frontend**: Next.js, React, Tailwind CSS
- **Backend**: Node.js, Express, Firebase/Firestore
- **AI**: Google Cloud Vertex AI
- **Payment**: Razorpay Sandbox
- **Database**: Firestore

## Quick Start

1. **Install dependencies**:
   ```bash
   npm run install:all
   ```

2. **Set up environment variables**:
   - Copy `backend/.env.example` to `backend/.env`
   - Copy `frontend/.env.example` to `frontend/.env.local`
   - Add your Google Cloud and Razorpay credentials

3. **Run the application**:
   ```bash
   npm run dev
   ```

4. **Access the application**:
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:5000

## Project Structure

```
├── frontend/          # Next.js frontend application
├── backend/           # Node.js backend API
├── docs/             # Documentation and setup guides
└── package.json      # Root package.json for scripts
```

## Demo Flow

1. Artisan signs up → uploads product → AI generates description/story
2. Product appears in marketplace
3. Customer browses → adds product to cart → makes test payment
4. Simulated delivery progress displayed
5. Show AI-generated content and storytelling as main differentiator

## Environment Setup

### Google Cloud Setup
1. Create a Google Cloud Project
2. Enable Vertex AI API
3. Create service account and download credentials
4. Set `GOOGLE_APPLICATION_CREDENTIALS` environment variable

### Razorpay Setup
1. Create Razorpay account
2. Get test API keys from dashboard
3. Add keys to environment variables

## Contributing

This is a hackathon project. Feel free to fork and enhance!



