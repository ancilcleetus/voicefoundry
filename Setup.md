# VoiceFoundry: SaaS platform for Custom Voice Generation from Text

## Download and install nvm:
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash

## in lieu of restarting the shell
\. "$HOME/.nvm/nvm.sh"

## Download and install Node.js:
nvm install 24

## Verify npm version:
npm -v # Should print "11.9.0".

## Verify npx version:
npx -v # Should print "11.9.0".

## Verify nvm version:
nvm -v # Should print "0.40.4".

## Verify the Node.js version:
node -v # Should print "v24.14.0".

## Verify the git version:
git --version # Should print "git version 2.25.1".

## Go to project parent directory
cd ~/Work/GitHub

## Create Nextjs app
npx create-next-app@16.1.6 voicefoundry

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

## Shadcn => A set of beautifully designed components that you can customize, extend, and build on
npx shadcn@latest --version # Should print "shadcn@4.0.8".

npx shadcn@3.8.5 init

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

## Install shadcn@3.8.5 to force shadcn version as 3.8.5 in package.json & package-lock.json
npm install shadcn@3.8.5

## Shadcn => Add button
npx shadcn@3.8.5 add button

✔ Checking registry.
✔ Installing dependencies.
✔ Created 1 file:
  - src/components/ui/button.tsx
  
  


# References:
1. https://nodejs.org/en/download
2. https://nextjs.org/docs/app/getting-started/installation#quick-start
3. https://ui.shadcn.com/

