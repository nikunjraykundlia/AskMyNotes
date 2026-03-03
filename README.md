# 🎓 AskMyNotes

**AskMyNotes** is your ultimate Study Copilot, designed to help students learn and interact with their study materials exactly how they need to. Say goodbye to hallucinations—AskMyNotes scopes its AI context strictly to the notes you upload!

---

## 🚀 Features

- **Subject-Scoped Context**  
  Organize your notes into dedicated Subjects (max 3 subjects). Upload your PDFs and TXT files directly to a subject, and the AI will only answer based on the material in that specific subject, completely avoiding hallucinations.

- **Intelligent AI Chatbot**  
  Ask direct questions about your notes or clarify concepts. The chatbot uses an advanced vector search mechanism to pull up exact answers.

- **Evidence-Backed Answers**  
  Every AI response comes with an explicit confidence score (High/Medium/Low) and exact citations pointing you to the supportive evidence and snippet from your notes.

- **Interactive Study Mode**  
  Auto-generate multiple-choice questions (MCQs) and short-answer queries straight from your study materials to vigorously test your knowledge. Validates answers and stores your study history.

- **Results Export**  
  Download your interactive study results as dynamic PDFs right from your browser, making revisions significantly easier.

- **Robust Authentication & Security**  
  Secure access crafted for a seamless user experience using Firebase Authentication paired with Custom Node JWT auth.

---

## 🏗️ Architecture & Tech Stack

AskMyNotes leverages a modern, event-driven infrastructure to process, embed, and query your notes seamlessly.

### **Frontend**
- **Framework**: [Next.js 16](https://nextjs.org/) (App Router, Turbopack), React 19
- **UI & Styling**: [Tailwind CSS v4](https://tailwindcss.com/), Radix UI, Shadcn UI
- **Animations & Visuals**: [Framer Motion](https://www.framer.com/motion/) with beautiful dynamic mesh backgrounds
- **Icons**: Lucide React
- **Client-Side Export**: `jspdf`, `html-to-image`

### **Backend & APIs**
- **API Setup**: Next.js App Router API Routes (`/api/subjects`, `/api/upload-notes`, `/api/generate-questions`, `/api/save-answers`, `/api/history`, etc.)
- **AI Orchestration**: **[n8n](https://n8n.io/)** (Webhooks mapping endpoints for file upload, RAG orchestration, study generation, and general chat over Railway).
- **RAG Pipeline**:
  - *Data Loaders & Recursive Text Splitters*
  - *Embeddings via LLM models*

### **Database & Storage**
- **Main DB & Vector Store**: **[Supabase](https://supabase.com/)** (PostgreSQL with `pgvector` for efficient similarity search and user history storage).
- **File Uploads**: **[ImageKit](https://imagekit.io/)** (PDF handling & structured URLs).
- **Authentication**: **Firebase** & **Firebase Admin** combined with `bcryptjs` and `jsonwebtoken`.

---

## 🛠️ Getting Started

### Prerequisites
- Node.js (v20+)
- Local or Cloud instances of Supabase, Firebase, ImageKit, and an active n8n web hook.

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd AskMyNotes
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up Environment Variables**
   Create a `.env.local` file in the root directory. You will need keys for:
   - **Supabase** (`NEXT_PUBLIC_SUPABASE_URL`, `NEXT_PUBLIC_SUPABASE_ANON_KEY`, `SUPABASE_SERVICE_ROLE_KEY`)
   - **Firebase** (`NEXT_PUBLIC_FIREBASE_API_KEY`, `NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN`, etc.)
   - **ImageKit** (`IMAGEKIT_PUBLIC_KEY`, `IMAGEKIT_PRIVATE_KEY`, `IMAGEKIT_URL_ENDPOINT`)
   - **JWT Authentication** (`JWT_SECRET`)

4. **Run the Development Server**
   ```bash
   npm run dev
   ```

5. Open [http://localhost:3000](http://localhost:3000) with your browser to launch the application.