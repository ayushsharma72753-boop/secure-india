# SECURE INDIA 🇮🇳
> A Real-Time Civic Issue Reporting System with 50-Meter Danger Alert

Secure India is a GPS-powered platform where citizens can report potholes, garbage, electricity and water issues directly to the concerned government department with real photo & live location proof.

Live Demo: **https://secure-india.vercel.app**

### 🚀 Key Features
- **50-Meter Danger Alert:** Automatically vibrates & alerts driver if a reported pothole is within 50 meters (using Haversine formula)
- **Real Email to Department:** Auto-sends real email from Gmail SMTP to state departments (PWD, Municipal, Electricity, Water)
- **State-Wise Routing:** Bihar, UP, Delhi and other states mapped to their official NIC emails
- **GPS + Reverse Geocoding:** Auto-detects city & state using OpenStreetMap Nominatim
- **Proof Based:** Every report includes GPS coordinates, pincode, photo (camera/gallery), and reporter email (CC)
- **Admin Dashboard:** Live map with all reports + Fixed/Delete controls

### 🛠️ Tech Stack
- Frontend: HTML, JS, Leaflet.js (OSM Maps)
- Backend: Supabase (Postgres, Auth, Storage, Edge Functions)
- Email: Gmail SMTP via Supabase Edge Function (Deno + smtp)
- Hosting: Vercel

### 📧 How Real Email Works
1. User submits report -> `reports` table insert
2. Postgres Trigger `on_new_report_email` fires
3. Calls Edge Function `cleversrnd-dept-email` via `pg_net`
4. Edge Function sends email via Gmail App Password to `dept_email` + CC to reporter

No paid domain needed for email.

### ⚙️ Setup
1. Clone repo
2. Create Supabase project, run `schema.sql`
3. Create bucket `pothole-photos`
4. Deploy Edge Function `cleversrnd-dept-email` with your Gmail & App Password
5. Run SQL trigger from `/sql/trigger.sql`

### 📄 License
MIT License - Free for everyone. Built for Digital India.

Made with ❤️ by Ayush Sharma - kanpur,Uttar Pradesh 
Jai Hind!
