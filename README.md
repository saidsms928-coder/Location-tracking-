# Mfumo wa Kuhifadhi Location (Location Tracking System)

## Description
A secure web application for tracking and storing user location data with proper permission handling. Built with Node.js and Express, this application captures GPS coordinates and stores them server-side for authorized users only.

## Features
- 🌍 Real-time geolocation tracking
- ✅ User permission-based location requests
- 💾 Server-side location data storage
- 🔒 Secure data handling
- 📱 Responsive mobile-friendly interface
- 🇸🇿 Swahili language interface

## Prerequisites
- Node.js (v14 or higher)
- npm (Node Package Manager)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/saidsms928-coder/Location-tracking-.git
cd Location-tracking-
```

2. Install dependencies:
```bash
npm install
```

3. Start the server:
```bash
npm start
```

The server will run on `http://localhost:3000` (or your configured PORT)

## Usage

1. Open your browser and navigate to `http://localhost:3000`
2. Click the "Ruhusu na Endelea" (Allow and Continue) button
3. Grant location permission when prompted
4. Your location will be saved to `locations.txt`

## Project Structure

- `server.js` - Express server and API endpoints
- `index.html` - Frontend interface with geolocation request
- `locations.txt` - File where location data is stored (auto-created)
- `package.json` - Project dependencies and scripts

## API Endpoints

### POST `/api/save-location`
Saves user location data to the server.

**Request Body:**
```json
{
  "latitude": 37.7749,
  "longitude": -122.4194,
  "timestamp": 1625097600000
}
```

**Success Response:**
```json
{
  "status": "success",
  "message": "Location imepokelewa vizuri."
}
```

## Technologies Used
- **Backend:** Node.js, Express.js
- **Frontend:** HTML5, CSS3, JavaScript
- **API:** RESTful with Geolocation API
- **Storage:** File-based (locations.txt)

## Security Note
This is a basic implementation. For production use, consider:
- Adding authentication/authorization
- Using a database instead of file storage
- Implementing HTTPS
- Adding rate limiting
- Implementing proper error handling

## License
MIT

## Author
saidsms928-coder

---

**Note:** This is the developer's first web project. Contributions and feedback are welcome!
