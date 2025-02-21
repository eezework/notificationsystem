# Notification System

Notification System

Objective:

The goal of this assignment is to assess your technical expertise in designing and implementing a distributed Notification System that integrates with an existing Tournament System.

You will build a multi-service architecture, handle different notification types, apply caching for performance, and write unit tests.

1. Tech Stack
  Preferrable
  Java, Kotlin, Scala Spring Boot, MySQL, Kafka, Junit & Mockito, OpenAPI

  But you can use different tech stack. Java is must.

2. System Overview
  The Notification System should be designed as a separate microservice that integrates with the existing Tournament System.

  High-Level Architecture

  -> Tournament System (Existing System)
	  •	When a new tournament is created or a player wins a tournament, it should trigger a notification event.

  -> Notification Service (New System to Implement)
  	•	Listens for tournament events (via Kafka) and sends notifications via Push, SMS, or Email.
  	•	Supports multi-channel notifications based on user preferences.
  	•	Caches notification templates for quick retrieval.

3. Functional Requirements

  -> Notification API
  	•	POST /notifications – Send a notification (Push/SMS/Email)
  	•	GET /notifications/{id} – Fetch notification details
  	•	GET /notifications/user/{userId} – Get all notifications for a user

  -> Tournament System Hook
  	•	Whenever a new tournament is created, a notification event should be published.
  	•	If a player wins a tournament, a notification should be triggered.

  -> Notification Channels (could be third party services)
  	•	Push Notification
  	•	SMS Notification 
  	•	Email Notification
  	•	The system should decide the channel based on user preferences.

  -> Event-Driven Architecture
  	•	Use Kafka to publish and consume tournament events.
  	•	Notifications should be sent asynchronously.

  -> Caching Mechanism
  	•	Cache frequently used notification templates (e.g. Your tournament starts soon.).
  	•	Expire cache when a template is updated.

  -> Business Logic Complexity
  	•	If a tournament start time is in less than 30 minutes, send Push + SMS.
  	•	If a player wins, send Email + Push.
  	•	Ensure users don’t receive duplicate notifications within a short timeframe.

  -> Unit Testing with Mockito
	  •	Mock Kafka consumers.
	  Write tests for:
    	•	Sending notifications
    	•	Handling events from the tournament system
    	•	Cache retrieval & invalidation logic

4. Non-Functional Requirements
  •	Multi-Layered Architecture (Controller, Service, Repository)
  •	Exception Handling
  •	Logging
  •	OpenAPI Documentation (Swagger)
  •	Docker Support (Dockerfile, docker-compose.yml)

5. Submission Guidelines
  Code should be hosted on a public GitHub repository
  Include a README.md with:
  	•	Setup instructions
  	•	API documentation
  	•	Explanation of event-driven architecture and caching

6. Evaluation Criteria
  •	Microservices Architecture
  •	Event-Driven Integration with Tournament System
  •	Multi-Channel Notification Handling
  •	Efficient Caching & Performance Optimization
  •	Unit Testing & Test Coverage
  •	Logging, Monitoring & Error Handling


-> Bonus Points (Optional Enhancements)
  •	Implement a Notification Scheduler for delayed notifications.
  •	Add WebSocket Support for real-time push notifications.
  •	Implement a Notification Preferences API where users can choose their preferred channels.


Note: You don’t need to worry about Tournament System. In below scenarios, the Tournament System will send information to Kafka Topic(s) and Notification System will consume those information and process further.
1.	When a new Tournament is created.
2.	When a player wins a Tournament.
