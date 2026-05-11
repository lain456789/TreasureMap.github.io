Vibe Coding Prompts: XJTLU Playful Treasure Map

### Step 1: The Vibe & UI Shell (Cyberpunk & Glassmorphism)
You are an expert Front-End Engineer. I want to build a single-file HTML web application called "XJTLU Playful Map for Study Abroad".

**Tech Stack**: Pure HTML5, CSS3, Vanilla JavaScript. Use the Leaflet.js CDN for mapping.

**Design System (The Vibe)**:
1. The overall aesthetic should be "Playful Dark/Cyberpunk". Use a dark background (e.g., `#1a1a2e`) with neon cyan (`#00ffcc`) and orange (`#ff9e00`) accents.
2. **UI Layout**:
   - A full-screen map container (`#map`) taking up 100vh and 100vw.
   - A floating information panel (`#info-panel`) absolutely positioned in the top-right corner. It should feature glassmorphism (`backdrop-filter: blur(10px)`), a semi-transparent dark background, and a neon cyan glowing border (`box-shadow`).
3. **Panel Content**:
   - A header for the university name.
   - A stats container with boxes for "QS World Ranking" and "XJTLU Admission Requirements (GPA/IELTS)".
   - A specific text area for a "Fun Fact / Alumni Comment" highlighted in italic orange.
   - A loading text indicator (e.g., "AI is searching... 🔮") with a CSS `pulse` animation.

Please generate the HTML skeleton and all the CSS styles for this setup. Hide the stats container and loading text by default.

### Step 2: Map Initialization & Marker Interactions
Now, let's implement the core map logic using Leaflet.js.

1. **Map Setup**: Initialize the map centered on a global view (zoom level 2). Use a dark-themed tile layer (e.g., CartoDB's `dark_all`).
2. **University Data**: Create an array of 5 universities (UCL, NUS, University of Melbourne, Columbia University, HKU) containing their names, latitudes, longitudes, and countries.
3. **Markers**: 
   - Loop through the array and add `CircleMarkers` to the map. Style them with a neon cyan fill and a white border.
   - Bind a tooltip to each marker showing the university name.
4. **Interaction**: 
   - Add a click event listener to each marker. 
   - On click, the map should perform a smooth cinematic zoom (`flyTo` zoom level 6) to the marker's coordinates.
   - Also on click, call a placeholder function `fetchUniversityInfoFromAI(uniName)` which we will define next.

### Step 3: DeepSeek AI Integration & Persona Injection
Finally, let's write the `fetchUniversityInfoFromAI(uniName)` function to connect to the DeepSeek API and inject a specific persona.

1. **UI State Management**: When the function is called, show the floating panel, hide the stats container, and display the pulsing loading text. Update the panel header with the selected university's name.
2. **The Prompt & Persona**: Construct a prompt for the LLM. The persona must be: "A sarcastic but helpful XJTLU senior" (西浦毕业的毒舌但热心的学长). 
3. **Strict JSON Output**: Instruct the LLM to return strictly a JSON object with no markdown formatting or extra text. The JSON must contain:
   - `"qs"`: A string representing the QS ranking number.
   - `"req"`: A short string for GPA and language requirements.
   - `"comment"`: A humorous, grounded comment or complaint about the school (e.g., regarding deadlines, hair loss, or food deserts).
4. **API Call**: Use `fetch` to POST to `https://api.deepseek.com/chat/completions`. Use the `deepseek-chat` model and enforce `response_format: { type: "json_object" }`. (Leave a clear comment where I should paste my API Key).
5. **Render Results**: Parse the returned JSON and update the DOM elements for QS ranking, requirements, and the fun fact. Hide the loading text and reveal the stats container. Add error handling to show a connection failure message if the API call drops.
Vibe Coding Prompts: XJTLU Treasure Map

### Step 1: The Vibe & UI Shell (Global Setup)
You are an expert Front-End Engineer and UI/UX Designer. I want to build a single-file HTML web application called "XJTLU Treasure Map for Study Abroad".

**Tech Stack**: Pure HTML5, CSS3, Vanilla JavaScript. No build tools. Use CDNs for Lucide Icons and Leaflet.js.

**Design System (The Vibe)**:
1. Implement a responsive CSS variable system supporting dual themes: Light (Swiss Spa Light) and Dark (Midnight Minimalist). Core variables must include background colors, surface colors, main text (white in dark mode), muted text, borders, and a primary accent color.
2. Global font stack should default to the Apple ecosystem: `-apple-system, BlinkMacSystemFont, "SF Pro Text", sans-serif`.
3. **UI Layout**:
   - **Top Navbar**: 64px height, glassmorphism effect (`backdrop-filter`), containing a brand logo, four main functional tabs (Explore, Challenge, Support, About), and a right-aligned section with a theme toggle, achievement button, and user avatar.
   - **Main Container**: Fixed below the navbar. Split into a Left Sidebar (480px width, containing 'Account', 'AI Advisor', and 'Favorites' sub-tabs) and a Right Content Area.
   - **Right Content Area**: Features its own top tab bar (Map, Achievement, Quiz, Emotion) with a relatively positioned container for the panels below it.

Please generate the complete HTML skeleton, CSS variable declarations, base flexbox layout styles, and the foundational JavaScript logic to handle 'Theme Toggling' and 'Tab Switching' for both the left sidebar and right content area.

### Step 2: The Explorer (Map Module)
Excellent. Now let's populate the first and most important panel in the main content area: the **Map Exploration** panel.

1. Initialize a Leaflet.js map inside `#map-panel`. Center the default view and set the zoom level to 2. Hide the default zoom control.
2. **Theme Synchronization**: The map's TileLayer must sync with the global theme (Light/Dark). Use a "Voyager" style for Light mode and a "Dark Matter" style for Dark mode.
3. **Data Injection**: Create a `universities` array in JavaScript containing at least 10 mainstream study-abroad institutions (e.g., Oxford, Cambridge, MIT, Stanford, University of Sydney, University of Melbourne). Each object should include: name, coordinates (lat, lng), country, city, and a short "senior alumni comment".
4. **Interactive Logic**:
   - Loop through the array and render `CircleMarkers` on the map.
   - On marker click, the map should smoothly pan and zoom (`flyTo`) to the specific coordinates.
   - Simultaneously, trigger a function `showUniversityModal(uni)` that hides the map view and displays a hidden "University Profile" panel, showing the university's details, the alumni comment, and an "Add to Favorites" button.

### Step 3: State & Storage (User & Favorites System)
Next, let's flesh out the **Account** and **Favorites** tabs in the left sidebar. We will use `localStorage` to simulate a backend database.

1. **User System**:
   - Create a basic Login/Register modal.
   - Store user data in localStorage under `xjlu_users` and `xjlu_user`.
   - If unauthenticated, the sidebar should display "Unverified". Once logged in, render the username and user stats.
2. **Favorites & Statistics**:
   - When a user clicks "Add to Favorites" on a university profile, save that university object to an `xjlu_favorites` array in localStorage.
   - In the Favorites tab of the sidebar:
     - Render the list of saved universities with a delete button.
     - Render a statistics grid showing the count of saved universities categorized by region (UK, US, Australia, Total).
3. **Todo List & Progress Bar**:
   - Below the Favorites list, implement an Application Todo List (e.g., "Prepare IELTS", "Draft PS", "Request Recommendation Letters").
   - Allow users to check off tasks and add new ones.
   - Include a Progress Bar at the top of this section that visually updates based on the completion percentage of the tasks.

### Step 4: The DeepSeek Integration (AI Assistant)
Now, let's inject AI capabilities into the system, focusing on the **AI Advisor** panel and API configuration in the left sidebar.

1. **API Configuration**: In the Account panel, add an input field for the user to enter their API Key. On save, store it in localStorage with a 5-minute expiration timestamp. If a valid key exists, display "AI Connected".
2. **Chat Interface**: Build a chat UI inside the AI Advisor panel, featuring distinct styling for user messages (`.chat-user`) and AI messages (`.chat-ai`).
3. **API Requests**:
   - Capture user input. Intercept and alert the user if the API Key is missing.
   - Use `fetch` to call `https://api.deepseek.com/chat/completions`.
   - Set the System Prompt to: "You are a senior advisor graduated from XJTLU. Your answers must be objective, extremely professional, and concise."
   - Display a loading animation (spinning Lucide loader icon) while waiting for the response.
4. **AI Application Evaluation**: Add an "Evaluate Application Success Rate" button at the bottom of the Favorites panel. On click, grab the currently selected favorite university and the user's saved achievements, construct a prompt, send it to the API, and render the evaluation report below the button.

### Step 5: Gamification & Support Panels
Let's complete the remaining three panels in the right main content area: Achievement, Quiz, and Emotion.

1. **Achievement Panel**:
   - Build a form to add new achievements (Title, and Type: Academic/Language/Experience).
   - Save achievements to localStorage and render them as a list or timeline. Clicking an achievement should display its details.
2. **Quiz Panel (Knowledge Challenge)**:
   - Build a quiz system designed for 30 study-abroad preparation questions (mock 5 core questions in JS to start, e.g., "What does GPA stand for?").
   - Flow: Start Screen -> Active Quiz Screen (with a top progress bar) -> Result Screen.
   - Visually highlight correct (green) and incorrect (red) answers upon selection, then automatically proceed to the next question.
3. **Emotion Panel (Emotional Support)**:
   - Provide four mood buttons (Great, Steady, Stressed, Anxious).
   - On click, reveal a predefined support message below. For example, clicking "Stressed" should output: "Decompression protocol recommended: Pause current work, step away from the screen, and execute 15 minutes of physical relaxation."

### Step 6: Mobile Polish (Responsive Design)
The core functionality is complete. The final step is pure CSS responsive optimization using media queries to ensure it looks perfect on desktop while remaining highly usable on mobile devices.

1. **`max-width: 1024px`**:
   - Change the left sidebar (`#left-sidebar`) to absolute positioning, hidden off-screen to the left (`left: -100%`).
   - Add a hamburger menu icon to the top navbar to toggle the sidebar's visibility.
2. **`max-width: 768px`**:
   - Hide the four main text tabs in the top navbar, keeping only the Logo and right-aligned icons.
   - Make the tab bar in the right main content area horizontally scrollable (`-webkit-overflow-scrolling: touch`) and hide the scrollbar.
   - Reduce padding and font sizes for all cards, modals, and statistics grids to fit smaller screens.
3. **Touch Targets**: Ensure all interactive elements (buttons, links, list items) have a minimum touch target size of 44px for mobile accessibility.
Vibe Coding Prompts: XJTLU Treasure Map (Advanced Version)

### Step 1: The Vibe, Shell & Onboarding Flow
You are an expert Front-End Engineer. I need to build a complex, single-file HTML/CSS/JS application called "XJTLU Treasure Map for Study Abroad". No build tools, use CDNs for Leaflet.js and Lucide Icons.

**Design System (The Vibe)**:
1. Color Palette: Dark/Purple theme. `--primary: #4f46e5`, `--primary-light: #a5b4fc`, `--accent: #7c3aed`, `--bg-primary: #1e1b4b`, `--bg-secondary: #2d3748`, `--bg-card: #374151`, `--text-primary: #f9fafb`. 
2. UI Style: Glassmorphism headers (`backdrop-filter: blur(10px)`), rounded cards (16px), smooth transitions, and gradient buttons.
3. Layout: A central container (max-width 1200px). A top header with navigation tabs (Explore, Recommend, Support, Account). The tabs control the visibility of 4 `<section>` elements.

**Feature 1: Onboarding System**:
1. On page load, show a full-screen `onboarding-overlay` asking the user: "Which Year Are You In?". Provide 4 cards for Year 1, 2, 3, and 4.
2. Clicking a card enables a "Let's Go!" button.
3. When clicked, hide the onboarding and trigger a `startGuidedFlow(grade)` function. For Year 1-3, show a step-by-step "Guided Flow" modal with a progress dot indicator teaching them how to set up the API key and use the app. For Year 4, skip the guide and go directly to the "Support" tab.
4. Set up the basic HTML structure, CSS, and JS tab-switching logic.

### Step 2: Explore Tab (Map & Fallback Data)
Let's build the "Explore" section.

1. **Map Container**: Add a `#map` div. Initialize Leaflet using the `https://{s}.basemaps.cartocdn.com/dark_all/{z}/{x}/{y}.png` tile layer.
2. **University Data**: Create an array of at least 15 global universities containing `name, lat, lng, rank, country, region`.
3. **Custom Markers**: Use `L.divIcon` to create custom markers (a circle with a linear gradient background and a Lucide graduation-cap icon inside).
4. **Interaction**: 
   - When a marker is clicked, `flyTo` the location smoothly.
   - Trigger a `showUniversityDetail(uni)` function. This opens a modal (`#map-info-overlay`).
   - The modal displays the university's Rank and Region. Below that, it should have a placeholder for "AI Content" and an "Add to Favorites" button.
5. **Fallback Database**: Create a `universityInfoDB` object containing mock descriptions, strengths, and admission requirements. If the user hasn't configured an API key, the modal should display this hardcoded data along with a prompt card suggesting they "Unlock AI Features" by entering their API key.

### Step 3: State Management (Account, Favorites & Support Tab)
We need to manage user data using `localStorage`.

1. **Support Tab - Todo List**: Create an "Application Progress" card. It needs an input to add tasks, a list of tasks (with a checkmark circle and delete button), and a visual progress bar (`#progress-fill`) at the top that calculates the percentage of completed tasks. Save to `localStorage`.
2. **Support Tab - Emotion**: Create a grid of 6 emotion buttons (Happy, Excited, Worried, Stressed, Tired, Hopeful). Clicking one displays a random supportive quote from a predefined dictionary.
3. **Account Tab - Favorites**: When a user clicks "Add to Favorites" in the map modal, save the university name to a `favorites` array in localStorage. Render this list in the Account tab with a delete button for each.
4. **Account Tab - Achievements**: Create a section displaying an `achievements` array. Add a button that opens a modal to add a new achievement (Title, Date, Description). Save to localStorage.
5. **Account Tab - Stats**: Display a top grid summarizing the total number of Favorites, Achievements, and the overall Progress % from the Todo list.

### Step 4: The Quiz & Recommendation Engine
Let's build the "University Recommendation" card inside the "Recommend" tab.

1. **Quiz UI**: Build a 7-step quiz interface (intro screen -> active question screen with progress bar -> result screen).
2. **Questions**: Create an array of 7 questions: 1) XJTLU School, 2) Current Year, 3) Target Country, 4) Target Major, 5) GPA range, 6) English Level, 7) Study Habit.
3. **Recommendation Algorithm**: 
   - When the user finishes, map their answers to specific scores (e.g., GPA 'excellent' = 95, English 'good' = 80).
   - Iterate through the university array. Calculate a "Match Score" for each university based on how closely the user's target country, major, GPA, and English scores align with the university's baseline requirements. (Mock these baselines in the array).
   - Sort and slice the top 6 universities.
4. **Results**: Render the top 6 matches with a "Match %" badge. Also, render a "Profile Summary" text block summarizing the user's answers.

### Step 5: AI Integration & API Key Timer
Now for the LLM integration across the app.

1. **API Key Management (Account Tab)**: 
   - Create an input for the OpenAI/DeepSeek API key. Save it to `sessionStorage` with a timestamp.
   - Implement an active countdown timer. The key expires after 1 hour. Display an active status badge (Green = Active, Yellow = Expiring Soon, Red = Expired).
2. **AI Chat (Recommend Tab)**: Implement a chat interface. On send, fetch from `https://api.deepseek.com/chat/completions` (model: `deepseek-chat`). Append user and AI messages dynamically. Show a spinner while loading. Handle API errors gracefully.
3. **Application Evaluation (Recommend Tab)**: Create a dropdown populated dynamically by the user's `favorites` array. Clicking "Evaluate" shows a hardcoded success rate estimate for now.
4. **AI Application Analysis (Account Tab)**: Add an input for "Target University" and an "Analyze" button. When clicked, gather the user's `achievements` from localStorage, construct a prompt ("Analyze this student profile for admission to [Target]..."), send it to the AI, and display the detailed analysis result below.

### Step 6: Mobile Polish & Refinement
Make the complex UI responsive for smaller screens using CSS media queries (`max-width: 768px` and `480px`).

1. **Navigation**: Make the top `nav-tabs-container` horizontally scrollable on mobile (`overflow-x: auto`, hide scrollbar).
2. **Grids & Cards**: Convert the `grid-2` and `grid-3` layouts to single columns (1fr) on mobile. Reduce padding inside all `.card` elements to 1rem or less.
3. **Map & Modals**: Reduce the `#map` height to 280px on mobile. Ensure all modals (`.modal-content`, `.map-info-content`, `.onboarding-container`) take up 95% of the screen width and restrict `max-height` to `85vh` with `overflow-y: auto` so content doesn't get cut off.
4. **Touch Targets**: Ensure all buttons, list items, and quiz options have comfortable padding for touch interaction.