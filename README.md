# Univents

Univents is an Android application for campus event management.  
The app allows users to browse events and register as **participants** or **committee members**, while admins can manage events and view registrations.  
The backend is powered by **Firebase Authentication** and **Cloud Firestore**.

---

## Features

- Application Workflow (Flow)
1. Users register using their email and password.
- Account data is stored in Firebase Authentication.
- User profile data is stored in Firestore.

2. Users log in.
- The system checks the user's role in Firestore:
- If the user is a user, they are directed to the user page.
- If the user is an admin, they are directed to the admin page.
- Users can view a list of events and register as participants or committee members.
Admins can manage events and view registration data.

### User
- Register and login using email & password
- Forgot password feature to reset password via email
- View available events
- Register for an event as:
  - Participant
  - Committee
- View registered events (My Events)
- Logout

### Admin
- Login as admin
- Create, update, and delete events
- View participant and committee lists for each event

---

## Tech Stack

- Android Studio
- Java
- Firebase Authentication
- Cloud Firestore
- RecyclerView
- Material Design Components

---

## Application Flow

1. **Authentication**
   - Users can register and log in using Firebase Authentication.
   - Users can reset their password using the "Forgot Password" feature by entering their registered email.
   - A password reset link will be sent to the user's email.
   - User profile data is stored in Firestore.

2. **Role Checking**
   - After login, the app checks the user role (`user` or `admin`) from Firestore.
   - Users are redirected to the appropriate home screen.

3. **Event Registration**
   - Users can browse events and register as participant or committee.
   - Registration data is stored under each event in Firestore.

4. **Admin Management**
   - Admins can manage event data and view registered users per event.

---

## Firestore Database Structure

users (collection)
└── userId (document)
├── name
├── email
└── role (user / admin)

events (collection)
└── eventId (document)
├── title
├── date
├── description
└── registrations (subcollection)
└── userId (document)
├── userName
└── role (participant / committee)


---

## Project Structure (Simplified)

com.example.univents
├── auth → Login & Register
├── user → User home, event list, my events
├── admin → Admin event management
├── model → Data models
└── utils → Firebase utilities

---

## Installation & Setup

1. Extract the project ZIP file
2. Open the project in **Android Studio**
3. Create a Firebase project
4. Add an Android app with package name: com.example.univents
5. Download `google-services.json` and place it in: app/google-services.json
6. Enable:
- Firebase Authentication (Email/Password)
- Cloud Firestore
7. Run the app using an emulator or physical device

---

## Admin Account Setup

1. Register a user normally
2. Open Firestore → `users` collection
3. Select the user document
4. Change: role = admin

---

## Notes

- Deleting a user from Firestore does **not** remove the Firebase Authentication account.
- To fully delete a user, remove them from both:
- Firebase Authentication
- Firestore database

---

## Author

Univents  
Android Campus Event Management Application
