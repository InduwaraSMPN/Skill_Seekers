# Quick Start Guide

## 🚀 Complete Setup in 5 Steps

### Prerequisites: Get the Code

**You MUST have the Skill Seeker code on your computer first:**

```bash
# Option A: Clone with Git (recommended)
git clone https://github.com/yusufkaraaslan/Skill_Seekers.git
cd Skill_Seekers

# Option B: Download ZIP file
# 1. Go to https://github.com/yusufkaraaslan/Skill_Seekers
# 2. Click green "Code" button → "Download ZIP"
# 3. Extract the ZIP file
# 4. Open terminal in the extracted folder
```

**Check Python Version:**
```bash
python3 --version
# Must show: Python 3.10.x or higher
```

---

### Step 1: Install Dependencies (2 minutes)

```bash
# Required for all users
pip3 install requests beautifulsoup4

# Optional: For API enhancement (costs money)
pip3 install anthropic
export ANTHROPIC_API_KEY=sk-ant-...
```

**Verify installation:**
```bash
python3 -c "import requests, bs4; print('✅ Dependencies installed')"
```

---

### Step 2: Try a Preset (Easiest)

```bash
# Make sure you're in the Skill_Seekers directory
pwd  # Should show .../Skill_Seekers

# Try Godot (game engine documentation)
python3 cli/doc_scraper.py --config configs/godot.json

# Or try React (web framework)
python3 cli/doc_scraper.py --config configs/react.json
```

**What happens:**
- Downloads documentation for 20-40 minutes
- Creates organized reference files
- Generates a basic SKILL.md file

---

### Step 3: Enhance the Skill (HIGHLY Recommended)

**LOCAL Enhancement (Free - uses Claude Code):**
```bash
python3 cli/enhance_skill_local.py output/godot/
# Takes 60 seconds, opens Claude Code automatically
```

**OR API Enhancement (Costs ~$0.20):**
```bash
python3 cli/enhance_skill.py output/godot/
# Takes 30 seconds, no Claude Code needed
```

**This transforms a basic SKILL.md into a comprehensive guide with real examples!**

---

### Step 4: Package the Skill

```bash
python3 cli/package_skill.py output/godot/
```

**Result:**
- Creates `output/godot.zip`
- Opens the output folder
- Shows upload instructions

---

### Step 5: Use in Claude

**Manual Upload (No API Key):**
1. Go to https://claude.ai/skills
2. Click "Upload Skill"
3. Select `output/godot.zip`
4. Done! ✅

**Automatic Upload (Requires API Key):**
```bash
python3 cli/upload_skill.py output/godot.zip
```

---

## ⚡ Fast Testing Workflow

Want to test quickly without waiting hours?

```bash
# 1. Edit config to limit pages (optional)
nano configs/react.json
# Change "max_pages": 500 to "max_pages": 20

# 2. Quick test scrape (2-3 minutes)
python3 cli/doc_scraper.py --config configs/react.json

# 3. Enhance instantly (60 seconds)
python3 cli/enhance_skill_local.py output/react/

# 4. Package (5 seconds)
python3 cli/package_skill.py output/react/
```

---

## 🔄 Using Existing Data (After First Scrape)

Once you've scraped once, you can rebuild instantly:

```bash
python3 cli/doc_scraper.py --config configs/react.json
# When prompted: ✓ Found existing data: 245 pages
# Use existing data? (y/n): y

# Or skip prompt:
python3 cli/doc_scraper.py --config configs/react.json --skip-scrape
```

**Why this is useful:**
- Test different enhancement options
- Rebuild after editing configs
- Create multiple packages from same data

---

## 🎯 Complete Example (Recommended)

```bash
# 1. Get the code (if not done)
git clone https://github.com/yusufkaraaslan/Skill_Seekers.git
cd Skill_Seekers

# 2. Install dependencies
pip3 install requests beautifulsoup4

# 3. Scrape with enhancement (does everything)
python3 cli/doc_scraper.py --config configs/react.json --enhance-local
# Wait 25 minutes total (scraping + enhancement)

# 4. Package (instant)
python3 cli/package_skill.py output/react/

# 5. Upload to Claude
python3 cli/upload_skill.py output/react.zip
# OR go to https://claude.ai/skills and upload react.zip manually
```

---

## 📋 Available Presets

```bash
# Game Development
python3 cli/doc_scraper.py --config configs/godot.json

# Web Frameworks  
python3 cli/doc_scraper.py --config configs/react.json
python3 cli/doc_scraper.py --config configs/vue.json

# Python Frameworks
python3 cli/doc_scraper.py --config configs/django.json
python3 cli/doc_scraper.py --config configs/fastapi.json

# See all presets
ls configs/
```

---

## 💡 Pro Tips

### Test Small First
```bash
# Edit any config file to test with 20 pages instead of 500
nano configs/react.json
# Find "max_pages": 500, change to "max_pages": 20
```

### Rebuild Without Re-scraping
```bash
# After first scrape, rebuild instantly:
python3 cli/doc_scraper.py --config configs/react.json --skip-scrape
```

### Create Custom Config
```bash
# Copy a preset and modify it
cp configs/react.json configs/myframework.json
nano configs/myframework.json  # Edit URLs, selectors, etc.
python3 cli/doc_scraper.py --config configs/myframework.json
```

### Interactive Mode
```bash
# Let the tool guide you step-by-step
python3 cli/doc_scraper.py --interactive
```

---

## 📁 What Gets Created

```
Skill_Seekers/
├── output/
│   ├── react_data/          # Raw scraped data (reusable!)
│   │   ├── pages/          # Individual page JSON files
│   │   └── summary.json    # Scraping statistics
│   └── react/              # The final skill
│       ├── SKILL.md        # Enhanced skill description ✨
│       ├── references/     # Organized documentation
│       │   ├── index.md    # Table of contents
│       │   ├── api.md      # API reference
│       │   └── examples.md  # Code examples
│       └── react.zip       # Packaged skill (what you upload)
```

---

## ❓ Troubleshooting

**"Command not found" errors?**
```bash
# Make sure you're in the right directory
pwd  # Should be .../Skill_Seekers

# Use cli/ prefix for all scripts
python3 cli/doc_scraper.py  # NOT python3 doc_scraper.py
```

**"Python 3.10+ required" error?**
```bash
# Update Python or use python3.10 directly
python3.10 cli/doc_scraper.py --config configs/react.json
```

**"Dependencies missing" error?**
```bash
pip3 install requests beautifulsoup4
```

**Need more help?**
- See **README.md** for complete documentation
- Check **docs/** folder for detailed guides
- Open an issue on GitHub for specific problems

---

## 🎮 Ready to Go?

```bash
# Pick one and try it!
python3 cli/doc_scraper.py --config configs/godot.json
python3 cli/doc_scraper.py --config configs/react.json
python3 cli/doc_scraper.py --interactive
```

That's it! Your first Claude skill is just 25 minutes away. 🚀



# React
python3 doc_scraper.py --config configs/react.json

# Vue.js
python3 doc_scraper.py --config configs/vue.json

# Django
python3 doc_scraper.py --config configs/django.json

# FastAPI
python3 doc_scraper.py --config configs/fastapi.json
```

---

## ⚡ Using Existing Data (Fast!)

If you already scraped once:

```bash
python3 doc_scraper.py --config configs/godot.json

# When prompted:
✓ Found existing data: 245 pages
Use existing data? (y/n): y

# Builds in seconds!
```

Or use `--skip-scrape`:
```bash
python3 doc_scraper.py --config configs/godot.json --skip-scrape
```

---

## 🎯 Complete Example (Recommended Workflow)

```bash
# 1. Install (once)
pip3 install requests beautifulsoup4

# 2. Scrape React docs with LOCAL enhancement
python3 doc_scraper.py --config configs/react.json --enhance-local
# Wait 15-30 minutes (scraping) + 60 seconds (enhancement)

# 3. Package
python3 package_skill.py output/react/

# 4. Use react.zip in Claude!
```

**Alternative: Enhancement after scraping**
```bash
# 2a. Scrape only (no enhancement)
python3 doc_scraper.py --config configs/react.json

# 2b. Enhance later
python3 enhance_skill_local.py output/react/

# 3. Package
python3 package_skill.py output/react/
```

---

## 💡 Pro Tips

### Test with Small Pages First
Edit config file:
```json
{
  "max_pages": 20  // Test with just 20 pages
}
```

### Rebuild Instantly
```bash
# After first scrape, you can rebuild instantly:
python3 doc_scraper.py --config configs/react.json --skip-scrape
```

### Create Custom Config
```bash
# Copy a preset
cp configs/react.json configs/myframework.json

# Edit it
nano configs/myframework.json

# Use it
python3 doc_scraper.py --config configs/myframework.json
```

---

## 📁 What You Get

```
output/
├── godot_data/          # Raw scraped data (reusable!)
└── godot/               # The skill
    ├── SKILL.md        # With real code examples!
    └── references/     # Organized docs
```

---

## ❓ Need Help?

See **README.md** for:
- Complete documentation
- Config file structure
- Troubleshooting
- Advanced usage

---

## 🎮 Let's Go!

```bash
# Godot
python3 doc_scraper.py --config configs/godot.json

# Or interactive
python3 doc_scraper.py --interactive
```

That's it! 🚀
