---
layout: post
date: 2025-06-23
author: "Fara Rahmasari Fahirun"
title: "Temu Darah: Location-Based Blood Donation App"
categories: [Android Studio, Firebase, Java]
description: Complete journey of building a location-based blood donation app, from concept to implementing complex features like real-time chat, geolocation, and history system.
tags: [Android Studio, Firebase, Firestore, GeoFire, Java, Mobile Development]
image: /assets/img/temudarah.jpg
---

# **Temu Darah**

A native Android application designed to bridge the gap between individuals in need of blood transfusions and donors ready to help. This app uses geolocation technology to connect users based on geographical proximity and blood type compatibility in **real-time**.

> **Mission:** Accelerate the blood donor search process through an efficient and reliable digital platform.

## **Team Collaboration**

This project was developed through collaborative effort by a dedicated team of three developers, each contributing unique expertise and skills to create a comprehensive blood donation platform.

### **Team Members & Contributions**

**1. Fara Rahmasari Fahirun** - *Lead Developer & System Architect*
- **Core Responsibilities:** System architecture design, Firebase backend integration, and geolocation implementation
- **Key Contributions:**
  - Designed and implemented GeoFire-based location search system
  - Developed real-time chat architecture using Firestore listeners
  - Created data enrichment patterns for multiple collection queries
  - Implemented authentication flow and user management system
  - Optimized app performance through caching mechanisms

**2. Andi Fauzan Alwan Pananrangi** - *Frontend Developer & UI/UX Designer*
- **Core Responsibilities:** User interface design, user experience optimization, and fragment management
- **Key Contributions:**
  - Designed intuitive and responsive user interface components
  - Implemented navigation between fragments (Home, Chat, History, Awards)
  - Created custom UI elements and layouts for donation requests
  - Developed gamification system and user dashboard
  - Ensured consistent Material Design implementation across the app

**3. Nancy Jiwono** - *Backend Developer & Quality Assurance*
- **Core Responsibilities:** Database schema design, API integration, and testing framework
- **Key Contributions:**
  - Designed efficient Firestore database structure and relationships
  - Implemented notification system and push messaging
  - Developed data validation and error handling mechanisms
  - Created comprehensive testing procedures and bug tracking
  - Optimized database queries for better performance

### **Collaborative Development Process**

**Planning & Design Phase**
- Conducted joint brainstorming sessions to identify core problems in blood donation process
- Collaborated on system requirements analysis and feature prioritization
- Created unified development roadmap with clear milestone deliverables

**Development Workflow**
- Utilized Git version control with feature-based branching strategy
- Implemented code review process to ensure quality and consistency
- Regular team meetings for progress updates and technical discussions
- Shared responsibility for documentation and code commenting

**Integration & Testing**
- Coordinated integration testing between frontend and backend components
- Cross-functional testing to ensure seamless user experience
- Joint debugging sessions for complex technical challenges
- Collaborative performance optimization and security reviews

## **Problem Statement**
<div align="center">
  <img src="/assets/img/temudarah2.png" alt="Problem Statement" style="max-width: 70%; height: auto; border-radius: 10px; margin: 20px 0;">
</div>

### **Challenges in Blood Donor Search**
**1. Manual Process**  
Donor search still relies on WhatsApp groups and unstructured social media platforms.

**2. Scattered Information**  
No centralized platform for coordination between requesters and blood donors.

**3. Critical Time**  
Emergency situations require rapid response that's difficult to achieve with conventional methods.

**4. Limited Reach**  
Difficult to find donors in specific geographical areas due to network limitations.

## **Key Features**
**1. Smart Location-Based Search**  
Donor search within a 50km radius using efficient geospatial algorithms powered by GeoFire technology.

**2. Real-time Chat System**  
Direct communication between requesters and potential donors with integrated push notification system.

**3. Personal Dashboard**  
- My Requests: Manage and monitor created donor requests
- History: Complete archive of donation activities and user interactions
- Awards: Gamification system to motivate active donors

**4. Smart Notifications**  
Automatic alerts for new messages, help offers, and donation status updates.

## **Application Architecture**

```
Temu Darah Application Architecture
├── Authentication Layer (Firebase Auth)
├── Main Activity Controller
│   ├── Home Fragment (Location-based search)
│   ├── Chat Fragment (Real-time messaging)
│   ├── My Requests Fragment (User requests management)
│   ├── History Fragment (Donation history)
│   └── Awards Fragment (Gamification system)
└── Backend Services (Cloud Firestore + GeoFire)
```

## **Technical Implementation**

**1. Geospatial Query with GeoFire**

**Challenge:** Display donor requests only around user location without fetching all data from database into the application.

**Solution:** GeoFire implementation for efficient and optimal location-based queries.

```java
// Initialize GeoFire for location search
private void initializeGeoFire() {
    DatabaseReference geoRef = FirebaseDatabase.getInstance()
        .getReference("donation_locations");
    geoFire = new GeoFire(geoRef);
}

// Query requests within specific radius
private void searchNearbyRequests(double latitude, double longitude) {
    GeoQuery geoQuery = geoFire.queryAtLocation(
        new GeoLocation(latitude, longitude), 
        SEARCH_RADIUS_KM
    );
    
    geoQuery.addGeoQueryEventListener(new GeoQueryEventListener() {
        @Override
        public void onKeyEntered(String key, GeoLocation location) {
            loadDonationRequest(key);
        }
        
        @Override
        public void onKeyMoved(String key, GeoLocation location) {
            updateRequestLocation(key, location);
        }
        
        @Override
        public void onKeyExited(String key) {
            removeRequestFromView(key);
        }
    });
}
```

**2. Real-time Chat Architecture**

```java
// ChatRoom Model
public class ChatRoom {
    private String chatId;
    private String requestId;
    private String requesterId;
    private String donorId;
    private String lastMessage;
    private long lastMessageTime;
    private Map<String, Boolean> participants;
    
    // Constructor and getter/setter methods
}

// Real-time chat implementation
private void setupChatListener() {
    chatRef.addSnapshotListener((snapshot, error) -> {
        if (error != null) {
            Log.w("Chat", "Listen failed.", error);
            return;
        }
        
        for (DocumentChange dc : snapshot.getDocumentChanges()) {
            switch (dc.getType()) {
                case ADDED:
                    Message newMessage = dc.getDocument().toObject(Message.class);
                    addMessageToChat(newMessage);
                    break;
                case MODIFIED:
                    // Handle message updates
                    break;
                case REMOVED:
                    // Handle message removal
                    break;
            }
        }
    });
}
```

**3. Data Enrichment Pattern**

**Problem:** Efficiently combining data from multiple collections (users, requests, donations).

```java
// Pattern for chained data retrieval
private void loadEnrichedDonationHistory() {
    activeDonationsRef
        .whereEqualTo("userId", currentUserId)
        .get()
        .addOnSuccessListener(donationSnapshot -> {
            for (DocumentSnapshot donation : donationSnapshot.getDocuments()) {
                String requestId = donation.getString("requestId");
                String partnerId = donation.getString("partnerId");
                
                // Chain 1: Get request details
                requestsRef.document(requestId).get()
                    .addOnSuccessListener(requestDoc -> {
                        DonationRequest request = requestDoc.toObject(DonationRequest.class);
                        
                        // Chain 2: Get partner details
                        usersRef.document(partnerId).get()
                            .addOnSuccessListener(userDoc -> {
                                User partner = userDoc.toObject(User.class);
                                
                                // Combine all data
                                EnrichedDonationHistory enriched = new EnrichedDonationHistory(
                                    donation, request, partner
                                );
                                updateHistoryView(enriched);
                            });
                    });
            }
        });
}
```

## **Challenges & Solutions**

#### **1. Chat Room Duplication**

**Problem:** Same user could have multiple chat rooms for different requests.

**Solution:** Implementation of unique chat ID based on user IDs combination.

```java
private String generateChatId(String userId1, String userId2) {
    // Ensure consistent ordering regardless of parameter order
    if (userId1.compareTo(userId2) < 0) {
        return userId1 + "_" + userId2;
    } else {
        return userId2 + "_" + userId1;
    }
}
```

### **2. Performance Optimization**

**Problem:** Loading multiple nested data causes lag and poor user experience.

**Solution:** Implementation of lazy loading and caching mechanism in the application.

```java
// Cache to avoid repeated queries
private Map<String, User> userCache = new HashMap<>();

private void loadUserData(String userId, OnUserLoadedCallback callback) {
    if (userCache.containsKey(userId)) {
        callback.onUserLoaded(userCache.get(userId));
        return;
    }
    
    usersRef.document(userId).get()
        .addOnSuccessListener(doc -> {
            User user = doc.toObject(User.class);
            userCache.put(userId, user);
            callback.onUserLoaded(user);
        });
}
```

## **Technology Stack**

| Category | Technology | Function |
|----------|-----------|----------|
| **Frontend** | Android Native (Java) | UI/UX Development |
| **Backend** | Firebase Suite | Authentication, Database, Storage |
| **Database** | Cloud Firestore | NoSQL Document Database |
| **Geolocation** | GeoFire | Geospatial Queries |
| **Real-time** | Firestore Listeners | Live Data Updates |
| **UI Libraries** | Glide, CircleImageView | Image Loading & UI Components |

### **Dependencies** (build.gradle)

```gradle
dependencies {
    // Firebase Core Services
    implementation 'com.google.firebase:firebase-auth:21.1.0'
    implementation 'com.google.firebase:firebase-firestore:24.4.1'
    implementation 'com.google.firebase:firebase-database:20.1.0'
    
    // Geolocation Services
    implementation 'com.firebase:geofire-android:3.1.0'
    
    // UI & Image Processing
    implementation 'com.github.bumptech.glide:glide:4.14.2'
    implementation 'de.hdodenhof:circleimageview:3.1.0'
    
    // Material Design Components
    implementation 'com.google.android.material:material:1.7.0'
}
```

## **Technical Achievements**
**1. Efficient Geospatial Query**  
GeoFire implementation enables location-based donor search with optimal performance.

**2. Real-time Communication**  
Chat system using Firestore listeners provides seamless communication experience.

**3. Scalable Architecture**  
Proper data separation allows the application to grow with increasing user base.

**4. Intuitive User Experience**  
Responsive and easy-to-understand interface increases application adoption.

## **Future Improvements**
- Machine Learning for donor demand prediction
- Integration with hospital systems
- Advanced notification scheduling
- Offline capability with local caching
- Analytics dashboard for administrators

---

> **Team Takeaway:** This collaborative project demonstrated that effective teamwork, combined with diverse technical expertise, can create impactful solutions for real-world problems. Each team member's unique contributions were essential in developing a comprehensive and user-friendly blood donation platform.

**Repository:** [View on GitHub](https://github.com/farafahirun/temu-darah)

---

*Interested in implementation details or want to contribute? Feel free to reach out to our development team!*