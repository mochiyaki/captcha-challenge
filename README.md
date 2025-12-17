# CAPTCHA Challenge

An interactive CAPTCHA challenge game built with React, TypeScript, and Tailwind CSS to test and demonstrate various CAPTCHA mechanisms while providing an engaging user experience.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Project Structure](#project-structure)
- [Specifications](#specifications)
- [Components](#components)
- [Installation](#installation)
- [Usage](#usage)
- [Development](#development)
- [Technologies](#technologies)

## Introduction

CAPTCHA Challenge is a modern web application that transforms the typically mundane CAPTCHA experience into an interactive game. Users are presented with a series of three randomly selected CAPTCHA challenges that test different human verification methods. The application tracks performance metrics including completion time, accuracy, and error rates, providing a final score and human-like assessment.

The project serves as both a demonstration of various CAPTCHA technologies and an exploration of user experience design for security mechanisms.

## Features

- **Multiple CAPTCHA Types**: Four different challenge types for varied user interaction
- **Real-time Scoring**: Dynamic scoring system with time bonuses and accuracy rewards
- **Audio Feedback**: Sound effects for user interactions and results
- **Performance Analytics**: Detailed statistics including speed ratings and human assessment
- **Responsive Design**: Mobile-friendly interface with modern UI
- **Accessibility**: Keyboard navigation and screen reader support

## Project Structure

```
captcha/
├── src/
│   ├── components/
│   │   ├── ArrowSequenceCaptcha.tsx    # Arrow sequence challenge component
│   │   ├── DistortedTextCaptcha.tsx    # Text recognition with distortion
│   │   ├── ImageGridCaptcha.tsx        # Image selection challenge
│   │   └── SliderCaptcha.tsx           # Slider puzzle component
│   ├── App.tsx                         # Main application component
│   ├── audio.ts                        # Audio system for sound effects
│   ├── captchaGenerators.ts            # CAPTCHA generation logic
│   ├── main.tsx                        # Application entry point
│   ├── types.ts                        # TypeScript type definitions
│   └── index.css                       # Global styles
├── public/
├── package.json                        # Project dependencies and scripts
├── vite.config.ts                      # Vite configuration
├── tailwind.config.js                  # Tailwind CSS configuration
├── tsconfig.json                       # TypeScript configuration
└── README.md                          # This file
```

## Specifications

### CAPTCHA Types

1. **Distorted Text** (`text`)
   - Random 6-character alphanumeric string
   - Canvas-rendered with noise, wavy lines, and character rotation
   - User must type the exact characters displayed

2. **Image Selection** (`image_grid`)
   - Grid of 12 emoji images with 3-4 correct items
   - Categories: bicycles, traffic lights, crosswalks, trees
   - User must select all correct images

3. **Arrow Sequence** (`arrows`)
   - 5-arrow sequence using ↑→↓←
   - User must click arrows in the displayed order
   - Sequence memorization challenge

4. **Slider Puzzle** (`slider`)
   - Target position between 70-80% with 5% tolerance
   - Horizontal slider interaction
   - Precision-based challenge

### Scoring System

- **Base Score**: 500 points
- **Time Bonus**: Up to 300 points (decreases with time taken)
- **Accuracy Bonus**: Up to 200 points (decreases with errors)
- **Speed Ratings**:
  - Lightning Fast ⚡ (< 15 seconds)
  - Quick 🚀 (< 30 seconds)
  - Steady 🐢 (< 60 seconds)
  - Careful (≥ 60 seconds)
- **Human Assessment**: Percentage-based human-like behavior rating

### Performance Metrics

- Total completion time
- Number of errors per challenge
- Accuracy percentage
- Average time per challenge
- Individual challenge timing breakdown

## Components

### Core Components

- **App.tsx**: Main application controller managing game state, screens, and statistics
- **AudioSystem**: Handles sound effects for user interactions

### CAPTCHA Components

#### DistortedTextCaptcha
- Renders distorted text on HTML5 Canvas
- Applies noise, wavy interference lines, and character rotation
- Includes text input field and verification button

#### ImageGridCaptcha
- Displays grid of emoji images
- Implements selection state management
- Verifies all correct images are selected

#### ArrowSequenceCaptcha
- Shows arrow sequence for memorization
- Provides clickable arrow buttons
- Tracks sequence input progress

#### SliderCaptcha
- Renders horizontal slider with target zone
- Calculates position accuracy within tolerance
- Visual feedback for completion

### Data Flow

```
App.tsx
├── captchaGenerators.ts (generates challenges)
├── Components (render challenges)
│   ├── onSubmit() → handleSuccess()
│   └── onError() → handleError()
└── AudioSystem (provides feedback)
```

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd captcha
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open your browser to `http://localhost:5173`

## Usage

1. **Start Screen**: Click "START CHALLENGE" to begin
2. **Game Screen**: Complete each of the 3 CAPTCHA challenges in sequence
3. **Results Screen**: View your performance statistics and score
4. **Play Again**: Click "PLAY AGAIN" to restart with new challenges

### Controls

- **Text CAPTCHA**: Type the displayed characters and press Enter or click VERIFY
- **Image Selection**: Click on correct images, then VERIFY
- **Arrow Sequence**: Click arrows in the order shown, then VERIFY
- **Slider**: Drag slider to target position, then VERIFY

## Development

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build

### Adding New CAPTCHA Types

1. Define the data structure in `types.ts`
2. Create a generator function in `captchaGenerators.ts`
3. Build the component in `src/components/`
4. Add the type mapping in `App.tsx`
5. Update the generator selection in `generateRandomCaptchas()`

### Styling

The application uses Tailwind CSS v4 with custom CSS variables for theming. Styles are located in:
- `src/index.css` - Global styles and CSS variables
- Component-specific styles are inline with Tailwind classes

## Technologies

- **Frontend Framework**: React 19 with TypeScript
- **Build Tool**: Vite
- **Styling**: Tailwind CSS v4
- **Audio**: Web Audio API
- **Canvas**: HTML5 Canvas for text distortion
- **Icons**: Emoji-based UI elements

### Dependencies

- React & React DOM
- Vite (development and build)
- Tailwind CSS (styling)
- TypeScript (type safety)
- PostCSS & Autoprefixer (CSS processing)

This project demonstrates modern web development practices while exploring the balance between security mechanisms and user experience design.
