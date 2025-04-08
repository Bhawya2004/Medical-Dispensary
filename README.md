# Chatbot with Fall Detection System

## Overview
This project combines a healthcare management system with a chatbot interface and fall detection capabilities. The system provides a comprehensive platform for users to access medical services, book appointments with doctors, request ambulances, and monitor for potential falls. The project is built using PHP, MySQL, Python, and integrates with Google's Gemini AI model for the chatbot functionality.

## Components

### User Authentication System
- **Login/Signup**: Secure user authentication system with session management
  - Password hashing for security
  - Session tracking to prevent unauthorized access
  - Login attempt monitoring to prevent brute force attacks
  - Automatic activity logging for audit trails
- **User Profiles**: User information management with profile updates
  - Personal information storage and management
  - Appointment history tracking
  - Health data integration with Google Fit
- **Admin Panel**: Administrative interface for system management
  - User account management
  - Doctor profile management
  - Appointment oversight and scheduling
  - Ambulance fleet management

### Healthcare Management
- **Doctor Booking**: Schedule appointments with specialized doctors
  - Filtering by specialization, rating, and availability
  - Real-time availability checking
  - Appointment confirmation and reminders
  - Rescheduling and cancellation options
- **Ambulance Services**: Request emergency ambulance services
  - Real-time ambulance tracking
  - Automatic assignment of nearest available ambulance
  - Location-based routing
  - Emergency contact notification
- **Video Consultations**: Remote medical consultations
  - Secure video conferencing integration
  - Prescription sharing capabilities
  - Medical record access during consultation
  - Follow-up appointment scheduling

### Fall Detection System
The system monitors for potential falls using computer vision techniques and alerts when suspicious movements are detected. It identifies falls through:

- **Sudden vertical drops**: The system measures the magnitude of downward movements
  - Tracks vertical position changes over time
  - Triggers alerts when drops exceed predefined thresholds
  - Records drop measurements in the log file
- **Unusual body aspect ratios**: Detects when body proportions change significantly
  - Analyzes the ratio of height to width of detected bodies
  - Compares current ratios to normal standing positions
  - Flags unusual ratios that may indicate a fall

The system logs all potential fall events with detailed information including timestamps, detection methods, and measurement values in the `fall_detection.log` file.

### Chatbot Interface (Medibot)
The chatbot provides a natural language interface powered by Google's Gemini 1.5 Pro model:

- **Medical Assistance**:
  - Answers health-related questions with accurate medical information
  - Provides first aid guidance in emergency situations
  - Offers medication information and potential interactions
  - Suggests lifestyle and wellness recommendations

- **Prescription Analysis**:
  - Processes images of prescriptions using computer vision
  - Extracts medication names, dosages, and instructions
  - Provides information about prescribed medications
  - Offers reminders for medication schedules

- **Fall Detection Integration**:
  - Receives and processes fall detection alerts
  - Initiates emergency protocols when falls are detected
  - Contacts emergency services or designated caregivers
  - Provides status updates on monitored individuals

- **System Management**:
  - Allows users to check appointment status
  - Facilitates booking or rescheduling appointments
  - Provides ambulance tracking information
  - Manages user preferences and settings

## File Structure and Functionality

### Database
- `database.sql`: Complete SQL schema for the entire system
  - Creates all necessary tables with appropriate relationships
  - Implements security features like password reset tokens
  - Sets up triggers for automatic event logging
  - Establishes indexes for optimized query performance

### Authentication
- `login.php`: User login interface and authentication
  - Validates user credentials against the database
  - Manages session creation and security
  - Tracks login attempts for security monitoring
  - Redirects to appropriate dashboard based on user role
- `signup.php`: New user registration
  - Collects and validates user information
  - Implements email verification
  - Creates secure user accounts with hashed passwords
  - Sets up initial user profiles
- `logout.php`: Session termination
  - Securely ends user sessions
  - Clears session data and cookies
  - Logs logout events for security tracking
  - Redirects to login page
- `db_connect.php`: Database connection configuration
  - Establishes secure connection to MySQL database
  - Manages connection parameters
  - Implements error handling for database connectivity issues
  - Sets character encoding and other database settings

### User Interface
- `booknow.php`: Interface for booking appointments with doctors
  - Displays available doctors with specializations and ratings
  - Implements date and time selection
  - Processes appointment requests
  - Shows user's existing appointments
- `book_consultation.php`: Schedule video consultations with doctors
  - Sets up video consultation appointments
  - Manages consultation scheduling
  - Handles consultation request processing
  - Redirects to video consultation interface
- `book_ambulance.php`: Request emergency ambulance services
  - Processes ambulance booking requests
  - Finds and assigns available ambulances
  - Updates ambulance availability status
  - Returns vehicle information to the user
- `index.php`: Main dashboard with health data integration
  - Displays user health statistics
  - Integrates with Google Fit API
  - Shows appointment summaries
  - Provides quick access to all system features

### Admin Management
- `delete_appointment.php`: Admin functionality to manage appointments
  - Allows administrators to cancel or reschedule appointments
  - Logs appointment changes for auditing
  - Sends notifications to affected users
  - Updates appointment database records
- `delete_admin.php`: Super admin functionality to manage admin accounts
  - Provides interface for removing administrator accounts
  - Implements security checks to prevent self-deletion
  - Manages administrator privileges
  - Maintains admin account integrity
- `delete_ambulance.php`: Admin functionality to manage ambulance fleet
  - Handles ambulance removal from the system
  - Manages related booking records
  - Updates database with fleet changes
  - Maintains data integrity with transaction support
- `delete_ambulance_booking.php`: Admin functionality to manage ambulance bookings
  - Processes ambulance booking cancellations
  - Updates ambulance availability status
  - Maintains booking records
  - Implements database transaction safety

### Chatbot System
- `chatbot.py`: Python-based AI chatbot using Google's Gemini model
  - Implements the Gemini 1.5 Pro model integration
  - Processes natural language queries
  - Handles multimodal inputs (text and images)
  - Maintains conversation context through chat sessions
  - Restricts responses to medical domain
  - Provides concise, helpful medical information
- `fall_detection.log`: Log file containing records of potential fall events
  - Records timestamps of detected falls
  - Documents detection methods used
  - Stores measurement values for vertical drops
  - Tracks unusual aspect ratios
  - Provides chronological history of fall events

### Frontend Assets
- `assets/js/google-fit.js`: Google Fit API integration
  - Handles authentication with Google's services
  - Fetches and displays user health data
  - Manages API responses and data visualization
  - Provides real-time health metric updates

## Database Structure
The system uses a MySQL database with the following key tables:

- `users`: Stores user account information
  - Personal details (name, email, contact information)
  - Authentication credentials (hashed passwords)
  - Account status and activity tracking
  - Profile image references

- `user_sessions`: Manages active user sessions
  - Session identifiers and tokens
  - Login timestamps and activity tracking
  - IP address and user agent information
  - Session status management

- `doctors`: Contains doctor profiles and availability
  - Professional qualifications and specializations
  - Availability schedules and working hours
  - Rating and review information
  - Profile images and contact details

- `appointments`: Tracks scheduled appointments
  - Patient and doctor associations
  - Appointment dates and times
  - Status tracking (scheduled, completed, cancelled)
  - Appointment notes and follow-up information

- `ambulances`: Manages ambulance fleet information
  - Vehicle details and registration information
  - Current availability status
  - Location tracking data
  - Driver information and contact details

- `ambulance_bookings`: Tracks ambulance service requests
  - Patient information and pickup location
  - Booking time and status
  - Assigned ambulance details
  - Emergency contact information

## Integration with External Services

### Firebase Integration
The system integrates with Firebase for:
- Real-time database functionality
- Authentication services
- Cloud messaging for notifications
- Analytics for usage tracking
- Remote configuration management

### Google Fit API
Health data integration provides:
- Activity and step counting
- Heart rate monitoring
- Sleep tracking
- Calorie expenditure calculation
- Weight and body measurements

### Google Gemini AI
The chatbot leverages Google's Gemini 1.5 Pro model for:
- Natural language understanding and generation
- Medical knowledge and healthcare guidance
- Multimodal capabilities (text and image processing)
- Contextual conversation management

## Usage
1. Register for an account using the signup page
2. Log in to access the dashboard
3. Book appointments with specialized doctors
4. Request ambulance services in emergencies
5. Schedule video consultations
6. Interact with the Medibot chatbot for medical assistance
7. Monitor fall detection alerts through the system
8. Connect Google Fit to track health metrics
9. View and manage your medical appointments

## Features
- Secure user authentication and session management
- Doctor appointment booking system
- Emergency ambulance request service
- AI-powered medical chatbot with prescription analysis
- Fall detection monitoring with alerts
- Administrative dashboard for system management
- Comprehensive logging and activity tracking
- Google Fit integration for health metrics
- Firebase integration for real-time functionality

## Requirements
- PHP 7.4+
- MySQL 5.7+
- Python 3.8+ (for chatbot and fall detection)
- Google Gemini API key
- Firebase account and configuration
- Google Fit API credentials
- Web server (Apache/Nginx)
- Camera for fall detection monitoring
- Node.js and npm for frontend dependencies

## Installation and Setup
1. Clone the repository
2. Import the database schema from `database.sql`
3. Configure database connection in `db_connect.php`
4. Set up Google Gemini API key for chatbot functionality
5. Configure Firebase credentials
6. Set up Google Fit API credentials
7. Install Python dependencies for the chatbot
8. Configure web server to serve the PHP files
9. Set up camera for fall detection system

## Future Enhancements
- Integration with emergency services
- Mobile app companion
- Voice command capabilities
- Machine learning for improved fall detection accuracy
- Remote monitoring for caregivers
- Electronic health records integration
- Prescription management system
- Telemedicine platform expansion
- Wearable device integration

## License
[Your chosen license]

## Repository
This project is maintained at: https://github.com/MerazMz/dispensary_medibot