# 🎓 Hire Bridge AI - Mock Interview Marketplace

> An AI-powered peer-to-peer mock interview platform where senior engineers mentor and conduct live video interviews with candidates. Built with cutting-edge web technologies for real-time video, AI feedback, and credit-based payments.



---

## ✨ Features

### For Interviewees (Candidates)
- 🔍 **Browse Expert Interviewers** - Filter by expertise, experience, and availability
- 💳 **Credit-Based Booking** - Purchase credits and book sessions with senior engineers
- 🎥 **Live Video Interviews** - 1:1 real-time video interviews with HD quality
- 💬 **Live Chat** - Message your interviewer during the session
- 🖥️ **Screen Sharing** - Share code, design, or system diagrams
- 📊 **AI-Generated Feedback** - Auto-transcription and AI analysis after each interview
- 📅 **Appointment Management** - Track upcoming and past interview sessions

### For Interviewers (Experts)
- 📈 **Create Professional Profile** - Showcase expertise, experience, and hourly rates
- ⏰ **Manage Availability** - Set flexible time slots for interviews
- 🎓 **AI Question Generator** - Get context-aware interview questions during calls
- 💰 **Earnings Dashboard** - Track credits earned and request payouts
- 📝 **Interview Tools** - Screen share, record, and generate automated feedback
- 📊 **Session History** - Review all conducted interviews and feedback

### Platform Features
- ✅ **Real-time Video Streaming** via Stream.io
- ✅ **Automatic Call Recording** (1080p quality)
- ✅ **Auto-Transcription** enabled for every session
- ✅ **AI Feedback Generation** using Google Generative AI
- ✅ **Rate Limiting & Fraud Prevention** via Arcjet
- ✅ **Secure Authentication** with Clerk
- ✅ **Email Notifications** via Resend
- ✅ **Dark Mode UI** with Tailwind CSS

---

## 🛠️ Tech Stack

### Frontend
- **Framework**: [Next.js 16](https://nextjs.org/) (React 19, App Router, Server Components)
- **Styling**: [Tailwind CSS 4](https://tailwindcss.com/)
- **UI Components**: [shadcn/ui](https://ui.shadcn.com/)
- **Icons**: [Lucide React](https://lucide.dev/)
- **Animations**: [Motion](https://motion.dev/)

### Backend & Infrastructure
- **Runtime**: Node.js
- **Database**: PostgreSQL with [Prisma ORM](https://www.prisma.io/)
- **Video/Chat**: [Stream.io Video SDK](https://getstream.io/) + [Stream Chat SDK](https://getstream.io/chat/)
- **Authentication**: [Clerk](https://clerk.com/)
- **AI**: [Google Generative AI (Gemini)](https://ai.google.dev/)
- **Rate Limiting**: [Arcjet](https://arcjet.com/)
- **Email**: [Resend](https://resend.com/)

### Development Tools
- **Package Manager**: npm
- **Linting**: ESLint
- **Code Quality**: Tailwind CSS 4, PostCSS 4

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ and npm
- PostgreSQL database
- Stream.io account
- Clerk account
- Google Cloud API key (Generative AI)
- Resend API key
- Arcjet API key

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/hire-bridge-ai.git
   cd hire-bridge-ai
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   
   Create a `.env.local` file:
   ```bash
   # Database
   DATABASE_URL="postgresql://user:password@localhost:5432/hire_bridge_ai"
   DIRECT_URL="postgresql://user:password@localhost:5432/hire_bridge_ai"

   # Stream.io
   NEXT_PUBLIC_STREAM_API_KEY="your_stream_api_key"
   STREAM_SECRET_KEY="your_stream_secret_key"

   # Clerk Authentication
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY="your_clerk_publishable_key"
   CLERK_SECRET_KEY="your_clerk_secret_key"

   # Google Generative AI (Gemini)
   GEMINI_API_KEY="your_gemini_api_key"

   # Resend Email
   RESEND_API_KEY="your_resend_api_key"

   # Arcjet Rate Limiting
   ARCJET_KEY="your_arcjet_key"

   # App Config
   NEXT_PUBLIC_APP_URL="http://localhost:3000"
   ADMIN_PAYOUT_PASSWORD="your_admin_password"
   ```

4. **Set up the database**
   ```bash
   npx prisma generate
   npx prisma migrate dev
   # Optional: Seed sample data
   npm run seed
   ```

5. **Start the development server**
   ```bash
   npm run dev
   ```

   Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 📁 Project Structure

```
├── app/                          # Next.js App Router
│   ├── (auth)/                   # Authentication pages (sign-in, sign-up)
│   ├── (main)/                   # Main app routes
│   │   ├── call/[callId]/        # Video call page
│   │   ├── appointments/         # Interviewee's bookings
│   │   ├── dashboard/            # Interviewer's dashboard
│   │   ├── explore/              # Browse interviewers
│   │   ├── interviewers/[id]/    # Interviewer profile & booking
│   │   ├── onboarding/           # Role selection
│   │   └── payout/              # Payout management
│   ├── api/webhooks/            # Stream.io webhook handlers
│   └── page.jsx                 # Landing page
├── components/                   # Reusable React components
│   ├── ui/                      # shadcn/ui components
│   ├── animate-ui/              # Custom animated components
│   └── [feature].jsx            # Feature-specific components
├── actions/                     # Server actions (API routes)
│   ├── booking.js               # Booking logic
│   ├── call.js                  # Call management
│   ├── dashboard.js             # Dashboard data & logic
│   ├── appointments.js          # Appointment queries
│   ├── aiQuestions.jsx          # AI question generation
│   └── [feature].js             # Feature-specific actions
├── lib/                         # Utility functions & configurations
│   ├── prisma.js               # Prisma client singleton
│   ├── arcjet.js               # Rate limiting setup
│   ├── helpers.js              # Utility functions
│   └── generated/prisma/       # Auto-generated Prisma types
├── prisma/                      # Database schema & migrations
│   ├── schema.prisma           # Data models
│   ├── seed.js                 # Database seeding
│   └── migrations/             # Schema migrations
├── emails/                      # Email templates
└── hooks/                       # Custom React hooks
```

---

## 🔄 Interview Flow

### 1. **Discovery** (`/explore`)
- Browse available expert interviewers
- Filter by expertise category (Frontend, Backend, DSA, System Design, etc.)
- View profiles with experience, company, and rates

### 2. **Booking** (`/interviewers/[id]`)
- Select available time slot
- Pay with credits (automatic deduction from account)
- Stream.io call is created with encryption and settings

### 3. **Interview Day**
- Interviewee: Check `/appointments` → Join session
- Interviewer: Check `/dashboard` → Join session

### 4. **Live Interview** (`/call/[callId]`)
- **Video Stream**: HD quality 1:1 video via Stream.io
- **Live Chat**: Real-time messaging throughout the call
- **Screen Sharing**: Both participants can share screens
- **AI Questions**: Interviewer gets AI-generated contextual questions
- **Recording**: Automatic high-quality recording (1080p)
- **Transcription**: Auto-transcription for post-call analysis

### 5. **Post-Interview**
- Call recording processed via webhook
- AI generates feedback using Gemini
- Feedback saved to database
- Interviewee receives email notification

---

## 🗄️ Database Schema Highlights

### Core Models
- **User** - Profiles with roles (INTERVIEWEE/INTERVIEWER)
- **Booking** - Interview sessions between two users
- **Availability** - Interviewer's available time slots
- **Feedback** - AI-generated post-interview feedback
- **Transaction** - Credit purchases and deductions
- **Payout** - Interviewer earnings management

### Key Features
- Credit-based payment system
- Automatic rate limiting (5 bookings/hour per user)
- Interview categorization (8 expertise categories)
- Flexible availability management
- Comprehensive audit trail

---

## 🔐 Security Features

- ✅ **Clerk Authentication** - Enterprise-grade auth
- ✅ **JWT Tokens** - Secure Stream.io API communication
- ✅ **Role-Based Access Control** - Interviewer vs Interviewee permissions
- ✅ **Rate Limiting** - Arcjet prevents abuse
- ✅ **HTTPS Only** - Encrypted data in transit
- ✅ **Database Encryption** - PostgreSQL with SSL
- ✅ **Admin Password Protection** - For sensitive operations

---

## 📊 API Endpoints (Server Actions)

### Booking
- `bookSlot()` - Reserve an interview session
- `getInterviewerProfile()` - Fetch interviewer details

### Calls
- `getCallData()` - Get video call token and metadata

### Appointments
- `getIntervieweeAppointments()` - List interviewee's bookings
- `getInterviewerBookings()` - List interviewer's sessions

### Dashboard
- `getDashboardStats()` - Analytics for interviewers
- `requestPayout()` - Withdraw earned credits

### AI
- `generateAIQuestions()` - Get interview questions

---

## 🛠️ Development

### Running in Development
```bash
npm run dev
```

### Building for Production
```bash
npm run build
npm start
```

### Database Migrations
```bash
# Create migration
npx prisma migrate dev --name migration_name

# Apply migrations
npx prisma migrate deploy

# Reset database (development only)
npx prisma migrate reset
```

### Seeding Data
```bash
npm run seed
```

---

## 📞 Support & Contributions

If you encounter issues or have suggestions:
1. Check existing GitHub issues
2. Create a detailed bug report with error logs
3. Submit a pull request with improvements

---

## 📜 License

This project is private and proprietary. Unauthorized copying or distribution is prohibited.

---

## 🤝 Credits

Built with passion using:
- Stream.io for reliable video infrastructure
- Clerk for secure authentication
- Google Generative AI for intelligent feedback
- Shadcn/ui for beautiful components
- Tailwind CSS for rapid styling

---

## 📱 Screenshots

### Landing Page
- Hero section with clear value proposition
- Browse interviewers grid
- Pricing information

### Interview Profile Page
- Interviewer details and expertise
- Availability calendar
- Booking interface

### Video Call Interface
- High-definition video stream
- Side panel with live chat
- AI question generator (interviewer only)
- Call controls (mute, share screen, leave)

### Dashboard
- Session analytics
- Earnings overview
- Payout requests
- Interview history

---

**Happy interviewing! 🚀**
