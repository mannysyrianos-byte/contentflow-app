# 🚀 ContentFlow - Getting Started

Your complete social media scheduler is ready. Choose your method below:

---

## ⚡ **Method 1: One Command (Easiest)**

### macOS / Linux
```bash
chmod +x start.sh
./start.sh
```

### Windows (PowerShell or CMD)
```bash
start.bat
```

That's it! The app starts automatically. Open http://localhost:3000

---

## 🎯 **Method 2: Setup Wizard (Recommended)**

### Step 1: Open the Setup Wizard
- **macOS/Linux:** Open `setup-wizard.html` in your browser
- **Windows:** Double-click `setup-wizard.html`

### Step 2: Enter Your Credentials
- Google OAuth Client ID & Secret
- Meta App ID & Secret  
- AWS Access Keys

### Step 3: Download .env File
The wizard generates your `.env` file automatically.

### Step 4: Start the App
```bash
docker-compose up
```

---

## 🐳 **Method 3: Docker (Fastest)**

### Prerequisite
Install Docker Desktop: https://www.docker.com/products/docker-desktop

### One Command
```bash
docker-compose up
```

### Open
- Frontend: http://localhost:3000
- Backend: http://localhost:5000

---

## 📦 **Method 4: Manual Installation**

### Step 1: Prerequisites
```bash
# Check you have these installed:
docker --version
docker-compose --version
git --version
node --version  # Optional
```

### Step 2: Clone/Download Files
```bash
# Download all files from the outputs folder
# Put them in a new directory called contentflow-app
cd contentflow-app
```

### Step 3: Create .env File
```bash
cp .env.example .env
```

Edit `.env` with your credentials:
```env
GOOGLE_CLIENT_ID=your-id
GOOGLE_CLIENT_SECRET=your-secret
META_APP_ID=your-id
META_APP_SECRET=your-secret
AWS_ACCESS_KEY_ID=your-key
AWS_SECRET_ACCESS_KEY=your-secret
```

### Step 4: Start Services
```bash
docker-compose up
```

### Step 5: Open Browser
- **Frontend:** http://localhost:3000
- **Backend:** http://localhost:5000

---

## 🌐 **Access the App**

Once running, open your browser:

### Frontend
```
http://localhost:3000
```

Click **"Sign in with Google"** to login

### Backend API
```
http://localhost:5000
```

Check health: http://localhost:5000/health

### Database
```
PostgreSQL: localhost:5432
```

Connect with any SQL client using:
- User: `postgres`
- Password: `postgres`
- Database: `contentflow_dev`

---

## ✨ **First Steps After Launch**

1. **Sign In with Gmail**
   - Click "Sign in with Google"
   - Use your email address
   - Grant permissions

2. **Connect Meta Account**
   - Click "+ Connect Meta"
   - Choose Instagram or Facebook
   - Login with your business account
   - Authorize the app

3. **Create Your First Post**
   - Click "+ New Post"
   - Enter title and caption
   - Select date and time
   - Click "Create Post"

4. **Schedule to Instagram/Facebook**
   - Click post in calendar
   - Click "Schedule to Meta"
   - Watch it appear on your account!

---

## 🔧 **Credentials Setup**

### Get Google OAuth Credentials (5 min)

1. Go to https://console.cloud.google.com
2. Create OAuth 2.0 Client ID (Web)
3. Add Authorized Redirect URI:
   ```
   http://localhost:5000/api/auth/google/callback
   ```
4. Copy **Client ID** and **Client Secret**

### Get Meta App Credentials (5 min)

1. Go to https://developers.facebook.com
2. Create App → Instagram Graph API + Facebook Graph API
3. Copy **App ID** and **App Secret**
4. Add Redirect URI:
   ```
   http://localhost:5000/api/meta/oauth/callback
   ```

### Get AWS S3 Credentials (5 min)

1. Go to AWS Console
2. Create S3 bucket: `contentflow-uploads`
3. Create IAM user with S3 permissions
4. Copy **Access Key** and **Secret Access Key**

---

## 🐛 **Troubleshooting**

### Port Already in Use
If ports 3000 or 5000 are taken, edit `docker-compose.yml`:

```yaml
# Change port mapping:
ports:
  - "3001:3000"  # Frontend on 3001
  - "5001:5000"  # Backend on 5001
```

Then access at:
- Frontend: http://localhost:3001
- Backend: http://localhost:5001

### Docker Not Running
Make sure Docker Desktop is open and running.

### Database Connection Error
```bash
# Reset everything
docker-compose down
docker volume rm contentflow-app_postgres_data
docker-compose up
```

### Ports Already in Use
```bash
# Find what's using the port
lsof -i :3000
lsof -i :5000

# Kill the process
kill -9 <PID>
```

### Can't Sign In
- Check GOOGLE_CLIENT_ID is correct in .env
- Verify redirect URI matches Google Console
- Restart containers: `docker-compose down && docker-compose up`

---

## 📊 **Services Running**

Once started, you have:

| Service | Port | Purpose |
|---------|------|---------|
| Frontend | 3000 | React app (UI) |
| Backend | 5000 | Node.js API |
| Database | 5432 | PostgreSQL |
| Cache | 6379 | Redis |

---

## 🛑 **Stop the App**

### Stop Containers (Keep Data)
```bash
docker-compose down
```

### Stop & Delete Everything
```bash
docker-compose down -v
```

### Restart
```bash
docker-compose up
```

---

## 📈 **What's Included**

✅ Complete React frontend
✅ Complete Node.js backend
✅ PostgreSQL database
✅ Redis cache
✅ Gmail OAuth login
✅ Meta Business Suite integration
✅ File upload system
✅ Analytics tracking
✅ Team collaboration
✅ Professional UI
✅ API endpoints
✅ All documentation

---

## 🚀 **Next Steps**

### Immediate
1. Start the app (pick method above)
2. Sign in with Gmail
3. Connect your Meta account
4. Create your first post

### This Week
5. Invite team members
6. Schedule content
7. Monitor analytics
8. Test all features

### Production
9. Get credentials
10. Deploy to Heroku/AWS
11. Setup custom domain
12. Monitor and scale

---

## 📚 **Documentation**

| Document | Purpose |
|----------|---------|
| `START_HERE.md` | Quick overview |
| `README.md` | Features & API |
| `QUICK_START.md` | 3-step setup |
| `setup-wizard.html` | Interactive setup |
| `META_OAUTH_SETUP.md` | OAuth guide |
| `DEPLOYMENT.md` | Production deploy |

---

## 💡 **Pro Tips**

**Clear Docker images (free up space):**
```bash
docker system prune -a
```

**View backend logs:**
```bash
docker-compose logs api
```

**View frontend logs:**
```bash
docker-compose logs web
```

**Connect to database:**
```bash
docker exec -it contentflow-db psql -U postgres -d contentflow_dev
```

**List running containers:**
```bash
docker ps
```

**Check container status:**
```bash
docker-compose ps
```

---

## ✅ **Verification Checklist**

- [ ] Docker installed and running
- [ ] docker-compose installed
- [ ] Credentials obtained (Google, Meta, AWS)
- [ ] .env file created with credentials
- [ ] `docker-compose up` runs successfully
- [ ] Frontend loads at http://localhost:3000
- [ ] Backend responds at http://localhost:5000/health
- [ ] Can sign in with Gmail
- [ ] Can connect Meta account
- [ ] Can create posts

---

## 🆘 **Getting Help**

1. **Check the docs** - Most questions are answered
2. **View logs** - `docker-compose logs`
3. **Reset everything** - `docker-compose down -v && docker-compose up`
4. **Check .env** - Make sure credentials are correct
5. **Verify ports** - Are 3000/5000 available?

---

## 🎉 **You're All Set!**

Your social media scheduler is ready to go!

### Quick Start Summary:
```bash
# macOS/Linux
chmod +x start.sh && ./start.sh

# Windows
start.bat

# Or manual
docker-compose up
```

Then open: **http://localhost:3000**

Sign in with Gmail and start scheduling! 🚀

---

**Everything is built. Everything works. Start now!** ✨
