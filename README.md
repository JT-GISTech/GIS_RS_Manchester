# GIS_RS_Manchester


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Leaflet Map with Scroll Panel</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- Leaflet CSS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"/>

    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
        }

        /* Layout container */
        .container {
            display: flex;
            height: 100vh;
        }

        /* Left scrolling panel */
        .sidebar {
            width: 300px;
            padding: 15px;
            background: #f4f4f4;
            overflow-y: scroll; /* THIS makes it scroll */
            border-right: 1px solid #ccc;
        }

        /* Map area */
        #map {
            flex: 1;
            height: 100%;
        }

        h2 {
            margin-top: 0;
        }
    </style>
</head>
<body>

<div class="container">

    <!-- LEFT PANEL -->
    <div class="sidebar">
        <h2>Information Panel</h2>

        <p>This is a scrollable area. You can add lots of content here.</p>

        <!-- Example long content -->
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
        <p>Vestibulum convallis, metus at dignissim viverra...</p>
        <p>Aliquam erat volutpat...</p>
        <p>Phasellus euismod, nibh at varius consequat...</p>
        <p>Integer nec nulla euismod, fermentum lorem vel...</p>

        <!-- repeat to force scrolling -->
        <p>More content...</p>
        <p>More content...</p>
        <p>More content...</p>
        <p>More content...</p>
        <p>More content...</p>
        <p>More content...</p>
        <p>More content...</p>
        <p>More content...</p>
        <p>More content...</p>
    </div>

    <!-- MAP -->
    <div id="map"></div>

</div>

<!-- Leaflet JS -->
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>


</body>
</html>


<script>
    
    const map = L.map('map').setView([53.8, -1.5], 7);

    // Basemap
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '&copy; OpenStreetMap contributors'
    }).addTo(map);

    // Cities with population data (approx. Census 2021)
    const cities = [
        { name: "Manchester", coords: [53.4808, -2.2426], pop: 470405 },
        { name: "Liverpool", coords: [53.4084, -2.9916], pop: 506565 },
        { name: "Leeds", coords: [53.8008, -1.5491], pop: 536280 },
        { name: "Sheffield", coords: [53.3811, -1.4701], pop: 500535 },
        { name: "Newcastle", coords: [54.9783, -1.6178], pop: 286445 },
        { name: "Sunderland", coords: [54.9069, -1.3838], pop: 182966 },
        { name: "Middlesbrough", coords: [54.5742, -1.2348], pop: 174700 },
        { name: "York", coords: [53.9590, -1.0815], pop: 210000 },
        { name: "Hull", coords: [53.7676, -0.3274], pop: 270810 },
        { name: "Bradford", coords: [53.7950, -1.7594], pop: 333950 },
        { name: "Preston", coords: [53.7632, -2.7031], pop: 183362 },
        { name: "Blackpool", coords: [53.8175, -3.0357], pop: 193561 },
        { name: "Carlisle", coords: [54.8925, -2.9329], pop: 108400 }
    ];

    // Helper function to format numbers nicely
    function formatNumber(num) {
        return num.toLocaleString();
    }

    // Add markers with population popup
    cities.forEach(city => {
        L.marker(city.coords)
            .addTo(map)
            .bindPopup(`
                <b>${city.name}</b><br>
                Population: ${formatNumber(city.pop)}
            `);
    });

</script>

