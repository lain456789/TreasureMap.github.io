# TreasureMap - Study Abroad Planning System

A comprehensive study abroad planning and application assistant system designed for XJTLU students. Features include map exploration, AI chat, quiz challenges, personalized onboarding, and more to help students better plan their study abroad journey.

## 🎯 Core Features

### 1. Personalized Onboarding Flow
- Grade-specific guidance based on academic year
- **Year 1**: API setup → AI chat consultation
- **Years 2-3**: Recommendation quiz → Add favorites → Achievements & AI analysis
- Runs on every page load without saving progress

### 2. Map Exploration
- Global university map visualization with Leaflet.js
- Click on universities to view detailed information (rankings, majors, requirements)
- University bookmark/favorite feature with localStorage synchronization

### 3. AI Chat Assistant
- Intelligent Q&A based on DeepSeek API
- Direct browser API calls without server infrastructure
- Study abroad related consultation and personalized advice
- Network error handling with user-friendly messages

### 4. University Recommendation Quiz
- Personalized university matching based on preferences
- Questions covering academic interests, location preferences, and budget
- Directly add recommended schools to favorites

### 5. Achievement System
- System achievements and custom achievements
- Visual achievement display with icons
- Progress persistence via localStorage

### 6. Favorites Management
- Save preferred universities to personal collection
- Synchronization across map, recommendations, and account page
- Quick access to saved university details

### 7. Emotional Support Module
- Mood tracking and regulation
- Motivational quotes and stress relief methods
- Psychological support during the study abroad journey

### 8. Application Progress Management
- **To-Do List System**: Default application process tasks
- **Progress Tracking**: Visual progress bars
- **Task Management**: Click to mark complete/incomplete

## 🛠️ Tech Stack

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Map**: Leaflet.js (v1.9.4)
- **Icons**: Lucide Icons
- **Storage**: sessionStorage (API keys), localStorage (user data)
- **AI**: DeepSeek API
- **Styling**: CSS Variables, Gradients, Responsive Design

## 📁 Project Structure

```
TreasureMap.github.io/
├── index.html          # Project portfolio page
├── project.html        # Main application file
└── README.md           # Project documentation
```

## 🚀 How to Use

1. **Clone the project**
   ```bash
   git clone https://github.com/lain456789/TreasureMap.github.io.git
   ```

2. **Open the project**
   - Open `index.html` directly in a browser (portfolio page)
   - Or open `project.html` for the main application
   - No server required - fully static site

3. **First-time Usage Flow**
   1. **Select Academic Year**: Choose Year 1, Year 2, Year 3, or Year 4
   2. **Complete Onboarding**: Follow grade-specific guidance
      - Year 1: Enter API key → Try AI chat
      - Years 2-3: Complete quiz → Add favorites → Explore achievements
   3. **Explore Features**: Navigate through Explore, Recommend, Support, and Account tabs

## 🔑 API Key Usage

- **Get API Key**: Apply for API Key from [DeepSeek Platform](https://platform.deepseek.com/)
- **Enter API Key**: Enter in the AI panel (Account tab or onboarding)
- **Validity**: Remains valid during browser session; cleared when page closes
- **Storage**: Securely stored in sessionStorage (not persisted)
- **Feature Unlock**: AI chat feature unlocks after entering valid API key

## 🎨 Interface Features

- **Modern Design**: Dark theme with purple/blue gradient color scheme
- **Responsive Layout**: Adapts to different screen sizes (desktop, tablet, mobile)
- **Interactive Experience**: Smooth transitions, hover effects, feedback animations
- **Visual Hierarchy**: Clear information architecture with card-based layout

## 🔧 Development Notes

- **No Backend Required**: Fully static HTML/CSS/JavaScript application
- **Data Privacy**: All user data stored locally on the device
- **API Security**: API keys stored in sessionStorage only, auto-expires on session end
- **Cross-Browser**: Tested on Chrome, Firefox, Safari, and Edge

## 📄 License

This project is for educational purposes. Please comply with the API service provider's terms of use.

## 📧 Contact

For questions or feedback, please contact the development team.
