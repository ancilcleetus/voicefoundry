# VoiceFoundry: Step-by-Step Development Log

## Installation of Libraries and Dependencies

### Download and install nvm:
* `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash`

### in lieu of restarting the shell
* `\. "$HOME/.nvm/nvm.sh"`

### Download and install Node.js:
* `nvm install 24`

### Verify npm version:
* `npm -v`  # Should print "11.9.0"

### Verify npx version:
* `npx -v`  # Should print "11.9.0"

### Verify nvm version:
* `nvm -v`  # Should print "0.40.4"

### Verify the Node.js version:
* `node -v`  # Should print "v24.14.0"

### Verify the git version:
* `git --version`  # Should print "git version 2.25.1"

### Go to project parent directory
* `cd ~/Work/GitHub`

## Project Setup, Auth, DB

### Next.js Setup

#### Create Next.js app
* `npx create-next-app@16.1.6 voicefoundry`

```
✔ Would you like to use the recommended Next.js defaults? › No, customize settings
✔ Would you like to use TypeScript? Yes
✔ Which linter would you like to use? ESLint
✔ Would you like to use React Compiler? No
✔ Would you like to use Tailwind CSS? Yes
✔ Would you like your code inside a `src/` directory? Yes
✔ Would you like to use App Router? (recommended) Yes
✔ Would you like to customize the import alias (`@/*` by default)? No

Creating a new Next.js app in /home/ancil/Work/GitHub/voicefoundry.

Using npm.

Initializing project with template: app-tw 


Installing dependencies:
- next
- react
- react-dom

Installing devDependencies:
- @tailwindcss/postcss
- @types/node
- @types/react
- @types/react-dom
- eslint
- eslint-config-next
- tailwindcss
- typescript


added 360 packages, and audited 361 packages in 44s

144 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

Generating route types...
✓ Types generated successfully

Initialized a git repository.

Success! Created voicefoundry at /home/ancil/Work/GitHub/voicefoundry
```

#### Shadcn => A set of beautifully designed components that you can customize, extend, and build on
* `npx shadcn@latest --version`  # Should print "shadcn@4.0.8"

* `npx shadcn@3.8.5 init`

```
✔ Preflight checks.
✔ Verifying framework. Found Next.js.
✔ Validating Tailwind CSS config. Found v4.
✔ Validating import alias.
✔ Which color would you like to use as the base color? › Neutral
✔ Writing components.json.
✔ Checking registry.
✔ Updating CSS variables in src/app/globals.css
✔ Updating src/app/globals.css
✔ Installing dependencies.
✔ Created 1 file:
  - src/lib/utils.ts

Success! Project initialization completed.
You may now add components.
```

#### Install shadcn@3.8.5 to force shadcn version as 3.8.5 in package.json & package-lock.json
* `npm install shadcn@3.8.5`

#### Shadcn => Add button
* `npx shadcn@3.8.5 add button`

```
✔ Checking registry.
✔ Installing dependencies.
✔ Created 1 file:
  - src/components/ui/button.tsx
```
  
#### Shadcn => Add all components (we can remove unnecessary components later)
* `npx shadcn@3.8.5 add --all`

```
⠼ Checking registry.Circular dependency detected in registry items
✔ Checking registry.
✔ Updating CSS variables in src/app/globals.css
✔ Installing dependencies.
✔ Created 56 files:
  - src/components/ui/accordion.tsx
  - src/components/ui/alert.tsx
  - src/components/ui/aspect-ratio.tsx
  - src/components/ui/avatar.tsx
  - src/components/ui/badge.tsx
  - src/components/ui/breadcrumb.tsx
  - src/components/ui/card.tsx
  - src/components/ui/checkbox.tsx
  - src/components/ui/collapsible.tsx
  - src/components/ui/context-menu.tsx
  - src/components/ui/dialog.tsx
  - src/components/ui/direction.tsx
  - src/components/ui/drawer.tsx
  - src/components/ui/dropdown-menu.tsx
  - src/components/ui/empty.tsx
  - src/components/ui/hover-card.tsx
  - src/components/ui/input.tsx
  - src/components/ui/input-otp.tsx
  - src/components/ui/kbd.tsx
  - src/components/ui/label.tsx
  - src/components/ui/menubar.tsx
  - src/components/ui/native-select.tsx
  - src/components/ui/navigation-menu.tsx
  - src/components/ui/popover.tsx
  - src/components/ui/progress.tsx
  - src/components/ui/radio-group.tsx
  - src/components/ui/resizable.tsx
  - src/components/ui/scroll-area.tsx
  - src/components/ui/select.tsx
  - src/components/ui/separator.tsx
  - src/components/ui/sheet.tsx
  - src/components/ui/skeleton.tsx
  - src/components/ui/slider.tsx
  - src/components/ui/sonner.tsx
  - src/components/ui/spinner.tsx
  - src/components/ui/switch.tsx
  - src/components/ui/table.tsx
  - src/components/ui/tabs.tsx
  - src/components/ui/textarea.tsx
  - src/components/ui/toggle.tsx
  - src/components/ui/tooltip.tsx
  - src/hooks/use-mobile.ts
  - src/components/ui/alert-dialog.tsx
  - src/components/ui/calendar.tsx
  - src/components/ui/carousel.tsx
  - src/components/ui/pagination.tsx
  - src/components/ui/chart.tsx
  - src/components/ui/command.tsx
  - src/components/ui/form.tsx
  - src/components/ui/button-group.tsx
  - src/components/ui/field.tsx
  - src/components/ui/item.tsx
  - src/components/ui/input-group.tsx
  - src/components/ui/toggle-group.tsx
  - src/components/ui/sidebar.tsx
  - src/components/ui/combobox.tsx
ℹ Skipped 1 files: (files might be identical, use --overwrite to overwrite)
  - src/components/ui/button.tsx

The `tooltip` component has been added. Remember to wrap your app with the `TooltipProvider` component.
```

```tsx title="app/layout.tsx"
import { TooltipProvider } from "@/components/ui/tooltip"

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en">
      <body>
        <TooltipProvider>{children}</TooltipProvider>
      </body>
    </html>
  )
}
```

#### layout.tsx => Replaced Geist Sans font with Inter font, added Toaster; page.tsx => Added toast on button click; Updated Steps.md; Built and verified working app in local

#### use-mobile.ts => Update MOBILE_BREAKPOINT from 768 to 1024; Updated globals.css; Updated Steps.md; Built and verified working app in local

### Clerk Authentication

#### Add authentication to our Nextjs app using Clerk
* `npm install @clerk/nextjs`

#### layout.tsx => Import ClerkProvider & wrap ClerkProvider around entire app; Clerk warning: You are running in keyless mode => Create VoiceFoundry application in Clerk with Email & Google Login and copy Clerk API keys, then paste those keys in a new .env file

#### `src/app/layout.tsx` — Root Layout

```tsx
import type { Metadata } from "next";
import { Inter, Geist_Mono } from "next/font/google";
import "./globals.css";
import { Toaster } from "sonner";
import { ClerkProvider } from "@clerk/nextjs";

const inter = Inter({
  variable: "--font-inter",
  subsets: ["latin"],
});

const geistMono = Geist_Mono({
  variable: "--font-geist-mono",
  subsets: ["latin"],
});

export const metadata: Metadata = {
  title: "Create Next App",
  description: "Generated by create next app",
};

export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
  return (
    <ClerkProvider>
      <html lang="en">
        <body
          className={`${inter.variable} ${geistMono.variable} antialiased`}
        >
          {children}
          <Toaster />
        </body>
      </html>
    </ClerkProvider>
  );
}
```

##### What this file does

In Next.js App Router, `layout.tsx` is a **special file** — it defines a shared UI shell that wraps every page in the app. The root `layout.tsx` (at `src/app/layout.tsx`) is the **outermost wrapper** — it wraps the entire application and renders once for the lifetime of the session.

Think of it as the **frame of a house** — the actual page content (`children`) changes from room to room, but the frame (fonts, auth context, toast notifications) always stays in place.

##### Line by line explanation

1. Imports

```tsx
import type { Metadata } from "next";
import { Inter, Geist_Mono } from "next/font/google";
import "./globals.css";
import { Toaster } from "sonner";
import { ClerkProvider } from "@clerk/nextjs";
```

- `Metadata` — TypeScript type from Next.js for defining page metadata (`<title>`, `<meta description>`, etc.) in a type-safe way
- `Inter, Geist_Mono` — Two Google Fonts loaded via Next.js's built-in font optimization system (no layout shift, no external network request at runtime)
- `"./globals.css"` — Imports global styles (Tailwind base styles + Shadcn CSS variables); must be imported here at the root so they apply to every page
- `Toaster` — The toast notification container from the `sonner` library; renders the floating notification UI
- `ClerkProvider` — Clerk's React context provider; wraps the entire app so every page and component has access to the currently signed-in user and auth state

2. Font configuration

```tsx
const inter = Inter({
  variable: "--font-inter",
  subsets: ["latin"],
});

const geistMono = Geist_Mono({
  variable: "--font-geist-mono",
  subsets: ["latin"],
});
```

- Each font is configured and exposed as a **CSS custom property** (CSS variable)
  - `Inter` → `--font-inter` (used for body/UI text)
  - `Geist_Mono` → `--font-geist-mono` (used for code/monospace text)
- `subsets: ["latin"]` — only downloads the Latin character set, keeping the font bundle small
- These CSS variables are then referenced by Tailwind in `globals.css` so you can use classes like `font-sans` or `font-mono` throughout the app

3. Metadata

```tsx
export const metadata: Metadata = {
  title: "Create Next App",
  description: "Generated by create next app",
};
```

- `export const metadata` is a **Next.js special export** — Next.js reads this object and automatically injects the correct `<title>` and `<meta name="description">` tags into the `<head>` of every page
- No need to manually write `<head>` tags — Next.js handles it for you
- This is currently the default placeholder text from `create-next-app` and would be updated to reflect VoiceFoundry branding

4. The RootLayout component

```tsx
export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
```

- `RootLayout` is the **required default export** for a Next.js layout file
- `children: React.ReactNode` — represents the page content that gets rendered inside this layout (e.g., the home page, sign-in page, dashboard, etc.)
- `Readonly<{...}>` — TypeScript utility type that makes the props object immutable, preventing accidental mutation of `children`

5. The JSX structure

```tsx
return (
  <ClerkProvider>
    <html lang="en">
      <body
        className={`${inter.variable} ${geistMono.variable} antialiased`}
      >
        {children}
        <Toaster />
      </body>
    </html>
  </ClerkProvider>
);
```

- `<ClerkProvider>` — **Must wrap the outermost element** so that Clerk's auth context is available everywhere in the component tree; any component anywhere in the app can now call Clerk hooks like `useUser()`, `useAuth()`, `useOrganization()` etc.
- `<html lang="en">` — Sets the document language to English; important for accessibility (screen readers) and SEO
- `<body className={...}>` — Applies the two font CSS variables and `antialiased` to the document body:
  - `${inter.variable}` → injects `--font-inter` into the DOM
  - `${geistMono.variable}` → injects `--font-geist-mono` into the DOM
  - `antialiased` → Tailwind class that enables smooth font rendering (uses `-webkit-font-smoothing: antialiased`)
- `{children}` — This is where the actual page content renders (home page, dashboard, etc.)
- `<Toaster />` — Placed **once at the root** so toast notifications triggered from any page or component in the app have a single place to render; if this were placed inside individual pages, toasts would disappear on navigation

##### The full picture simply

```
Browser Request (any page)
       │
       ▼
 <ClerkProvider>          ← Auth context available everywhere
   <html lang="en">
     <body
       fonts + antialiased  ← Consistent typography across all pages
     >
       {children}           ← The actual page content renders here
       <Toaster />          ← Toast notifications render here (once, globally)
     </body>
   </html>
 </ClerkProvider>
```

Every page in the app automatically gets:
- ✅ Clerk authentication context (login state, user info, org info)
- ✅ Consistent fonts (Inter + Geist Mono via CSS variables)
- ✅ Global styles (Tailwind + Shadcn design tokens)
- ✅ Toast notification support (via Sonner's `<Toaster />`)

#### Added src/proxy.ts (for Next.js version before 16, it was called middleware.ts); proxy.ts => added rules for public & protected routes

#### Added Sign-in, Sign-up pages (based on Clerk documentation) and org-selection page

#### Clerk Dashboard => Enable Organizations => Select 'Membership Required' => Click 'Enable'; We now have secure authentication & multi-tenancy in the VoiceFoundry app; Middleware Flow => User can only use the app if they login and select an organization

#### src/app/page.tsx => Added 'Welcome to VoiceFoundry' message, OrganizationSwitcher and UserButton in welcome page

### Prisma Database

#### Install dependencies
* Step 1: `npm install @prisma/adapter-pg @prisma/client @t3-oss/env-nextjs pg`
  * `pg` => The core PostgreSQL client for Node.js (node-postgres)
  * `@prisma/client` => The core Prisma ORM client for database access
  * `@prisma/adapter-pg` => PostgreSQL driver adapter for Prisma ORM
  * `@t3-oss/env-nextjs` => Type-safe environment variable validation for Next.js from the T3 stack; breaks the app if we forget to add env variables
* Step 2: `npm install --save-dev prisma @types/pg dotenv tsx`
  * Dev dependencies (Only required during development, no need in runtime)
  * `prisma` => CLI tool used by developers for commands like `npx prisma init` etc, deployed app just uses `@prisma/client`
  * `@types/pg` => TypeScript type definitions for the `pg` package (since `pg` written in JavaScript with no TypeScript types), Only needed during development/compilation — TypeScript is stripped at runtime
  * `dotenv` => Loads environment variables from a `.env` file into `process.env`, Not needed in production — platforms like Vercel, Railway, or Docker inject env vars directly into the environment without needing a `.env` file
  * `tsx` => TypeScript Execute — runs `.ts` / `.tsx` files directly without compiling, Not needed at runtime — production runs compiled JS, not raw TypeScript
  
#### Create Prisma Postgres database
* `npx prisma init --db`

```
This will create a project for you on console.prisma.io and requires you to be authenticated.
✔ Would you like to authenticate? Yes
Let's set up your Prisma Postgres database!
✔ Select your region: ap-southeast-1 - Asia Pacific (Singapore)
✔ Enter a project name: VoiceFoundry
✔ Success! Your Prisma Postgres database is ready ✅

We created an initial schema.prisma file and a .env file with your DATABASE_URL environment variable already set.

--- Next steps ---

Go to https://pris.ly/ppg-init for detailed instructions.

1. Define your database schema

    Open the `schema.prisma` file and define your first models. Each model becomes a table in your database. Check the docs if you need inspiration: https://pris.ly/ppg-init.

2. Apply migrations

    Once you've designed your schema, a migration is the process of actually creating those tables in the real database.
    
    Run the following command to create and apply a migration:
    `npx prisma migrate dev --name init`
    
    Every time you change your schema later (add a column, add a new model), you run this command again with a new name (e.g., `npx prisma migrate dev --name add_profile_picture`) and it updates the database safely.

3. Manage your data

    Prisma Studio is a visual interface — like a simple spreadsheet view of your database — where you can see, add, edit, and delete rows without writing any code or SQL.
    
    View and edit your data locally by running this command:
    `npx prisma studio`
    
    ...or online in Console:
    https://console.prisma.io/cmo1763qd0ah50zfb0z2qvkvu/cmo17dai90bfd14dw1gbt24b9/cmo17dai90bfb14dwqeyrixpo/studio

4. Send queries from your app

    To access your database from a JavaScript/TypeScript app, you need to use Prisma ORM. Go here for step-by-step instructions: https://pris.ly/ppg-init
```

#### Updated schema.prisma with enum VoiceVariant, VoiceCategory; models Voice, Generation

#### Create first migration of Prisma Postgres DB with name 'init'
* `npx prisma migrate dev --name init`

```
Loaded Prisma config from prisma.config.ts.

Prisma schema loaded from prisma/schema.prisma.
Datasource "db": PostgreSQL database "postgres", schema "public" at "db.prisma.io:5432"

Applying migration `20260417081233_init`

The following migration(s) have been created and applied from new schema changes:

prisma/migrations/
  └─ 20260417081233_init/
    └─ migration.sql

Your database is now in sync with your schema.
```

#### Generate (or Update) the Prisma Client (TypeScript/JavaScript code) that lets our app talk to the database
* `npx prisma generate`

```
Loaded Prisma config from prisma.config.ts.

Prisma schema loaded from prisma/schema.prisma.

✔ Generated Prisma Client (7.7.0) to ./src/generated/prisma in 133ms
```

#### Create src/lib/db.ts

```
import { PrismaClient } from "@/generated/prisma/client";
import { PrismaPg } from "@prisma/adapter-pg";

const adapter = new PrismaPg({
    connectionString: process.env.DATABASE_URL,
});

const globalForPrisma = global as unknown as { prisma: PrismaClient };

const prisma = globalForPrisma.prisma || new PrismaClient({adapter});

if (process.env.NODE_ENV !== "production") globalForPrisma.prisma = prisma;

export { prisma };
```

##### The problem this file solves

  In Next.js development, every time you save a file, the server **restarts and re-runs your code**. Without this file, your app would create **hundreds of new database connections** during development — which is wasteful and can crash your database.

  This file uses Prisma Singleton pattern and solves this by creating `PrismaClient` once and sharing it everywhere, ensuring **only one Prisma connection exists at a time**.

##### Line by line explanation

1. Imports

```ts
import { PrismaClient } from "@/generated/prisma/client";
import { PrismaPg } from "@prisma/adapter-pg";
```
- `PrismaClient` — the auto-generated database client (from `prisma generate`)
- `PrismaPg` — the adapter that tells Prisma to use the `pg` (PostgreSQL) driver to actually connect

2. Setting up the connection

```ts
const adapter = new PrismaPg({
    connectionString: process.env.DATABASE_URL,
});
```

- Creates a PostgreSQL connection using the `DATABASE_URL` from your `.env` file
- Think of this as **dialing the phone number of your database** — the connection string is the number, and the adapter is the phone

3. The global variable trick
​
```ts
const globalForPrisma = global as unknown as { prisma: PrismaClient };
```

- `global` is a special object in Node.js that **persists across hot reloads** (server restarts in development)
- This line just says: "treat `global` as an object that may have a `prisma` property on it"
- Think of `global` like a **sticky note board** that survives even when the server restarts — you can stick your Prisma client on it so it doesn't get recreated

4. Reuse or create the client

```ts
const prisma = globalForPrisma.prisma || new PrismaClient({ adapter });
```

This is the core logic. In plain English:

> "If a Prisma client already exists on the global sticky board, reuse it. If not, create a brand new one."

- First server start → `globalForPrisma.prisma` is empty → creates a **new** `PrismaClient`
- After a hot reload → `globalForPrisma.prisma` already exists → **reuses** the existing one

This prevents multiple connections piling up.

5. Save to global in development only
​
```ts
if (process.env.NODE_ENV !== "production") globalForPrisma.prisma = prisma;
```

- **In development:** saves the Prisma client to the global sticky board so it survives hot reloads
- **In production:** skips this — in production the server doesn't hot reload, so a new `PrismaClient` is created once and lives for the lifetime of the server naturally

6. Export

```ts
export { prisma };
```

Makes the single shared Prisma instance available to your entire app. Every file that does `import { prisma } from '@/lib/db'` gets the **same one connection**, not a new one.

##### The full picture simply

```
First load
    │
    ├── global.prisma exists? 
    │       NO → Create new PrismaClient → Save to global
    │
Hot reload (dev only)
    │
    ├── global.prisma exists?
    │       YES → Reuse it → No new connection created ✅
    │
Production
    │
    └── Server starts once → One PrismaClient → Lives forever ✅
```

# References:
1. https://nodejs.org/en/download
2. https://nextjs.org/docs/app/getting-started/installation#quick-start
3. https://ui.shadcn.com/
4. https://www.prisma.io/

* `claude --resume b35473d0-608d-4912-9cd6-2d83ad8bac13 --bare`
