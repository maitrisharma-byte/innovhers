# innovhers
canva link- https://www.canva.com/design/DAHB2KLSFTU/vlSnrpBb2bVMMu8fTyIHEQ/edit?utm_content=DAHB2KLSFTU&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton
# MatchMaker - Intelligent Startup-Investor Matchmaking Platform

A full-stack web application for startup-investor matchmaking with AI-powered insights, built with Flask backend and modern frontend using Tailwind CSS.

## 🚀 Features

### Core Features
- **Role-based Authentication**: Separate signup/login for startups and investors
- **Profile Management**: Comprehensive profile creation with sectors, stages, funding requirements
- **Intelligent Matching Engine**: 0-100 score based on 5 dimensions:
  - Stage alignment
  - Sector match
  - Funding compatibility
  - Geographic proximity
  - Thematic fit
- **Ranked Recommendations**: Smart algorithm suggests best matches with filtering
- **Deep-dive Analysis**: Detailed view with radar charts and AI insights
- **Connection Requests**: Send/accept/reject connection requests
- **Real-time Messaging**: Built-in chat for connected users
- **AI Auto-Messaging System**: 🤖 NEW!
  - Personalized intro messages when connections are sent
  - Context-aware conversation suggestions
  - Smart reply recommendations based on profiles
- **Verification Badges**: DPIIT for startups, SEBI for investors

### AI-Powered Insights (Groq API)
- **AI Chatbot Assistant**: 🤖 NEW!
  - Available on every page
  - Context-aware help and guidance
  - Knows your profile and connections
  - Only answers platform-related questions
  - Smart suggestions and tips
- **Growth Projections**: AI-generated growth potential analysis
- **Investment Analysis**: Use of funds, risks, opportunity scoring
- **Competitive Landscape**: Competitor identification and differentiation strategies
- **Uniqueness Score**: Gauge how unique your startup is
- **Pitch Perfector**: AI feedback on pitch quality with grading
- **Funding Readiness Meter**: Profile completeness scoring

### Startup Intelligence Suite
- **Competitor Radar**: Notifications about similar startups
- **Uniqueness Score**: Visual gauge with AI suggestions
- **Funding Readiness**: Progress bar with recommendations
- **Pitch Perfector**: A/B testing with AI feedback

## 🛠️ Tech Stack

### Backend
- **Flask** - Web framework
- **Flask-SQLAlchemy** - ORM
- **Flask-JWT-Extended** - Authentication
- **Flask-CORS** - Cross-origin support
- **SQLite** - Database (development)
- **Groq API** - AI insights
- **Faker** - Dummy data generation

### Frontend
- **HTML5**
- **Tailwind CSS** (CDN) - Styling
- **Vanilla JavaScript** - Logic
- **Chart.js** - Radar charts
- **Fetch API** - Backend communication

## 📁 Project Structure

```
vega/
├── backend/
│   ├── app.py                 # Main Flask application
│   ├── models.py              # SQLAlchemy models
│   ├── auth.py                # Authentication routes
│   ├── profiles.py            # Profile CRUD routes
│   ├── matching.py            # Matching algorithm & recommendations
│   ├── connections.py         # Connection & messaging endpoints
│   ├── ai_insights.py         # Groq API integration
│   ├── seed.py                # Database seeding script
│   ├── config.py              # Configuration
│   ├── requirements.txt       # Python dependencies
│   ├── .env                   # Environment variables
│   └── .env.example           # Environment template
├── frontend/
│   ├── index.html             # Landing page
│   ├── login.html             # Login page
│   ├── signup-startup.html    # Startup signup
│   ├── signup-investor.html   # Investor signup
│   ├── profile-startup.html   # Startup profile editor
│   ├── profile-investor.html  # Investor profile editor
│   ├── dashboard-startup.html # Startup dashboard with intelligence
│   ├── dashboard-investor.html # Investor dashboard
│   ├── startup-detail.html    # Deep-dive for investors
│   ├── investor-detail.html   # Deep-dive for startups
│   ├── my-connections.html    # Connections & messaging
│   └── js/
│       └── api.js             # API utility functions
└── README.md                  # This file
```

## 🚦 Getting Started

### Prerequisites
- Python 3.10 or higher
- pip (Python package manager)
- A Groq API key (get from [console.groq.com](https://console.groq.com))

### Installation

1. **Clone or navigate to the repository**
   ```bash
   cd c:\Users\mahis\OneDrive\Documents\vega
   ```

2. **Set up Python virtual environment**
   ```bash
   cd backend
   python -m venv venv
   
   # On Windows:
   venv\Scripts\activate
   
   # On macOS/Linux:
   source venv/bin/activate
   ```

3. **Install Python dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   
   Copy `.env.example` to `.env`:
   ```bash
   copy .env.example .env
   ```
   
   Edit `.env` and add your Groq API key:
   ```
   JWT_SECRET_KEY=your-secret-key-here-change-in-production
   GROQ_API_KEY=your-groq-api-key-here
   DATABASE_URL=sqlite:///matchmaking.db
   ```

5. **Initialize database and seed data**
   ```bash
   python seed.py
   ```
   
   This will create the database and populate it with 8 startups and 8 investors, plus sample connections.

6. **Start the Flask server**
   ```bash
   python app.py
   ```
   
   Server will start at `http://127.0.0.1:5000`

7. **Open the frontend**
   
   Open `frontend/index.html` in your web browser, or use a simple HTTP server:
   
   ```bash
   # In a new terminal, from the frontend directory:
   cd ../frontend
   python -m http.server 8000
   ```
   
   Then navigate to `http://localhost:8000`

## 🎮 Usage

### Demo Credentials

After running the seed script, you can login with:

**Startups:**
- Email: `startup1@example.com` to `startup8@example.com`
- Password: `password123`

**Investors:**
- Email: `investor1@example.com` to `investor8@example.com`
- Password: `password123`

### User Flow

#### For Startups:
1. Sign up as a startup → Create profile
2. View dashboard with:
   - Uniqueness score
   - Funding readiness meter
   - Pitch perfector
   - Recommended investors
3. Click on an investor to see deep-dive with match breakdown
4. Send connection request
5. Once accepted, chat in "My Connections"

#### For Investors:
1. Sign up as an investor → Create profile
2. View dashboard with recommended startups
3. Apply filters (stage, sector, location, verified)
4. Click "Deep Dive" to see:
   - Radar chart showing compatibility
   - AI insights (growth, investment analysis, competitive landscape)
   - Traction and team details
5. Send connection request
6. Chat with connected startups

## 🔌 API Endpoints

### Authentication
- `POST /api/register` - Register new user
- `POST /api/login` - Login and get JWT token
- `GET /api/me` - Get current user info

### Profiles
- `GET /api/profile` - Get own profile
- `POST /api/profile/startup` - Create/update startup profile
- `POST /api/profile/investor` - Create/update investor profile
- `GET /api/profile/startup/<id>` - Public startup profile
- `GET /api/profile/investor/<id>` - Public investor profile

### Matching & Recommendations
- `GET /api/recommendations/startups` - Recommended startups for investor
- `GET /api/recommendations/investors` - Recommended investors for startup
- `GET /api/match/breakdown` - Detailed match score breakdown

### Connections
- `POST /api/connections` - Send connection request
- `GET /api/connections/pending` - Get pending requests
- `PUT /api/connections/<id>` - Accept/reject request
- `GET /api/connections` - Get accepted connections
- `GET /api/connections/<id>/messages` - Get messages
- `POST /api/connections/<id>/messages` - Send message

### AI Insights
- `GET /api/ai/startup-insights/<id>` - Growth, investment, competitive analysis
- `GET /api/ai/startup-uniqueness/<id>` - Uniqueness score and suggestions
- `POST /api/ai/pitch-feedback` - Grade and improve pitch
- `GET /api/ai/funding-readiness/<id>` - Readiness score

## 🎨 Design Highlights

- **Clean, modern UI** with Tailwind CSS
- **Responsive design** works on desktop and mobile
- **Smooth animations** and transitions
- **Intuitive navigation** with role-based menus
- **Visual feedback** for all actions
- **Accessibility** considerations

## 🧪 Testing

Manual testing checklist:

- [ ] Register as startup and investor
- [ ] Create profiles for both roles
- [ ] View recommendations with filtering
- [ ] Check match scores and radar charts
- [ ] View AI insights on startup detail page
- [ ] Test intelligence features (uniqueness, readiness, pitch perfector)
- [ ] Send and accept connection requests
- [ ] Exchange messages
- [ ] Verify badges display correctly
- [ ] Test logout and re-login

## 🐛 Troubleshooting

### CORS Issues
If you see CORS errors, make sure Flask backend is running and CORS is enabled in `app.py`.

### Database Issues
Delete `matchmaking.db` and run `python seed.py` again to reset.

### Groq API Issues
If AI features aren't working:
1. Check your API key in `.env`
2. Verify you have credits on your Groq account
3. AI features fall back to mock responses if API fails

### Port Already in Use
If port 5000 is busy, change in `app.py`:
```python
app.run(debug=True, host='0.0.0.0', port=5001)
```

## 🔐 Security Notes

For production deployment:
- Change `JWT_SECRET_KEY` to a strong random string
- Use PostgreSQL instead of SQLite
- Enable HTTPS
- Add rate limiting
- Implement proper password policies
- Add input validation and sanitization
- Use environment-specific configs

## 📊 Database Schema

### Users
- id, email, password_hash, role, created_at

### StartupProfile
- id, user_id, company_name, stage, sectors, location, funding_min/max, pitch, team_size, traction, is_verified

### InvestorProfile
- id, user_id, name, investor_type, check_min/max, preferred_stages, preferred_sectors, geo_focus, thematic_focus, past_investments, is_verified

### Connection
- id, sender_id, receiver_id, status, created_at

### Message
- id, connection_id, sender_id, content, timestamp

## 🤝 Contributing

This is a hackathon project. Feel free to fork and extend!

## 📝 License

This project is provided as-is for educational and demonstration purposes.

## 🙏 Acknowledgments

- Tailwind CSS for the styling framework
- Chart.js for radar charts
- Groq for AI capabilities
- Faker for generating test data

## 📧 Contact

For questions or issues, please open an issue in the repository.

---

**Built with ❤️ for the Startup-Investor Matchmaking Hackathon**
