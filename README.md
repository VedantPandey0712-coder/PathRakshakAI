# NagarKon Urban Intelligence

A working prototype of an AI + IoT civic operations platform. It detects issues from citizen or sensor reports, assigns an explainable priority, predicts response urgency, and displays the live city signal in a responsive dashboard.

## Project Links

- GitHub: https://github.com/VedantPandey0712-coder/NagarKonGuard
- Live demo: https://nagar-kon-guard-6m2m-ehn9sfncq-vedantpandey0712-coders-projects.vercel.app
- Local dashboard: http://localhost:3000

## Run

Requires Node.js 18 or newer. No npm install is required.

```powershell
cd main
npm start
```

Open http://localhost:3000.

## Verify

```powershell
npm test
```

## Deploy to Vercel

From the `main` directory, install the Vercel CLI and deploy:

```powershell
npm install -g vercel
vercel login
vercel
```

When prompted, use the current directory as the project root, keep the detected defaults, and run `vercel --prod` for the production deployment. The included `vercel.json` serves `frontend/` as static files and routes `/api/*` to the existing Node backend.

The API currently stores reports in memory. That works for a demo, but data can reset when Vercel creates a new serverless instance. Use a hosted database before relying on this for production data.

## Project map

- `backend/server.js` - HTTP API, in-memory civic issue store, static file server.
- `ai/engine.js` - explainable issue classifier, priority scorer, and risk forecast.
- `iot/simulator.js` - simulated water, air quality, and bin sensors.
- `frontend/` - dashboard and issue intake experience.
- `integration/smoke-test.js` - end-to-end health, AI, forecast, and UI check.

The in-memory store makes the demo immediately runnable. The next production step is replacing it with PostgreSQL/TimescaleDB, connecting MQTT or Azure IoT Hub, and swapping the heuristic engine for a trained model behind a versioned inference API.
