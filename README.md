# AI-Powered Overlay Assistant

A sophisticated desktop application that provides intelligent assistance through a transparent overlay interface. Built with Electron and powered by Google's Gemini AI.

## ✨ Features

- **Transparent Overlay**: Always-on-top interface that doesn't interfere with your workflow
- **AI-Powered Analysis**: Leverages Google Gemini for intelligent screenshot and text analysis
- **Screen Capture**: Take screenshots and get instant AI feedback
- **OCR Integration**: Extract text from images using Tesseract.js
- **Keyboard Shortcuts**: Quick access with customizable hotkeys
- **Cross-Platform**: Works on Windows, macOS, and Linux

## 🚀 Quick Setup

### Requirements

- Node.js (v16 or higher)
- Git
- Google Gemini API key ([Get yours here](https://makersuite.google.com/app/apikey))

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repository-url>
   cd cluely-replica
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment**
   
   Create a `.env` file in the root directory:
   ```env
   GEMINI_API_KEY=your_gemini_api_key_here
   ```

## 🎯 Usage

### Development Mode

Start the development server and Electron app:

```bash
# Terminal 1: Start Vite dev server
npm run dev -- --port 5180

# Terminal 2: Start Electron app
NODE_ENV=development npm run electron:dev
```

### Production Build

Build and package the application:

```bash
npm run build
```

The packaged app will be available in the `release` folder.

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Cmd/Ctrl + B` | Toggle window visibility |
| `Cmd/Ctrl + H` | Take screenshot |
| `Cmd/Enter` | Get AI solution |
| `Cmd/Ctrl + Arrow Keys` | Move window position |
| `Cmd/Ctrl + Q` | Quit application |

## 🔧 Configuration

### Window Settings

The overlay window can be customized by modifying the Electron BrowserWindow configuration in `electron/main.ts`:

```typescript
const win = new BrowserWindow({
  transparent: true,
  alwaysOnTop: true,
  frame: false,
  skipTaskbar: true,
  // ... other options
});
```

### AI Model Configuration

Update the AI model settings in `electron/LLMHelper.ts`:

```typescript
this.model = genAI.getGenerativeModel({ 
  model: "gemini-2.0-flash" 
});
```

## 🛠️ Troubleshooting

### Application Won't Start

1. **Port conflicts**: Ensure port 5180 is available
   ```bash
   # Check what's using the port
   lsof -i :5180
   
   # Kill the process if needed
   kill [PID]
   ```

2. **Dependency issues**: Clean and reinstall
   ```bash
   rm -rf node_modules package-lock.json
   npm install
   ```

3. **Environment variables**: Verify your `.env` file is properly configured

### Performance Issues

- **High CPU usage**: OCR processing can be intensive; consider reducing screenshot frequency
- **Memory leaks**: Restart the application if it becomes unresponsive
- **GPU acceleration**: Ensure hardware acceleration is enabled in your system

### Platform-Specific Issues

**macOS**
- Grant screen recording permissions in System Preferences > Security & Privacy
- Allow the app to run if blocked by Gatekeeper

**Windows**
- Run as administrator if experiencing permission issues
- Add exclusion to Windows Defender if needed

**Linux**
- Install required dependencies: `libxtst6`, `libxrandr2`, `libasound2-dev`

## 📁 Project Structure

```
├── electron/              # Electron main process
│   ├── main.ts           # Application entry point
│   ├── LLMHelper.ts      # AI integration
│   └── ScreenshotHelper.ts # Screen capture utilities
├── src/                  # React frontend
│   ├── _pages/           # Main application pages
│   ├── components/       # Reusable UI components
│   └── types/            # TypeScript definitions
└── dist/                 # Built application files
```

## 🤝 Contributing

We welcome contributions! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Development Guidelines

- Follow TypeScript best practices
- Maintain consistent code formatting
- Add tests for new features
- Update documentation as needed

## 📄 License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## 🔒 Privacy & Security

- **Local Processing**: Screenshots and data are processed locally when possible
- **API Usage**: Only necessary data is sent to external AI services
- **No Data Storage**: No personal information is permanently stored
- **Transparent Operations**: All data processing is logged and visible

## 💡 Use Cases

- **Development Assistance**: Get instant help with code problems
- **Research Support**: Analyze and summarize content from screenshots
- **Accessibility**: Screen reading and text extraction for visually impaired users
- **Productivity**: Quick answers without switching between applications

---

**Note**: This application is designed for educational and productivity purposes. Please use responsibly and in accordance with your organization's policies.
