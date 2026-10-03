#WayPoint
WayPoint is a front-end web application that simulates a multi-modal, inter-city transport network. Built entirely in a single file using HTML, Tailwind CSS, raw JavaScript, and Leaflet.js, it leverages core computer science concepts to solve real-world routing and urban mobility challenges.

Why This Project Was Made
This project was developed to bridge the gap between theoretical computer science and practical software engineering. The primary goal was to apply Data Structures and Algorithms (DSA) -- specifically Graph Theory and Shortest Path algorithms -- to a real-world scenario: intelligent urban mobility.

Instead of building a standard CRUD application, this project focuses on algorithmic logic, dynamic state management, and geospatial mapping. It serves as a robust demonstration of how complex data relationships (cities, highways, tolls, transit schedules, and roadside amenities) can be efficiently processed and visualized in the browser without relying on a heavy backend server.

How This Helps
For Travelers and Commuters: It provides a unified dashboard to compare travel modes (Car, Bus, Train). By generating realistic schedules, calculating multi-leg train transfers, and detailing explicit highway layovers, users get a comprehensive view of their journey's time and financial cost.

For EV and Alternative Fuel Drivers: The system dynamically filters and plots verified EV Superchargers, CNG stations, and Petrol pumps strictly along the user's computed route, eliminating range anxiety for inter-city travel.

For Urban Infrastructure Planning: By simulating real-world disruptions (such as the scheduled maintenance closure of the Mumbai-Pune Expressway), the application demonstrates how a network automatically reroutes traffic to alternative corridors (like the Old NH-48), allowing planners to visualize the impact of infrastructure bottlenecks.

Core DSA Features Implemented
1. Graph Data Structure (Adjacency List)
Concept: The map is modeled as an undirected weighted graph where vertices are cities and edges are the connecting highways or rail lines.

Implementation:

Vertices: Cities (Mumbai, Pune, Delhi, Jaipur, Bangalore) act as nodes, storing geographic coordinates.

Edges: The routes connecting the cities. Edges store multiple weights, including physical distance, toll costs, and transit mode constraints.

Storage: Represented in JavaScript using an Adjacency List (Hash Map), which allows for highly efficient traversal compared to an adjacency matrix.

2. Dijkstra's Shortest Path Algorithm
Concept: A greedy algorithm that finds the shortest path between a starting node and all other nodes in a weighted graph.

Implementation: When a user selects an Origin and Destination, the system runs a custom implementation of Dijkstra's algorithm. It explores the graph, constantly updating the minimum known distance to each city. Once the destination is reached, the algorithm backtracks using a pointer map to reconstruct the exact optimal path.

3. Priority Queue (Min-Heap Simulation)
Concept: An abstract data type used to efficiently retrieve the element with the highest priority (in this case, the lowest travel distance).

Implementation: During the execution of Dijkstra's algorithm, a dynamic array sorted at each insertion mimics a Priority Queue. This ensures the algorithm always explores the most promising (shortest) highway corridor next, minimizing unnecessary computations.

4. Dynamic Edge Masking (Temporal Graphs)
Concept: Modifying graph topology at runtime based on external temporal conditions.

Implementation: The algorithm evaluates the user's selected travel date. If the date falls on or before a specific cutoff (October 10), the primary Expressway edge is programmatically severed (masked) with an infinite weight. The algorithm automatically falls back to calculating the next best path (the Old Highway corridor), simulating real-time road closure rerouting.

5. Hash Maps for Constant Time Lookups
Concept: Using key-value pairs for O(1) time complexity data retrieval.

Implementation: Multi-leg train transfers, bus operator details, and city coordinates are stored in nested dictionaries. When generating transit schedules, the system generates a composite key (e.g., "Bangalore-Jaipur") to instantly fetch leg-by-leg train data, layover durations, and station names without needing to iterate through heavy arrays.

Technical Stack
Frontend: HTML5, standard DOM JavaScript

Styling: Tailwind CSS (via CDN) with native Dark Mode support

Geospatial Mapping: Leaflet.js

Map Tiles: Mapbox API

Icons: FontAwesome 6

How to Run
Clone the repository or download the index.html file.

Ensure you have an active internet connection (required to fetch the Tailwind, Leaflet, and Mapbox assets).

Open the index.html file directly in any modern web browser.
