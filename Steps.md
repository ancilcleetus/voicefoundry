# VoiceFoundry: Step-by-Step Development Log

## Installation of Libraries and Dependencies

### Download and install nvm:
* `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash`

### in lieu of restarting the shell
* `\. "$HOME/.nvm/nvm.sh"`

### Download and install Node.js:
* `nvm install 24`

### Verify npm version:
* `npm -v` # Should print "11.9.0"

### Verify npx version:
* `npx -v` # Should print "11.9.0"

### Verify nvm version:
* `nvm -v` # Should print "0.40.4"

### Verify the Node.js version:
* `node -v` # Should print "v24.14.0"

### Verify the git version:
* `git --version` # Should print "git version 2.25.1"

### Go to project parent directory
* `cd ~/Work/GitHub`

## Next.js Setup

### Create Next.js app
* `npx create-next-app@16.1.6 voicefoundry`

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

### Shadcn => A set of beautifully designed components that you can customize, extend, and build on
* `npx shadcn@latest --version` # Should print "shadcn@4.0.8"

* `npx shadcn@3.8.5 init`

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

### Install shadcn@3.8.5 to force shadcn version as 3.8.5 in package.json & package-lock.json
* `npm install shadcn@3.8.5`

### Shadcn => Add button
* `npx shadcn@3.8.5 add button`

✔ Checking registry.
✔ Installing dependencies.
✔ Created 1 file:
  - src/components/ui/button.tsx
  
### Shadcn => Add all components (we can remove unnecessary components later)
* `npx shadcn@3.8.5 add --all`

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

### layout.tsx => Replaced Geist Sans font with Inter font, added Toaster; page.tsx => Added toast on button click; Updated Steps.md; Built and verified working app in local

### use-mobile.ts => Update MOBILE_BREAKPOINT from 768 to 1024; Updated globals.css; Updated Steps.md; Built and verified working app in local

## Clerk Authentication

### Add authentication to our Nextjs app using Clerk
* `npm install @clerk/nextjs`

### layout.tsx => Import ClerkProvider & wrap ClerkProvider around entire app; Clerk warning: You are running in keyless mode => Create VoiceFoundry application in Clerk with Email & Google Login and copy Clerk API keys, then paste those keys in a new .env file

### Added src/proxy.ts (for Next.js version before 16, it was called middleware.ts); proxy.ts => added rules for public & protected routes

### Added Sign-in, Sign-up pages (based on Clerk documentation) and org-selection page

### Clerk Dashboard => Enable Organizations => Select 'Membership Required' => Click 'Enable'; We now have secure authentication & multi-tenancy in the VoiceFoundry app; Middleware Flow => User can only use the app if they login and select an organization

### src/app/page.tsx => Added 'Welcome to VoiceFoundry' message, OrganizationSwitcher and UserButton in welcome page

# References:
1. https://nodejs.org/en/download
2. https://nextjs.org/docs/app/getting-started/installation#quick-start
3. https://ui.shadcn.com/

