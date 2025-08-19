```markdown
## Detailed Implementation Plan for CHILFLEX OTT Website

### Overview
We will build a modern OTT platform dedicated to web series under the CHILFLEX brand. The website will include a landing (home) page with a hero section, an episodes listing page displaying each OTT episode as a card, an episode detail page with an HTML5 video player (with play, pause, download and other controls), and authentication pages (login and registration). A global error page and responsive, modern UI components (navbar, footer, episode card) will be created. All pages will be integrated using the Next.js App Router with TypeScript and styled via updated global CSS. Error handling and client-side validations will be implemented across forms and dynamic routes. Any placeholder images required (for the hero banner and episode thumbnails) will use placehold.co with descriptive parameters.

### New/Modified Files and Step-by-Step Outline

1. **Global Styles and Configuration**
   - **File:** `src/app/globals.css`
     - Extend typography, spacing, and color definitions to achieve a modern, flat design.
     - Add responsive breakpoints and utility classes for margins/paddings.
   - **File:** `next.config.ts`
     - Verify static asset handling (ensure video and image file types are served correctly).

2. **Homepage (Landing Page)**
   - **File:** `src/app/page.tsx`
     - Create a landing page that includes:
       - A **Hero Section** featuring a placeholder banner image:
         ```tsx
         <img 
           src={"https://placehold.co/1920x1080?text=CHILFLEX+Modern+Hero+Banner+with+Vibrant+Colorful+Background"} 
           alt="Modern hero banner displaying CHILFLEX branding with vibrant colors and modern typography" 
           onError={(e) => { e.currentTarget.style.display = 'none'; }} 
         />
         ```
       - Prominent display of the CHILFLEX logo name and tagline.
       - A call-to-action button linking to the episodes listing page (`/episodes`).
       - Integration of the Navbar and Footer components.

3. **Navbar Component**
   - **File:** `src/components/Navbar.tsx`
     - Build a responsive navbar with links: Home, Episodes, Login, Register.
     - Use simple HTML and CSS (or inline styles from globals.css) to enforce modern spacing and typography.
     - Incorporate error fallback for navigation errors.

4. **Footer Component**
   - **File:** `src/components/Footer.tsx`
     - Create a clean footer with copyright text (e.g., "© CHILFLEX 2023. All rights reserved").
     - Ensure consistent styling with the overall theme.

5. **Episodes Listing Page**
   - **File:** `src/app/episodes/page.tsx`
     - Create a page that displays a list of OTT episodes using static/mock data.
     - Import and render the `EpisodeCard` component for each episode in a grid layout.
     - Implement error handling (try/catch) during data fetching and display friendly error messages if needed.

6. **Episode Card Component**
   - **File:** `src/components/EpisodeCard.tsx`
     - Accept props (id, title, description, thumbnail, video URL).
     - Layout a modern card with:
       - A placeholder thumbnail image:
         ```tsx
         <img 
           src={"https://placehold.co/400x300?text=Episode+Thumbnail+Image+for+CHILFLEX+Web+Series"} 
           alt="Episode thumbnail showing a snapshot of the web series with modern design elements" 
           onError={(e) => { e.currentTarget.src = "fallback-image.png"; }} 
         />
         ```
       - Title and a brief description.
       - A “Watch Now” button linking to `/episodes/[id]`.
     - Ensure proper accessibility and error handling on image load.

7. **Episode Detail Page (Dynamic Route)**
   - **File:** `src/app/episodes/[id]/page.tsx`
     - Retrieve the episode ID from route parameters and fetch corresponding static/mock data.
     - Render the episode title, detailed description, and embed an HTML5 video player:
       ```tsx
       <video controls style={{ width: '100%', maxWidth: '800px' }}>
         <source src={episode.videoUrl} type="video/mp4" />
         Your browser does not support the video tag.
       </video>
       ```
     - Add additional UI elements such as a “Back to Episodes” button.
     - Handle errors for invalid IDs gracefully, perhaps redirecting to the error page.

8. **Authentication Pages**
   - **Login Page**
     - **File:** `src/app/login/page.tsx`
       - Create a form with email and password fields using existing UI components (from `src/components/ui/form.tsx`, `input.tsx`, and `button.tsx`).
       - Implement client-side validation for empty fields and proper email format.
   - **Registration Page**
     - **File:** `src/app/register/page.tsx`
       - Build a registration form with fields for username, email, password, and confirm password.
       - Validate matching passwords and proper email formats. Use clear error messages.

9. **Global Error Handling**
   - **File:** `src/app/error.tsx`
     - Implement an error boundary page that catches rendering or navigation issues.
     - Display a friendly error message with a “Go Home” button to redirect back to the homepage.

10. **Testing and Best Practices**
    - Use robust try/catch blocks in data fetching and route handling to prevent runtime errors.
    - Validate form inputs on authentication pages and show user-friendly error messages.
    - Test each page and component manually, ensuring the video controls (play, pause, download) work as expected using the HTML5 video element.
    - Ensure responsive design by testing on multiple screen sizes.

## Summary
- Create a landing page (`src/app/page.tsx`) with a hero section, modern typography, and a call-to-action using a placeholder banner image.  
- Implement new Navbar and Footer components (`src/components/Navbar.tsx` and `src/components/Footer.tsx`) to support smooth navigation.  
- Build episodes listing (`src/app/episodes/page.tsx`) and episode detail dynamic pages (`src/app/episodes/[id]/page.tsx`) with modern video player functionality.  
- Develop authentication pages for login and registration with proper client-side validation.  
- Introduce an error handling page (`src/app/error.tsx`) to gracefully handle runtime errors.  
- Update `globals.css` and `next.config.ts` for consistent, responsive UI design.  
- All new components use clean HTML, CSS, and accessible placeholder images.  
- Best practices such as error handling, accessibility, and responsive design have been integrated throughout.  
