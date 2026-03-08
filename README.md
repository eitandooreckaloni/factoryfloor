# FactoryFloor | Command Center

A dark-themed command center dashboard for monitoring an AI app factory pipeline.

## Features

- **Real-time Pipeline Monitoring**: Fetches data every 15 seconds from the pipeline API
- **Kanban Board Interface**: Visual representation of ideas moving through pipeline stages
- **Status Counters**: Glowing status indicators showing deployed, building, QA failures, and killed ideas
- **Interactive Detail Panel**: Click any idea card to view detailed metrics, QA status, and build information
- **Radar Charts**: Visual representation of idea rankings across 6 dimensions
- **Industrial Dark Theme**: Neon accents (cyan, magenta, green, amber) on dark surfaces with monospace fonts
- **Production Ready**: TypeScript, error handling, responsive design

## Pipeline Stages

- **Active**: New ideas in the pipeline
- **Specced**: Ideas with complete specifications
- **Designed**: Ideas with UI/UX design complete
- **Building**: Ideas currently being built
- **Built**: Ideas with initial build complete
- **Developed**: Ideas with development complete
- **QA Pass**: Ideas that passed quality assurance
- **QA Fail**: Ideas that failed quality assurance
- **Deployed**: Live production ideas

## Tech Stack

- **Next.js 14**: React framework with App Router
- **TypeScript**: Type-safe development
- **Tailwind CSS**: Utility-first styling with dark theme
- **Custom SVG Components**: Radar charts and visualizations

## Getting Started

1. **Install dependencies**:
   ```bash
   npm install
   ```

2. **Run development server**:
   ```bash
   npm run dev
   ```

3. **Open**: [http://localhost:3000](http://localhost:3000)

## API Integration

The dashboard connects to `https://eitan-openclaw.duckdns.org/api/pipeline` and expects JSON in the following format:

```json
{
  "next_id": 123,
  "ideas": [
    {
      "id": 1,
      "name": "Idea Name",
      "status": "active",
      "one_liner": "Brief description",
      "ranking": {
        "pain": 8,
        "market": 7,
        "buildability": 9,
        "moat": 6,
        "revenue": 7,
        "virality": 8,
        "weighted_score": 7.5
      },
      "repo_url": "https://github.com/...",
      "live_url": "https://example.com",
      "developer_output": {
        "build_status": "completed",
        "files_implemented": ["file1.tsx", "file2.ts"],
        "build_errors": []
      },
      "qa_output": {
        "verdict": "pass",
        "build_ok": true,
        "lint_ok": true,
        "issues": [],
        "coverage": {
          "pages_found": 5,
          "pages_expected": 5,
          "endpoints_found": 3,
          "endpoints_expected": 3,
          "components_found": 12,
          "components_expected": 12
        }
      }
    }
  ]
}
```

## Production Build

```bash
npm run build
npm start
```

## Architecture

- **Real-time Updates**: Uses `useEffect` with `setInterval` for periodic API polling
- **State Management**: React hooks for local state management
- **Error Handling**: Comprehensive error handling for API failures
- **Performance**: Optimized rendering with proper React patterns
- **Accessibility**: Keyboard navigation and screen reader support
- **Responsive**: Adapts to different screen sizes

## Customization

- Modify `STATUS_CONFIG` in `page.tsx` to adjust pipeline stages and colors
- Update API endpoint in the `fetchData` function
- Customize colors and themes in `tailwind.config.js`
- Adjust polling interval (currently 15 seconds) in the `useEffect` hook