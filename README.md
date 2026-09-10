# Smart Ground-Truthing & Digital Biodiversity System

### COS30049 Computing Technology Innovation Project

Mobile application for the Smart Ground-Truthing and Digital Biodiversity System developed for the COS30049 group project.

The mobile application is designed primarily for botanists and field personnel to document plants in the field, including QR code scanning, GPS collection, photographs, offline data collection, and synchronisation with the central biodiversity system.

---

# Tech Stack

| Technology    | Purpose                                       |
| ------------- | --------------------------------------------- |
| React Native  | Mobile application framework                  |
| Expo          | React Native development platform and tooling |
| TypeScript    | Type-safe development                         |
| Expo Router   | Application navigation                        |
| SQLite        | Local offline data storage                    |
| Supabase      | Backend services                              |
| PostgreSQL    | Central relational database                   |
| PostGIS       | Geographic/location data                      |
| Expo Camera   | Camera and QR/barcode scanning                |
| Expo Location | GPS/location services                         |
| Git + GitHub  | Version control and collaboration             |
| ESLint        | Code quality                                  |
| Prettier      | Code formatting                               |

---

# 1. Prerequisites

Before setting up the project, install:

### Required

- [Node.js LTS](https://nodejs.org/)
- [Git](https://git-scm.com/)
- [Visual Studio Code](https://code.visualstudio.com/)
- An Android smartphone
- [Expo Go](https://expo.dev/go) on your Android smartphone

### Recommended

Use a physical Android phone during development because this application uses:

- Camera
- QR scanning
- GPS
- Offline storage
- Network connectivity

Testing on a real device allows us to verify behaviour closer to how the application will actually be used in the field.

---

# 2. Recommended VS Code Extensions

Install the following extensions:

### Required

1. **ES7+ React/Redux/React-Native Snippets**
2. **ESLint**
3. **Prettier - Code formatter**
4. **GitLens**
5. **Error Lens**

### Optional

6. **React Native Tools**
7. **GitHub Pull Requests and Issues**

The web and mobile repositories should use the same formatting and coding conventions wherever possible.

---

# 3. Check Your Installation

Open the VS Code terminal:

**Terminal → New Terminal**

Check Node.js:

```bash
node --version
```

Check npm:

```bash
npm --version
```

Check Git:

```bash
git --version
```

Example:

```text
node v22.x.x
npm 10.x.x
git version 2.x.x
```

Use a current Node.js LTS release.

---

# 4. Clone the Repository

Do **not** create a new Expo application if the repository already exists.

Clone the existing project:

```bash
git clone <GITHUB_REPOSITORY_URL>
```

For example:

```bash
git clone https://github.com/OUR-ORGANISATION/biodiversity-mobile.git
```

Enter the project:

```bash
cd biodiversity-mobile
```

Open it in VS Code:

```bash
code .
```

---

# 5. Install Dependencies

Inside the project directory, run:

```bash
npm install
```

This installs the dependencies specified in `package.json`.

Do not commit the `node_modules` directory to GitHub.

It should already be excluded through `.gitignore`.

---

# 6. Start the Expo Development Server

Run:

```bash
npx expo start
```

Expo will start the development server and display a QR code.

You should see something similar to:

```text
Starting project...
Metro waiting on...
› Scan the QR code with Expo Go
```

---

# 7. Run the Application on Your Android Phone

### Step 1

Make sure your computer and Android phone are connected to the same Wi-Fi network.

### Step 2

Open **Expo Go** on your Android phone.

### Step 3

Scan the QR code displayed by Expo.

### Step 4

The application should open on your phone.

If the QR code does not work, check the connection instructions displayed in the Expo terminal.

---

# 8. Test Hot Reloading

Open:

```text
src/app/index.tsx
```

Change some text in the screen.

For example:

```tsx
import { Text, View } from "react-native";

export default function HomeScreen() {
  return (
    <View>
      <Text>Smart Biodiversity System</Text>
    </View>
  );
}
```

Save the file.

The application should update automatically on the connected device.

---

# 9. Understand the Project Structure

The project uses Expo Router and TypeScript.

The structure will generally look like:

```text
biodiversity-mobile/
│
├── src/
│   ├── app/
│   │   ├── _layout.tsx
│   │   ├── index.tsx
│   │   ├── login/
│   │   ├── home/
│   │   ├── plants/
│   │   ├── observations/
│   │   ├── scanner/
│   │   └── sync/
│   │
│   ├── components/
│   │   ├── common/
│   │   ├── plants/
│   │   ├── observations/
│   │   └── forms/
│   │
│   ├── database/
│   │   ├── database.ts
│   │   ├── migrations/
│   │   └── repositories/
│   │
│   ├── services/
│   │   ├── authService.ts
│   │   ├── plantService.ts
│   │   ├── observationService.ts
│   │   └── syncService.ts
│   │
│   ├── hooks/
│   ├── types/
│   └── utils/
│
├── assets/
├── app.json
├── package.json
├── tsconfig.json
└── README.md
```

The structure may change as development progresses.

Discuss major structural changes with the team before implementing them.

---

# 10. Important Mobile Modules

The mobile application will eventually contain the following major modules:

```text
Authentication
     │
     ▼
Home / Dashboard
     │
     ├── Scan QR
     │
     ├── Plant Information
     │
     ├── Create Observation
     │
     ├── Capture Photo
     │
     ├── Capture GPS
     │
     └── Synchronisation
```

The main field workflow should eventually resemble:

```text
Scan QR
   ↓
Identify Plant
   ↓
Create Observation
   ↓
Capture Plant Photo
   ↓
Capture GPS
   ↓
Validate Record
   ↓
Save Locally
   ↓
Synchronise When Online
```

---

# 11. Install Required Expo Packages

The project will use Expo packages for the main hardware and offline features.

### SQLite

Install:

```bash
npx expo install expo-sqlite
```

SQLite will provide persistent local storage for offline field observations.

### Camera

Install:

```bash
npx expo install expo-camera
```

The camera package will be used for:

- Photographing plants
- QR/barcode scanning

### Location

Install:

```bash
npx expo install expo-location
```

This will be used to capture GPS coordinates for plant observations.

---

# 12. Supabase

The mobile application will eventually communicate with our Supabase backend.

Install:

```bash
npm install @supabase/supabase-js
```

Supabase will be used for:

- Authentication
- Plant data
- Observation data
- Cloud synchronisation
- File storage
- Realtime data where required

---

# 13. Environment Variables

Do not place Supabase configuration directly into source code.

Create:

```text
.env.local
```

Use:

```text
.env.example
```

as the template.

The file will contain values similar to:

```text
EXPO_PUBLIC_SUPABASE_URL=your_supabase_url
EXPO_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
```

The exact values should be obtained through the team's agreed development setup.

### Security

Never commit:

```text
.env
.env.local
```

to GitHub.

Never commit:

- Passwords
- Private API keys
- Service-role keys
- Database passwords
- Access tokens
- Other secrets

Only variables intended to be exposed to the client application should use the `EXPO_PUBLIC_` prefix.

---

# 14. Offline Storage

Offline operation is a core requirement of the project.

The mobile application should continue to work when there is no internet connection.

Expected architecture:

```text
                MOBILE APPLICATION
                       │
              ┌────────┴────────┐
              │                 │
           Online            Offline
              │                 │
              ▼                 ▼
          Supabase            SQLite
              │                 │
              └────────┬────────┘
                       │
                Synchronisation
                       │
                       ▼
                  Cloud Data
```

For example:

```text
No Internet
     ↓
Create Observation
     ↓
Capture GPS
     ↓
Take Photo
     ↓
Save to SQLite
     ↓
Pending Sync
```

When internet connectivity returns:

```text
Internet Available
        ↓
Sync Queue
        ↓
Supabase
        ↓
Sync Successful
        ↓
Mark Record as Synced
```

Do not bypass the local database by assuming that field users will always have an internet connection.

---

# 15. Development Workflow

Before starting work:

```bash
git pull
```

Create a branch for your task:

```bash
git checkout -b feature/qr-scanner
```

Work on your changes.

Check your changes:

```bash
git status
```

Stage them:

```bash
git add .
```

Commit:

```bash
git commit -m "feat: add QR scanner"
```

Push:

```bash
git push -u origin feature/qr-scanner
```

Then create a Pull Request.

---

# 16. Branch Naming

Use descriptive branch names.

### Features

```text
feature/authentication
feature/qr-scanner
feature/plant-record
feature/photo-capture
feature/gps
feature/offline-storage
feature/offline-sync
```

### Bug fixes

```text
fix/camera-permission
fix/gps-timeout
fix/duplicate-observation
fix/sync-failure
```

### Documentation

```text
docs/mobile-setup
docs/offline-architecture
docs/testing
```

Avoid names such as:

```text
test
stuff
new
changes
final
final2
```

---

# 17. Commit Message Convention

Use meaningful commit messages.

### Feature

```bash
git commit -m "feat: add plant observation form"
```

### Bug Fix

```bash
git commit -m "fix: handle denied location permission"
```

### Testing

```bash
git commit -m "test: add observation validation tests"
```

### Documentation

```bash
git commit -m "docs: update mobile setup instructions"
```

### Refactoring

```bash
git commit -m "refactor: separate observation database repository"
```

---

# 18. Pull Request Requirements

Before creating a Pull Request:

```bash
npm run lint
```

Also make sure the application can start successfully:

```bash
npx expo start
```

Your Pull Request should explain:

### What changed?

Example:

```text
Implemented the QR scanning screen using Expo Camera.
```

### Why?

```text
Required for identifying tagged plant records in the field.
```

### How was it tested?

Example:

```text
Tested QR scanning against:
- Valid plant QR code
- Invalid QR code
- Duplicate QR scan
- Camera permission denied
```

Include screenshots or short videos for significant UI changes where useful.

---

# 19. Code Style

Use TypeScript throughout the project.

Prefer:

```tsx
interface Plant {
  id: string;
  scientificName: string;
  commonName: string;
}
```

rather than relying heavily on untyped data.

Use functional React components.

Keep components focused.

Avoid placing large amounts of business logic inside screen files.

For example:

```text
Screen
  ↓
Service
  ↓
Repository / API
  ↓
Database
```

rather than:

```text
Screen
  ↓
Everything
```

---

# 20. Database Access

Do not put database operations throughout every component.

Use services/repositories.

For example:

```text
src/
└── services/
    ├── plantService.ts
    ├── observationService.ts
    └── syncService.ts
```

Local SQLite access should be separated into the database layer:

```text
src/
└── database/
    ├── database.ts
    ├── migrations/
    └── repositories/
```

This makes the offline system easier to maintain and test.

---

# 21. Permissions

This application uses device hardware and will request permissions.

Potential permissions include:

- Camera
- Location

Do not assume that a permission will always be granted.

The application should handle:

```text
Permission Granted
        ↓
Continue

Permission Denied
        ↓
Explain why the feature is unavailable
        ↓
Provide appropriate recovery guidance
```

For example, a user who denies camera permission should receive a clear message rather than seeing a broken QR scanner.

---

# 22. Testing on a Real Device

The mobile application should be tested on a physical Android device regularly.

At minimum, test:

```text
Camera
QR Scanner
GPS
SQLite
Offline Mode
Online Mode
Synchronisation
Permissions
Network interruption
```

For offline testing:

```text
1. Start the application.
2. Disable Wi-Fi/mobile data.
3. Create an observation.
4. Capture GPS.
5. Capture a photo.
6. Save the observation.
7. Close and reopen the application.
8. Confirm the observation still exists.
9. Restore internet.
10. Synchronise.
11. Confirm the record appears in Supabase.
```

This is one of the most important test scenarios in the project.

---

# 23. Expo Go vs Development Builds

During initial development, the team may use Expo Go for rapid testing.

However, some project features may eventually require a development build depending on the libraries and native functionality being used.

Do not assume that the final demonstration application must run through Expo Go.

The team will decide on the final build/deployment workflow as development progresses.

---

# 24. Common Problems

## `node` or `npm` is not recognised

Check:

```bash
node --version
npm --version
```

If Node.js was just installed, restart VS Code.

---

## Expo command fails

Make sure you are inside the project:

```bash
cd biodiversity-mobile
```

Then run:

```bash
npx expo start
```

---

## QR code cannot connect to phone

Check that:

```text
Computer
   ↕
Same Wi-Fi
   ↕
Android Phone
```

If the connection still fails, read the connection information shown by Expo and try the supported connection options.

---

## Dependencies are missing

Run:

```bash
npm install
```

Then restart Expo:

```bash
npx expo start
```

---

## Camera does not work

Check:

1. Camera permission is granted.
2. The application is running on the expected device.
3. The Expo/development build supports the camera functionality being used.
4. The phone's camera itself works.

---

## GPS does not work

Check:

1. Location services are enabled.
2. The application has location permission.
3. The device has access to a usable location signal.
4. The application handles unavailable location gracefully.

---

# 25. Important Project Rules

### 1. Do not work directly on `main`

Create a feature branch.

### 2. Pull before starting work

```bash
git pull
```

### 3. Do not commit secrets

Never commit `.env.local`.

### 4. Test hardware features on a real device

Especially:

- QR
- Camera
- GPS
- Offline storage

### 5. Do not make major architecture changes without discussion

Discuss changes involving:

- Database structure
- Offline synchronisation
- Authentication
- Navigation
- Shared services
- Dependencies

with the team.

### 6. Keep `main` stable

Do not merge incomplete features into `main`.

---

# 26. Quick Start

For teammates who already have Node.js, Git, VS Code and Expo Go installed:

```bash
git clone <GITHUB_REPOSITORY_URL>

cd biodiversity-mobile

npm install

# Create .env.local using .env.example

npx expo start
```

Then scan the Expo QR code using Expo Go.

---

# 27. Setup Checklist

Before beginning development:

```text
[ ] Node.js installed
[ ] npm working
[ ] Git working
[ ] VS Code installed
[ ] Recommended extensions installed
[ ] Android phone available
[ ] Expo Go installed
[ ] Repository cloned
[ ] npm install completed
[ ] .env.local configured
[ ] Expo development server starts
[ ] Application opens on phone
[ ] Hot reload works
[ ] TypeScript works
[ ] SQLite installed
[ ] Camera installed
[ ] Location installed
[ ] Supabase package installed
[ ] Git branch created
```

Once all items are complete, the mobile development environment is ready.

---

# 28. Useful Resources

### Expo

https://docs.expo.dev/

### Expo Router

https://docs.expo.dev/router/

### React Native

https://reactnative.dev/

### TypeScript

https://www.typescriptlang.org/

### Expo SQLite

https://docs.expo.dev/versions/latest/sdk/sqlite/

### Expo Camera

https://docs.expo.dev/versions/latest/sdk/camera/

### Expo Location

https://docs.expo.dev/versions/latest/sdk/location/

### Supabase

https://supabase.com/docs

### Git

https://git-scm.com/doc

---

# Project

**COS30049 Computing Technology Innovation Project**

**Smart Ground-Truthing and Digital Biodiversity System for Plant Species Documentation**

Industry Partner:

**NeuonAI (Sarawak Forestry Corporation's commercialisation partner)**
