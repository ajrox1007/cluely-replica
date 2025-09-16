# Technical Documentation: Transparent Overlay Application

This document explains the technical architecture and implementation of a transparent overlay application built with Electron.

![Application Screenshot](image.png)

### How the Application Works (Technical Breakdown)

This application uses Electron, a desktop app framework based on Chromium and Node.js, to create a transparent, always-on-top overlay:

- **Transparent Window (**`transparent: true`**)** – This Electron BrowserWindow property ensures the background is fully transparent, showing only explicitly rendered content.
- **Always On Top (**`alwaysOnTop: true`**)** – Electron's flag forces the overlay window to persistently float above all other applications, making it consistently accessible without being covered.

Here's an example code snippet: 

```javascript
const { BrowserWindow } = require('electron');

const win = new BrowserWindow({
  width: 800,
  height: 600,
  transparent: true,
  frame: false,
  alwaysOnTop: true,
  skipTaskbar: true,
  resizable: false,
  fullscreen: false,
  webPreferences: {
    nodeIntegration: true,
    contextIsolation: false,
  }
});
win.loadURL('file://' + __dirname + '/index.html');
```

### Backend Communication

The overlay captures clipboard data, screenshots, or selected text and sends this information to an AI backend (e.g., Google Gemini) via HTTP requests. This backend quickly processes and returns useful suggestions or solutions.

### Screen Capture and OCR

The implementation uses native modules to capture specific screen areas and run OCR (Optical Character Recognition) using libraries like Tesseract.js. This allows the overlay to extract text directly from your screen.

### Clipboard Monitoring

Electron continuously listens for clipboard changes, immediately activating AI-assisted processing whenever new text is copied.

### Technical Considerations

- **Security Restrictions**: macOS and Windows can detect and restrict invisible overlays in secure or fullscreen contexts.
- **Performance Impact**: OCR processes and constant clipboard monitoring can increase CPU and GPU usage.

### Use Cases for Overlay Technology

This transparent overlay technology has many practical applications:

- **Development Assistant**: Real-time code suggestions and documentation lookup without leaving your IDE.
- **Customer Support Tools**: Contextual response suggestions during customer interactions.
- **Training and Onboarding**: Interactive guidance overlays for new software or processes.
- **Accessibility Tools**: Screen reading and navigation assistance for users with disabilities.

### Getting Started

This project is open source and available for educational and development purposes. Please refer to the README.md file for installation and setup instructions.