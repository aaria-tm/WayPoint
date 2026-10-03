WayPoint
WayPoint is a single-file front-end web application that simulates a dynamic, multi-modal transit network connecting five major Indian hubs: Mumbai, Pune, Delhi, Jaipur, and Bangalore. Built with HTML, Tailwind CSS, raw JavaScript, and Leaflet.js, it avoids backend dependencies by computing complex graph traversals and temporal routing logic entirely in the browser.

Why This Project Was Made
This project was built to transition Data Structures and Algorithms (DSA) from abstract concepts into a visual, interactive utility. Standard routing apps hide their logic behind black-box APIs; WayPoint exposes the underlying Graph Theory. It was designed to handle real-world edge cases that standard Dijkstra implementations ignore, such as temporal road closures, multi-leg transit layovers, and route-specific fuel filtering.

How This Helps
Algorithmic Route Comparison: Users don't just see a line on a map; they get dynamically computed travel times based on mode-specific speeds (e.g., Trains at 85 km/h vs. Buses at 55 km/h), alongside exact toll and fuel cost estimations calculated at 13-14 km/l.

Realistic Transit Logic: It generates authentic travel itineraries. If a user travels from Bangalore to Delhi via train, the system calculates a multi-leg journey, factoring in Leg 1 (e.g., Udyan Express), a specific platform layover duration at a transfer hub (Mumbai Central), and Leg 2 (e.g., Rajdhani Express), complete with itemized fares.

Smart Corridor Infrastructure: Instead of plotting every gas station in the country, the application filters an array of 22 geo-coded infrastructure points (Tata Power EV chargers, MGL CNG, BPCL Petrol) checking if they belong strictly to the vertices of the active computed route.

Core DSA Features Implemented
1. Adjacency List (Graph Representation)
Implementation: The transport network is modeled as an undirected, weighted graph. The 5 cities act as Vertices (V), and the highway/rail corridors (e.g., NE-4 Expressway, Golden Quadrilateral) act as Edges (E).

Specificity: It is stored as a JavaScript Object (Hash Map) mapping each city to an array of its neighbors. This Adjacency List ensures efficient O(V + E) memory usage and traversal compared to a rigid Adjacency Matrix.

2. Dijkstra's Shortest Path Algorithm
Implementation: When a user selects an Origin and Destination, a custom JavaScript implementation of Dijkstra's algorithm computes the most efficient path.

Specificity: It explores the graph by accumulating edge weights (physical distance in km). Once the target node is reached, it backtracks using a prev pointer map to construct the exact sequence of cities and highway waypoints to display on the Leaflet map.

3. Priority Queue Simulation
Implementation: To optimize Dijkstra's node exploration, the application utilizes a dynamically sorted array that mimics a Min-Heap Priority Queue.

Specificity: At each step, it sorts the unvisited nodes by their current shortest accumulated distance. This ensures the algorithm always explores the mathematically most promising corridor next, guaranteeing optimal path discovery.

4. Temporal Graph Routing (Dynamic Edge Masking)
Implementation: Graph topology adapts at runtime based on external temporal state (the user's <input type="date">).

Specificity: The Mumbai-Pune Expressway is programmed with a hardcoded maintenance closure until October 10, 2026. If the user selects a date on or before October 10, the algorithm programmatically severs the primary 148km edge by assigning it an infinite weight. Dijkstra automatically recalculates and forces the route through the 155km Old NH-48 alternate path (via Khandala Ghat), updating the timeline and travel duration accordingly.

5. Constant-Time O(1) Hash Map Lookups
Implementation: Retrieval of complex, multi-variable transit schedules is optimized using composite dictionary keys.

Specificity: Instead of using O(N) loops to search through arrays of train schedules, the system generates a composite string key (e.g., "Bangalore-Jaipur") from the calculated graph endpoints. This allows instantaneous O(1) retrieval of authentic carrier names, multi-leg transfer logic, and base pricing.

Technical Stack
Frontend Environment: HTML5, standard DOM JavaScript (Zero build tools required)

Styling Framework: Tailwind CSS (via CDN)

Geospatial Rendering: Leaflet.js

Map Tile Provider: Mapbox API (Public Token integration)

How to Run
Clone the repository or download the index.html file.

Ensure you have an active internet connection to load the external CDNs (Tailwind, Leaflet, Mapbox).

Open the index.html file directly in any modern web browser. The application runs entirely client-side.
