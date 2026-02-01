# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file web application for personal color analysis (퍼스널칼라 진단). The project consists of a standalone HTML file with embedded CSS and JavaScript that provides an interactive quiz to determine a user's seasonal color type.

## File Structure

- `personal-color.html` - Main application (single self-contained HTML file with inline CSS/JS)
- `.idx/dev.nix` - Firebase Studio environment configuration
- `.idx/airules.md` - Gemini AI rules for Firebase Studio Nix projects

## Development Environment

This project runs in Firebase Studio (Project IDX), which uses Nix for environment configuration.

### Environment Configuration

The `.idx/dev.nix` file defines the development environment. Currently minimal configuration as this is a static HTML project with no build dependencies.

To modify the environment:
1. Edit `.idx/dev.nix` with required packages/tools
2. Reload the workspace for changes to take effect

### Running the Application

Since this is a static HTML file, simply open it in a web browser:

```bash
# View the file locally
xdg-open personal-color.html

# Or serve via the built-in web server at http://localhost:80
```

No build process or package installation is required.

## Application Architecture

### Single-File Structure

The `personal-color.html` file contains three main sections:
1. **HTML** - Three screen layouts (start, question, result)
2. **CSS** - Responsive styling with gradient themes and animations
3. **JavaScript** - Quiz logic, scoring system, and UI state management

### Key Components

**Screens:**
- `startScreen` - Landing page with call-to-action
- `questionScreen` - 12-question quiz with progress tracking
- `resultScreen` - Detailed results with color palettes and styling tips

**Data Structures:**
- `questions[]` - Array of 12 question objects with scoring weights for each season type
- `results{}` - Object containing detailed information for each of 4 seasonal color types (spring, summer, autumn, winter)
- `scores{}` - Runtime tracking of accumulated points per season type

**Scoring System:**
Each answer option contains a `scores` object with weights for all four seasonal types:
```javascript
{ spring: 3, summer: 0, autumn: 1, winter: 0 }
```

The highest total score determines the user's personal color type.

### State Management

- Uses plain JavaScript with DOM manipulation
- LocalStorage for saving results (`personalColorResult`, `personalColorDate`)
- No external dependencies or frameworks

## Key Features

- 12-question diagnostic quiz
- 4 seasonal color types with detailed results
- Responsive design (mobile-optimized)
- Progress tracking
- Answer navigation (back/forward)
- Result download as text file
- Placeholder for KakaoTalk sharing (requires developer registration)

## Customization Points

When modifying the application:

**Adding/Editing Questions:**
- Modify the `questions` array
- Ensure each option has scores for all four types (spring, summer, autumn, winter)
- Update `questions.length` references if changing question count

**Changing Result Content:**
- Edit the `results` object
- Each type requires: type, subtitle, description, colors[], tips[], avoid, celebrities[]

**Styling Changes:**
- All CSS is in the `<style>` section
- Main color scheme uses `#667eea` and `#764ba2` gradient
- Responsive breakpoint at 600px

**Language/Localization:**
- Currently Korean only
- All text is inline in HTML/JS - search and replace for translation
- Update `<html lang="ko">` attribute when changing language
