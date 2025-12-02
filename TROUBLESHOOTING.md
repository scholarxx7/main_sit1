# 🔧 Troubleshooting Guide - Unparalleled Scholar

## Common Issues & Solutions

### 🚫 Issue 1: "Route not found" Error

**Symptoms:**
- Browser shows: `{"error":"Route not found","message":"The requested resource does not exist"}`
- Happens when accessing any page

**Solution:**
1. **Stop the server:**
   ```bash
   # Press Ctrl + C in the terminal running npm run dev
   ```

2. **Restart the server:**
   ```bash
   npm run dev
   ```

3. **Wait for confirmation:**
   ```
   ╔═══════════════════════════════════════════════════════════╗
   ║        🎓 UNPARALLELED SCHOLAR - API SERVER 🎓           ║
   ║        Server running on port 3000                        ║
   ╚═══════════════════════════════════════════════════════════╝
   ```

4. **Navigate to:** `http://localhost:3000` (not `/index.html`)

---

### ⚠️ Issue 2: "EADDRINUSE" Error

**Symptoms:**
```
Error: listen EADDRINUSE: address already in use :::3000
```

**Solution:**

**Option A - Kill the process (Windows):**
```powershell
# Find the process using port 3000
netstat -ano | findstr :3000

# Kill the process (replace PID with actual number)
taskkill /PID <PID> /F

# Restart server
npm run dev
```

**Option B - Use a different port:**
```bash
# Edit .env file
PORT=3001

# Restart server
npm run dev
```

---

### 🔒 Issue 3: "Too many requests" Error

**Symptoms:**
- Message: "Too many requests from this IP, please try again later"
- Happens after rapid page navigation

**Solution:**
1. **Wait 1 minute** - Rate limiting will reset
2. **Or temporarily disable rate limiting:**
   - Edit `server/middleware/security.js`
   - Increase the `windowMs` or `max` values
   - Restart server

**Current limits:**
- Global: 100 requests per 15 minutes
- API: 50 requests per 15 minutes

---

### 📁 Issue 4: Static Files Not Loading (CSS/JS/Images)

**Symptoms:**
- Page loads but no styling
- Console errors: "Failed to load resource"

**Solution:**
1. **Check file paths in HTML:**
   ```html
   <!-- Correct paths -->
   <link rel="stylesheet" href="../../client/css/index.css">
   <script src="../../client/js/app.js"></script>
   <img src="../../client/img/logo.png">
   ```

2. **Verify server static file configuration:**
   ```javascript
   // In server/server.js
   app.use('/client', express.static(path.join(__dirname, '../client')));
   ```

3. **Clear browser cache:**
   - Press `Ctrl + Shift + R` (hard refresh)

---

### 🌐 Issue 5: Pages Not Found (404)

**Symptoms:**
- New pages show 404 error
- Navigation links don't work

**Solution:**
1. **Verify route exists in `server/server.js`:**
   ```javascript
   app.get('/pages/about.html', (req, res) => {
     res.sendFile(path.join(__dirname, '../src/pages/about.html'));
   });
   ```

2. **Check file exists:**
   ```
   src/pages/about.html ✓
   src/pages/blog.html ✓
   src/pages/blog-post.html ✓
   src/pages/course-detail.html ✓
   ```

3. **Restart server** after adding new routes

---

### 🔄 Issue 6: Changes Not Reflecting

**Symptoms:**
- Made code changes but nothing updates
- Old content still showing

**Solution:**
1. **For HTML/CSS changes:**
   - Hard refresh: `Ctrl + Shift + R`
   - Clear cache: `Ctrl + Shift + Delete`

2. **For server changes:**
   - Restart server: `Ctrl + C` then `npm run dev`
   - Check nodemon is watching files

3. **For JavaScript changes:**
   - Clear browser cache
   - Check browser console for errors

---

## 🚀 Quick Start Checklist

Before starting development, ensure:

- [ ] Node.js installed (v18+)
- [ ] Dependencies installed: `npm install`
- [ ] `.env` file exists (copy from `.env.example`)
- [ ] Port 3000 is available
- [ ] Server starts without errors

---

## 📋 Correct URLs for Each Page

| Page | URL |
|------|-----|
| **Homepage** | `http://localhost:3000` |
| **About Us** | `http://localhost:3000/pages/about.html` |
| **Courses** | `http://localhost:3000/pages/courses.html` |
| **Course Detail** | `http://localhost:3000/pages/course-detail.html` |
| **Blog** | `http://localhost:3000/pages/blog.html` |
| **Blog Post** | `http://localhost:3000/pages/blog-post.html` |
| **Contact** | `http://localhost:3000/pages/contact.html` |
| **API Health** | `http://localhost:3000/api/health` |

---

## 🛠️ Development Commands

```bash
# Start development server (with auto-reload)
npm run dev

# Start production server
npm start

# Install dependencies
npm install

# Check for errors
npm test
```

---

## 📊 Checking Server Status

### Verify server is running:
```bash
# Windows PowerShell
netstat -ano | findstr :3000

# Should show: TCP 0.0.0.0:3000 LISTENING
```

### Test API endpoint:
```bash
# Using curl
curl http://localhost:3000/api/health

# Expected response:
# {"status":"OK","message":"Unparalleled Scholar API is running","version":"1.0.0","project":"US.V1"}
```

### Check in browser:
Navigate to: `http://localhost:3000/api/health`

---

## 🐛 Debug Mode

Enable detailed logging:

1. **Edit `.env`:**
   ```
   NODE_ENV=development
   DEBUG=true
   ```

2. **Restart server**

3. **Check console** for detailed error messages

---

## 📞 Still Having Issues?

1. **Check the logs:**
   - Look at terminal output for errors
   - Check browser console (F12)

2. **Verify file structure:**
   ```
   Scholar Site/
   ├── src/
   │   ├── index.html
   │   └── pages/
   │       ├── about.html
   │       ├── blog.html
   │       ├── blog-post.html
   │       ├── course-detail.html
   │       ├── contact.html
   │       └── courses.html
   ├── server/
   │   └── server.js
   └── client/
       ├── css/
       ├── js/
       └── img/
   ```

3. **Review recent changes:**
   - Check git diff if using version control
   - Undo recent changes if needed

---

## ✅ Success Indicators

You'll know everything is working when:

- ✅ Server starts without errors
- ✅ Homepage loads at `http://localhost:3000`
- ✅ All navigation links work
- ✅ CSS and images load correctly
- ✅ No console errors in browser
- ✅ API health check returns OK

---

**Built with ❤️ by Srijan Kumar | Srijanxi Technologies**  
**© 2024 Unparalleled Scholar. All rights reserved.**
