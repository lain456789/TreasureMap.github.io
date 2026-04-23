# XJTLU Treasure Map 系统架构

```
XJTLU Treasure Map for Study Abroad
│
├── Frontend Layer
│   ├── Navigation Bar (#navbar)
│   │   ├── Brand Logo & Title
│   │   ├── Nav Links (index.html ↔ project.html 路由)
│   │   ├── Theme Toggle (Light/Dark 模式)
│   │   └── Settings Button (API Key 管理)
│   │
│   ├── Main Content Area
│   │   ├── Left Panel - University Map (#map)
│   │   │   ├── Interactive Leaflet Map
│   │   │   ├── Clustered University Markers
│   │   │   └── Country/Region Filter
│   │   │
│   │   └── Right Panel - Content Tabs
│   │       ├── University Details Panel
│   │       ├── Favorites List Panel
│   │       ├── Todo List Panel
│   │       └── GPA Calculator Panel
│   │
│   └── Settings Modal
│       ├── API Key Input (5分钟过期机制)
│       ├── Theme Preference
│       └── Data Management
│
├── Data Layer
│   ├── University Database (95所大学)
│   │   ├── UK (18所)
│   │   ├── USA (30所)
│   │   ├── Australia (8所)
│   │   ├── Canada (5所)
│   │   ├── Singapore (2所)
│   │   ├── Hong Kong (5所)
│   │   ├── China (6所)
│   │   └── Europe (17所)
│   │
│   ├── LocalStorage 持久化
│   │   ├── xjlu_favorites
│   │   ├── xjlu_todos
│   │   ├── xjlu_api_key (加密 + 时间戳)
│   │   └── xjlu_theme
│   │
│   └── API 集成
│       └── Moonshot AI API (moonshot-v1-8k)
│
├── Key Features
│   ├── 🗺️ Interactive World Map
│   ├── 🤖 AI Query System
│   ├── ⭐ Favorites Management
│   ├── ✅ Todo List
│   ├── 🧮 GPA Calculator
│   └── 🎨 Theme System
│
└── Technical Stack
    ├── Frontend: Vanilla JS + HTML5 + CSS3
    ├── Map: Leaflet.js
    ├── Icons: Lucide Icons
    ├── AI: Moonshot API (moonshot-v1-8k)
    ├── Storage: localStorage
    └── Responsive: CSS Media Queries
```
