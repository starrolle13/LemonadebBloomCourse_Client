# Lemonade Bloom Course - Frontend Code

This is the complete React frontend for the Lemonade Bloom course platform.

## What's Included

- **React 19** - Modern React with hooks
- **Tailwind CSS 4** - Utility-first styling
- **shadcn/ui** - Pre-built UI components
- **tRPC** - Type-safe API communication
- **Vite** - Fast build tool

## File Structure

```
src/
├── pages/           # Page components (Home, Module, Booking)
├── components/      # Reusable UI components
├── lib/            # Utilities and tRPC client
├── contexts/       # React contexts (Theme, etc)
├── hooks/          # Custom React hooks
├── _core/          # Core functionality (auth, etc)
├── index.css       # Global styles with brand colors
├── App.tsx         # Main app with routing
└── main.tsx        # Entry point
```

## Key Pages

1. **Home.tsx** - Dashboard with course modules, progress tracking, booking/webinar cards
2. **Module.tsx** - Individual module content with quizzes and progress
3. **Booking.tsx** - Setup call ($499) and webinar ($19.99) booking

## Brand Colors

- Primary Orange: `#C46E2F`
- Pink: `#CTUSRUST` 
- Cream: `#F4ECE7`
- Typography: Poppins, Nunito (no cursive fonts)

## Setup Instructions

### 1. Install Dependencies
```bash
pnpm install
```

### 2. Environment Variables
Create a `.env.local` file with:
```
VITE_APP_ID=your_app_id
VITE_OAUTH_PORTAL_URL=your_oauth_url
VITE_FRONTEND_FORGE_API_KEY=your_api_key
VITE_FRONTEND_FORGE_API_URL=your_api_url
VITE_STRIPE_PUBLISHABLE_KEY=your_stripe_key
VITE_ANALYTICS_ENDPOINT=your_analytics_endpoint
VITE_ANALYTICS_WEBSITE_ID=your_analytics_id
```

### 3. Run Development Server
```bash
pnpm dev
```

The app will be available at `http://localhost:5173`

### 4. Build for Production
```bash
pnpm build
```

Output will be in the `dist/` directory.

## Key Features

✅ **8 Course Modules** - Complete Walmart seller curriculum
✅ **Interactive Quizzes** - 3 questions per module with scoring
✅ **Progress Tracking** - Visual progress bar and completion tracking
✅ **Booking System** - $499 setup calls with Stripe integration
✅ **Webinar Enrollment** - $19.99 webinar with payment
✅ **Downloadable Resources** - Course workbook and welcome guide
✅ **Modern Design** - Brand-aligned with professional hero images
✅ **Responsive** - Mobile and desktop optimized

## API Integration

The frontend communicates with the backend via tRPC. Key procedures:

- `trpc.course.getModules` - Fetch all modules
- `trpc.course.getModule` - Fetch single module
- `trpc.course.getQuizzes` - Fetch quiz questions
- `trpc.course.submitQuiz` - Submit quiz answers
- `trpc.course.completeModule` - Mark module complete
- `trpc.payment.createCheckoutSession` - Create Stripe session

## Authentication

Uses Manus OAuth for authentication. The `useAuth()` hook provides:
- `user` - Current user object
- `isAuthenticated` - Boolean auth status
- `logout()` - Logout function
- `getLoginUrl()` - OAuth login URL

## Customization

### Change Brand Colors
Edit `src/index.css` and update the CSS variables in `:root`:
```css
:root {
  --primary: oklch(0.58 0.18 30);  /* Orange */
  --accent: oklch(0.75 0.15 20);   /* Pink */
  /* ... more colors ... */
}
```

### Add New Pages
1. Create `src/pages/NewPage.tsx`
2. Add route in `src/App.tsx`
3. Use tRPC hooks for data fetching

### Modify Quiz Questions
Quiz data comes from the backend database. To update:
1. Modify `server/seed-db.mjs` with new questions
2. Run seed script to update database

## Deployment

### Manus (Recommended)
- Already configured and working
- Click "Publish" in Manus dashboard

### Netlify
- Requires backend separation (see NETLIFY_DEPLOYMENT_GUIDE.md)
- Frontend can deploy to Netlify, but needs separate backend

### Vercel
- Similar to Netlify
- Requires environment variables configuration

## Troubleshooting

**Blank page after login?**
- Check browser console for errors (F12)
- Verify environment variables are set
- Check that backend API is accessible

**Styles not loading?**
- Clear browser cache (Ctrl+Shift+Delete)
- Rebuild: `pnpm build`

**Quiz not submitting?**
- Verify backend is running
- Check network tab in browser DevTools
- Ensure database connection is working

## Support

For issues or questions about the frontend code, check:
- `src/pages/` for page implementations
- `src/components/` for UI components
- `src/lib/trpc.ts` for API configuration

---

**Version**: 1.0.0
**Last Updated**: March 15, 2026
**Status**: Production Ready
