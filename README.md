# Smart India Hackathon Workshop
# Date: 16.10.2026
## Register Number: 212224040189
## Name: MERIL GOLDLINA A
## Problem Title
SIH 1710: Enhancing Navigation for Railway Station Facilities and Locations
## Problem Description
Background: Railway stations are complex environments with numerous facilities and locations such as ticket counters, platforms, restrooms, food courts, and waiting areas. Passengers often face difficulties in navigating these spaces, especially in large or unfamiliar stations. Efficient and user-friendly navigation systems are crucial for improving passenger experience, reducing congestion, and ensuring timely travel connections. Description: The problem involves developing a comprehensive navigation solution for railway stations that assists passengers in locating various facilities and destinations within the station premises. This includes creating detailed maps, providing real-time directions, and integrating features such as accessibility options for individuals with disabilities. The solution should be intuitive, easy to use, and accessible via multiple platforms, including mobile devices and digital kiosks. Key challenges include updating navigation information in real-time, ensuring accuracy, and accommodating the diverse needs of all passengers. Expected Solution: The expected solution is a multi-platform navigation system that provides detailed, real-time directions to all facilities and locations within a railway station. This system should include: A mobile application with 3D interactive maps and step-by-step navigation. Digital kiosks located throughout the station with touch-screen interfaces. Voice-guided navigation for visually impaired passengers. Regular updates to reflect changes in station layout and facility locations. Integration with existing railway apps and services for seamless user experience. The solution should enhance the overall passenger experience by reducing confusion, saving time, and improving accessibility within the station.

## Problem Creater's Organization
Ministry of Railway

## Idea

TrackWay – Intelligent Railway Station Wayfinding Platform

TrackWay is a smart indoor wayfinding platform that helps passengers navigate railway stations using digital floor maps, personalized route recommendations, and location-based guidance.

The system represents a railway station as a connected network of locations and pathways. Passengers can select their destination, identify their starting point using a QR code or manual selection, and receive a route tailored to their navigation needs.

Key Features

* Interactive Maps: Shows platforms, entrances, exits and other station facilities.
* Route Planning: Finds a suitable route from the starting point to the destination.
* Accessibility Support: Helps users find routes using lifts and ramps where mapped and available.
* Voice Guidance: Reads directions aloud for passengers who need audio assistance.
* Multiple Languages: Provides directions in English, Tamil, Hindi and other supported languages.
* QR Code Navigation: Uses QR codes at selected locations to identify the passenger's starting point.
* Facility Updates: Allows authorized staff to update facility details and mark closed pathways.
* Mobile and Kiosk Access: Works through a mobile website or station touchscreen kiosk.
* Offline Maps: Allows users to view previously downloaded maps without an internet connection.
* Future Integration: Can be connected to authorized railway information services in the future.


## Proposed Solution / Architecture Diagram

```
          TRACKWAY: RAILWAY STATION WAYFINDING SYSTEM
                              |
               +--------------+--------------+
               |                             |
        PASSENGER / USER              STATION ADMIN
               |                             |
               v                             v
      +-------------------+        +-------------------+
      | Mobile Web App   |        | Admin Dashboard   |
      | Touchscreen Kiosk|        | Facility Updates   |
      +-------------------+        +-------------------+
               |
               v
      +--------------------------------------+
      |       PRESENTATION LAYER             |
      | Interactive Map | Search | QR Scanner|
      | Language Selection | Accessibility   |
      +--------------------------------------+
                         |
                         v
      +--------------------------------------+
      |       APPLICATION LAYER              |
      |           FastAPI Backend            |
      +--------------------------------------+
                          |
       +-------+----------+----------------+
       |                  |                |
       v                  v                v
+---------------+ +----------------+ +----------------+
| Facility      | | QR Location    | | User Preference|
| Search        | | Detection      | | Management     |
+---------------+ +----------------+ +----------------+
       |                  |                |
       +------------------+----------------+
                          |
                          v
              +--------------------------+
              |     ROUTING ENGINE       |
              |   Dijkstra's Algorithm   |
              +--------------------------+
                          |
                          v
              +--------------------------+
              | Station Pathway Graph    |
              | Accessible Route Rules   |
              +--------------------------+
                          |
                          v
              +--------------------------+
              |      DATA LAYER          |
              | Station Maps & Facilities|
              | Pathways & QR Locations  |
              | Facility Status          |
              +--------------------------+
                          |
                          v
              +--------------------------+
              | Route & Directions       |
              | Voice Guidance           |
              | Offline Map Cache        |
              +--------------------------+
                          |
                          v
              +--------------------------+
              | Highlighted Route and    |
              | Step-by-Step Directions  |
              +--------------------------+
                          |
                          v
                      PASSENGER

```


## Use Cases

| No. | Actor | Scenario | Expected Outcome |
|---|---|---|---|
| 1 | First-time passenger | Needs to reach a particular platform | Receives a highlighted route and directional instructions |
| 2 | Wheelchair user | Needs to reach a platform without using stairs | Receives a route using mapped accessible pathways or a notice when none is available |
| 3 | Visually impaired passenger | Needs to locate a restroom or exit | Receives spoken directions through supported accessibility features |
| 4 | General passenger | Searches for a ticket counter or waiting hall | Finds the facility and receives directions |
| 5 | Passenger unfamiliar with local languages | Selects a preferred interface language | Receives translated navigation instructions where supported |
| 6 | Kiosk visitor | Needs assistance without using a personal smartphone | Uses a touchscreen interface to view directions |
| 7 | Station administrator | A passage becomes unavailable | Updates the pathway status so subsequent route calculations can avoid it |
| 8 | Passenger with limited connectivity | Opens a previously downloaded station map | Views cached map information when offline support is available |
| 9 | Railway operations team | Reviews facility records | Maintains station information through authorized administrative controls |

## Architecture Explanation

1. **Passenger Interface:** Allows users to search for destinations, select accessibility preferences, view maps, and follow navigation instructions.
2. **Backend API:** Processes requests, retrieves facility information, and coordinates route calculations.
3. **Station Map Database:** Stores mapped locations, facility details, pathway connections, and accessibility attributes.
4. **Routing Engine:** Calculates a suitable path between the passenger's starting point and destination using Dijkstra's algorithm.
5. **QR Location Module:** Identifies mapped checkpoints through scanned QR codes and supplies the corresponding location to the routing engine.
6. **Voice Guidance Module:** Converts navigation instructions into spoken directions using supported browser or device capabilities.
7. **Management Dashboard:** Enables authorized personnel to maintain station information and update unavailable facilities or pathways.
8. **Offline Support:** Uses locally cached map data to provide access to previously downloaded station information when connectivity is limited.

## Working Process

1. The passenger opens TrackWay using a mobile browser or station kiosk.
2. The passenger selects the station and identifies their current location.
3. The passenger searches for a platform or facility.
4. The routing engine calculates a path based on available station connections and the selected accessibility preferences.
5. The application displays the route and provides step-by-step directions.
6. Voice guidance can read the directions aloud when enabled.
7. If a pathway is marked unavailable in the station data, the system attempts to calculate an alternative route.
8. Authorized staff maintain facility and pathway information through the management dashboard.
<br>
<img width="1441" height="1092" alt="image" src="https://github.com/user-attachments/assets/2c5cb3bd-9fcf-4678-90fd-d6bd98629e57" />


## Technology Stack

| Layer | Proposed Technology | Purpose |
|---|---|---|
| Frontend | HTML5, CSS3, JavaScript | Develop the passenger interface |
| Interactive maps | SVG-based indoor maps | Display mapped station locations and highlighted routes |
| Progressive Web App | Web App Manifest, Service Worker, Cache API | Support installation and offline caching |
| Backend | Python 3, FastAPI | Provide application APIs |
| API server | Uvicorn | Run the FastAPI application |
| Data validation | Pydantic | Validate API request and response data |
| Routing algorithm | Dijkstra's algorithm | Calculate routes on a weighted station graph |
| Prototype data storage | JSON | Store sample station layouts and pathway connections |
| Production database | PostgreSQL with PostGIS | Store structured facility and spatial information |
| Real-time communication | WebSockets or Server-Sent Events | Support future live updates |
| Voice guidance | Web Speech API | Read navigation instructions aloud where supported |
| Accessibility | ARIA, semantic HTML, keyboard controls | Improve accessibility for assistive technologies |
| QR-code support | Browser camera API and QR-scanning library | Identify mapped station checkpoints |
| Testing | pytest and HTTPX | Test backend functionality and APIs |
| Version control | Git and GitHub | Manage source code and collaboration |
| Deployment | Docker and Docker Compose | Package and run application services |

## Dependencies

### Software Dependencies

- **Python 3:** Required for backend development.
- **FastAPI:** Used to implement REST API endpoints.
- **Uvicorn:** Runs the backend application server.
- **Pydantic:** Validates incoming data and application models.
- **pytest:** Supports automated testing of application functionality.
- **HTTPX:** Enables API testing.
- **HTML, CSS, and JavaScript:** Build the web interface.
- **SVG map assets:** Represent the station layout and navigation paths.
- **Browser APIs:** Provide camera access, caching, network requests, and speech functionality where supported.
- **QR-scanning library:** Decodes location identifiers from station QR codes.

### Data Dependencies

- Digital or manually prepared station floor plans.
- Location records for platforms, entrances, exits, and facilities.
- Pathway connections between mapped locations.
- Accessibility attributes for lifts, ramps, stairs, and corridors.
- QR-code identifiers associated with known locations.
- Verified facility availability and pathway closure information.

### Hardware Dependencies

- A computer for development and testing.
- A smartphone or camera-enabled device for QR scanning.
- A web browser for accessing the application.
- Printed QR codes for demonstration checkpoints.
- An optional touchscreen display and speaker for kiosk demonstrations.

### External Integration Dependencies

- Access to verified railway station maps and facility information.
- Authorized train or platform information services if railway integration is implemented.
- Internet connectivity for live backend requests and updates.
- Suitable hosting infrastructure for a deployed version.
- Optional indoor positioning hardware if continuous positioning is introduced in a future release.

### Operational Dependencies

- Authorized personnel to maintain station maps and facility records.
- Periodic verification of route and accessibility information.
- A process for reporting and confirming temporary pathway closures.
- Translation review to ensure that navigation instructions are clear and accurate.

