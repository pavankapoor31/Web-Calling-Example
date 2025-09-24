# Bolna Web Calling Demo

A modern, responsive web application demonstrating how to integrate and use the Bolna Web Calling library for AI-powered voice calls.


## Quick Start

1. **Clone or download** this repository
2. **Open** `index.html` in your web browser
3. **Enter your credentials**:
   - Agent ID (from your Bolna dashboard)
   - Access Token (from your Bolna account)
   - WebSocket Host (defaults to `wss://ws.bolna.ai/`)
4. **Click "Start Call"** to begin

## Prerequisites

Before using this demo, you'll need:

- A **Bolna account** with an active agent
- Your **Agent ID** from the Bolna dashboard
- A valid **Access Token** for authentication
- A modern web browser with WebRTC support

## Getting Your Credentials

### Agent ID
1. Log into your [Bolna dashboard](https://dashboard.bolna.ai)
2. Navigate to your agent settings
3. Copy the Agent ID from the configuration panel

### Access Token
1. Go to your account settings in the Bolna dashboard
2. Navigate to the API section
3. Generate a new access token or copy an existing one
4. Keep this token secure and never share it publicly

## API Reference

### BolnaWebCalling Constructor

```javascript
const webCalling = new BolnaWebCalling({
  agentId: 'your-agent-id',
  accessToken: 'your-access-token',
  websocketHost: 'wss://ws.bolna.ai/',
  contextData: {},
  
  // Callbacks
  onCallStateChange: (isActive) => {
    console.log('Call state changed:', isActive);
  },
  onFirstAudioPacket: () => {
    console.log('First audio packet received');
  },
  onError: (type, error) => {
    console.error('Error:', type, error.message);
  }
});
```

### Methods

#### `initiateWebCall()`
Starts a new web call session.

```javascript
webCalling.initiateWebCall();
```

#### `endWebCall()`
Ends the current call session.

```javascript
webCalling.endWebCall();
```

#### `isCallActive()`
Returns `true` if a call is currently active.

```javascript
const isActive = webCalling.isCallActive();
```

#### `isConnected()`
Returns `true` if the WebSocket connection is established.

```javascript
const isConnected = webCalling.isConnected();
```

### Callbacks

#### `onCallStateChange(isActive)`
Triggered when the call state changes.

- `isActive` (boolean): Whether the call is currently active

#### `onFirstAudioPacket()`
Triggered when the first audio packet is received from the agent.

#### `onError(type, error)`
Triggered when an error occurs.

- `type` (string): The type of error
- `error` (object): Error details including message

## Configuration Options

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `agentId` | string | Yes | Your Bolna agent ID |
| `accessToken` | string | Yes | Your Bolna access token |
| `websocketHost` | string | Yes | WebSocket server URL |
| `contextData` | object | No | Additional context data to pass to the agent |
| `onCallStateChange` | function | No | Callback for call state changes |
| `onFirstAudioPacket` | function | No | Callback for first audio packet |
| `onError` | function | No | Callback for error handling |


## Security Considerations

- **Never expose your access token** in client-side code for production use
- **Use environment variables** or secure configuration management
- **Implement proper authentication** for production deployments
- **Use HTTPS** for all production deployments

## Troubleshooting

### Common Issues

**Call not starting:**
- Verify your Agent ID and Access Token are correct
- Check that your agent is active in the Bolna dashboard
- Ensure your browser supports WebRTC

**Connection errors:**
- Verify the WebSocket host URL is correct
- Check your internet connection
- Ensure no firewall is blocking WebSocket connections

**Audio issues:**
- Grant microphone permissions when prompted
- Check your browser's audio settings
- Ensure your microphone is working in other applications
- Documentation: [docs.bolna.ai](https://docs.bolna.ai)

---

**Made with ❤️**
