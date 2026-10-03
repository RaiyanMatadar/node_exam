# Event Slot Booker

This project is a small Node.js + Express + MongoDB API for creating event slots and checking their availability.

The screenshots show a Postman flow for:
- creating a slot with `POST /api/slots`
- retrieving slot status with `GET /api/slots`

## Tech stack
- Node.js
- Express.js
- MongoDB + Mongoose

## Project structure
- `server.js` — bootstrap entry file
- `src/server.js` — starts the API
- `src/routes/` — API endpoints
- `src/controllers/` — request logic
- `src/models/` — MongoDB schemas
- `src/config/db.js` — database connection

## Setup
1. Install Node.js and MongoDB.
2. Open the project folder.
3. Install dependencies:

```bash
npm install
```

4. Make sure MongoDB is running locally on:

```env
MONGO_URI=mongodb://127.0.0.1:27017/eventSlotBooker
PORT=5000
```

5. Start the app:

```bash
npm start
```

Or in development mode:

```bash
npm run dev
```

## Test the API
### 1) Check server is running
```bash
curl http://localhost:5000/
```

Expected response:
```json
{ "message": "Event Slot Booker API is running" }
```

### 2) Create a slot
`POST http://localhost:5000/api/slots`

Request body:
```json
{
  "eventName": "JavaScript Workshop",
  "date": "2026-10-10",
  "startTime": "10:00 AM",
  "endTime": "12:00 PM",
  "location": "Computer Lab 1",
  "capacity": 3
}
```

### 3) Get all slots
```bash
curl http://localhost:5000/api/slots
```

### 4) Get one slot by ID
```bash
curl http://localhost:5000/api/slots/:id
```

## Notes
- `availableSeats` is calculated from slot capacity and booked seats.
- The app is a backend API only; there is no frontend interface in this project.
