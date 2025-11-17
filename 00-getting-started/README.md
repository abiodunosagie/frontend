# 00 - Getting Started

> **"A journey of a thousand miles begins with a single step."** - Lao Tzu

Welcome to Day Zero. Before we write a single line of code, let's set up your workspace like a professional. This matters more than you think.

---

## 🎯 What You'll Set Up

1. **VS Code** - Your code editor (where you'll spend most of your time)
2. **Node.js & npm** - JavaScript runtime and package manager
3. **Git** - Version control (track your progress)
4. **Browser Dev Tools** - Your debugging superpower
5. **VS Code Extensions** - Tools that make coding easier

---

## 📦 Step 1: Install VS Code

### What is VS Code?

Imagine Microsoft Word, but for code. It:
- **Colors your code** (makes it easier to read)
- **Catches mistakes** (before you even run your code)
- **Auto-completes** (like your phone's keyboard)
- **Organizes files** (keeps your projects tidy)

### Installation

**You already have VS Code!** (You mentioned you'll use it)

But let's make sure it's configured properly.

---

## 📦 Step 2: Install Node.js

### What is Node.js?

Think of Node.js as a **translator** that lets JavaScript run on your computer (not just in browsers).

You need it to:
- Run development servers
- Install packages (pre-made code you can use)
- Use modern tools like React and Next.js

### Installation

**Check if you have it already:**

Open VS Code, press `` Ctrl+` `` (backtick key, above Tab), and type:

```bash
node --version
```

**If you see a version number (like v18.17.0):** You're good! ✅

**If you get "command not found":** Let's install it.

1. **Download:** Go to https://nodejs.org
2. **Choose:** LTS version (Long Term Support - the stable one)
3. **Install:** Run the installer (keep clicking "Next")
4. **Verify:** Close and reopen VS Code, then run `node --version` again

---

## 📦 Step 3: Set Up Git

### What is Git?

Git is like a **time machine** for your code. It:
- Saves snapshots of your project (so you can go back if you break something)
- Lets you track what changed and when
- Is industry-standard (every developer uses it)

### Check if you have it:

```bash
git --version
```

**If you see a version:** You're good! ✅

**If not:** Download from https://git-scm.com

---

## 🎨 Step 4: Install Essential VS Code Extensions

Extensions are like apps for your code editor. Let's install the essential ones:

### How to Install Extensions

1. Click the **Extensions** icon in VS Code (left sidebar, looks like building blocks)
2. Search for the extension name
3. Click **Install**

### Essential Extensions:

| Extension | Why You Need It |
|-----------|-----------------|
| **Live Server** | See your changes instantly in the browser |
| **Prettier** | Auto-formats your code (makes it pretty) |
| **ESLint** | Catches JavaScript errors before you run code |
| **Auto Rename Tag** | Changes closing tags when you change opening tags |
| **Path Intellisense** | Auto-completes file paths |
| **ES7+ React Snippets** | Shortcuts for writing React code faster |
| **Tailwind CSS IntelliSense** | Auto-complete for CSS (we'll use this later) |

**Install all of these now.** Trust me.

---

## 🔧 Step 5: Configure VS Code Settings

Let's make VS Code work better for you.

### Enable Format on Save

1. Press `Ctrl+,` (opens Settings)
2. Search for "format on save"
3. **Check the box** ✅

Now your code auto-formats every time you save. Beautiful.

### Set Prettier as Default Formatter

1. In Settings, search for "default formatter"
2. Select **Prettier - Code formatter**

---

## 🌐 Step 6: Understand Browser Dev Tools

### What are Dev Tools?

Every browser has **hidden developer tools** that let you:
- See the HTML structure of any webpage
- Test CSS changes live
- Debug JavaScript errors
- View network requests (API calls!)

### How to Open Dev Tools:

**In Chrome or Edge:**
- Press `F12` or `Ctrl+Shift+I`
- Or right-click any webpage → "Inspect"

**Try it now:**
1. Open Google.com
2. Press F12
3. Click the **Elements** tab
4. Hover over the HTML - watch how it highlights parts of the page!

This is your **X-ray vision** for the web. You'll use it constantly.

---

## 📁 Step 7: Create Your Learning Folder

Let's organize your work properly.

### Create this folder structure:

```
Documents/
  frontend-learning/
    (this is where you'll do all exercises)
```

### In VS Code:

1. **File → Open Folder**
2. Navigate to your `frontend-learning` folder
3. Click **Select Folder**

Now VS Code is focused on this workspace. Perfect.

---

## ✅ Verification Checklist

Before moving to the next lesson, make sure:

- [ ] VS Code is installed and configured
- [ ] Node.js is installed (`node --version` works)
- [ ] Git is installed (`git --version` works)
- [ ] All 7 extensions are installed
- [ ] Format on save is enabled
- [ ] You know how to open browser dev tools
- [ ] You have a dedicated learning folder open in VS Code

---

## 🎉 You're Ready!

Your development environment is now **professional-grade**. The same tools used at Google, Facebook, and every tech company.

The hard part is done. Now the fun begins.

---

## 🚀 Next Step

Head to **[01-html-foundations](../01-html-foundations/README.md)** and let's build your first webpage.

---

**Remember:** If you get stuck, that's normal. Confusion means you're learning. Push through it.

You've got this. 💪
