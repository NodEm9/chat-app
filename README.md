# Chat App

## Table of Contents

**1**. Introduction
**2**. Features
**3**. Prerequisites
**4**. Installation
**5**. Firebase Setup
**6**. Running the App
**7**. Project Structure
**8**. Components
- App
- Start
- Chat
- CustomActions

**9**.  Accessibility
**10**. Known Issues
**11**. Contributing
**12**. License

### Introduction

This project is a React Native chat application that allows users to communicate with each other in real-time. Users can sign in anonymously, send text messages, images, their location, and audio recordings. The app also supports offline functionality by caching messages locally and resyncing when a network connection is re-established.

#### Features

- Anonymous Sign-In: Users can sign in anonymously to start chatting.
- Real-Time Chat: Exchange messages in real-time.
- Media Sharing: Share images, audio recordings, and location.
- Offline Support: Caches messages locally when offline and syncs them when back online.
- Customizable UI: Users can choose a background color for their chat screen.
- Accessibility: The app includes various accessibility features to support users with disabilities.

#### Prerequisites

Before running this application, ensure you have the following installed:

- Node.js (version 14 or later)
- npm or yarn (latest version)
- Expo CLI (for running the React Native project)
- Firebase Account (for Firestore and Authentication)

##### Installation

**1**. Clone the repository:

```bash
# git clone https://github.com/yourusername/chat-app.git
## cd chat-app
```

**2**. Install dependencies:
```bash
# npm install
```
or

```bash
# yarn install
```

**3**. Install Expo CLI (if not already installed):

```bash
# npm install -g expo-cli
```

#### Firebase Setup

**1**. Create a Firebase project at [Firebase Console](https://firebase.google.com/).

**2**. Enable Firestore and Authentication:

- Go to the Firestore Database section, create a database, and set it up in test mode for development.
- Enable Anonymous Authentication under the Authentication section.

**3**. Add your Firebase configuration:

- Copy the Firebase configuration details from the Firebase console.
- Paste the configuration into the firebaseConfig object inside the App.js file.

```js
// App.js

const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

##### Running the App

**1**. Start the Expo server:

```bash
# expo start
```
**2**. Run the app on your device:

- Use the Expo Go app on your Android/iOS device to scan the QR code.
- Alternatively, you can run it on an emulator.

##### Project Structure

```bash
 
├── assets/                     # Contains images and other static assets
├── components/                 # Contains all React components
│   ├── Chat.js                 # Chat screen component
│   ├── CustomActions.js        # Custom actions component for chat
│   └── Start.js                # Start screen component
├── App.js                      # Main entry point of the application
├── package.json                # Project metadata and dependencies
└── README.md                   # Documentation for the project
```

##### Components

`App.js`

- Description: The main entry point of the application. It sets up the Firebase connection, handles network connectivity, and initializes the navigation stack.

- Key Features

  - Initializes Firebase and Firestore services.
  - Monitors network connection status using useNetInfo.
  - Configures navigation between the Start and Chat screens.

`Start.js`

- Description: The starting screen where users can input their name and select a background color before joining the chat.

- Key Features:

- User can input their name.
  - User can select a background color for the chat screen.
  - Anonymous authentication using Firebase.
  - Navigates to the Chat screen with user preferences passed as parameters.

`Chat.js`

- Description: The main chat screen where users exchange messages.

- Key Features:
  - Displays messages in real-time using Firestore.
  - Supports sending text, images, audio recordings, and location data.
  - Handles offline mode by storing messages in AsyncStorage.
  - Provides customizable UI elements like chat bubbles and input toolbar.

`CustomActions.js`

- Description: A component that provides additional actions in the chat, such as picking images, taking photos, sharing location, and recording audio.

- Key Features:

  - Integrates with the device's media library, camera, and location services.
  - Supports audio recording using Expo's Audio API.
  - Uploads media to Firebase Storage and sends the download URL in the chat.

##### Accessibility

The app includes several accessibility features:

- Accessible buttons and labels: Ensures that all interactive elements are accessible via screen readers.
- Custom accessibility labels: Describes the purpose of each interactive element.
- Touchable area adjustments: Ensures that touchable areas are large enough for users with motor impairments.

##### Known Issues

- Offline Storage: Cached messages are sometimes not reloaded properly when switching between offline and online modes.
- Audio Playback: Audio might not play on all devices due to varying support for file formats.


##### Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes. Make sure to adhere to the code style and include proper documentation for any new features.
