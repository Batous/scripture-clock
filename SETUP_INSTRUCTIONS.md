# Multi-Church Bible Display Platform - Setup Instructions

## 📦 What You Have

1. **multichurch_bible_platform.html** - The main app file
2. **churches_database.json** - Churches database (you'll update this)

## 🚀 How to Deploy (FREE Hosting)

### Option 1: GitHub Pages (Recommended)

1. **Create a GitHub account** (if you don't have one): https://github.com
2. **Create a new repository**:
   - Name it: `bible-display` (or anything you want)
   - Make it Public
   - Check "Add a README file"

3. **Upload your files**:
   - Click "Add file" → "Upload files"
   - Drag and drop BOTH files:
     - `multichurch_bible_platform.html`
     - `churches_database.json`
   - Click "Commit changes"

4. **Enable GitHub Pages**:
   - Go to Settings → Pages
   - Source: Deploy from a branch
   - Branch: main
   - Folder: / (root)
   - Click Save

5. **Get your URL**:
   - Your app will be at: `https://YOUR-USERNAME.github.io/bible-display/multichurch_bible_platform.html`
   - Share this URL with your users!

### Option 2: Netlify Drop (Easier but less control)

1. Go to https://app.netlify.com/drop
2. Create a folder on your computer with both files
3. Drag the folder onto Netlify Drop
4. You'll get a URL like: `https://random-name.netlify.app`
5. You can customize the URL in Netlify settings

## 📝 How to Update Churches Database

### When a Pastor Wants to Go Live:

1. **Open `churches_database.json`** in GitHub (or download it)
2. **Find their church** (by church ID)
3. **Update the liveStream section**:

```json
"liveStream": {
  "isActive": true,                           ← Change to true
  "url": "https://youtube.com/watch?v=xxxxx", ← Add stream URL
  "title": "Sunday Morning Service",          ← Add title
  "startTime": "2025-02-16T09:00:00Z",       ← Start time
  "endTime": "2025-02-16T11:00:00Z"          ← End time
}
```

4. **Commit the changes** (in GitHub) or re-upload to Netlify
5. **Users will see the live banner** within 1 minute!

### After Stream Ends:

Change `"isActive"` back to `false`:

```json
"liveStream": {
  "isActive": false,
  "url": "",
  "title": "",
  ...
}
```

## 👨‍💼 Adding New Churches

In `churches_database.json`, add a new church object:

```json
{
  "id": "church005",                          ← Unique ID
  "name": "Your Church Name",
  "location": "City, Country",
  "timezone": "Africa/Johannesburg",
  "tradition": "protestant",                   ← or catholic/orthodox
  "pastor": "Pastor Name",
  "contact": "email@church.example",
  "liveStream": {
    "isActive": false,
    "url": "",
    "title": "",
    "startTime": "",
    "endTime": "",
    "schedule": [
      {
        "day": "Sunday",
        "time": "09:00",
        "duration": 120,
        "title": "Sunday Service"
      }
    ]
  }
}
```

## 🔐 Future: Pastor Login System (Option B)

When you're ready for pastors to update their own streams:

### What You'll Need:
1. **Backend Server**: Node.js, Python, or PHP
2. **Database**: Firebase (easiest), MongoDB, or PostgreSQL
3. **Authentication**: Firebase Auth or Auth0
4. **Hosting**: Heroku ($5/month), DigitalOcean ($5/month), or Vercel (free tier)

### Steps:
1. Build API endpoints for pastors to update their streams
2. Add login page with email/password
3. Each pastor can only edit their own church
4. Changes reflect in real-time

**Cost**: ~$5-20/month depending on traffic

## 📱 How Users Use It

1. **First Time**:
   - Open the URL you give them
   - Choose language (English/French/Spanish/Portuguese)
   - Choose Bible source (Bible.com or Offline)
   - Select their church from dropdown
   - Choose tradition (Protestant/Catholic/Orthodox)
   - Click "Begin Display"

2. **Daily Use**:
   - App remembers their settings
   - Shows clock + rotating Bible verses
   - If their church goes live → Banner appears at bottom
   - Click "Watch Now" to open stream
   - After stream ends → Returns to normal display

3. **Settings**:
   - Click "⚙️ Settings" button at top to change preferences anytime

## 🎨 Customization Ideas

### Change Colors:
Edit the CSS gradients in the HTML file:
```css
.bg-ordinary { background: linear-gradient(135deg, #2e7d32 0%, #1b5e20 100%); }
```

### Add More Languages:
1. Add language button in HTML
2. Add translations object in JavaScript
3. Add Bible verses in that language

### Add More Bible Versions:
Currently uses sample verses. To integrate Bible.com API:
1. Get API key from Bible.com
2. Replace `getTodaysVerse()` function with API call
3. Handle different translations (NIV, KJV, ESV, etc.)

## 🐛 Troubleshooting

**Setup screen doesn't appear:**
- Clear browser cache
- Open in incognito/private mode
- Check browser console for errors

**Churches not loading:**
- Make sure `churches_database.json` is in same folder as HTML
- Check JSON syntax (use JSONLint.com to validate)
- Check browser console for CORS errors

**Live stream banner not showing:**
- Verify `isActive: true` in JSON
- Check that URL is valid
- Wait 1 minute for next check cycle

## 📧 Support

Contact: contact@batouskb.io

## 🎯 Next Steps

1. Deploy to GitHub Pages or Netlify
2. Test with 1-2 churches first
3. Share URL with your congregation
4. Monitor usage for 1 month
5. Plan Option B (pastor login) if needed

---

**Quick Start Checklist:**
- [ ] Upload files to GitHub
- [ ] Enable GitHub Pages
- [ ] Test the URL yourself
- [ ] Add real church data to JSON
- [ ] Share URL with test group
- [ ] Get feedback
- [ ] Scale up!
