# Chatbot with Fall Detection System

## Overview
This project combines a healthcare management system with a chatbot interface and fall detection capabilities. The system provides a comprehensive platform for users to access medical services, book appointments with doctors, request ambulances, and monitor for potential falls.

## Components

### User Authentication System
- **Login/Signup**: Secure user authentication system with session management
- **User Profiles**: User information management with profile updates
- **Admin Panel**: Administrative interface for system management

### Healthcare Management
- **Doctor Booking**: Schedule appointments with specialized doctors
- **Ambulance Services**: Request emergency ambulance services
- **Video Consultations**: Remote medical consultations

### Fall Detection System
The system monitors for potential falls using computer vision techniques and alerts when suspicious movements are detected. It identifies falls through:

- Sudden vertical drops (measuring the magnitude of downward movements)
- Unusual body aspect ratios (detecting when body proportions change significantly)

The system logs all potential fall events with detailed information including timestamps, detection methods, and measurement values.

### Chatbot Interface
The chatbot (Medibot) provides a natural language interface for:
- Receiving fall alerts
- Checking system status
- Configuring detection parameters
- Requesting assistance
- Analyzing prescriptions and medicines through image processing

## File Structure and Functionality

### Database
- `database.sql`: SQL schema for the entire system, including users, sessions, doctors, appointments, and ambulance bookings

### Authentication
- `login.php`: User login interface and authentication
- `signup.php`: New user registration
- `logout.php`: Session termination
- `db_connect.php`: Database connection configuration

### User Interface
- `booknow.php`: Interface for booking appointments with doctors
- `book_consultation.php`: Schedule video consultations with doctors
- `book_ambulance.php`: Request emergency ambulance services

### Admin Management
- `delete_appointment.php`: Admin functionality to manage appointments
- `delete_admin.php`: Super admin functionality to manage admin accounts
- `delete_ambulance.php`: Admin functionality to manage ambulance fleet
- `delete_ambulance_booking.php`: Admin functionality to manage ambulance bookings

### Chatbot System
- `chatbot.py`: Python-based AI chatbot using Google's Gemini model for medical assistance
- `fall_detection.log`: Log file containing records of potential fall events

## Database Structure
The system uses a MySQL database with the following key tables:
- `users`: Stores user account information
- `user_sessions`: Manages active user sessions
- `doctors`: Contains doctor profiles and availability
- `appointments`: Tracks scheduled appointments
- `ambulances`: Manages ambulance fleet information
- `ambulance_bookings`: Tracks ambulance service requests

## Usage
1. Register for an account using the signup page
2. Log in to access the dashboard
3. Book appointments with specialized doctors
4. Request ambulance services in emergencies
5. Schedule video consultations
6. Interact with the Medibot chatbot for medical assistance
7. Monitor fall detection alerts through the system

## Features
- Secure user authentication and session management
- Doctor appointment booking system
- Emergency ambulance request service
- AI-powered medical chatbot
- Fall detection monitoring with alerts
- Administrative dashboard for system management
- Comprehensive logging and activity tracking

## Requirements
- PHP 7.4+
- MySQL 5.7+
- Python 3.8+ (for chatbot and fall detection)
- Google Gemini API key
- Web server (Apache/Nginx)
- Camera for fall detection monitoring

## Future Enhancements
- Integration with emergency services
- Mobile app companion
- Voice command capabilities
- Machine learning for improved fall detection accuracy
- Remote monitoring for caregivers
- Electronic health records integration
- Prescription management system

## License
[Your chosen license]