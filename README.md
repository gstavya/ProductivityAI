# Jarvis - Voice-Controlled Google API Assistant

A voice-controlled personal assistant that integrates with Google's suite of services (Gmail, Google Calendar, Google Drive, and Google Contacts) using speech recognition and AI-powered natural language processing.

## 🚀 Features

### Voice Interface

- **Speech Recognition**: Uses Google's speech recognition API to convert voice commands to text
- **Text-to-Speech**: Responds with voice feedback using macOS's built-in text-to-speech
- **Natural Language Processing**: Powered by OpenAI's GPT-3.5-turbo for intelligent command interpretation

### Google Services Integration

#### 📧 Gmail (`gmail.py`)

- **Create Drafts**: Compose and save email drafts
- **Send Emails**: Send emails directly to recipients
- **Smart Email Search**: Find emails using natural language descriptions with RAG (Retrieval-Augmented Generation)
- **Date Range Filtering**: Search emails within specific date ranges

#### 📅 Google Calendar (`gcalendar.py`)

- **Create Events**: Schedule new calendar events with attendees
- **View Upcoming Events**: Get a list of upcoming events
- **Smart Event Search**: Find specific events using natural language descriptions
- **Date Range Queries**: Search events within custom date ranges

#### 📁 Google Drive (`gdrive.py`)

- **File Search**: Find files using natural language descriptions
- **Date-Based Filtering**: Search files modified within specific date ranges
- **RAG-Powered Search**: Uses vector embeddings for intelligent file discovery

#### 👥 Google Contacts (`gcontacts.py`)

- **Contact Lookup**: Find specific contacts by name (handles speech recognition errors)
- **List All Contacts**: Retrieve complete contact list with names and emails
- **Fuzzy Name Matching**: Intelligently matches spoken names to contact entries

## 🛠️ Installation

### Prerequisites

- Python 3.11+
- macOS (for text-to-speech functionality)
- Google Cloud Project with APIs enabled

### Setup

1. **Clone the repository**

   ```bash
   git clone <your-repo-url>
   cd <your-repo-name>
   ```

2. **Create and activate virtual environment**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Set up Google API credentials**

   - Create a Google Cloud Project
   - Enable the following APIs:
     - Gmail API
     - Google Calendar API
     - Google Drive API
     - Google People API
   - Download `credentials.json` and place it in the project root
   - Run the authentication flow to generate `token.json`

5. **Configure environment variables**
   Create a `.env` file with:
   ```
   OPENAI_API_KEY=your_openai_api_key_here
   ```

## 📋 Dependencies

The project requires the following key packages:

- `langchain` - AI framework for building applications
- `langchain-openai` - OpenAI integration
- `google-api-python-client` - Google APIs client library
- `google-auth-oauthlib` - OAuth authentication
- `speech_recognition` - Speech recognition
- `python-dotenv` - Environment variable management
- `chromadb` - Vector database for RAG
- `scikit-learn` - Machine learning utilities

## 🎯 Usage

### Starting the Assistant

```bash
python app.py
```

### Voice Commands Examples

#### Email Management

- "Send an email to john@example.com about the meeting tomorrow"
- "Find emails from Sarah about the project"
- "Create a draft email to the team about the quarterly report"

#### Calendar Management

- "Schedule a meeting with Alice tomorrow at 2 PM"
- "What are my upcoming events?"
- "Find the meeting about the budget from last week"

#### File Management

- "Find the presentation I worked on last month"
- "Search for documents about the marketing campaign"

#### Contact Management

- "Find John Smith's contact information"
- "Show me all my contacts"

### Exiting the Assistant

Say "thanks", "bye", or "thank you" to exit the application.

## 🔧 Configuration

### Time Zone

The application is configured for Pacific Time Zone. To change this, modify the timezone settings in `gcalendar.py`.

### Speech Recognition

- Language: English (en)
- Timeout: 5 seconds for voice input
- Voice: Daniel (macOS text-to-speech)

### AI Model

- Model: GPT-3.5-turbo
- Temperature: Default
- Max tokens: Default

## 📁 Project Structure

```
├── app.py              # Main application with voice interface
├── gmail.py            # Gmail API integration
├── gcalendar.py        # Google Calendar API integration
├── gdrive              # Google Drive API integration
├── gcontacts.py        # Google Contacts API integration
├── credentials.json    # Google API credentials (not in repo)
├── token.json          # OAuth token (not in repo)
├── .env               # Environment variables (not in repo)
└── README.md          # This file
```

## 🔐 Security Notes

- **Never commit** `credentials.json`, `token.json`, or `.env` files
- Keep your API keys secure and rotate them regularly
- The application requests minimal necessary permissions for each Google service

## 🚨 Troubleshooting

### Common Issues

1. **Speech Recognition Not Working**

   - Ensure microphone permissions are granted
   - Check internet connection (required for Google Speech API)

2. **Google API Authentication Errors**

   - Verify `credentials.json` is in the project root
   - Ensure `token.json` exists and is valid
   - Check that all required Google APIs are enabled

3. **Text-to-Speech Not Working**

   - This feature requires macOS
   - Verify the "Daniel" voice is available in System Preferences

4. **OpenAI API Errors**
   - Verify your OpenAI API key is set in `.env`
   - Check your OpenAI account has sufficient credits

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Google APIs for providing the backend services
- OpenAI for the language model capabilities
- LangChain for the AI framework
- The open-source community for the various libraries used

---

**Note**: This is a personal assistant application. Please ensure you have proper authorization to access the Google services and contacts you're querying.
