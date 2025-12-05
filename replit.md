# Clio - Cloud Notes App

## Overview
Clio is a full-stack notes application with cloud storage and user authentication. It features a clean, Notion/Linear-inspired UI with wiki-style linking capabilities, rich markdown editor, note tagging, and version history for comprehensive note management.

## Tech Stack
- **Frontend**: React with TypeScript, Tailwind CSS, shadcn/ui components
- **Backend**: Node.js + Express.js
- **Database**: PostgreSQL with Drizzle ORM
- **Markdown Editor**: @uiw/react-md-editor with live preview
- **Authentication**: bcrypt password hashing, JWT tokens in HTTP-only cookies
- **State Management**: TanStack Query (React Query)

## Project Structure
```
├── client/                  # Frontend React application
│   ├── src/
│   │   ├── components/      # React components
│   │   │   ├── auth-screen.tsx      # Login/Register form
│   │   │   ├── notes-sidebar.tsx    # Left sidebar with notes list & tags
│   │   │   ├── note-editor.tsx      # Main editor with backlinks & tags
│   │   │   └── version-history.tsx  # Version history sheet component
│   │   ├── lib/
│   │   │   ├── auth.tsx     # Auth context and hooks
│   │   │   ├── theme.tsx    # Dark/light theme provider
│   │   │   └── queryClient.ts # TanStack Query setup
│   │   ├── pages/
│   │   │   └── home.tsx     # Main notes page
│   │   └── App.tsx          # Root component
├── server/
│   ├── index.ts             # Express server entrypoint
│   ├── routes.ts            # API routes (auth + notes + tags + versions)
│   ├── auth.ts              # Auth utilities (JWT, bcrypt)
│   ├── db.ts                # Database connection
│   └── storage.ts           # Storage interface with PostgreSQL
├── shared/
│   └── schema.ts            # Data models, Drizzle schema, Zod schemas
```

## Data Model
### Users
- `id`: UUID (primary key)
- `email`: Unique email address
- `passwordHash`: bcrypt hashed password
- `createdAt`: Account creation timestamp

### Notes
- `id`: UUID (primary key)
- `userId`: Foreign key to users
- `title`: Note title
- `content`: Note content (supports wiki links [[Note Title]] and markdown)
- `createdAt`: Creation timestamp
- `updatedAt`: Last update timestamp

### Tags
- `id`: UUID (primary key)
- `userId`: Foreign key to users
- `name`: Tag name
- `color`: Hex color code for visual identification

### NoteTags (Join Table)
- `noteId`: Foreign key to notes
- `tagId`: Foreign key to tags

### NoteVersions
- `id`: UUID (primary key)
- `noteId`: Foreign key to notes
- `title`: Snapshot of note title at this version
- `content`: Snapshot of note content at this version
- `version`: Auto-incrementing version number
- `createdAt`: Version creation timestamp

## API Endpoints

### Authentication
- `POST /api/register` - Create new account
- `POST /api/login` - Login with email/password
- `POST /api/logout` - Clear session
- `GET /api/me` - Get current user

### Notes (require authentication)
- `GET /api/notes` - Get all notes for current user (with tags)
- `GET /api/notes/:id` - Get single note (with tags)
- `POST /api/notes` - Create new note
- `PUT /api/notes/:id` - Update note (auto-creates version snapshot)
- `DELETE /api/notes/:id` - Delete note
- `POST /api/notes/import` - Bulk import notes

### Tags (require authentication)
- `GET /api/tags` - Get all tags for current user
- `POST /api/tags` - Create new tag
- `PUT /api/tags/:id` - Update tag
- `DELETE /api/tags/:id` - Delete tag
- `PUT /api/notes/:id/tags` - Update note's tags

### Version History (require authentication)
- `GET /api/notes/:id/versions` - Get version history for a note
- `GET /api/notes/:id/versions/:versionId` - Get specific version
- `POST /api/notes/:id/versions/:versionId/restore` - Restore note to specific version

## Features
1. **User Authentication**: Email + password with secure bcrypt hashing
2. **Auto-save**: Notes save automatically with 300ms debounce
3. **Wiki-style Links**: Use [[Note Title]] syntax to link notes
4. **Backlinks Panel**: See all notes that link to the current note
5. **Dark/Light Theme**: Toggle between themes (persisted in localStorage)
6. **Search**: Client-side search by title and content
7. **Export/Import**: Download notes as JSON, import from JSON file
8. **Note Tagging**: Organize notes with colored tags, filter by tag
9. **Rich Markdown Editor**: Three modes (Edit, Preview, Live split-view) with formatting toolbar
10. **Version History**: Automatic version snapshots on each edit, restore to any previous version

## Running the App
The app runs on port 5000 with `npm run dev`. Both frontend and backend are served from the same port.

## Database Commands
- `npm run db:push` - Push schema changes to database
- `npm run db:push --force` - Force push schema changes

## Recent Changes
- Implemented note tagging system with color-coded tags
- Added rich text markdown editor with Edit/Preview/Live modes
- Integrated @uiw/react-md-editor with formatting toolbar
- Added comprehensive version history with restore functionality
- Version snapshots created automatically on note updates
