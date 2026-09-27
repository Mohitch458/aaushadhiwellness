# Aaushadhi Wellness

Aaushadhi Wellness is an online storefront for Ayurvedic wellness products. It is built with Next.js and uses Strapi as its product and order-management backend.

Live site: [aaushadhiwellness.in](https://aaushadhiwellness.in/)

## Features

- Browse the product catalog, product details, and featured collections.
- Add products to a persistent cart and proceed through checkout.
- Sign in with email one-time passcode verification.
- Check Indian delivery pincodes and shipping estimates through iCarry.
- Place Cash on Delivery orders and book shipments through iCarry.
- View brand information, contact details, and store policies.

Online payment is not configured. Checkout currently supports Cash on Delivery.

## Tech Stack

- Next.js 16 with the App Router
- React 19 and TypeScript
- Tailwind CSS 4
- Strapi for product, customer, and order data
- Resend for email verification
- iCarry for delivery serviceability, estimates, and shipment booking

## Requirements

- Node.js 20.9 or later
- npm
- A Strapi backend for the live catalog, authentication, and order workflows

The storefront can start without a reachable Strapi instance, but product data will be empty and backend-dependent workflows will not work.

## Local Development

1. Install dependencies:

	```bash
	npm ci
	```

2. Create a `.env.local` file in the project root and set the values described below.

3. Start the development server:

	```bash
	npm run dev
	```

4. Open [http://localhost:3000](http://localhost:3000).

To access the development server from another device on the same network, run:

```bash
npm run dev -- --hostname 0.0.0.0
```

Then open `http://<computer-ip>:3000` on that device.

## Environment Variables

| Variable | Purpose |
| --- | --- |
| `NEXT_PUBLIC_STRAPI_URL` | Strapi base URL. Defaults to `http://localhost:1337`. |
| `STRAPI_API_TOKEN` | Strapi API token used by server-side catalog, customer, and order requests. |
| `RESEND_API_KEY` | Resend API key for email OTP delivery. |
| `RESEND_FROM_EMAIL` | Verified sender address for OTP emails. Defaults to Resend's onboarding address. |
| `SESSION_SECRET` | Secret used to sign sessions. Set a unique, strong value outside local development. |
| `ICARRY_API_USERNAME` | iCarry API username for delivery checks and shipment booking. |
| `ICARRY_API_KEY` | iCarry API key. |
| `WAREHOUSE_PINCODE` | Origin pincode used for delivery estimates. Defaults to `302020`. |
| `ICARRY_PICKUP_ADDRESS_ID` | Pickup address ID from the iCarry account, used when booking shipments. |

Keep `.env.local` and production secrets private. Never commit real credentials to the repository.

## Commands

```bash
npm run dev    # Start the development server
npm run lint   # Run ESLint
npm run build  # Create a production build
npm start      # Serve the production build
```

Run `npm run build` before `npm start`.

## Backend Setup

Configure Strapi with the product, category, customer, OTP session, and order content types used by the app. Provide a server-side API token with the permissions required for those requests. Configure iCarry credentials and a pickup address to enable delivery estimates and shipment booking. Configure Resend with an authorized sender to enable email OTP sign-in.

## Deployment

Deploy as a Node.js Next.js application. Set the environment variables in the hosting provider, make sure the Strapi backend is reachable by the deployed server, then build and start the app with `npm run build` and `npm start` (or use the provider's equivalent Next.js deployment flow).
