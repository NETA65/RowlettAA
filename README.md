# Rowlett Group of AA Website

**Live Site:** https://rowlettaa.org/

A modern, feature-rich single-page application (SPA) for the Rowlett Group of Alcoholics Anonymous in Garland, TX. This website serves as a comprehensive resource hub providing meeting schedules, event calendars, recovery tools, literature, and community information—all in a single, optimized HTML file.

## Quick Facts

- **Location:** 362 Oaks Trail #162, Garland, TX 75043
- **Contact:** (972) 925-0096 | rowlettaa@gmail.com
- **Founded:** 1995
- **Technology:** Single HTML file (358KB) - No build process required
- **Features:** 12 pages/sections, PWA support, offline capable, mobile responsive
- **Weekly Meetings:** 15 meetings across 7 days
- **Architecture:** Vanilla JavaScript SPA with Tailwind CSS

---

## Table of Contents

### Getting Started
1. [Application Overview](#application-overview)
2. [Features and Pages](#features-and-pages)
3. [Architecture and Technical Design](#architecture-and-technical-design)

### Content Management
4. [How to Update Events](#how-to-update-events)
5. [How to Update Meeting Schedule](#how-to-update-meeting-schedule)
6. [How to Update Content](#how-to-update-content)

### Technical Reference
7. [Deployment](#deployment)
8. [JavaScript Functions Reference](#javascript-functions-reference)
9. [Styling and Design System](#styling-and-design-system)
10. [Performance and Optimization](#performance-and-optimization)
11. [Troubleshooting](#troubleshooting)
12. [Support](#support)

---

## Application Overview

### What is This Website?

The Rowlett Group AA website is a single-page application (SPA) that consolidates all group information, resources, and tools into one optimized file. Unlike traditional multi-page websites, this application:

- **Loads once, navigates instantly** - All content loads on first visit, then navigation is instant
- **Works offline** - Progressive Web App (PWA) features allow offline access to all content
- **No build process** - Simple HTML file that can be edited directly and deployed immediately
- **Mobile-first** - Fully responsive design works on all devices
- **Self-contained** - No external dependencies beyond CDN resources (Tailwind CSS, Font Awesome)

### Core Purpose

The website serves multiple audiences:

1. **Newcomers** - Find meetings, understand AA, access resources
2. **Members** - Stay updated on events, access literature, use recovery tools
3. **Visitors** - Learn about the group, find contact information, understand AA principles
4. **Service Workers** - Access group information for directories and outreach

### Key Statistics

- **358KB total file size** - Optimized for fast loading
- **12 distinct pages/sections** - Full website in single-page format
- **15 weekly meetings** - Complete schedule with filtering
- **Dynamic events system** - Automatic date handling, recurring patterns, category filtering
- **59 JavaScript functions** - 100% utilized, zero dead code
- **6 event categories** - Rowlett, Speaker, Area, Service, Crashed meetings, Fellowship events
- **5 color-coded event types** - Visual distinction for quick identification

---

## Features and Pages

The application contains 12 main sections, each serving a specific purpose:

### 1. Home Page
**Purpose:** Welcome visitors, provide quick overview and navigation

**Features:**
- Hero section with group name and tagline
- Quick access navigation to all sections
- Meeting highlight (today's meetings)
- Welcome message and AA preamble
- Responsive carousel of recovery quotes
- Call-to-action buttons (Find Meeting, Upcoming Events, Contact)

**Content Location:** Lines ~1500-1700 in index.html

---

### 2. Events Calendar
**Purpose:** Display upcoming and past AA-related events with intelligent filtering

**Features:**
- **Dynamic date calculation** - Events automatically show/hide based on dates
- **Recurring event support** - Monthly patterns (e.g., "third Monday") and series patterns
- **Category filtering** - Toggle between All, Rowlett, Speaker, Area, Service, Crashed events
- **Event series grouping** - Multiple dates shown in single card with strikethrough for past dates
- **Countdown timers** - Shows days until upcoming events
- **Color-coded categories** - Visual distinction by event type
- **Automatic archiving** - Events older than 6 months automatically hidden
- **Past events toggle** - View historical events when needed

**Event Categories:**
- **Rowlett Events** (Blue) - Group-specific events, celebrations, business meetings
- **Speaker Events** (Purple) - Speaker meetings, shares, testimonials
- **Area Events** (Indigo) - Dallas Area events, district meetings
- **Service Events** (Green) - Workshops, GSR orientations, service opportunities
- **Crashed Meetings** (Orange) - When group members support other groups
- **Fellowship** (Pink) - Social events, potlucks, informal gatherings

**How It Works:**
1. Events defined in `eventsData` array (line 3226)
2. Processed on page load with date calculations
3. Cached for instant category filtering
4. Rendered with appropriate styling and interactive elements
5. Updated in real-time as dates pass

**Content Location:**
- Events data: Line 3226-3450
- Processing logic: Line 4200-4300
- Rendering: Line 4050-4150

---

### 3. Meeting Schedule
**Purpose:** Complete weekly meeting schedule with current meeting highlighting

**Features:**
- **15 weekly meetings** across all 7 days
- **Real-time highlighting** - Current meeting highlighted automatically
- **Open/Closed indicators** - Clear designation of meeting types
- **Meeting type labels** - Discussion, Big Book Study, Step Study, etc.
- **Special notes** - First Monday speaker meetings, etc.
- **Next Group Conscience display** - Automatically calculates third Monday
- **Today's meetings** - Quick view of current day's schedule
- **Responsive layout** - Mobile-optimized schedule display

**Meeting Types:**
- **Open meetings** - Anyone welcome (alcoholics and non-alcoholics)
- **Closed meetings** - AA members only

**Meeting Formats:**
- Discussion meetings
- Big Book Study
- Step Study
- Traditions Study
- Foundations meetings
- Speaker meetings (1st Monday)

**How It Works:**
1. Schedule defined in `meetingSchedule` array (line 4014)
2. Current time calculated to highlight active meetings
3. Today's meetings filtered and displayed
4. Group Conscience date calculated using `getRecurringDate()` function
5. Special meeting notes displayed conditionally

**Content Location:**
- Schedule data: Line 4014-4080
- Initialization: Line 3990-4090
- Group Conscience calculation: Line 3998-4010

---

### 4. About Us
**Purpose:** Share group history, mission, and information

**Features:**
- Group history and founding (1995)
- Mission statement aligned with AA traditions
- Group description and atmosphere
- Location information with map link
- Parking and accessibility information
- Group size and demographics
- Special characteristics and focus areas
- Links to other AA resources

**Content Highlights:**
- 30 years of service to the community
- Home group model explanation
- Newcomer-friendly environment
- Service-oriented community

**Content Location:** Lines ~2100-2300

---

### 5. Contact Information
**Purpose:** Provide all contact methods and location details

**Features:**
- Physical address with map link
- Phone number (clickable on mobile)
- Email address (clickable mailto link)
- Google Maps integration
- Directions and landmarks
- Parking information
- Accessibility details
- Best times to call
- Email response time expectations

**Contact Details:**
- **Address:** 362 Oaks Trail #162, Garland, TX 75043
- **Phone:** (972) 925-0096
- **Email:** rowlettaa@gmail.com

**Content Location:** Lines ~2850-2950

---

### 6. Sobriety Calculator
**Purpose:** Calculate time sober and display recovery milestones

**Features:**
- **Date-based calculation** - Enter sobriety date, get exact time sober
- **Multiple time units** - Shows years, months, days, hours, minutes
- **Milestone tracking** - Highlights significant sobriety dates (30 days, 90 days, 1 year, etc.)
- **Next milestone countdown** - Shows days until next milestone
- **Encouragement messages** - Positive reinforcement based on time
- **Shareable results** - Copy/paste formatted output
- **Mobile-optimized input** - Date picker on mobile devices
- **Validation** - Prevents future dates, handles leap years

**Milestones Tracked:**
- 24 hours, 30 days, 60 days, 90 days
- 6 months, 9 months, 1 year
- Multi-year anniversaries

**How It Works:**
1. User enters sobriety date
2. JavaScript calculates difference from today
3. Displays in human-readable format
4. Checks against milestone array
5. Shows congratulations and next milestone

**Content Location:**
- UI: Lines ~2400-2500
- Logic: Lines ~4500-4650

---

### 7. Literature Library
**Purpose:** Provide access to AA literature, readings, and resources

**Features:**
- **Big Book chapters** - Direct PDF links to each chapter
- **12 Steps and 12 Traditions** - Complete text with commentary
- **Daily reflections** - Today's reading automatically highlighted
- **Pamphlet library** - Common AA pamphlets
- **Video resources** - Speakers, educational content
- **Audio resources** - Big Book audiobook chapters
- **PDF previews** - Page numbers and descriptions
- **External links** - Official AA.org resources
- **Mobile-friendly viewing** - Responsive PDF links

**Literature Included:**
- Big Book (all chapters)
- 12 & 12
- Living Sober
- Daily Reflections
- Common pamphlets (Newcomer, Sponsorship, etc.)

**Content Location:**
- Chapter links: Lines ~5010-5090
- Daily reflections: Lines ~5100-5150
- Resource library: Lines ~5160-5250

---

### 8. Step Study Guide
**Purpose:** Interactive tool for working the 12 Steps

**Features:**
- **All 12 Steps** with full text
- **Reflection questions** for each step
- **Journal prompts** - Guided writing exercises
- **Progress tracking** - Mark steps as completed
- **Personal notes** - localStorage saves notes for each step
- **Printable worksheets** - Generate PDF-ready formats
- **Big Book page references** - Direct links to relevant chapters
- **Sponsor guide integration** - Questions for sponsor discussion
- **Mobile note-taking** - Optimized for phone journaling

**Step-by-Step Features:**
- Step text from AA literature
- 5-10 reflection questions per step
- Related Big Book chapters
- Common challenges and solutions
- Sponsor discussion topics

**How It Works:**
1. Select step from dropdown or navigation
2. View step text and questions
3. Write notes in text area
4. Notes auto-save to localStorage
5. Progress tracked across sessions

**Content Location:**
- Step content: Lines ~4650-4800
- Note saving: Lines ~4820-4870
- Progress tracking: Lines ~4880-4920

---

### 9. Newcomer Resources
**Purpose:** Essential information for people new to AA

**Features:**
- **What is AA?** - Clear explanation of program
- **What to expect** - First meeting guide
- **Common questions** - FAQ for newcomers
- **Sobriety basics** - Early recovery tips
- **Sponsorship explained** - How to find and work with sponsor
- **Meeting etiquette** - Do's and don'ts
- **Getting started** - First 90 days guide
- **Crisis resources** - Hotlines and emergency contacts
- **Glossary** - Common AA terms and phrases
- **Myths debunked** - Addressing misconceptions

**Newcomer FAQ Topics:**
- Do I have to speak?
- What is anonymity?
- Do I need to be religious?
- How do I find a sponsor?
- What are the Steps?
- How long does recovery take?

**Content Location:** Lines ~2500-2700

---

### 10. Service Opportunities
**Purpose:** Connect members with service work and volunteer opportunities

**Features:**
- **Meeting service positions** - Chair, secretary, treasurer, etc.
- **Group service roles** - GSR, literature coordinator, etc.
- **Area service** - District and area committees
- **12-Step calls** - Helping other alcoholics
- **Facility service** - Setup, cleanup, maintenance
- **Treatment facilities** - Carrying message to hospitals and institutions
- **Special events** - Help with speaker meetings, celebrations
- **Service organization contacts** - Dallas Area, GSO, etc.
- **Current openings** - Positions needing volunteers
- **Service descriptions** - What each role entails

**Service Categories:**
- **Group Level** - Home group commitments
- **District Level** - Dallas Area service
- **Area Level** - Regional service structure
- **Treatment Facilities** - Magdalen House, Homeward Bound, etc.
- **Correctional Facilities** - Carrying message to prisons
- **Special Events** - Organizing and supporting events

**Organizations Listed:**
- Magdalen House (women's recovery)
- Homeward Bound (men's recovery)
- Dallas Area 66 service
- North Texas treatment centers

**Content Location:** Lines ~4870-4940

---

### 11. Group History Timeline
**Purpose:** Share the Rowlett Group journey from 1995 to present

**Features:**
- **Interactive timeline** - Visual chronological display
- **Decade markers** - Major eras in group history
- **Key milestones** - Founding, growth, challenges, achievements
- **Member stories** - Testimonials from different periods
- **Photo integration** - Historical images (if available)
- **Expansion events** - When group grew or changed
- **Anniversary celebrations** - Significant dates
- **Community impact** - How group has served area

**Timeline Periods:**
- **1995-2000** - Founding and early years
- **2000-2010** - Growth and establishment
- **2010-2020** - Community expansion
- **2020-Present** - Modern era and challenges

**How It Works:**
1. Timeline data in array format (line 5321)
2. JavaScript generates visual timeline
3. Each period has icon, title, description, highlights
4. Responsive design adjusts for mobile/desktop

**Content Location:** Lines ~5321-5400

---

### 12. Resources and Links
**Purpose:** External AA resources and helpful links

**Features:**
- **AA.org** - Official AA website
- **Dallas Area 66** - Local AA service
- **Meeting finders** - National and local meeting directories
- **Literature sources** - Where to buy AA books
- **Online meetings** - Virtual AA meetings
- **AA history** - Archives and historical resources
- **Service resources** - GSO, conference information
- **Recovery apps** - Mobile apps for recovery
- **Treatment resources** - Professional help options
- **Crisis hotlines** - Emergency support numbers

**Resource Categories:**
- Official AA Resources
- Local Dallas Area Resources
- Online/Virtual Meetings
- Literature and Books
- Service Structure
- Treatment and Professional Help
- Crisis Support

**Content Location:** Lines ~5400-5500

---

## Architecture and Technical Design

### Single-Page Application (SPA) Architecture

**What is an SPA?**

A single-page application loads all HTML, CSS, and JavaScript once, then dynamically updates the page content without refreshing. This provides:

- **Instant navigation** - No page reloads between sections
- **Better performance** - Content loads once, reused throughout session
- **App-like experience** - Smooth transitions and interactions
- **Offline capability** - PWA features enable offline use
- **State preservation** - User's place and data persist during navigation

**How This SPA Works:**

```
User visits rowlettaa.org
        ↓
Browser loads index.html (358KB)
        ↓
All 12 pages loaded into memory
        ↓
User clicks navigation
        ↓
JavaScript hides current page, shows target page
        ↓
No server request needed - instant transition
```

### File Structure

Everything is contained in a single `index.html` file organized into sections:

```
index.html (358KB)
├── Lines 1-100: Document Head
│   ├── Meta tags (SEO, social sharing, PWA)
│   ├── Structured data (JSON-LD for search engines)
│   ├── External resources (Tailwind CSS, Font Awesome, Google Fonts)
│   └── PWA manifest and configuration
│
├── Lines 100-1500: Inline Styles
│   ├── Custom CSS overrides
│   ├── Animation definitions
│   ├── Print styles
│   └── Responsive breakpoint adjustments
│
├── Lines 1500-3000: HTML Content
│   ├── Navigation header
│   ├── 12 page sections (all in DOM, hidden/shown with classes)
│   ├── Footer
│   └── Modals and overlays
│
└── Lines 3000-6000+: JavaScript Code
    ├── Global functions (dates, utilities)
    ├── Event data and processing
    ├── Page initialization functions
    ├── Interactive features (calculator, notes, etc.)
    └── Event handlers and navigation
```

### Navigation System

**How Pages Switch:**

The SPA uses CSS classes to show/hide pages:

```javascript
function showPage(pageId) {
    // Hide all pages
    document.querySelectorAll('.page').forEach(page => {
        page.classList.add('hidden');
    });

    // Show target page
    document.getElementById(pageId).classList.remove('hidden');

    // Update navigation highlighting
    updateNavigation(pageId);

    // Run page-specific initialization
    if (pageId === 'events') initEventsPage();
    if (pageId === 'schedule') initSchedulePage();
}
```

**Key Functions:**
- `showPage(pageId)` - Main navigation function
- `initEventsPage()` - Initializes events calendar (line ~4200)
- `initSchedulePage()` - Initializes meeting schedule (line ~3990)
- Page-specific initialization functions for each section

### Data Management

**Events Data Structure:**

```javascript
const eventsData = [
    {
        date: '2025-12-25',              // Date string or recurring pattern
        title: 'Event Name',             // Event title
        time: '7:30 PM',                 // Time string
        location: 'Venue Name',          // Location name
        address: 'Full Address',         // Street address
        category: 'rowlett',             // Event category
        description: 'Event details',    // Full description
        speaker: { name, homeGroup },    // Optional speaker info
        requirements: 'Open to all',     // Access requirements
        guestsWelcome: true,             // Boolean
        mapLink: 'Google Maps URL',      // Map link
        bgColor: 'bg-blue-50',          // Tailwind background
        borderColor: 'border-blue-400',  // Tailwind border
        textColor: 'text-blue-900'       // Tailwind text
    }
];
```

**Meeting Schedule Structure:**

```javascript
const meetingSchedule = [
    {
        day: "Monday",
        dayIndex: 1,
        meetings: [
            {
                time: "12:00 PM",
                type: "closed",
                name: "Discussion Meeting",
                note: "Optional special note"
            }
        ]
    }
];
```

### Recurring Date Patterns

The application supports three types of recurring events:

**1. Monthly Recurring (Standard Pattern)**
```javascript
date: 'recurring-third-monday'
```

Supported patterns:
- `recurring-first-[day]` through `recurring-fourth-[day]`
- `recurring-last-[day]`
- Days: monday, tuesday, wednesday, thursday, friday, saturday, sunday

**2. All Days in Month (Series Pattern)**
```javascript
date: 'recurring-all-tuesday:2025-12'
```

Generates ALL occurrences of a weekday in a specific month:
- `recurring-all-tuesday:2025-12` = All Tuesdays in December 2025
- `recurring-all-wednesday:2026-01` = All Wednesdays in January 2026

**How Recurring Dates Work:**

```javascript
// Core date calculation function (line ~3069)
function getRecurringDate(recurringType, year, month) {
    // Parse pattern: 'recurring-third-monday' → occurrence='third', day='monday'
    const parts = recurringType.replace('recurring-', '').split('-');
    const occurrence = parts[0];  // first, second, third, fourth, last
    const dayName = parts[1];     // monday, tuesday, etc.

    // Find target day of week (0=Sunday, 6=Saturday)
    const targetDay = dayNames.indexOf(dayName);

    // Calculate date based on occurrence
    // Returns Date object for the specific occurrence
}

// Series date calculation (line ~3095)
function getAllWeekdayDatesInMonth(dayName, year, month) {
    // Generates array of ALL dates for a weekday in a month
    // Example: All Tuesdays in December 2025 = [Dec 2, Dec 9, Dec 16, Dec 23, Dec 30]
    const dates = [];

    // Loop through month, collect matching weekdays
    while (currentDate <= lastDay) {
        if (currentDate.getDay() === targetDay) {
            dates.push(new Date(currentDate));
        }
        currentDate.setDate(currentDate.getDate() + 1);
    }

    return dates;  // Array of Date objects
}
```

### Event Processing and Caching

**Performance Optimization:**

Events are processed once on page load and cached for instant filtering:

```javascript
// Line ~4200
function initEventsPage() {
    if (processedEvents) {
        // Use cached events for instant filtering
        displayEvents(processedEvents);
        return;
    }

    // Process events once
    processedEvents = processEventsData(eventsData);

    // Cache for future use
    displayEvents(processedEvents);
}
```

**Event Processing Steps:**

1. **Parse date patterns** - Convert recurring patterns to actual dates
2. **Calculate series** - Generate all dates for series patterns
3. **Filter by date** - Separate future, current, and past events
4. **Sort chronologically** - Order by date/time
5. **Apply 6-month rule** - Hide events older than 6 months
6. **Cache results** - Store for instant category filtering

**Category Filtering:**

```javascript
// Line ~4280
function filterEventsByCategory(category) {
    if (category === 'all') {
        displayEvents(processedEvents);
    } else {
        const filtered = processedEvents.filter(e => e.event.category === category);
        displayEvents(filtered);
    }
    // No reprocessing - uses cached data
}
```

### Progressive Web App (PWA) Features

**What is PWA?**

Progressive Web Apps work like native mobile apps:
- Install to home screen
- Work offline
- Fast loading
- App-like interface

**PWA Implementation:**

**Manifest File** (line ~50-80):
```html
<link rel="manifest" href="data:application/json;base64,...">
```

Defines:
- App name and short name
- Icons (192x192, 512x512)
- Theme colors
- Display mode (standalone)
- Start URL

**Service Worker** (if implemented):
- Caches index.html for offline use
- Provides offline fallback
- Updates cache on new version

**Offline Capability:**
- All content in single file
- External resources (Tailwind, Font Awesome) cached by browser
- LocalStorage for user data (notes, preferences)

### State Management

**LocalStorage Usage:**

The application uses browser localStorage to persist user data:

```javascript
// Save step study notes
localStorage.setItem('step-notes-1', noteContent);

// Retrieve notes
const savedNotes = localStorage.getItem('step-notes-1');

// Clear data
localStorage.removeItem('step-notes-1');
```

**Data Stored:**
- Step study notes (12 items, one per step)
- User preferences (future implementation)
- Calculator history (future implementation)

**Benefits:**
- Data persists across sessions
- No server required
- Instant access
- Privacy (stays on user's device)

---

## How to Update Events

Events are the most frequently updated content. This section provides complete templates and instructions.

### Events Data Location

All events are defined in the `eventsData` array starting at **line 3226** in `index.html`.

```javascript
const eventsData = [
    {
        // Event object here
    },
    {
        // Another event
    }
    // ... more events
];
```

### Quick Start: Adding a New Event

**Step-by-step:**

1. Open `index.html` in your code editor
2. Search for `const eventsData = [` (line 3226)
3. Scroll to the end of the array (before the closing `];`)
4. Copy one of the templates below
5. Paste before the closing `];`
6. Modify the fields for your event
7. Ensure there's a comma after the previous event
8. Save the file
9. Test locally by opening in browser
10. Upload to server

### Event Templates

Copy and paste these templates, then customize:

#### One-Time Event

```javascript
{
    date: '2025-12-25',
    title: 'Christmas Day Open House',
    time: '10:00 AM - 6:00 PM',
    location: 'Rowlett Group',
    address: '362 Oaks Trail #162, Garland, TX 75043',
    category: 'rowlett',
    description: 'Open all day for fellowship and support. Join us for coffee, conversation, and community.',
    requirements: 'Open to all',
    guestsWelcome: true,
    mapLink: 'https://maps.google.com/?q=362+Oaks+Trail+162+Garland+TX+75043',
    bgColor: 'bg-blue-50',
    borderColor: 'border-blue-400',
    textColor: 'text-blue-900'
},
```

**When to use:** Single-occurrence events like holidays, anniversaries, special celebrations.

---

#### Monthly Recurring Event

```javascript
{
    date: 'recurring-third-monday',
    title: 'Group Conscience Meeting',
    time: '6:00 PM',
    location: 'Rowlett Group',
    address: '362 Oaks Trail #162, Garland, TX 75043',
    category: 'rowlett',
    description: 'Monthly business meeting for home group members. Discuss group matters, finances, and service positions.',
    requirements: 'Closed - Rowlett Group members only',
    guestsWelcome: false,
    mapLink: 'https://maps.google.com/?q=362+Oaks+Trail+162+Garland+TX+75043',
    bgColor: 'bg-blue-50',
    borderColor: 'border-blue-400',
    textColor: 'text-blue-900'
},
```

**When to use:** Events that repeat monthly on a specific occurrence (first Monday, third Saturday, etc.).

**Available patterns:**
- `recurring-first-monday` through `recurring-first-sunday`
- `recurring-second-monday` through `recurring-second-sunday`
- `recurring-third-monday` through `recurring-third-sunday`
- `recurring-fourth-monday` through `recurring-fourth-sunday`
- `recurring-last-monday` through `recurring-last-sunday`

---

#### Speaker Series (All Days in Month)

```javascript
{
    date: 'recurring-all-tuesday:2025-12',
    title: 'December Speaker Series',
    time: '7:30 PM',
    location: 'Rowlett Group',
    address: '362 Oaks Trail #162, Garland, TX 75043',
    category: 'speaker',
    speaker: {
        name: 'Various Speakers',
        homeGroup: 'Rowlett Group'
    },
    requirements: 'Open to all',
    guestsWelcome: true,
    description: 'Different Rowlett Group members speaking each Tuesday in December. Come hear diverse perspectives on recovery.',
    mapLink: 'https://maps.google.com/?q=362+Oaks+Trail+162+Garland+TX+75043',
    details: 'Weekly speaker series throughout the month.',
    bgColor: 'bg-purple-50',
    borderColor: 'border-purple-400',
    textColor: 'text-purple-900'
},
```

**When to use:** Events happening on ALL occurrences of a weekday in a specific month.

**How it works:**
- Pattern: `recurring-all-[day]:[YYYY-MM]`
- Example: `recurring-all-tuesday:2025-12` generates Dec 2, 9, 16, 23, 30 (all Tuesdays)
- Displays as ONE event card showing all dates
- Past dates automatically struck through
- Perfect for monthly speaker series, themed weeks, etc.

---

#### Speaker Event with Full Details

```javascript
{
    date: '2025-12-01',
    title: 'Matt C. - A Blast from the Past!',
    time: '7:30 PM',
    location: 'Rowlett Group',
    address: '362 Oaks Trail #162, Garland, TX 75043',
    category: 'speaker',
    speaker: {
        name: 'Matt C.',
        homeGroup: 'Rowlett Group',
        bio: '15 years sober, founding member',
        sobrietyDate: '2010-01-15'
    },
    requirements: 'Open to all',
    guestsWelcome: true,
    description: 'Join us as Matt C. shares his experience, strength, and hope. Matt has been a cornerstone of our group for over a decade.',
    mapLink: 'https://maps.google.com/?q=362+Oaks+Trail+162+Garland+TX+75043',
    details: 'Welcome back, Matt! Long-time Rowlett Group member returns to share his journey.',
    bgColor: 'bg-purple-50',
    borderColor: 'border-purple-400',
    textColor: 'text-purple-900'
},
```

**When to use:** Individual speaker events with detailed speaker information.

**Optional speaker fields:**
- `name` - Speaker's first name and last initial
- `homeGroup` - Their home group
- `bio` - Brief biography
- `sobrietyDate` - Date they got sober (automatically calculates time)

---

#### Workshop/Service Event

```javascript
{
    date: '2025-12-06',
    title: 'How to Chair a Meeting Workshop',
    time: '2:00 PM - 4:00 PM',
    location: 'McKinney Fellowship Group',
    address: '802 E University Dr, McKinney, TX 75069',
    category: 'service',
    description: 'Learn the basics of chairing an AA meeting! This workshop covers meeting formats, traditions in action, and practical tips for leading effective meetings.',
    requirements: 'Closed - AA members only',
    guestsWelcome: false,
    mapLink: 'https://maps.google.com/?q=802+E+University+Dr+McKinney+TX+75069',
    details: 'Perfect for newcomers to service and those wanting to improve their chairing skills.',
    hostGroup: 'McKinney Fellowship Group',
    groupInvolvement: 'All Rowlett Group members encouraged to join and strengthen their service skills!',
    bgColor: 'bg-green-50',
    borderColor: 'border-green-400',
    textColor: 'text-green-900'
},
```

**When to use:** Workshops, GSR orientations, service training, learning opportunities.

**Service event specifics:**
- Always use `category: 'service'` and green colors
- Include `hostGroup` if not at Rowlett
- Add `groupInvolvement` to encourage participation
- Specify `requirements` and `guestsWelcome: false` for AA-only events

---

#### Area/Dallas Event

```javascript
{
    date: '2026-01-25',
    title: 'Dallas Area 66 Assembly',
    time: '9:00 AM - 3:00 PM',
    location: 'Lover\'s Lane United Methodist Church',
    address: '9200 Inwood Rd, Dallas, TX 75220',
    category: 'area',
    description: 'Quarterly Dallas Area assembly. All AA members welcome to participate in area service.',
    requirements: 'Open to all AA members',
    guestsWelcome: false,
    mapLink: 'https://maps.google.com/?q=9200+Inwood+Rd+Dallas+TX+75220',
    hostGroup: 'Dallas Area 66',
    groupInvolvement: 'GSRs and interested members encouraged to attend.',
    details: 'Lunch provided. Bring district reports if you are a GSR.',
    bgColor: 'bg-indigo-50',
    borderColor: 'border-indigo-400',
    textColor: 'text-indigo-900'
},
```

**When to use:** Dallas Area events, district meetings, assemblies, conferences.

---

#### Anniversary Celebration

```javascript
{
    date: '2026-03-15',
    title: 'Rowlett Group 30th Anniversary Celebration',
    time: '5:30 PM - 9:00 PM',
    location: 'Rowlett Group',
    address: '362 Oaks Trail #162, Garland, TX 75043',
    category: 'rowlett',
    description: 'Celebrating 30 years of carrying the message! Join us for fellowship, food, speakers, and celebration.',
    requirements: 'Open to all',
    guestsWelcome: true,
    potluck: true,
    timeParts: {
        '5:30 PM': 'Potluck Dinner',
        '7:00 PM': 'Speaker Meeting',
        '8:30 PM': 'Cake & Fellowship'
    },
    mapLink: 'https://maps.google.com/?q=362+Oaks+Trail+162+Garland+TX+75043',
    details: 'Bring a dish to share! Speaker TBA.',
    bgColor: 'bg-yellow-50',
    borderColor: 'border-yellow-400',
    textColor: 'text-yellow-900'
},
```

**When to use:** Anniversaries, birthdays, milestone celebrations.

**Special fields:**
- `potluck: true` - Shows potluck icon and notice
- `timeParts` - Object defining multiple time segments
- Use yellow colors for celebrations

---

### Event Field Reference

**Required Fields (every event must have):**

| Field | Type | Example | Description |
|-------|------|---------|-------------|
| `date` | String | `'2025-12-25'` or `'recurring-third-monday'` | Date or recurring pattern |
| `title` | String | `'Christmas Open House'` | Event name |
| `time` | String | `'7:30 PM'` or `'2:00 PM - 4:00 PM'` | Time of event |
| `location` | String | `'Rowlett Group'` | Venue name |
| `address` | String | `'362 Oaks Trail #162, Garland, TX 75043'` | Full street address |
| `category` | String | `'rowlett'`, `'speaker'`, `'area'`, `'service'`, `'crashed'` | Event category |
| `bgColor` | String | `'bg-blue-50'` | Tailwind background color class |
| `borderColor` | String | `'border-blue-400'` | Tailwind border color class |
| `textColor` | String | `'text-blue-900'` | Tailwind text color class |

**Optional Fields:**

| Field | Type | Example | Description |
|-------|------|---------|-------------|
| `description` | String | `'Join us for fellowship...'` | Detailed event description |
| `requirements` | String | `'Open to all'` or `'Closed - AA members only'` | Access requirements |
| `guestsWelcome` | Boolean | `true` or `false` | Whether non-AA guests welcome |
| `speaker` | Object | `{ name: 'John D.', homeGroup: 'Rowlett' }` | Speaker information |
| `timeParts` | Object | `{ '5:30 PM': 'Dinner', '7:00 PM': 'Meeting' }` | Multi-segment events |
| `potluck` | Boolean | `true` | Whether event includes potluck |
| `mapLink` | String | `'https://maps.google.com/...'` | Google Maps link |
| `hostGroup` | String | `'McKinney Fellowship Group'` | Hosting organization |
| `groupInvolvement` | String | `'All members encouraged...'` | How Rowlett participates |
| `details` | String | `'Bring a dish to share'` | Additional notes |

**Speaker Object Fields:**

```javascript
speaker: {
    name: 'John D.',                    // Required
    homeGroup: 'Rowlett Group',         // Optional
    bio: '10 years sober',              // Optional
    sobrietyDate: '2015-06-01'         // Optional (auto-calculates time)
}
```

### Recurring Event Patterns

**Monthly Patterns:** `'recurring-[occurrence]-[day]'`

**Format:** `recurring-[first|second|third|fourth|last]-[weekday]`

**Examples:**
```javascript
'recurring-first-monday'      // 1st Monday each month
'recurring-second-tuesday'    // 2nd Tuesday each month
'recurring-third-monday'      // 3rd Monday each month (Group Conscience)
'recurring-fourth-saturday'   // 4th Saturday each month
'recurring-last-sunday'       // Last Sunday each month
```

**Valid weekdays:** monday, tuesday, wednesday, thursday, friday, saturday, sunday

**How it works:**
- Automatically calculates next occurrence
- Shows in future events until date passes
- Then calculates next month's occurrence
- Continues indefinitely

---

**All Days in Month Pattern:** `'recurring-all-[day]:[YYYY-MM]'`

**Format:** `recurring-all-[weekday]:[year-month]`

**Examples:**
```javascript
'recurring-all-tuesday:2025-12'    // All Tuesdays in December 2025
'recurring-all-wednesday:2026-01'  // All Wednesdays in January 2026
'recurring-all-thursday:2025-11'   // All Thursdays in November 2025
```

**How it works:**
- Generates ALL dates for that weekday in the specified month
- Example: `recurring-all-tuesday:2025-12` creates:
  - December 2, 2025
  - December 9, 2025
  - December 16, 2025
  - December 23, 2025
  - December 30, 2025
- Displays as ONE event card showing all dates
- Past dates automatically struck through
- Event hides when all dates have passed

**Perfect for:**
- Monthly speaker series
- Themed meeting weeks
- Special programming for a specific month
- Guest speaker visiting multiple times

---

### Event Color Guide

Use these color combinations for visual consistency:

```javascript
// Rowlett Group Events (Blue)
bgColor: 'bg-blue-50'
borderColor: 'border-blue-400'
textColor: 'text-blue-900'
// Use for: Group events, business meetings, group-specific activities

// Speaker Events (Purple)
bgColor: 'bg-purple-50'
borderColor: 'border-purple-400'
textColor: 'text-purple-900'
// Use for: Speaker meetings, shares, testimonials

// Workshops/Service Events (Green)
bgColor: 'bg-green-50'
borderColor: 'border-green-400'
textColor: 'text-green-900'
// Use for: Workshops, training, GSR orientations, service events

// Anniversary/Special Events (Yellow)
bgColor: 'bg-yellow-50'
borderColor: 'border-yellow-400'
textColor: 'text-yellow-900'
// Use for: Anniversaries, birthdays, celebrations, milestones

// Area/Dallas Events (Indigo)
bgColor: 'bg-indigo-50'
borderColor: 'border-indigo-400'
textColor: 'text-indigo-900'
// Use for: Area assemblies, district meetings, Dallas Area events

// Fellowship/Social (Pink)
bgColor: 'bg-pink-50'
borderColor: 'border-pink-400'
textColor: 'text-pink-900'
// Use for: Potlucks, social events, informal gatherings

// Crashed Meetings (Orange)
bgColor: 'bg-orange-50'
borderColor: 'border-orange-400'
textColor: 'text-orange-900'
// Use for: When group members crash other groups' events
```

### Editing Existing Events

**To modify an event:**

1. Search for the event title in `index.html`
2. Find the event object (starts with `{`, ends with `},`)
3. Modify the desired fields
4. Maintain proper JSON syntax (quotes, commas)
5. Save and test

**Example edit:**

```javascript
// Before
{
    date: '2025-12-01',
    title: 'Speaker Meeting',
    time: '7:00 PM',
    // ... rest of event
}

// After (changed date and time)
{
    date: '2025-12-08',
    title: 'Speaker Meeting',
    time: '7:30 PM',
    // ... rest of event
}
```

### Removing Events

**Permanent removal:**

1. Find the event object
2. Delete from opening `{` to closing `},`
3. Ensure commas are correct between remaining events
4. Save

**Temporary removal (commenting out):**

```javascript
// Use block comments to hide event temporarily
/*  {
    date: '2025-12-25',
    title: 'Event to Hide',
    time: '10:00 AM',
    location: 'Rowlett Group',
    // ... rest of event
},  */
```

**Note:** Commented events can be uncommented later by removing `/*` and `*/`.

### Common Event Mistakes

**Missing comma:**
```javascript
{
    date: '2025-12-01',
    title: 'Event 1'
}  // ❌ Missing comma here!
{
    date: '2025-12-02',
    title: 'Event 2'
}
```

**Fixed:**
```javascript
{
    date: '2025-12-01',
    title: 'Event 1'
},  // ✅ Comma added
{
    date: '2025-12-02',
    title: 'Event 2'
}
```

**Missing quotes:**
```javascript
{
    date: 2025-12-01,  // ❌ Should be '2025-12-01'
    title: Event,      // ❌ Should be 'Event'
}
```

**Incorrect category:**
```javascript
{
    category: 'meeting',  // ❌ Invalid category
}
```

**Valid categories:** `'rowlett'`, `'speaker'`, `'area'`, `'service'`, `'crashed'`

---

## How to Update Meeting Schedule

The weekly meeting schedule defines all regular meetings. This is separate from events.

### Schedule Data Location

Meeting schedule is in the `initSchedulePage` function at **line 3990** in `index.html`.

Find the `meetingSchedule` array around **line 4014**:

```javascript
const meetingSchedule = [
    { day: "Sunday", dayIndex: 0, meetings: [ /* meetings */ ]},
    { day: "Monday", dayIndex: 1, meetings: [ /* meetings */ ]},
    // ... all 7 days
];
```

### Current Schedule

**Complete weekly schedule:**

```javascript
const meetingSchedule = [
    { day: "Sunday", dayIndex: 0, meetings: [
        { time: "11:00 AM", type: "open", name: "Discussion Meeting" }
    ]},

    { day: "Monday", dayIndex: 1, meetings: [
        { time: "12:00 PM", type: "closed", name: "Discussion Meeting" },
        { time: "7:30 PM", type: "closed", name: "Big Book Study", note: "1st Monday Open Speaker Meeting" }
    ]},

    { day: "Tuesday", dayIndex: 2, meetings: [
        { time: "12:00 PM", type: "closed", name: "Discussion Meeting" },
        { time: "7:30 PM", type: "closed", name: "Foundations Meeting" }
    ]},

    { day: "Wednesday", dayIndex: 3, meetings: [
        { time: "12:00 PM", type: "closed", name: "Discussion Meeting" },
        { time: "7:30 PM", type: "closed", name: "Step Study" }
    ]},

    { day: "Thursday", dayIndex: 4, meetings: [
        { time: "12:00 PM", type: "closed", name: "Discussion Meeting" },
        { time: "7:30 PM", type: "closed", name: "Traditions Study" }
    ]},

    { day: "Friday", dayIndex: 5, meetings: [
        { time: "12:00 PM", type: "closed", name: "Discussion Meeting" },
        { time: "7:30 PM", type: "closed", name: "Living Sober" }
    ]},

    { day: "Saturday", dayIndex: 6, meetings: [
        { time: "11:00 AM", type: "open", name: "Discussion Meeting" },
        { time: "7:30 PM", type: "closed", name: "Big Book Study" }
    ]}
];
```

### Meeting Object Structure

Each meeting has these fields:

```javascript
{
    time: "7:30 PM",           // Required: Meeting time
    type: "open",              // Required: "open" or "closed"
    name: "Discussion Meeting", // Required: Meeting format/name
    note: "Special note"       // Optional: Additional information
}
```

**Field descriptions:**

| Field | Required | Values | Description |
|-------|----------|--------|-------------|
| `time` | Yes | `"7:30 PM"`, `"12:00 PM"` | Meeting start time |
| `type` | Yes | `"open"` or `"closed"` | Meeting type |
| `name` | Yes | Any string | Meeting format/name |
| `note` | No | Any string | Special notes or exceptions |

### Meeting Types and Formats

**Types:**
- `"open"` - Anyone welcome (alcoholics and non-alcoholics)
- `"closed"` - AA members only (or those with drinking problem)

**Common formats:**
- `"Discussion Meeting"` - Group discussion format
- `"Big Book Study"` - Study Alcoholics Anonymous text
- `"Step Study"` - Focus on one of the 12 Steps
- `"Traditions Study"` - Study the 12 Traditions
- `"Foundations Meeting"` - Core AA principles
- `"Living Sober"` - Study Living Sober book
- `"Speaker Meeting"` - Speaker shares story

### Adding a New Meeting

**Example: Add a 6:00 PM Newcomer meeting on Wednesday**

1. Find Wednesday in the schedule array
2. Add to the meetings array:

```javascript
{ day: "Wednesday", dayIndex: 3, meetings: [
    { time: "12:00 PM", type: "closed", name: "Discussion Meeting" },
    { time: "6:00 PM", type: "open", name: "Newcomer Meeting" },  // ← New meeting added
    { time: "7:30 PM", type: "closed", name: "Step Study" }
]},
```

**Important:** Meetings in the array don't need to be in time order, but it's good practice.

### Removing a Meeting

Find the meeting object and delete it:

```javascript
// Before
{ day: "Friday", dayIndex: 5, meetings: [
    { time: "12:00 PM", type: "closed", name: "Discussion Meeting" },
    { time: "7:30 PM", type: "closed", name: "Living Sober" }
]},

// After (removed 12:00 PM meeting)
{ day: "Friday", dayIndex: 5, meetings: [
    { time: "7:30 PM", type: "closed", name: "Living Sober" }
]},
```

### Changing Meeting Type or Time

**Example: Change Tuesday 7:30 PM from closed to open**

```javascript
// Before
{ time: "7:30 PM", type: "closed", name: "Foundations Meeting" }

// After
{ time: "7:30 PM", type: "open", name: "Foundations Meeting" }
```

**Example: Change meeting time from 7:30 PM to 7:00 PM**

```javascript
// Before
{ time: "7:30 PM", type: "closed", name: "Step Study" }

// After
{ time: "7:00 PM", type: "closed", name: "Step Study" }
```

### Updating Group Conscience Date

Group Conscience is calculated automatically using the recurring date function.

**Location:** Line ~3998

```javascript
let thirdMonday = getRecurringDate('recurring-third-monday', conscienceYear, conscienceMonth);
```

**To change from 3rd Monday to different day:**

```javascript
// Change to first Monday
let conscienceDate = getRecurringDate('recurring-first-monday', conscienceYear, conscienceMonth);

// Change to last Saturday
let conscienceDate = getRecurringDate('recurring-last-saturday', conscienceYear, conscienceMonth);

// Change to second Tuesday
let conscienceDate = getRecurringDate('recurring-second-tuesday', conscienceYear, conscienceMonth);
```

**Available patterns:**
- `'recurring-first-[day]'`
- `'recurring-second-[day]'`
- `'recurring-third-[day]'`
- `'recurring-fourth-[day]'`
- `'recurring-last-[day]'`

Days: monday, tuesday, wednesday, thursday, friday, saturday, sunday

### Special Meeting Notes

Use the `note` field for special information:

```javascript
{
    time: "7:30 PM",
    type: "closed",
    name: "Big Book Study",
    note: "1st Monday Open Speaker Meeting"
}
```

This note will display on the meeting card to indicate the exception.

---

## How to Update Content

Beyond events and schedule, here's how to update other website content.

### Contact Information

**Main Contact Section** (around line 2850):

```html
<div class="contact-info">
    <p><strong>Phone:</strong> <a href="tel:+19729250096">(972) 925-0096</a></p>
    <p><strong>Email:</strong> <a href="mailto:rowlettaa@gmail.com">rowlettaa@gmail.com</a></p>
    <p><strong>Address:</strong> 362 Oaks Trail #162, Garland, TX 75043</p>
</div>
```

**To update phone number:**
1. Change the number in `tel:+19729250096` (use format: +1 then 10 digits, no spaces)
2. Change the displayed number `(972) 925-0096`

**To update email:**
1. Change `mailto:rowlettaa@gmail.com` to new email
2. Change displayed text

**To update address:**
1. Change the address text
2. Update Google Maps links throughout site (search for `maps.google.com`)

---

**Footer** (around line 3050):

```html
<footer class="bg-gray-800 text-white py-6">
    <div class="container mx-auto text-center">
        <p>&copy; <span id="copyright-year"></span> Rowlett Group of AA. All Rights Reserved.</p>
        <p class="text-sm mt-2">Rowlett Group of Alcoholics Anonymous</p>
    </div>
</footer>
```

The year updates automatically via JavaScript (`copyright-year` element).

### Group History Timeline

**Location:** Line ~5321 in `generateTimelineHTML` function

**Timeline structure:**

```javascript
const timelineData = [
    {
        year: "1995",
        title: "The Beginning",
        description: "Rowlett Group founded by dedicated AA members",
        icon: "fas fa-star",
        highlights: [
            "First meeting held in small room",
            "Core founding members establish traditions",
            "Weekly meetings begin"
        ]
    },
    {
        year: "2000",
        title: "Growing Community",
        description: "Group expands and strengthens",
        icon: "fas fa-users",
        highlights: [
            "Membership grows to 50+ regular attendees",
            "Additional weekly meetings added",
            "Service structure established"
        ]
    }
    // ... more periods
];
```

**To add a new period:**

1. Find the timeline array
2. Add new object with year, title, description, icon, highlights
3. Use Font Awesome icon names (fas fa-star, fas fa-users, etc.)

**Font Awesome icons available:**
- `fas fa-star` - Star (beginnings, important)
- `fas fa-users` - People (community, growth)
- `fas fa-home` - House (establishment, location)
- `fas fa-heart` - Heart (love, fellowship)
- `fas fa-trophy` - Trophy (achievements)
- `fas fa-calendar` - Calendar (events, time)
- See more at https://fontawesome.com/icons

### Literature Links

**Big Book Chapters** (around line 5010-5040):

```javascript
const bigBookChapters = [
    {
        title: "Chapter 1: Bill's Story",
        pdfUrl: "https://www.aa.org/sites/default/files/literature/...",
        pages: "1-16",
        description: "Bill W. tells his story"
    },
    {
        title: "Chapter 2: There is a Solution",
        pdfUrl: "https://www.aa.org/sites/default/files/literature/...",
        pages: "17-29",
        description: "The solution to alcoholism"
    }
    // ... more chapters
];
```

**To update a PDF link:**
1. Find the chapter
2. Replace `pdfUrl` with new URL
3. Update `pages` if different
4. Update `description` if needed

**To add a new resource:**

```javascript
{
    title: "New Pamphlet Name",
    pdfUrl: "https://www.aa.org/path/to/pamphlet.pdf",
    pages: "1-10",
    description: "Description of pamphlet"
}
```

### Service Opportunities

**Location:** Line ~4870-4940

**Structure:**

```javascript
const serviceOpportunities = [
    {
        title: "Magdalen House",
        description: "Women's recovery home providing support and structure",
        contact: "(214) 324-9261",
        website: "www.magdalenhouse.org",
        type: "Treatment Facility"
    }
    // ... more opportunities
];
```

**To add new service opportunity:**

```javascript
{
    title: "New Organization",
    description: "What they do",
    contact: "(XXX) XXX-XXXX",
    website: "www.example.org",
    type: "Category"
}
```

**Common types:**
- Treatment Facility
- Correctional Facility
- Service Committee
- Area Service
- Special Needs

### Updating Meta Tags (SEO)

**Location:** Lines 1-100

**Key meta tags:**

```html
<title>Rowlett Group of AA | Garland, TX</title>
<meta name="description" content="Rowlett Group of Alcoholics Anonymous...">
<meta name="keywords" content="AA, Alcoholics Anonymous, Rowlett, Garland, TX, meetings, recovery">

<!-- Open Graph (Facebook) -->
<meta property="og:title" content="Rowlett Group of AA">
<meta property="og:description" content="...">
<meta property="og:url" content="https://rowlettaa.org/">

<!-- Twitter -->
<meta name="twitter:title" content="Rowlett Group of AA">
<meta name="twitter:description" content="...">
```

**To update:**
1. Change title tags for browser tab and social sharing
2. Update descriptions for search engines
3. Ensure consistency across all meta tags

---

## Deployment

### Prerequisites

You need ONE of the following:

- FTP/SFTP access credentials (username, password, server address)
- Web hosting control panel access (cPanel, Plesk, etc.)
- Git repository access (if using version control deployment)

### Local Testing (CRITICAL)

**Always test locally before deploying:**

1. Open `index.html` directly in web browser (double-click or File > Open)
2. Check all pages/sections:
   - Click through all navigation links
   - View Events page, test category filtering
   - Check Schedule page
   - Test Sobriety Calculator
   - Verify Literature links
   - Check all external links
3. Open browser console (F12) and check for JavaScript errors
4. Test on mobile (resize browser window or use device emulator)
5. Verify all changes display correctly

**Pre-deployment checklist:**

- [ ] All events display correctly
- [ ] Event dates are accurate
- [ ] No JavaScript errors in console (F12)
- [ ] All links work
- [ ] Mobile view looks good
- [ ] Changes saved to file
- [ ] Backup of previous version made

### Deployment Methods

#### Method 1: FTP/SFTP Upload

**Tools needed:**
- FTP client (FileZilla, Cyberduck, WinSCP)
- FTP credentials from hosting provider

**Steps:**
1. Open FTP client
2. Connect to server using credentials
3. Navigate to web root directory (usually `public_html` or `www`)
4. Upload `index.html`
5. Overwrite existing file when prompted
6. Wait for upload to complete
7. Verify at https://rowlettaa.org/

**Common FTP settings:**
- Host: `ftp.yourdomain.com` or `sftp.yourdomain.com`
- Port: 21 (FTP) or 22 (SFTP)
- Protocol: FTP or SFTP (SFTP is more secure)

---

#### Method 2: cPanel File Manager

**Steps:**
1. Log into cPanel
2. Click "File Manager"
3. Navigate to `public_html`
4. Click "Upload"
5. Select `index.html` from your computer
6. Overwrite when prompted
7. Verify at https://rowlettaa.org/

**Advantages:**
- No additional software needed
- Works in any browser
- Simple interface

---

#### Method 3: Git Deployment

**If using Git/GitHub:**

```bash
# Make changes to index.html
# Commit changes
git add index.html
git commit -m "Update events for December 2025"

# Push to repository
git push origin main

# If using automated deployment, changes go live automatically
# Otherwise, pull on server or use deployment trigger
```

**Advantages:**
- Version control
- Change history
- Easy rollback
- Team collaboration

---

### Post-Deployment Verification

**After uploading, verify:**

1. Visit https://rowlettaa.org/
2. Hard refresh (Ctrl+F5 or Cmd+Shift+R) to clear cache
3. Check all pages
4. Verify changes appear correctly
5. Test on mobile device
6. Check browser console for errors

**If changes don't appear:**
- Hard refresh browser (Ctrl+F5)
- Clear browser cache
- Check file uploaded to correct location
- Verify file replaced old version
- Wait a few minutes for CDN/cache to update

### Backup Strategy

**Before every deployment:**

1. Download current `index.html` from server
2. Rename with date: `index-backup-2025-11-18.html`
3. Store in backups folder
4. Keep at least 5 most recent backups

**Quick rollback:**
If something breaks, upload the most recent backup file.

---

## JavaScript Functions Reference

The application uses 59 JavaScript functions, all actively used. Here's a reference for major functions.

### Global Utility Functions

#### Date and Time Functions

**`getRecurringDate(recurringType, year, month)`** - Line ~3069
- **Purpose:** Calculate date for recurring patterns (third Monday, last Saturday, etc.)
- **Parameters:**
  - `recurringType` - String like `'recurring-third-monday'`
  - `year` - 4-digit year
  - `month` - Month (0-11, JavaScript format)
- **Returns:** Date object for the calculated date
- **Used by:** Events page, schedule page, group conscience calculation

```javascript
// Example
const thirdMonday = getRecurringDate('recurring-third-monday', 2025, 11); // Dec 2025
```

---

**`getAllWeekdayDatesInMonth(dayName, year, month)`** - Line ~3095
- **Purpose:** Generate array of ALL occurrences of a weekday in a month
- **Parameters:**
  - `dayName` - String like `'tuesday'`
  - `year` - 4-digit year
  - `month` - Month (0-11)
- **Returns:** Array of Date objects
- **Used by:** Events page for series patterns

```javascript
// Example
const allTuesdays = getAllWeekdayDatesInMonth('tuesday', 2025, 11);
// Returns [Dec 2, Dec 9, Dec 16, Dec 23, Dec 30]
```

---

**`getDaysUntil(targetDate)`** - Line ~3150
- **Purpose:** Calculate days between today and target date
- **Parameters:** `targetDate` - Date object
- **Returns:** Number of days (can be negative for past dates)
- **Used by:** Event countdown timers

---

**`getCountdownText(days)`** - Line ~3165
- **Purpose:** Convert days number to human-readable countdown
- **Parameters:** `days` - Number of days
- **Returns:** String like "In 5 days" or "Tomorrow"
- **Used by:** Event cards

---

#### String and Formatting Functions

**`formatDate(date, format)`** - Line ~3180
- **Purpose:** Format Date object as string
- **Parameters:**
  - `date` - Date object
  - `format` - Format string (`'long'`, `'short'`, `'time'`)
- **Returns:** Formatted string
- **Examples:**
  - `'long'` → "Monday, December 25, 2025"
  - `'short'` → "12/25/2025"
  - `'time'` → "7:30 PM"

---

**`sanitizeHTML(str)`** - Line ~3210
- **Purpose:** Escape HTML to prevent XSS
- **Parameters:** `str` - String potentially containing HTML
- **Returns:** Sanitized string
- **Used by:** All content rendering functions

---

### Navigation Functions

**`showPage(pageId)`** - Line ~3300
- **Purpose:** Switch between pages in SPA
- **Parameters:** `pageId` - String ID of target page
- **Process:**
  1. Hides all pages
  2. Shows target page
  3. Updates navigation highlighting
  4. Runs page-specific initialization
  5. Scrolls to top
  6. Updates URL hash

```javascript
// Example
showPage('events');  // Shows events page
showPage('schedule'); // Shows schedule page
```

---

**`updateNavigation(pageId)`** - Line ~3350
- **Purpose:** Update navigation menu highlighting
- **Parameters:** `pageId` - Current page ID
- **Process:** Adds `active` class to current page link

---

**`handleNavClick(event)`** - Line ~3370
- **Purpose:** Handle navigation link clicks
- **Process:**
  1. Prevents default link behavior
  2. Extracts page ID from link
  3. Calls `showPage()`

---

### Events Page Functions

**`initEventsPage()`** - Line ~4200
- **Purpose:** Initialize events calendar page
- **Process:**
  1. Check if events already processed (cache)
  2. If not, process all events
  3. Render events
  4. Set up category filtering
  5. Initialize toggle buttons

---

**`processEventsData(eventsData)`** - Line ~4230
- **Purpose:** Process raw events into displayable format
- **Parameters:** `eventsData` - Array of event objects
- **Returns:** Object with `futureEvents` and `pastEvents` arrays
- **Process:**
  1. Loop through each event
  2. Parse date patterns
  3. Generate series dates if needed
  4. Calculate if future or past
  5. Filter events older than 6 months
  6. Sort chronologically

**Handles three date types:**
- Simple dates: `'2025-12-25'`
- Monthly recurring: `'recurring-third-monday'`
- Series patterns: `'recurring-all-tuesday:2025-12'`

---

**`renderEvent(eventData, isPast)`** - Line ~4050
- **Purpose:** Render single event card HTML
- **Parameters:**
  - `eventData` - Event object with date
  - `isPast` - Boolean, true if showing past event
- **Returns:** HTML string
- **Features:**
  - Color-coded by category
  - Shows multiple dates if series
  - Strikes through past dates
  - Displays speaker info if present
  - Shows countdown if upcoming
  - Map links
  - Potluck icons

---

**`filterEventsByCategory(category)`** - Line ~4280
- **Purpose:** Filter events by category
- **Parameters:** `category` - String (`'all'`, `'rowlett'`, `'speaker'`, etc.)
- **Process:**
  1. Uses cached processed events
  2. Filters by category
  3. Re-renders filtered list
  4. Updates active filter button

---

**`togglePastEvents()`** - Line ~4320
- **Purpose:** Show/hide past events section
- **Process:** Toggles visibility of past events container

---

### Schedule Page Functions

**`initSchedulePage()`** - Line ~3990
- **Purpose:** Initialize meeting schedule page
- **Process:**
  1. Calculate today's day of week
  2. Calculate current time
  3. Calculate next Group Conscience date
  4. Render schedule with highlighting
  5. Display today's meetings
  6. Show Group Conscience info

---

**`renderSchedule(scheduleData, currentDay, currentTime)`** - Line ~4100
- **Purpose:** Render weekly schedule HTML
- **Parameters:**
  - `scheduleData` - Meeting schedule array
  - `currentDay` - Today's day index (0-6)
  - `currentTime` - Current time for highlighting
- **Returns:** HTML string
- **Features:**
  - Highlights current day
  - Highlights current meeting
  - Shows open/closed badges
  - Displays meeting notes
  - Responsive layout

---

**`getTodaysMeetings(scheduleData, dayIndex)`** - Line ~4170
- **Purpose:** Get meetings for specific day
- **Parameters:**
  - `scheduleData` - Schedule array
  - `dayIndex` - Day index (0-6)
- **Returns:** Array of today's meetings
- **Used by:** "Today's Meetings" quick view

---

### Sobriety Calculator Functions

**`calculateSobriety(sobrietyDate)`** - Line ~4500
- **Purpose:** Calculate time sober from date
- **Parameters:** `sobrietyDate` - Date object of sobriety date
- **Returns:** Object with years, months, days, hours, minutes
- **Features:**
  - Handles leap years
  - Calculates exact time
  - Identifies next milestone

```javascript
// Example
const result = calculateSobriety(new Date('2020-01-15'));
// Returns: { years: 5, months: 10, days: 3, hours: 12, minutes: 30, nextMilestone: '6 years' }
```

---

**`getMilestone(days)`** - Line ~4550
- **Purpose:** Identify sobriety milestone based on days
- **Parameters:** `days` - Total days sober
- **Returns:** String describing milestone or null
- **Milestones:**
  - 1 day (24 hours)
  - 30 days
  - 60 days
  - 90 days
  - 6 months (180 days)
  - 9 months (270 days)
  - 1 year (365 days)
  - Multi-year anniversaries

---

**`displaySobrietyResult(result)`** - Line ~4590
- **Purpose:** Render sobriety calculation results
- **Parameters:** `result` - Object from `calculateSobriety()`
- **Process:** Creates formatted HTML with congratulations, time breakdown, milestone badges

---

### Literature Functions

**`initLiteraturePage()`** - Line ~5000
- **Purpose:** Initialize literature page
- **Process:**
  1. Load Big Book chapter links
  2. Display daily reflection
  3. Organize by category
  4. Set up PDF links

---

**`renderChapterLinks(chapters)`** - Line ~5050
- **Purpose:** Render Big Book chapter list
- **Parameters:** `chapters` - Array of chapter objects
- **Returns:** HTML string with links

---

**`getDailyReflection()`** - Line ~5100
- **Purpose:** Get today's daily reflection
- **Process:**
  1. Calculate day of year
  2. Fetch corresponding reflection
  3. Display with date

---

### Step Study Functions

**`initStepStudyPage()`** - Line ~4650
- **Purpose:** Initialize step study page
- **Process:**
  1. Load all 12 steps
  2. Set up step selector
  3. Load saved notes from localStorage
  4. Set up auto-save

---

**`loadStep(stepNumber)`** - Line ~4700
- **Purpose:** Load specific step content
- **Parameters:** `stepNumber` - Number 1-12
- **Process:**
  1. Display step text
  2. Show reflection questions
  3. Load saved notes
  4. Update progress indicator

---

**`saveStepNotes(stepNumber, notes)`** - Line ~4820
- **Purpose:** Save step notes to localStorage
- **Parameters:**
  - `stepNumber` - Number 1-12
  - `notes` - String content
- **Storage:** `localStorage.setItem('step-notes-' + stepNumber, notes)`

---

**`loadStepNotes(stepNumber)`** - Line ~4850
- **Purpose:** Load saved notes for step
- **Parameters:** `stepNumber` - Number 1-12
- **Returns:** Saved notes string or empty string

---

### Service Functions

**`initServicePage()`** - Line ~4870
- **Purpose:** Initialize service opportunities page
- **Process:**
  1. Load service opportunities data
  2. Categorize by type
  3. Render with contact info
  4. Set up external links

---

**`renderServiceOpportunities(opportunities)`** - Line ~4920
- **Purpose:** Render service opportunities list
- **Parameters:** `opportunities` - Array of service objects
- **Returns:** HTML string with cards

---

### History Functions

**`generateTimelineHTML(timelineData)`** - Line ~5321
- **Purpose:** Generate group history timeline
- **Parameters:** `timelineData` - Array of timeline period objects
- **Returns:** HTML string with visual timeline
- **Features:**
  - Chronological layout
  - Icons for each period
  - Expandable details
  - Highlights list

---

### Utility Functions

**`debounce(func, wait)`** - Line ~3250
- **Purpose:** Limit function call frequency
- **Parameters:**
  - `func` - Function to debounce
  - `wait` - Milliseconds to wait
- **Returns:** Debounced function
- **Used by:** Search, scroll handlers

---

**`isMobile()`** - Line ~3280
- **Purpose:** Detect if user on mobile device
- **Returns:** Boolean
- **Used by:** Responsive features

---

**`copyToClipboard(text)`** - Line ~5450
- **Purpose:** Copy text to clipboard
- **Parameters:** `text` - String to copy
- **Used by:** Sobriety calculator, share features

---

## Styling and Design System

### Tailwind CSS

The website uses **Tailwind CSS**, a utility-first CSS framework loaded via CDN.

**CDN Link** (line ~85):
```html
<script src="https://cdn.tailwindcss.com"></script>
```

**What is Tailwind?**

Instead of writing custom CSS, Tailwind provides utility classes:

```html
<!-- Traditional CSS -->
<div class="card">...</div>
<style>.card { padding: 1rem; margin: 1rem; background: white; }</style>

<!-- Tailwind CSS -->
<div class="p-4 m-4 bg-white">...</div>
```

### Common Tailwind Classes Used

**Spacing:**
- `p-4` - Padding: 1rem (16px)
- `m-4` - Margin: 1rem
- `px-6` - Padding left and right: 1.5rem
- `py-3` - Padding top and bottom: 0.75rem
- `mt-8` - Margin top: 2rem
- `space-y-4` - Vertical space between children: 1rem

**Colors:**
- `bg-blue-50` - Light blue background
- `text-blue-900` - Dark blue text
- `border-blue-400` - Medium blue border
- Numbers: 50 (lightest) to 900 (darkest)

**Layout:**
- `flex` - Flexbox container
- `grid` - Grid container
- `container` - Centered container with max-width
- `mx-auto` - Margin auto (centers)

**Responsive:**
- `sm:` - Small screens (640px+)
- `md:` - Medium screens (768px+)
- `lg:` - Large screens (1024px+)
- `xl:` - Extra large (1280px+)

**Example responsive:**
```html
<div class="text-sm md:text-base lg:text-lg">
  <!-- Small text on mobile, medium on tablet, large on desktop -->
</div>
```

### Color Palette

**Event Categories:**

| Category | Background | Border | Text |
|----------|-----------|--------|------|
| Rowlett | `bg-blue-50` | `border-blue-400` | `text-blue-900` |
| Speaker | `bg-purple-50` | `border-purple-400` | `text-purple-900` |
| Service | `bg-green-50` | `border-green-400` | `text-green-900` |
| Anniversary | `bg-yellow-50` | `border-yellow-400` | `text-yellow-900` |
| Area | `bg-indigo-50` | `border-indigo-400` | `text-indigo-900` |
| Fellowship | `bg-pink-50` | `border-pink-400` | `text-pink-900` |

**UI Colors:**
- Primary: Blue (`blue-600`, `blue-700`)
- Success: Green (`green-600`)
- Warning: Yellow (`yellow-500`)
- Danger: Red (`red-600`)
- Neutral: Gray (`gray-100` to `gray-900`)

### Typography

**Font Family:**

```css
font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
```

Loaded from Google Fonts CDN.

**Text Sizes:**
- `text-xs` - 0.75rem (12px)
- `text-sm` - 0.875rem (14px)
- `text-base` - 1rem (16px) - Default
- `text-lg` - 1.125rem (18px)
- `text-xl` - 1.25rem (20px)
- `text-2xl` - 1.5rem (24px)
- `text-3xl` - 1.875rem (30px)
- `text-4xl` - 2.25rem (36px)

**Font Weights:**
- `font-normal` - 400
- `font-medium` - 500
- `font-semibold` - 600
- `font-bold` - 700

### Responsive Design

**Breakpoints:**

```
sm:  640px  (Tablet)
md:  768px  (Tablet landscape)
lg:  1024px (Desktop)
xl:  1280px (Large desktop)
```

**Mobile-First Approach:**

Classes without prefix apply to all sizes. Prefixed classes apply at breakpoint and above.

```html
<div class="text-sm md:text-base lg:text-lg">
  <!-- Mobile: small, Tablet: base, Desktop: large -->
</div>

<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
  <!-- Mobile: 1 column, Tablet: 2 columns, Desktop: 3 columns -->
</div>
```

### Custom CSS

**Location:** Lines 100-1500

**Custom Animations:**

```css
@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

.fade-in {
    animation: fadeIn 0.3s ease-in;
}
```

**Print Styles:**

```css
@media print {
    nav, footer, .no-print {
        display: none;
    }
    .page {
        display: block !important;
    }
}
```

Ensures website prints nicely.

### Icons

**Font Awesome** loaded via CDN:

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
```

**Usage:**
```html
<i class="fas fa-calendar"></i>  <!-- Calendar icon -->
<i class="fas fa-map-marker-alt"></i>  <!-- Location pin -->
<i class="fas fa-users"></i>  <!-- People/group -->
```

**Common icons:**
- `fa-calendar` - Calendar
- `fa-clock` - Time
- `fa-map-marker-alt` - Location
- `fa-phone` - Phone
- `fa-envelope` - Email
- `fa-users` - Group/people
- `fa-book` - Book/literature
- `fa-home` - Home
- `fa-star` - Star/favorite

---

## Performance and Optimization

### File Size Optimization

**Current size:** 358KB

**Optimization techniques:**

1. **Single file** - Only one HTTP request
2. **Minification opportunity** - Could minify HTML/CSS/JS (not currently done for maintainability)
3. **CDN resources** - External resources cached by browser
4. **Inline critical CSS** - No external stylesheets to load
5. **No images** - All icons from Font Awesome

**Load time:**
- First visit: ~1-2 seconds (358KB + CDN resources)
- Subsequent visits: Instant (cached)

### Event Caching

**Problem:** Processing 50+ events on every category filter is slow.

**Solution:** Process once, cache results.

```javascript
let processedEvents = null;

function initEventsPage() {
    if (processedEvents) {
        // Use cached data - instant
        displayEvents(processedEvents);
        return;
    }

    // Process once
    processedEvents = processEventsData(eventsData);
    displayEvents(processedEvents);
}
```

**Result:** Category filtering is instant after initial load.

### Code Optimization

**Consolidated functions** (Version 1.1):

Eliminated duplicate date calculation functions:
- Before: `getThirdMonday()`, `getFirstSaturday()`, `getLastSaturday()`, `getRecurringDate()`
- After: Single `getRecurringDate()` function used everywhere

**Benefits:**
- Smaller file size
- Single source of truth
- Easier maintenance
- No duplicate logic

### Browser Caching

**Service Worker** (if implemented):

```javascript
self.addEventListener('install', (event) => {
    event.waitUntil(
        caches.open('rowlett-aa-v1').then((cache) => {
            return cache.addAll([
                '/',
                '/index.html'
            ]);
        })
    );
});
```

Allows offline access to entire website.

### PWA Optimization

**Manifest configuration:**

```json
{
    "name": "Rowlett Group of AA",
    "short_name": "Rowlett AA",
    "start_url": "/",
    "display": "standalone",
    "background_color": "#ffffff",
    "theme_color": "#2563eb",
    "icons": [
        {
            "src": "/icon-192.png",
            "sizes": "192x192",
            "type": "image/png"
        },
        {
            "src": "/icon-512.png",
            "sizes": "512x512",
            "type": "image/png"
        }
    ]
}
```

Enables:
- Install to home screen
- App-like experience
- Splash screen
- Theme color in browser

---

## Troubleshooting

### Events Not Displaying

**Symptom:** Events page is blank or shows no events.

**Possible causes:**

1. **JavaScript error** - Check browser console (F12)
   - Look for red error messages
   - Common: Syntax error in `eventsData` array

2. **Missing comma** in events array
   ```javascript
   // ❌ Wrong - missing comma
   {
       date: '2025-12-01',
       title: 'Event 1'
   }
   {
       date: '2025-12-02',
       title: 'Event 2'
   }

   // ✅ Correct - comma after first event
   {
       date: '2025-12-01',
       title: 'Event 1'
   },
   {
       date: '2025-12-02',
       title: 'Event 2'
   }
   ```

3. **All events are past** - Events older than 6 months automatically hide
   - Check "Show Past Events" toggle
   - Verify event dates are in future

4. **Invalid date format**
   ```javascript
   // ❌ Wrong formats
   date: '12/25/2025'
   date: 'December 25, 2025'

   // ✅ Correct format
   date: '2025-12-25'  // YYYY-MM-DD
   ```

**Solutions:**
1. Open browser console (F12)
2. Look for error messages
3. Fix syntax errors
4. Validate JSON syntax at https://jsonlint.com/
5. Clear browser cache (Ctrl+F5)

---

### Schedule Not Showing

**Symptom:** Meeting schedule is blank.

**Possible causes:**

1. **JavaScript error** in `meetingSchedule` array
2. **Missing dayIndex** field
3. **Invalid meeting type** (must be `"open"` or `"closed"`)

**Check:**
```javascript
// Ensure each day has dayIndex
{ day: "Monday", dayIndex: 1, meetings: [...] }
// dayIndex: 0=Sunday, 1=Monday, ... 6=Saturday
```

**Solution:**
1. Check console for errors
2. Verify all days 0-6 are present
3. Ensure `meetings` is an array

---

### Past Events Still Showing

**Symptom:** Old events still appear in "Upcoming Events".

**Explanation:** This is expected behavior for:
- Recurring events (continue showing until next occurrence passes)
- Events less than 6 months old

**Intentional behavior:**
- Events automatically hide after all dates pass
- 6-month cutoff for past events
- Recurring events show next occurrence

**To manually hide an event:**
Comment it out:
```javascript
/*  {
    date: '2025-01-01',
    title: 'Old Event',
    // ... rest
},  */
```

---

### Broken Layout/Styling

**Symptom:** Page looks broken, unstyled, or misaligned.

**Possible causes:**

1. **Tailwind CSS not loading** - Check internet connection
2. **Unclosed HTML tag** - Missing closing `</div>`, `</p>`, etc.
3. **Invalid Tailwind class** - Typo in class name

**Solutions:**

1. **Check Tailwind CDN:**
   - Open browser console Network tab
   - Look for failed requests to cdn.tailwindcss.com
   - If failed, check internet connection

2. **Validate HTML:**
   - Use https://validator.w3.org/
   - Upload or paste your HTML
   - Fix any errors reported

3. **Check for unclosed tags:**
   ```html
   <!-- ❌ Wrong - missing closing div -->
   <div class="container">
       <p>Content</p>

   <!-- ✅ Correct -->
   <div class="container">
       <p>Content</p>
   </div>
   ```

---

### JavaScript Errors

**Symptom:** Features not working, console shows errors.

**How to check:**
1. Press F12 to open browser DevTools
2. Click "Console" tab
3. Look for red error messages

**Common errors:**

**1. Uncaught SyntaxError: Unexpected token**
- Cause: Missing comma, quote, or bracket
- Solution: Check line number in error, fix syntax

**2. Uncaught ReferenceError: X is not defined**
- Cause: Function or variable doesn't exist
- Solution: Check spelling, ensure function is defined

**3. Uncaught TypeError: Cannot read property 'X' of null**
- Cause: Trying to access element that doesn't exist
- Solution: Check element IDs, ensure HTML is correct

---

### Changes Not Appearing After Upload

**Symptom:** Updated file, but website still shows old content.

**Cause:** Browser cache or CDN cache.

**Solutions:**

1. **Hard refresh:**
   - Windows/Linux: Ctrl + F5
   - Mac: Cmd + Shift + R

2. **Clear browser cache:**
   - Chrome: Settings > Privacy > Clear browsing data
   - Firefox: Options > Privacy > Clear Data
   - Safari: Safari > Clear History

3. **Check file uploaded correctly:**
   - Download file from server
   - Compare to local file
   - Verify file size matches

4. **Bypass cache with query string:**
   - Add `?v=2` to URL: `https://rowlettaa.org/?v=2`
   - Changes number each update

5. **Wait for CDN:**
   - Some hosts cache files
   - May take 5-15 minutes to update
   - Check again later

---

### Mobile Display Issues

**Symptom:** Website looks wrong on mobile.

**Possible causes:**

1. **Missing viewport meta tag** - Should be present (line ~20)
   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   ```

2. **Fixed widths** - Avoid `width: 600px;` in custom CSS
   - Use percentage or max-width instead

3. **Text too small** - Ensure minimum font size
   - Use `text-sm` or larger on mobile

**Testing on desktop:**
1. Open browser DevTools (F12)
2. Click device icon (toggle device toolbar)
3. Select mobile device (iPhone, Pixel, etc.)
4. Test responsiveness

---

### Google Maps Links Not Working

**Symptom:** Map links don't open or go to wrong location.

**Solution:**

Ensure proper URL format:
```javascript
// ✅ Correct format
mapLink: 'https://maps.google.com/?q=362+Oaks+Trail+162+Garland+TX+75043'

// Replace spaces with +
// Full address including ZIP
```

**To generate map link:**
1. Go to Google Maps
2. Search for address
3. Click "Share"
4. Copy link
5. Use in `mapLink` field

---

## Support

### Getting Help

**For content updates:**
- **Email:** rowlettaa@gmail.com
- **Phone:** (972) 925-0096
- **Best times:** Weekdays 9 AM - 5 PM

**For technical issues:**
1. Check this README troubleshooting section
2. Check browser console (F12) for errors
3. Validate HTML at https://validator.w3.org/
4. Test in different browsers
5. Contact technical support

---

### Helpful Tools

**Validation:**
- **HTML Validator:** https://validator.w3.org/
- **JSON Validator:** https://jsonlint.com/
- **CSS Validator:** https://jigsaw.w3.org/css-validator/

**Testing:**
- **Browser DevTools:** Press F12 in any browser
- **Mobile Emulator:** In DevTools, click device icon
- **PageSpeed Insights:** https://pagespeed.web.dev/

**Editing:**
- **VS Code:** https://code.visualstudio.com/ (recommended)
- **Sublime Text:** https://www.sublimetext.com/
- **Notepad++:** https://notepad-plus-plus.org/

**FTP Clients:**
- **FileZilla:** https://filezilla-project.org/ (free, cross-platform)
- **Cyberduck:** https://cyberduck.io/ (Mac/Windows)
- **WinSCP:** https://winscp.net/ (Windows)

---

### Quick Tips

1. **Always backup** `index.html` before making changes
   - Download from server
   - Rename with date: `index-backup-2025-11-18.html`

2. **Test locally** before uploading
   - Open file in browser
   - Check all changes
   - Verify no errors

3. **Use a code editor** with syntax highlighting
   - VS Code recommended
   - Highlights syntax errors
   - Auto-completes code

4. **Validate dates** - Use YYYY-MM-DD format
   - ✅ `'2025-12-25'`
   - ❌ `'12/25/2025'`

5. **Check commas** - Each event needs comma after it (except last)
   ```javascript
   { event: 1 },  // ✅ Comma
   { event: 2 },  // ✅ Comma
   { event: 3 }   // ✅ No comma (last item)
   ```

6. **Use browser console** - Press F12 to see errors
   - Red messages = errors to fix
   - Yellow warnings = optional improvements

7. **Hard refresh after changes** - Ctrl+F5 (Windows) or Cmd+Shift+R (Mac)
   - Clears cache
   - Shows latest changes

8. **Keep it simple** - Don't overcomplicate
   - Copy existing examples
   - Change only what's needed
   - Test after each change

---

## Changelog

### Version 1.1 (November 2025)

**New Features:**
- **Event series pattern:** `recurring-all-[day]:[YYYY-MM]` for month-wide event series
  - Example: `recurring-all-tuesday:2025-12` generates all Tuesdays in December
  - Displays as single card with all dates
  - Past dates automatically struck through
- **Event caching:** Events processed once, cached for instant category filtering
- **Comprehensive README:** Complete application documentation and update guide

**Code Improvements:**
- Consolidated date calculation functions (eliminated duplicates)
- Removed unused functions (`getThirdMonday`, `getLastSaturday`, `getFirstSaturday`)
- Global `getRecurringDate()` function used by both events and schedule pages
- Single source of truth for recurring date logic
- 100% function utilization (59 functions, all used)

**Events Added:**
- Matt C. speaker event (December 1, 2025)
- December Tuesday speaker series (Rowlett Group members)
- How to Chair a Meeting workshop (December 6, 2025)
- GSR Orientation workshop (January 18, 2026)

**Performance:**
- File size: 358KB (optimized)
- Event processing: Cached for instant filtering
- No dead code: All functions actively used

**Documentation:**
- Complete README.md rewrite
- Practical update templates
- Comprehensive function reference
- Troubleshooting guide
- Deployment instructions

---

### Version 1.0 (October 2025)

**Initial Release:**

**Pages/Sections (12):**
- Home page with navigation
- Events calendar with filtering
- Meeting schedule with highlighting
- About us / Group information
- Contact information
- Sobriety calculator
- Literature library
- Step study guide with notes
- Newcomer resources
- Service opportunities
- Group history timeline
- Resources and links

**Features:**
- Dynamic events system with recurring patterns
- 15 weekly meetings
- Real-time schedule highlighting
- Sobriety calculator with milestones
- Interactive step study with localStorage notes
- Responsive mobile design
- PWA support (offline capable)
- SEO optimized
- Single-file architecture (275KB)

**Technologies:**
- Vanilla JavaScript (no frameworks)
- Tailwind CSS via CDN
- Font Awesome icons
- Google Fonts (Inter)
- LocalStorage for persistence

---

## Project Information

**Last Updated:** November 2025
**Maintained by:** Rowlett Group of AA
**Website:** https://rowlettaa.org/
**Contact:** rowlettaa@gmail.com | (972) 925-0096
**Location:** 362 Oaks Trail #162, Garland, TX 75043

**Version:** 1.1
**License:** Use restricted to Rowlett Group of AA
**Platform:** Single-file HTML/CSS/JavaScript application

---

## Quick Reference Card

**Most Common Tasks:**

| Task | Location | Action |
|------|----------|--------|
| Add event | Line 3226 | Copy template, paste before `];`, edit fields |
| Remove event | Line 3226 | Find event, delete or comment out |
| Add meeting | Line 4014 | Find day, add meeting object to array |
| Change Group Conscience | Line 3998 | Update recurring pattern |
| Update contact info | Line 2850 | Edit phone, email, address |
| Change copyright | Line 3050 | Edit footer (year auto-updates) |
| Test changes | N/A | Open index.html in browser, press F12 |
| Deploy | N/A | Upload via FTP, cPanel, or Git |
| Fix errors | N/A | Press F12, check Console tab |
| Backup | N/A | Download current file, rename with date |

**Emergency Rollback:**
1. Find most recent backup file
2. Upload via FTP or cPanel
3. Overwrites broken version
4. Hard refresh browser (Ctrl+F5)

---

**End of README**
