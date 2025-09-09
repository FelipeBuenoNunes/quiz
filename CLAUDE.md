# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Brazilian Portuguese quiz game called "Jogo dos Baús" (Chest Game) built as a single-page web application. The game presents 10 randomly selected questions from a pool of 30 questions, where players click on chests to answer trivia questions and progress through the game.

## Architecture

- **Single-file application**: All functionality is contained in `index.html` with embedded CSS and JavaScript
- **Client-side only**: No server dependencies, runs entirely in the browser
- **Dual data loading**: Questions load from `perguntas.json` via HTTP or fall back to embedded questions in the HTML for `file://` protocol support
- **Progressive Web App features**: Responsive design, dark/light theme toggle, localStorage for game progress persistence

## File Structure

- `index.html` - Main game application (CSS, HTML, JavaScript all embedded)
- `perguntas.json` - External question database (30 trivia questions in Portuguese)
- `README.md` - Basic project description
- `.git/` - Git repository

## Development Commands

This is a vanilla HTML/CSS/JavaScript project with no build process, dependencies, or testing framework configured. To develop or test:

1. **Running the game**: Open `index.html` directly in a web browser or serve via local HTTP server
2. **Testing questions**: Modify `perguntas.json` to add/edit questions following the existing format
3. **Local development**: Use any static file server (e.g., `python -m http.server` or VS Code Live Server extension)

## Key Technical Details

### Question Format
Each question in `perguntas.json` follows this structure:
```json
{
    "id": number,
    "question": "string",
    "options": ["option1", "option2", "option3", "option4"],
    "correctIndex": number,
    "explanation": "string",
    "explanationWrong": "string (optional)"
}
```

### Game State Management
- Uses `localStorage` for progress persistence
- Game state includes: opened chests, score, timer, selected questions, theme preference
- Automatically saves/loads progress on page refresh

### Accessibility Features
- Keyboard navigation support (arrow keys, Enter, Escape)
- ARIA labels and roles for screen readers
- High contrast dark theme toggle
- Focus management for modal interactions

## Localization
All content is in Brazilian Portuguese, including:
- UI text and instructions
- Question content
- Error messages and explanations