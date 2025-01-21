
### Install latest next project with page router
* npx create-next-app@latest

### Run these dependency in the project 
* npm install next@latest react@latest react-dom@latest

### Steps to Add the App Router
* Enable App Router
* To start using the app directory (App Router), you must enable it in your next.config.js file.

#### Update or create next.config.ts:
```tsx
import type { NextConfig } from "next";

const nextConfig: NextConfig = {
  /* config options here */
  appDir: true,
  reactStrictMode: true,
};

export default nextConfig;
```
#### Create the app Directory
* Add an app directory to the root of your project. This will contain routes using the new App Router.
```tsx
/project-root
  /app
    /layout.js
    /folder_name/page.tsx
  /pages
    /index.js
    /api/hello.js
```
#### Define an App Router Route
* Create the required layout.js and page.js files in the app directory. The layout.js is required for the App Router to define a layout for all nested routes.

```tsx
app/layout.js

import React, { ReactNode } from 'react';
import "@/styles/globals.css";

interface RootLayoutProps {
  children: ReactNode;
}

export default function RootLayout({ children }: RootLayoutProps) {
  return (
    <html lang="en">
      <body>
        <main>{children}</main>
      </body>
    </html>
  );
}

```

#### Avoid Conflicts
* Ensure there are no conflicting routes between app and pages:

* If a route exists in both directories, the Pages Router (pages) will take precedence.
Example: If pages/index.js and app/page.js both define /, only pages/index.js will be used.
To avoid conflicts, keep app routes distinct. For instance:

* Use app/app for App Router routes, so /app is handled by the App Router.
Keep pages/index.js for the root route (/)

```tsx
Final File Structure

/project-root
  /app
    /layout.js       <-- Required for App Router
    /app/page.js     <-- Handles `/app`
  /pages
    /index.js        <-- Handles `/`
    /api/hello.js    <-- API routes
 
```
