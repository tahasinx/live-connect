# PeerChat - WebRTC Video Chat Application

A modern, real-time video chat application built with WebRTC technology, featuring peer-to-peer communication, status tracking, and a beautiful responsive UI.

## 🌟 Features

### Core Functionality
- **Peer-to-Peer Video Calls**: Direct browser-to-browser video communication using WebRTC
- **Real-time Status Tracking**: Monitor online/offline/idle status of connected peers
- **Automatic Reconnection**: Seamless reconnection handling with fallback peer IDs
- **Idle Detection**: Automatic status updates when users are away (15-minute timeout)
- **Responsive Design**: Works perfectly on desktop, tablet, and mobile devices

### User Interface
- **Modern Dashboard**: Clean, professional interface built with Bootstrap
- **Status Indicators**: Visual badges showing connection status (Online/Offline/Idle)
- **Fullscreen Video Modal**: Immersive video calling experience
- **Control Buttons**: Easy-to-use connect, disconnect, and reconnect controls
- **Mobile Optimized**: Touch-friendly interface with responsive video layouts

### Technical Features
- **WebRTC Integration**: Uses PeerJS for simplified WebRTC implementation
- **STUN/TURN Servers**: Reliable connection establishment across different networks
- **Connection Management**: Robust handling of connection states and errors
- **Browser Notifications**: Desktop notifications for connection events
- **Visibility API**: Smart status updates based on tab visibility

## 🚀 Quick Start

### Prerequisites
- Modern web browser with WebRTC support (Chrome, Firefox, Safari, Edge)
- Web server (Apache, Nginx, or any local development server)
- No additional dependencies required - everything is CDN-hosted

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/peerchat.git
   cd peerchat
   ```

2. **Start a local server**
   ```bash
   # Using Python 3
   python -m http.server 8000
   
   # Using Node.js (if you have http-server installed)
   npx http-server
   
   # Using PHP
   php -S localhost:8000
   ```

3. **Open in browser**
   - Navigate to `http://localhost:8000`
   - Allow camera and microphone permissions when prompted
   - The application will automatically attempt to connect

### Usage

1. **Initial Connection**
   - The app automatically tries to connect using predefined peer IDs
   - If the first peer ID is unavailable, it automatically tries the second one
   - Status indicators show connection progress

2. **Video Calling**
   - Click the video call button to open the fullscreen video modal
   - Your local video appears in the top-right corner
   - Remote video fills the main area
   - Use the disconnect button to end the call

3. **Status Management**
   - **Online**: Active and connected
   - **Idle**: Tab is hidden or inactive (15-minute timeout)
   - **Offline**: Disconnected or unavailable

## 📁 Project Structure

```
project_chat/
├── index.html              # Main application interface
├── stage1.html            # Alternative implementation
├── assets/
│   ├── css/
│   │   ├── app.min.css    # Bootstrap-based UI framework
│   │   └── custom.css     # Custom styles for video chat
│   ├── js/
│   │   ├── app.min.js     # Core JavaScript framework
│   │   └── pages/
│   │       └── chat.js    # Chat functionality (minified)
│   ├── images/            # UI assets and avatars
│   └── vendors/           # Third-party libraries
└── README.md              # This file
```

## 🔧 Configuration

### Peer IDs
The application uses two predefined peer IDs for testing:
- `11111-22222-33333-44444-55555`
- `66666-77777-88888-99999-00000`

To customize for production:
1. Edit the `peerId1` and `peerId2` variables in the JavaScript
2. Implement a proper peer ID generation system
3. Consider using a signaling server for dynamic peer discovery

### STUN/TURN Servers
Current configuration uses:
- Google STUN server: `stun:stun.l.google.com:19302`
- TURN server: `turn:try-turn.vercel.app`

For production deployment, consider:
- Setting up your own TURN server
- Using a commercial WebRTC service
- Implementing proper authentication

## 🌐 Browser Support

| Browser | Version | Support |
|---------|---------|---------|
| Chrome | 60+ | ✅ Full Support |
| Firefox | 55+ | ✅ Full Support |
| Safari | 11+ | ✅ Full Support |
| Edge | 79+ | ✅ Full Support |

## 🔒 Security Considerations

- **HTTPS Required**: WebRTC requires secure context for camera/microphone access
- **TURN Server Security**: Implement proper authentication for production TURN servers
- **Peer ID Validation**: Validate peer IDs to prevent unauthorized connections
- **Content Security Policy**: Consider implementing CSP headers

## 🚧 Development

### Local Development
1. Use a local web server (don't open files directly)
2. Enable browser developer tools for debugging
3. Check the console for connection logs
4. Test with multiple browser tabs/windows

### Customization
- **UI Theme**: Modify `assets/css/custom.css` for styling changes
- **Peer Logic**: Edit the JavaScript section in HTML files
- **Video Layout**: Adjust video container styles in CSS
- **Timeout Settings**: Modify `idleLimit` variable (currently 15 minutes)

## 📝 API Reference

### PeerJS Events
- `peer.on('open')`: Peer connection established
- `peer.on('connection')`: Incoming connection received
- `peer.on('error')`: Connection error occurred
- `peer.on('disconnected')`: Peer disconnected

### Status Functions
- `updateStatus(peerID, status, badge)`: Update UI status display
- `notifyPeers(status)`: Send status update to connected peer
- `setupPeer(id)`: Initialize peer connection
- `handleDisconnection()`: Clean up connections

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **PeerJS**: Simplified WebRTC implementation
- **Bootstrap**: UI framework and components
- **Enlink Template**: Base admin dashboard design
- **WebRTC Community**: Standards and documentation

## 📞 Support

For support and questions:
- Create an issue on GitHub
- Check the browser console for error messages
- Ensure your browser supports WebRTC
- Verify camera/microphone permissions are granted

---

**Built with ❤️ using WebRTC technology**

