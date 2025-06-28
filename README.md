Django Twitter-like Social Media Application
A modern, feature-rich social media platform built with Django that mimics core Twitter functionality. Users can create, share, edit, and delete tweets with photo attachments in a clean, responsive interface.
Features
🔐 User Authentication System

User Registration: Custom user registration with email validation
Secure Login/Logout: Django's built-in authentication system
Session Management: Secure user session handling
Protected Routes: Login-required functionality for posting and editing

📝 Tweet Management

Create Tweets: Compose tweets with text (up to 240 characters)
Photo Uploads: Attach images to tweets with automatic media handling
Edit Tweets: Modify your own tweets (text and photos)
Delete Tweets: Remove tweets with confirmation prompts
Real-time Feed: View all tweets in chronological order (newest first)

🖼️ Media Handling

Image Upload: Support for photo attachments in tweets
Media Storage: Organized file structure in /media/photos/ directory
Static Files: Proper handling of CSS, JavaScript, and images

🔒 Security & Permissions

User Isolation: Users can only edit/delete their own tweets
CSRF Protection: Built-in Django security features
Login Required: Protected endpoints for tweet operations
Form Validation: Server-side validation for all user inputs

Technology Stack

Backend: Django (Python)
Database: SQLite3 (development) / PostgreSQL (production ready)
Frontend: HTML Templates with Django Template Engine
Media Storage: Django's file handling system
Authentication: Django's built-in User model and authentication
Forms: Django ModelForms for data validation

Project Structure
DJANGO_FINAL/
├── twitterlike/
│   ├── firstproject/           # Main project configuration
│   ├── media/                  # User uploaded media files
│   ├── static/                 # Static files (CSS, JS, images)
│   ├── templates/              # HTML templates
│   └── tweet/                  # Main application
│       ├── migrations/         # Database migration files
│       ├── templates/          # App-specific templates
│       ├── __init__.py
│       ├── admin.py           # Django admin configuration
│       ├── apps.py            # App configuration
│       ├── forms.py           # Django forms
│       ├── models.py          # Database models
│       ├── tests.py           # Unit tests
│       ├── urls.py            # URL routing
│       └── views.py           # View functions
├── db.sqlite3                 # Database file
└── manage.py                  # Django management script
Installation and Setup
Prerequisites

Python 3.8 or higher
pip (Python package installer)
Virtual environment (recommended)

Step-by-Step Installation

Clone the repository
bashgit clone https://github.com/yourusername/django-twitter-clone.git
cd django-twitter-clone

Create and activate virtual environment
bashpython -m venv twitter_env
source twitter_env/bin/activate  # On Windows: twitter_env\Scripts\activate

Install required dependencies
bashpip install django
pip install Pillow  # For image handling

Apply database migrations
bashpython manage.py makemigrations
python manage.py migrate

Create a superuser (optional, for admin access)
bashpython manage.py createsuperuser

Collect static files (for production)
bashpython manage.py collectstatic

Run the development server
bashpython manage.py runserver

Access the application

Open your browser and navigate to http://127.0.0.1:8000/
Register a new account or login to start tweeting!



Usage Guide
Getting Started

Register: Create a new account using the registration form
Login: Access your account with your credentials
Create Tweets:

Write your message (up to 240 characters)
Optionally attach a photo
Click "Tweet" to share


View Feed: Browse all tweets in the main timeline
Manage Your Tweets: Edit or delete your own tweets
Logout: Safely logout when finished

Key Features

Tweet Timeline: See all tweets from all users in chronological order
Character Limit: 240-character limit enforces concise messaging
Photo Sharing: Upload and share images with your tweets
Edit Functionality: Modify your tweets after posting
Delete with Confirmation: Safe deletion with confirmation prompts

URL Structure
URL PatternView FunctionDescriptionLogin Required/tweet_listHome page with tweet feedNo/create/tweet_createCreate new tweetYes/<int:tweet_id>/edit/tweet_editEdit specific tweetYes/<int:tweet_id>/delete/tweet_deleteDelete specific tweetYes/register/registerUser registrationNo
Database Schema
Tweet Model
FieldTypeDescriptionConstraintsidBigAutoFieldPrimary keyAuto-incrementuserForeignKeyTweet authorLinks to User model, CASCADE deletetextCharFieldTweet contentMax 240 charactersphotoImageFieldOptional imageUpload to 'photos/', nullablecreated_atDateTimeFieldCreation timestampAuto-generatedupdated_atDateTimeFieldLast update timestampAuto-updated
Relationships

User → Tweet: One-to-Many (One user can have many tweets)
Cascade Deletion: When a user is deleted, all their tweets are automatically removed

Forms and Validation
TweetForm

Fields: text, photo
Validation: Character limits, file type validation
Media Handling: Automatic image processing and storage

UserRegistrationForm

Fields: username, email, password1, password2
Validation: Email format, password confirmation, unique username
Security: Password hashing and validation

Security Features

Authentication Required: Tweet creation, editing, and deletion require login
Ownership Validation: Users can only modify their own tweets
CSRF Protection: All forms include CSRF tokens
Secure Media Uploads: File type validation and secure storage
Password Security: Django's built-in password hashing

Development
Running Tests
bashpython manage.py test tweet
Database Management
bash# Create new migrations after model changes
python manage.py makemigrations

# Apply migrations
python manage.py migrate

# Access Django shell
python manage.py shell
Admin Interface

Access at http://127.0.0.1:8000/admin/
Manage users and tweets through Django admin
Requires superuser account

Production Deployment
Environment Variables
Create a .env file for production settings:
SECRET_KEY=your-secret-key
DEBUG=False
ALLOWED_HOSTS=yourdomain.com,www.yourdomain.com
DATABASE_URL=your-database-url
Production Checklist

 Set DEBUG = False
 Configure proper database (PostgreSQL recommended)
 Set up static file serving
 Configure media file storage (AWS S3, etc.)
 Set secure secret key
 Configure HTTPS
 Set up proper logging

Contributing

Fork the repository
Create a feature branch (git checkout -b feature/amazing-feature)
Commit your changes (git commit -m 'Add amazing feature')
Push to the branch (git push origin feature/amazing-feature)
Open a Pull Request

Development Guidelines

Follow PEP 8 style guidelines
Add tests for new features
Update documentation for significant changes
Ensure migrations are included for model changes

Future Enhancements
Planned Features

User Profiles: Detailed user pages with bio and follower counts
Follow System: Follow/unfollow other users
Like System: Like and unlike tweets
Retweet Functionality: Share other users' tweets
Hashtag Support: Tag and search tweets by hashtags
Mentions System: @username mentions with notifications
Real-time Updates: WebSocket integration for live timeline updates
Direct Messages: Private messaging between users
Tweet Threading: Reply to tweets and create conversation threads
Search Functionality: Search tweets by content, user, or hashtag
Mobile App: React Native or Flutter mobile application
REST API: Full RESTful API for third-party integrations

Technical Improvements

Caching: Redis integration for improved performance
Pagination: Efficient pagination for large tweet volumes
Image Processing: Automatic image resizing and optimization
Email Notifications: Email alerts for mentions and follows
Rate Limiting: API rate limiting to prevent abuse
Advanced Security: Two-factor authentication

Known Issues

Registration form has a minor bug (POST vs post method)
Media files need proper production storage configuration
No pagination implemented for large datasets


Support
For questions, bug reports, or feature requests:

Check existing GitHub Issues
Create a new issue with detailed description
Include error messages and steps to reproduce problems

Acknowledgments

Django Framework: For providing robust web development tools
Django Community: For excellent documentation and support
Twitter: For inspiration and UI/UX reference
Bootstrap: For responsive design components (if used)
