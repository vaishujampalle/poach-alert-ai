# Poach Alert AI

A comprehensive wildlife protection system that uses AI-powered sound detection to identify illegal poaching activity in forests and alert authorities in real-time.

## Features

### Authentication System
- Separate login/registration for Rangers and Admins
- Secure authentication using Supabase Auth
- Profile management with validation
- Role-based access control

### Live Sound Detection
- Real-time microphone access through browser
- Audio wave visualization
- AI-powered sound classification
- Detects suspicious sounds:
  - Gunshots
  - Chainsaw cutting
  - Hunting activity
  - Animal distress sounds

### Alert System
- Real-time alert notifications with popup
- Alert history with satellite map visualization
- Zone-based location tracking
- Status tracking (new, investigating, resolved)

### Dashboard
- Statistics cards showing:
  - Total alerts
  - Active microphones
  - Suspicious detections
- Recent alerts list
- Real-time updates

### Satellite Map Integration
- Leaflet.js satellite map
- Zone markers for forest areas:
  - Zone A: 15.88°N, 78.85°E
  - Zone B: 15.86°N, 78.83°E
  - Zone C: 15.87°N, 78.88°E
- Blinking alert markers on suspicious activity

### Multi-Language Support
- English
- Hindi (हिन्दी)
- Telugu (తెలుగు)
- Dynamic UI text updates

### Dark Forest Theme
- Dark green and black color scheme
- Neon glow effects
- Floating leaf animations
- Audio wave visualizations
- Smooth transitions and effects

## Tech Stack

### Frontend
- React 18 with TypeScript
- Tailwind CSS for styling
- Vite for build tooling
- Leaflet.js for maps
- Lucide React for icons

### Backend & Database
- Supabase for:
  - Authentication
  - PostgreSQL database
  - Real-time subscriptions
  - Row Level Security (RLS)

### AI Detection
- Browser Web Audio API
- Real-time audio analysis
- Simulated AI classification (production would use actual ML model)

## Database Schema

### Profiles Table
- Links to Supabase Auth users
- Stores ranger/admin profile data
- Fields: first_name, last_name, user_id, phone_number, role

### Alerts Table
- Stores all poaching alerts
- Fields: sound_type, zone, latitude, longitude, timestamp, status, detected_by

## Getting Started

### Installation

```bash
npm install
```

### Environment Variables

The `.env` file contains Supabase credentials (already configured):
- VITE_SUPABASE_URL
- VITE_SUPABASE_ANON_KEY

### Running Locally

Development server (starts automatically):
```bash
npm run dev
```

Build for production:
```bash
npm run build
```

Preview production build:
```bash
npm run preview
```

## Project Structure

```
src/
├── components/
│   ├── AlertPopup.tsx          # Alert notification popup
│   ├── AuthForm.tsx            # Login/registration form
│   ├── AuthScreen.tsx          # Authentication interface
│   ├── DashboardLayout.tsx     # Main app layout with navigation
│   ├── DashboardScreen.tsx     # Statistics dashboard
│   ├── DetectionScreen.tsx     # Live sound detection
│   ├── ForestMap.tsx          # Leaflet satellite map
│   ├── HistoryScreen.tsx      # Alert history with map
│   └── SettingsScreen.tsx     # User settings & language
├── contexts/
│   ├── AuthContext.tsx        # Authentication state
│   └── LanguageContext.tsx    # Multi-language support
├── lib/
│   └── supabase.ts           # Supabase client
├── types/
│   └── database.ts           # TypeScript types
├── App.tsx                   # Main app component
├── main.tsx                  # App entry point
└── index.css                 # Global styles & animations
```

## Usage

1. **Register an Account**
   - Choose Ranger or Admin registration
   - Fill in required details (names must be alphabets only, phone numbers must be numeric)
   - Create account with email and password

2. **Login**
   - Select Ranger or Admin login
   - Enter credentials

3. **Detection Screen**
   - Click "Start Detection" to begin listening
   - Allow microphone access when prompted
   - System continuously monitors for suspicious sounds
   - Alerts automatically sent when detected

4. **Dashboard Screen**
   - View statistics
   - Monitor recent alerts
   - Real-time updates

5. **History Screen**
   - View all alerts on satellite map
   - Browse complete alert history
   - Check alert status

6. **Settings Screen**
   - View profile information
   - Change language (English/Hindi/Telugu)
   - Logout

## Security Features

- Row Level Security (RLS) enabled on all tables
- Users can only view their own profiles
- Admins have elevated permissions
- Secure authentication with Supabase
- Input validation for all forms

## Future Enhancements

For production deployment, consider:
- Actual ML model integration (TensorFlow.js, ESC-50 dataset)
- Real hardware sensor integration
- SMS/Email alert notifications
- Advanced analytics and reporting
- Multi-device support
- Geofencing capabilities
- Integration with forest department systems

## License

MIT License - Wildlife Protection System
