# NASA Space Biology Knowledge Engine

A modern, responsive search engine for NASA space biology research articles with advanced filtering capabilities and Firebase Realtime Database integration.

## Live Demo
(Space Bio Explorer) [https://n08e48j2n8h1-deploy.space.z.ai/]

## AI Model
(Space Bio AI Model) [https://huggingface.co/Gka60/space-apps-challenge-1000]

## Features

- **NASA-style Design**: Clean, minimalist interface with stunning space-themed header featuring astronaut and Earth imagery
- **Firebase Integration**: Real-time data synchronization with Firebase Realtime Database
- **Smart Search**: Search through article titles and abstracts from live database
- **Advanced Filtering System**: 
  - Category/Topic filtering
  - Author filtering  
  - Year range filtering with slider
  - Active filter display with individual clear options
- **Rich Article Cards**: Display titles, abstracts, graphical abstracts, authors, years, categories, and similar articles
- **Responsive Design**: Works seamlessly on desktop and mobile devices
- **Loading Animations**: Smooth loading states during search and data fetching
- **Error Handling**: Comprehensive error handling with retry functionality
- **Visual Effects**: 
  - Space-themed header with parallax effect
  - Floating search bar with glassmorphism
  - Fade-in animations and pulse effects
- **Filter Management**: Clear all filters or remove individual filters

## Firebase Integration

### Database Configuration
- **Database URL**: `https://<your-firebase-project-name>default-rtdb.firebaseio.com/`
- **API Key**: `AIzaS***************************`
- **Real-time Data**: Articles are fetched from Firebase Realtime Database
- **API Endpoint**: `/api/articles` handles server-side data fetching

### Data Structure
The Firebase database expects articles with the following structure:
```json
{
  "articles": {
    "article_id_1": {
      "title": "Article Title",
      "abstract": "Article abstract content",
      "link": "https://example.com/article",
      "graphical_abstract_url": "https://example.com/image.jpg",
      "similar_articles": "url1,url2,url3",
      "year": 2023,
      "category": "Plant Biology",
      "author": "Dr. Name"
    }
  }
}
```

## Project Structure

```
src/
├── app/
│   ├── page.tsx              # Main application component with Firebase integration
│   ├── layout.tsx            # Root layout
│   ├── globals.css           # Global styles and animations
│   └── api/
│       └── articles/
│           └── route.ts      # API route for Firebase data fetching
├── components/
│   └── ui/                   # shadcn/ui components
├── lib/
│   ├── firebase.ts           # Firebase configuration and setup
│   └── utils.ts              # Utility functions
└── hooks/
    └── use-toast.ts          # Toast notifications
```

## API Endpoints

### GET /api/articles
Fetches articles from Firebase Realtime Database with optional filtering.

**Query Parameters:**
- `search`: Search term for title and abstract
- `category`: Filter by category
- `author`: Filter by author
- `yearMin`: Minimum year filter
- `yearMax`: Maximum year filter

**Response:**
```json
{
  "articles": [...],
  "total": 10,
  "message": "Articles fetched successfully"
}
```

## Getting Started

1. The application is already running on `http://localhost:3000`
2. Articles are automatically loaded from Firebase on page load
3. Try searching for terms like:
   - "plant growth"
   - "muscle atrophy"
   - "radiation exposure"
   - "bone density"
   - "photosynthesis"

4. Use the filtering system:
   - Click "Show Filters" to display filtering options
   - Select a category to filter by research topic
   - Choose an author to see their publications
   - Use the year range slider to filter by publication date
   - Combine multiple filters for precise results
   - Click "Clear All" to reset all filters

## Data Loading

### Initial Load
- Articles are fetched from Firebase when the app loads
- Loading skeleton is shown during data fetching
- Error handling with retry functionality if Firebase connection fails

### Real-time Updates
- The app can be extended to listen for real-time Firebase updates
- Current implementation fetches data on load and search

### Error Handling
- Comprehensive error handling for Firebase connection issues
- User-friendly error messages with retry options
- Graceful fallback to empty state if database is unavailable

## Data Format

The application expects data with the following fields:

- `title`: Article title
- `link`: URL to the full article
- `abstract`: Article abstract/description
- `graphical_abstract_url`: URL to graphical abstract image (optional)
- `similar_articles`: Comma-separated URLs to similar articles (optional)
- `year`: Publication year (optional)
- `category`: Research category/topic (optional)
- `author`: Author name (optional)

### Sample Data Row

```json
{
  "title": "Spaceflight Affects Plant Growth",
  "link": "https://example.com/article",
  "abstract": "This study examines plant growth in microgravity...",
  "graphical_abstract_url": "https://example.com/image.jpg",
  "similar_articles": "https://example.com/similar1,https://example.com/similar2",
  "year": 2023,
  "category": "Plant Biology",
  "author": "Dr. Sarah Johnson"
}
```

## Filtering System

### Available Filters

1. **Search Bar**: Full-text search in titles and abstracts
2. **Category Filter**: Filter by research categories (Plant Biology, Human Physiology, etc.)
3. **Author Filter**: Filter by specific authors
4. **Year Range Filter**: Slider to filter articles by publication year

### Filter Features

- **Toggle Panel**: Show/hide filter panel to save screen space
- **Active Filter Indicators**: Visual badges showing active filters
- **Individual Filter Clear**: Remove specific filters without clearing others
- **Clear All**: Reset all filters at once
- **Real-time Results**: See filtered results count as you adjust filters
- **Responsive Layout**: Filters adapt to mobile and desktop screens

### Filter Categories Available

- Plant Biology
- Human Physiology  
- Radiation Biology
- Immunology
- Microbiology
- Biochemistry
- Neuroscience

## Search Functionality

- Searches through both title and abstract fields
- Case-insensitive matching
- Real-time search results
- Loading states during search
- "No results" handling with helpful suggestions

## Design System

- **Colors**: 
  - Primary: #005288 (NASA blue)
  - Background: White with space-themed header
  - Text: Gray scale with white text on header
- **Typography**: Clean, readable fonts with responsive sizing
- **Components**: shadcn/ui component library
- **Responsive**: Mobile-first design approach
- **Visual Effects**:
  - Glassmorphism search bar
  - Animated fade-in effects
  - Pulse animations
  - Backdrop blur effects
  - Gradient overlays

### Header Design

- **Background**: High-quality space image with astronaut and Earth
- **Overlay**: Gradient overlay for text readability
- **Content**: Large title, subtitle, and feature badges
- **Animation**: Fade-in effect on load
- **Badges**: Glassmorphism style with backdrop blur

## Key Components

### Search Bar
- Centered layout with glow animation
- Keyboard support (Enter to search)
- Loading state indicator
- Placeholder text with examples

### Article Cards
- Title with NASA blue color
- Abstract text (truncated to 300 characters)
- Graphical abstract thumbnail (when available)
- "Read More" button linking to original article
- Similar articles section with clickable links

### Loading States
- Skeleton cards during search
- Spinning indicator in search button
- Smooth transitions and animations

## Getting Started

1. The application is already running on `http://localhost:3000`
2. Try searching for terms like:
   - "plant growth"
   - "muscle atrophy"
   - "radiation exposure"
   - "bone density"
   - "photosynthesis"

3. Use the filtering system:
   - Click "Show Filters" to display filtering options
   - Select a category to filter by research topic
   - Choose an author to see their publications
   - Use the year range slider to filter by publication date
   - Combine multiple filters for precise results
   - Click "Clear All" to reset all filters

## Usage Examples

### Example 1: Basic Search
1. Type "plant" in the search bar
2. Press Enter or click the search button
3. View all plant-related research articles

### Example 2: Category Filtering
1. Click "Show Filters"
2. Select "Human Physiology" from the category dropdown
3. Click search to see all human physiology articles

### Example 3: Combined Filtering
1. Search for "radiation"
2. Select "Radiation Biology" category
3. Set year range to 2022-2024
4. See recent radiation biology research

### Example 4: Author Search
1. Click "Show Filters"
2. Select "Dr. Sarah Johnson" from author dropdown
3. View all publications by this author

## Future Enhancements

- CSV file upload functionality
- Pagination for large result sets
- Advanced filtering (by year, topic, etc.)
- Analytics dashboard
- Export functionality
- Bookmarking system
- Advanced search operators

## Technology Stack

- **Framework**: Next.js 15 with App Router
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **UI Components**: shadcn/ui
- **Icons**: Lucide React
- **Data Handling**: Custom CSV parser

## Sample Data

The application includes sample NASA space biology research articles covering:
- Plant biology in space
- Human physiology changes
- Radiation effects
- Bone and muscle atrophy
- Immune system changes
- Microbiome adaptation
- Cardiovascular adaptation
- Neurovestibular changes

This provides a realistic demonstration of the search functionality with actual space biology research topics.....
