# Deployment Guide - Vercel

## 🚀 Quick Deploy

### Option 1: Vercel CLI
```bash
npm install -g vercel
cd flowers-react
vercel
```

### Option 2: GitHub Integration
1. Push your code to GitHub
2. Go to [vercel.com](https://vercel.com)
3. Import your repository
4. Vercel will auto-detect it's a Vite project

### Option 3: Vercel Dashboard
1. Go to [vercel.com/dashboard](https://vercel.com/dashboard)
2. Click "Add New Project"
3. Import your Git repository
4. Configure:
   - **Framework Preset**: Vite
   - **Root Directory**: `flowers-react` (if repo root is parent folder)
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist`
   - **Install Command**: `npm install`

## ⚙️ Configuration

### vercel.json
The `vercel.json` file is already configured to handle client-side routing:
- All routes (`/`, `/flowers`, `/gallery`, `/kaleidoscope`) redirect to `index.html`
- React Router handles routing on the client side
- This prevents 404 errors when refreshing pages

### Build Settings
- **Build Command**: `npm run build`
- **Output Directory**: `dist`
- **Node Version**: 18.x or higher (auto-detected)

## 🔧 Troubleshooting

### 404 Error on Refresh
✅ **Fixed!** The `vercel.json` file handles this automatically.

### Images Not Loading
- Ensure images are in `public/img/` folder
- Vite serves them from root: `/img/filename.jpg`
- Check that images are copied during build

### Build Fails
- Check Node.js version (18+ required)
- Ensure all dependencies are in `package.json`
- Check build logs in Vercel dashboard

### Environment Variables
If you need env variables:
1. Go to Vercel project settings
2. Add variables in "Environment Variables" section
3. Use `import.meta.env.VITE_*` in your code

## 📦 What Gets Deployed

- ✅ `dist/` folder (build output)
- ✅ `vercel.json` (routing config)
- ✅ `package.json` (dependencies)
- ❌ `src/` (source files - not needed)
- ❌ `node_modules/` (installed on Vercel)
- ❌ Development files

## 🔄 After Deployment

1. **Test all routes**:
   - `/` - Homepage
   - `/flowers` - Flowers page
   - `/gallery` - Gallery slider
   - `/kaleidoscope` - Interactive flower

2. **Test refresh** on each page (should not show 404)

3. **Check images** load correctly

4. **Test mobile** responsiveness

## 📝 Notes

- Vercel automatically handles HTTPS
- Custom domains can be added in project settings
- Preview deployments are created for each PR
- Production deployments on main branch push
