# Pos Let's Salaya - Web Frontend

A point-of-sale (POS) system for restaurants/cafes built with Next.js and MongoDB.

## Project Overview

This system provides both frontend (customer-facing) and backend (admin) interfaces:

- **Frontend**: Order processing on tablet devices
- **Backend**: Inventory management, reporting, and settings

## Key Features

- **Product Management**: Add, edit, remove products and manage inventory
- **Automatic Inventory**: Inventory updates automatically with sales
- **Fixed Pricing**: Prices are locked in the system to prevent manual entry errors
- **Order Routing**: Orders automatically sent to different destinations based on product type
  - Drinks → Counter
  - Food → Kitchen
- **Secure Access**: PIN-based authentication for staff
- **Receipt Printing**: Automatic receipt printing with orders

## Project Structure

```
├── app/                    # Next.js App Router
│   ├── api/                # API routes
│   ├── admin/              # Admin/Backend pages
│   │   ├── inventory/      # Product/inventory management
│   │   ├── reports/        # Sales reports
│   │   └── settings/       # System settings
│   ├── pos/                # POS/Frontend pages
│   │   ├── menu/           # Menu selection
│   │   ├── cart/           # Order processing
│   │   ├── checkout/       # Payment processing
│   │   └── receipt/        # Receipt view
│   └── auth/               # Authentication pages
├── components/             # Reusable UI components
│   ├── admin/              # Admin-specific components
│   ├── pos/                # POS-specific components
│   ├── layout/             # Layout components
│   └── ui/                 # Generic UI components
├── lib/                    # Shared utilities and libraries
│   ├── db/                 # MongoDB connection and utilities
│   ├── auth/               # Authentication utilities
│   ├── api/                # API client functions
│   └── utils/              # Helper functions
├── models/                 # MongoDB models
├── public/                 # Static assets
└── styles/                 # Global styles
```

## Database Schema

**Products**
- `_id`: ObjectId
- `name`: String
- `price`: Number
- `category`: String
- `type`: String (food/drink)
- `imageUrl`: String
- `quantity`: Number
- `isActive`: Boolean

**Orders**
- `_id`: ObjectId
- `orderNumber`: String
- `items`: Array of OrderItems
- `totalAmount`: Number
- `status`: String
- `destination`: String (counter/kitchen)
- `createdAt`: Date
- `completedAt`: Date

**Users**
- `_id`: ObjectId
- `name`: String
- `pin`: String (hashed)
- `role`: String
- `isActive`: Boolean

## Getting Started

First, install dependencies:

```bash
npm install
# or
yarn install
```

Then, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the application.

## Environment Variables

Create a `.env.local` file with:

```
MONGODB_URI=your_mongodb_connection_string
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=your_auth_secret
```

## Technologies

- Next.js (Frontend/Backend)
- MongoDB (Database)
- NextAuth.js (Authentication)
- Tailwind CSS (Styling)
- React Printing (Receipt printing)

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
