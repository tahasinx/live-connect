# Live Connect - Real-Time Communication (RTC) App

A modern, real-time video chat and messaging application built with WebRTC technology, featuring peer-to-peer communication, status tracking, and a beautiful responsive UI.

## 🌟 Features

### Core Functionality
- **Peer-to-Peer Video & Audio Calls**: Direct browser-to-browser video and audio communication using WebRTC
- **Text Messaging**: Real-time chat with a dedicated message modal, independent of call state
- **Connection Status Sync**: Live status indicators (Online, Idle, In Call, Disconnected) with periodic sync and visual feedback
- **Manual Call Flow**: Calls are only initiated by user action, with ringing modal and manual accept/decline
- **Ringtone on Incoming/Outgoing Calls**: Both caller and callee hear a ringtone (using `assets/sounds/ring-tone-68676.mp3`) when a call is initiated, until it is answered or declined. Ringtone stops automatically when the call is handled.
- **Idle Detection**: Automatic status updates when users are away (15-minute timeout)
- **Automatic Reconnection**: Seamless reconnection handling with fallback peer IDs
- **Responsive Design**: Works perfectly on desktop, tablet, and mobile devices

### User Interface
- **Modern Dashboard**: Clean, professional interface built with Bootstrap
- **Status Indicators**: Visual badges showing connection status (Online/Offline/Idle/In Call)
- **Fullscreen Video Modal**: Immersive video calling experience
- **Dedicated Chat Modal**: Message modal slides in from the right, always accessible
- **Control Buttons**: Easy-to-use connect, disconnect, and reconnect controls
- **Mobile Optimized**: Touch-friendly interface with responsive video layouts

### Technical Features
- **WebRTC Integration**: Uses PeerJS for simplified WebRTC implementation
- **STUN/TURN Servers**: Reliable connection establishment across different networks
- **Connection Management**: Robust handling of connection states and errors
- **Visibility API**: Smart status updates based on tab visibility
- **Single Connection Enforcement**: Prevents duplicate connections and message handlers

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

2. **Video/Audio Calling**
   - Click the call button to open the call type selection modal
   - Choose video or audio call
   - The remote peer sees a ringing modal and can accept or decline
   - **Ringtone:** Both caller and callee will hear a ringtone until the call is answered or declined.
   - Your local video appears in the top-right corner; remote video fills the main area
   - Use the disconnect button to end the call
   - **Improved Status Handling:** After a call is disconnected or rejected, the status is always reset to "Online" for both peers, and the call modal is closed automatically.

3. **Text Messaging**
   - Click the chat button to open the message modal (can be used independently of calls)
   - Messages are delivered in real time if the connection is established
   - The message modal auto-opens when a new message is received

4. **Status Management**
   - **Online**: Active and connected
   - **Idle**: Tab is hidden or inactive (15-minute timeout)
   - **In Call**: Peer is on a call
   - **Offline**: Disconnected or unavailable

## 📁 Project Structure

```
project_chat/
├── index.html              # Main application interface
├── assets/
│   ├── css/
│   │   ├── app.min.css    # Bootstrap-based UI framework
│   │   └── custom.css     # Custom styles for video chat and chat modal
│   ├── js/
│   │   ├── app.min.js     # Core JavaScript framework
│   │   └── pages/
│   │       └── chat.js    # Chat functionality (minified, not used in main flow)
│   ├── images/            # UI assets and avatars
│   ├── sounds/
│   │   └── ring-tone-68676.mp3 # Ringtone audio for calls
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
Current configuration uses Metered.ca STUN/TURN servers for reliable NAT traversal.

For production deployment, consider:
- Setting up your own TURN server
- Using a commercial WebRTC service
- Implementing proper authentication

## 🌐 Browser Support

| Browser | Version | Support |
|---------|---------|---------|
| Chrome  | 60+     | ✅ Full Support |
| Firefox | 55+     | ✅ Full Support |
| Safari  | 11+     | ✅ Full Support |
| Edge    | 79+     | ✅ Full Support |

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

## 🛑 Limitations (Current Version)

- **Two-Peer Limit**: Only two users can join and communicate in a session. No group chat or multi-party calls are supported.
- **Static Peer IDs**: Peer IDs are hardcoded for demo/testing. No dynamic peer discovery or user registration.
- **No Authentication**: Anyone with the peer ID can connect; there is no user authentication or authorization.
- **No Persistent Chat**: Messages are not stored or persisted; chat is session-based only.
- **No File Sharing**: Only text messages and media streams (audio/video) are supported.
- **No Push Notifications**: No desktop or mobile push notifications for incoming calls/messages.
- **No Server-Side Signaling**: PeerJS cloud server is used for signaling; not suitable for production scale or privacy.
- **No Mobile App**: This is a web-only solution; not packaged as a native mobile app.
- **No Screen Sharing**: Only camera/microphone streams are supported.
- **No Recording**: No built-in call or message recording features.

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

