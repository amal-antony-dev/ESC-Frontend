# ESC-Frontend

The web app for **[EcoSwapChain](https://github.com/amal-antony-dev/ecoswapchain)**, a recommerce platform where every item is a Solana NFT, payments are held in escrow, and keeping products in use earns SwapCoin rewards.

> **Status:** part of my final-year college project (2025).
>
> Case study: [amal-antony-dev.vercel.app](https://amal-antony-dev.vercel.app/#work/ecoswapchain/overview)

## Part of EcoSwapChain

| Repo | Role |
|---|---|
| [ecoswapchain](https://github.com/amal-antony-dev/ecoswapchain) | Django API, Celery workers, websockets. **Start here for full setup.** |
| **ESC-Frontend** | This repo: React + TypeScript web app |
| [ESC-BlockChain](https://github.com/amal-antony-dev/ESC-BlockChain) | Node.js treasury service on Solana |
| [Sustainability-Prediction](https://github.com/amal-antony-dev/Sustainability-Prediction) | Sustainability-scoring model |

## What's in the app

**For traders**
- Register with an email OTP. A Solana wallet is created in the browser, and its private key is **encrypted client-side with AES-GCM using a key derived from your password (PBKDF2, 100,000 iterations)**, so every on-chain action needs that password.
- Create a listing and mint it as an NFT (Metaplex Token Metadata via Umi), with certifications and a minting animation.
- Browse and buy items, negotiate in a live chat, pay into escrow and track the order through hubs on a map.
- See each item's ownership history, relist owned NFTs, and manage addresses and the SwapCoin wallet.

**For admins**
- Dashboard of NFTs and orders.
- Add shipping hubs on a Leaflet map and connect them with routes.

**For hub managers**
- Log in and verify items arriving at a hub before escrow is released.

## Tech

React 18 · TypeScript · Vite · Material UI · Redux Toolkit · React Router · Axios · Leaflet / React-Leaflet · Recharts · Three.js (react-three-fiber) · Framer Motion · `@solana/web3.js` · `@solana/spl-token` · Metaplex Umi + Token Metadata

## Layout

```
EcoSwapChain/src/
├── BlockChain/      NFT minting and transfer, SwapCoin fee transfer, wallet encryption
├── Components/      Pages by feature: Registration, Login, NFT, Orders, Wallet, Hub, Admin, ShippingPartner, LandingPage
└── Redux/           Store slices and API endpoint config
```

## Run it

```bash
cd EcoSwapChain
npm install
npm run dev        # http://localhost:5173
```

The API base URL is set in `src/Components/API/api.tsx` (`BASE_URL`). Point it at your local Django server, for example `http://localhost:8000/`. The backend, Solana and Pinata setup is in the [ecoswapchain README](https://github.com/amal-antony-dev/ecoswapchain#run-it-locally).

Other scripts: `npm run build` (type-check and build), `npm run lint`, `npm run preview`.
