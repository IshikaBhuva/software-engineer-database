DEVELOPMENT DOCUMENTATION: SIMPLE STUDY GROUP FINDER

1. SYSTEM ARCHITECTURE
The application follows a classic Client-Server architecture designed for scalability and clear separation of concerns.
- Frontend: Single Page Application (SPA) built using HTML5, CSS3 (Flexbox/Grid), and Vanilla JavaScript.
- Backend: RESTful API server built with Node.js and the Express.js framework.
- Data Management: In-memory data structures (JavaScript arrays) used for rapid prototyping and state management without the overhead of a formal database engine.

2. TECH STACK & DEPENDENCIES
- Runtime: Node.js
- Framework: Express.js (v4.18.2+)
- Middleware: 
    * cors: Enables Cross-Origin Resource Sharing for frontend-backend communication.
    * body-parser: Parses incoming request bodies (JSON).
- Frontend: CSS Custom Properties (Variables) for theming, DOM API for dynamic UI updates, and Fetch API for backend integration.

3. BACKEND IMPLEMENTATION (server.js)
The server manages state for two primary entities: 'users' and 'groups'.

Key API Endpoints:
- POST /login: Initializes user profiles and session data.
- GET /groups: Returns the list of available study groups.
- POST /groups: Allows users to create new study groups (uses unshift to prioritize new content).
- POST /groups/join: Implements logic for group participation.
- POST /course: Adds academic courses to a user's profile.
- POST /course/remove: Removes courses from the profile.

Server-Side Logic & Validation:
- Group ID Generation: Uses Date.now() for unique identifiers.
- Join Validation: Includes checks to prevent duplicate joins and enforces group capacity limits.
- Static Routing: Serves the frontend files directly using express.static.

4. FRONTEND DEVELOPMENT (index.html/JS)
The frontend is built as a responsive dashboard with a sidebar-based navigation system.

Key Components:
- State Management: A central 'app' object in JavaScript manages the local user state, synchronized with the backend via async/await fetch calls.
- Dynamic Rendering: Functions (renderDiscover, renderMyGroups, updateCourseUI) programmatically generate HTML elements based on the current application state.
- Tab Switching: A lightweight system to toggle visibility between 'Discover', 'My Groups', and 'Chats' views without page reloads.
- UI/UX Design: Implements a modern design system using CSS variables, featuring modals for group creation and a simulated real-time messaging interface.

5. DATA STRUCTURE SAMPLES
- Group Object: { id, name, course, desc, members, limit }
- User Object: { id, name, uni, courses: [], joinedGroups: [] }

6. DEVELOPMENT WORKFLOW
The project is structured for easy deployment:
1. Environment setup via 'npm install' to fetch dependencies listed in package.json.
2. Execution via 'npm start' which triggers 'node server.js'.
3. The server defaults to PORT 3000, handling both API requests and frontend delivery.
