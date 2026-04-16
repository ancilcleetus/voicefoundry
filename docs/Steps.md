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

# References:
1. https://nodejs.org/en/download
2. https://nextjs.org/docs/app/getting-started/installation#quick-start
3. https://ui.shadcn.com/
4. https://www.prisma.io/
