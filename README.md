# Foto Owl

Foto Owl is a native React Native + TypeScript photo gallery app built for the Foto Owl internship assignment. Users can create a local account, browse a Picsum image gallery, search and filter by author, save favorites, download images to their device gallery, and manage their profile.

## Features

- Local registration with validation for all required fields
- Gender radio buttons and city dropdown selection
- Local login and persistent session
- Picsum gallery using `https://picsum.photos/v2/list?page=1&limit=50`
- FlatList image grid with loading, error, empty, retry, and pull-to-refresh states
- Real-time, case-insensitive author search
- All Images, Author A–M, and Author N–Z filters
- Search and filter working together
- Simple author sorting in A–Z and Z–A order
- Progressive image loading with FlatList `onEndReached`
- Persistent favorites stored with image data
- Favorites screen with author search and remove support
- Image details with full-size image, author, ID, favorite toggle, and gallery download
- Full-screen image viewer from the details screen
- Profile display and local profile editing
- Logout while retaining registration data and favorites
- Light and dark mode preference stored locally
- Small reusable UI components and a shared Context provider

## Tech stack

- React Native
- Expo Router
- TypeScript
- React Hooks
- React Navigation through Expo Router
- AsyncStorage
- React Context for centralized state
- Picsum API
- Expo MediaLibrary and FileSystem for downloads

## Setup

From the repository root:

```bash
pnpm install
pnpm --filter @workspace/foto-owl run dev
```

Open the Expo preview or scan the QR code with Expo Go on a device.

## Folder structure

```text
app/
  (auth)/       Login and registration
  (tabs)/       Explore, Favorites, and Profile tabs
  detail.tsx    Full image details and download
components/
  ui.tsx        Reusable buttons, inputs, cards, and states
context/
  AppContext.tsx
services/
  storage.ts
types/
  index.ts
constants/
  colors.ts
```

## API

The Explore screen fetches the required Picsum endpoint:

```text
https://picsum.photos/v2/list?page=1&limit=50
```

The first 16 filtered results are shown initially. More results are revealed when the user reaches the end of the FlatList.

## Local storage

AsyncStorage stores:

- The registered user credentials and profile information
- Whether the user is logged in
- Favorite image objects
- Light/dark mode preference

No backend is used for registration or login because the assignment specifically requests local credential validation.

## Assumptions

- A single registered user is supported on the device.
- Favorite image data is saved along with the ID so favorites remain viewable after a restart.
- Gallery download is available on native iOS and Android. The web preview explains that a device is required for gallery saving.
- The Picsum request returns enough data for the assignment, so pagination is implemented as progressive reveal rather than multiple API pages.

## Assignment coverage

- [x] Registration and required-field validation
- [x] Gender radio buttons and city dropdown
- [x] Login and local credential validation
- [x] Session persistence
- [x] Home gallery and Picsum API
- [x] FlatList, loading, error, empty, and retry states
- [x] Pull-to-refresh
- [x] Author search
- [x] A–M and N–Z filters
- [x] Combined search and filter behavior
- [x] Author sorting
- [x] Infinite scrolling experience
- [x] Favorites and persistent storage
- [x] Favorites screen and search
- [x] Image details, full-size image, and full-screen viewer
- [x] Device gallery download with permission handling
- [x] Profile, profile editing, and persistence
- [x] Logout
- [x] Centralized state
- [x] README documentation

## Bonus features

- [x] Dark mode preference
- [x] Reusable components
- [x] Native device gallery permission and download flow