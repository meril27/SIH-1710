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

| No. | User                        | Action                      | Result                             |
| --- | --------------------------- | --------------------------- | ---------------------------------- |
| 1   | Passenger                   | Searches for a platform     | Gets directions                    |
| 2   | Wheelchair user             | Looks for a step-free route | Finds an accessible path           |
| 3   | Visually impaired passenger | Enables voice guidance      | Hears directions                   |
| 4   | Passenger                   | Searches for a facility     | Finds its location                 |
| 5   | Passenger                   | Selects a language          | Gets directions in that language   |
| 6   | Kiosk visitor               | Uses a station kiosk        | Gets directions without a phone    |
| 7   | Station administrator       | Updates facility details    | Information stays updated          |
| 8   | Passenger                   | Opens a downloaded map      | Views the map offline              |
| 9   | Railway operations team     | Reviews station records     | Keeps station information accurate |

<br>
<img width="1536" height="825" alt="TrackWay Railway Wayfinding Use Case Diagram" src="https://github.com/user-attachments/assets/67aeb5aa-98d1-4def-b668-6233626bae38" />


## Technology Stack

| Layer          | Technology             | Purpose                            |
| -------------- | ---------------------- | ---------------------------------- |
| Frontend       | HTML, CSS, JavaScript  | User interface                     |
| Maps           | SVG                    | Display station maps               |
| Backend        | Python, FastAPI        | Process requests                   |
| Server         | Uvicorn                | Run the backend                    |
| Routing        | Dijkstra's Algorithm   | Find routes                        |
| Data Storage   | JSON                   | Store station data                 |
| Database       | PostgreSQL             | Store station information          |
| Voice Guidance | Web Speech API         | Speak directions                   |
| QR Scanning    | Camera API, QR library | Identify locations                 |
| Testing        | pytest, HTTPX          | Test the application               |
| Deployment     | Docker                 | Run the application in a container |



## Dependencies

### Software Dependencies

* Python and FastAPI for the backend.
* HTML, CSS, and JavaScript for the interface.
* Uvicorn to run the server.
* A QR-scanning library to scan QR codes.
* SVG maps to display station layouts.
* pytest and HTTPX for testing.

### Data Dependencies

* Station maps and facility locations.
* Connections between pathways.
* Information about lifts, ramps, and stairs.
* QR codes linked to station locations.
* Updated facility and pathway status.

### Hardware Dependencies

* Computer for development.
* Smartphone or camera-enabled device.
* Web browser.
* Printed QR codes for demonstration.
* Optional touchscreen kiosk and speaker.

### External Dependencies

* Verified railway station maps.
* Internet connection for live updates.
* Authorized railway information services for future integration.
