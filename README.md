<p align="center">
  <img src="https://github.com/RobSchilderr/nextjs-native-starter/assets/35261620/52cd8433-f8d2-4bfd-9b0e-d753690330b2" width="500">
</p>

### Use Next.js on iOS and Android + access to native APIs with Capacitor

This monorepo provides a starter project for building a truly **universal** application with Next.js, Tailwind CSS, and Capacitor. This allows you to use NextJS and React on iOS and Android. You don't need React Native or Expo anymore. Now, you can truly share all your code between all platforms while staying in your familiar web-dev stack.

For authentication and session management, we use Supertokens and have official support from their team to continue supporting secure-auth on all platforms. The project is structured using Turborepo, with one repository for the web application and another for the mobile app. The code for both is shared using a `ui` package and other packages.

Live example: https://www.next-capacitor-supertokens.app/

TIP: in the code you find some "Important Capacitor note" which explains the differences in authentication via web/app.

<img width="375" alt="Screenshot_2023-02-20_at_6 00 08_PM" src="https://user-images.githubusercontent.com/35261620/232318901-c4bb8eeb-aa04-42f3-bc33-82cbc454ebc9.png">

## How to use

1. Run: `npx create-supertokens-app@latest --manager=yarn`
2. Pick a name for your app
3. Choose 'Capacitor'
4. Make sure to have `yarn` and `npm` installed on your computer: If you don't have NPM, install NPM first. Then when you have npm, make sure to install `yarn` with the following command: `npm install --global yarn`
5. Type `cd <folder>` to go to the folder and then type `yarn install` and then `yarn dev`
6. For iOS: go to the `next-app` folder and run `yarn build` and `yarn open:ios`
7. for Android: go to the `next-app` folder and run `yarn build` and `yarn open:android`

8. To continue, I would suggest to read the [Capacitor docs](https://capacitorjs.com/docs) and [Supertokens docs](https://supertokens.com/docs/guides).

9. Supertokens also supports [Authentication with JWT](https://supertokens.com/docs/thirdpartyemailpassword/hasura-integration/with-jwt). A good rule of thumb for mobile apps is that authentication should _usually_ (always exceptions 😄 ) be handled through something like JWTs. Supertokens their authentication with JWTs make it super easy to set up with [Hasura](https://hasura.io/docs/latest/index/), for more broad role-based access control and an easy-to-use API.  In this [Youtube video](https://www.youtube.com/watch?v=sgicweOyDyk), Rishabh Poddar (co-founder and CTO Supertokens) explains his vision. By combining Supertokens and Hasura with a PostgreSQL instance hosted on Heroku/Render/Railway, you'd have a very compelling alternative to Supabase or Firebase without being locked in. In this repository, I added an example of JWT authentication as of 29/08/2023, if things are not clear, let me know on Discord or Twitter.

<img width="1436" alt="Screenshot_2023-02-20_at_6 00 08_PM" src="https://user-images.githubusercontent.com/35261620/221919365-4f784876-a79b-4f42-84e2-bbfc90ed91e2.png">

---

## Benefits of using this starter project

This starter project provides several benefits to developers looking to build a web application with authentication and session management, as well as a mobile application using Capacitor. Some of the benefits include:

- Faster development: At least 85% of your web/app code will be shared. Also, I provide a pre-configured development environment with several packages and tools already set up.

- Unified UI: By using the same React UI for both the web and mobile application, you only have to design that component once with TailwindCSS and use it everywhere. This saves you tons of time and also gives you a consistent UI accross your applications. Have your UI for desktop, tablet and phone in only one file.

- Can use any web/js library: No need to try to reinvent the wheel.

- No big difference in performance: If you're a skilled React developer, you can create a high-performance Capacitor app that can match or even exceed the performance of a React Native app. Capacitor provides access to native device features through standard web APIs, so you can leverage your existing web development skills and knowledge to build cross-platform mobile apps. Webview based apps on modern devices are quite performant nowadays, especially on iOS.

- Security: By using Supertokens for authentication and session management, you can be confident that your users' data is secure and that common security issues like XSS and CSRF attacks are mitigated.

- More developers: a bigger pool of developers to collaborate with than when using Flutter or React Native. React is now the biggest framework on the planet and is [not dying soon](https://tkdodo.eu/blog/why-react-isnt-dying).

- Scalability: This starter project is built on top of Turborepo, which allows developers to easily add new packages and applications to the monorepo as their project grows and scales.

---

## Common questions:

### Why not make a PWA instead?

The biggest advantage Capacitor brings is full native access and app store distribution. Yes, PWAs can do a lot, but they

- Can't interface with every native iOS/Android SDK or feature out today or coming out tomorrow. Capacitor can.

- Can't use the massive ecosystem of third-party native SDKs. Capacitor can.

- As of yet, push notifications on iOS for PWA's is not fully done yet.

So, if those things matter to you, Capacitor is the way to go. You can build your app such that you're building a PWA first but then "enhancing" it with native Capacitor plugins or custom native code. The decision is not either/or because Capacitor was built to enable PWAs to run natively with almost 100% code sharing on the web.

Capacitor will offer APIs for various smartphone functionalities like the keyboard, camera, Near Field Communication (NFC), and contacts. It will also provide interfaces for native machine learning Software Development Kits (SDKs) and Google Maps. Moreover, Capacitor allows the execution of code even when the app is closed, thanks to its background plugins, among other features.

One side note that I have to add is that, if your app requires a lot of performance on Android (especially old Android phones), there is this trade off you have to make: [WebView performance significantly slower than PWA](https://bugs.chromium.org/p/chromium/issues/detail?id=1289741). I do not experience this issue on iOS and it is barely noticable on newer Android phones.

### Why did you use to not use Ionic?

I appreciate the swift development process that comes from working exclusively with React and TailwindCSS. Leveraging pre-existing Tailwind components means I can bypass the need for original design work, thereby speeding up the development process. Utilizing Ionic would necessitate designing the UI/UX myself, and its web support doesn't replicate the same feel or appearance as when I develop with Tailwind.

### When would you choose Ionic?

Ionic would be my go-to if I had a project that necessitated designing all elements from the ground up, demanded excellent mobile user experience, and also required web deployment, albeit with the web aspect being less critical than the mobile application.

### So when to choose Capacitor over other alternatives like React Native or Flutter?

<img width="800" src="https://ionic.io/blog/wp-content/uploads/2023/01/Framework-Decision-Flowchart-1-1024x830.png" />

If you have more questions about Capacitor, I recommend you to read: [Capacitor: Everything You’ve Ever Wanted to Know](https://ionic.io/blog/capacitor-everything-youve-ever-wanted-to-know)

---

## Differences from related repositories:

[Next.js + Tailwind CSS + Ionic Framework + Capacitor Mobile Starter](https://github.com/mlynch/nextjs-tailwind-ionic-capacitor-starter) - This current repository uses Turborepo, while the [Ionic example](https://github.com/mlynch/nextjs-tailwind-ionic-capacitor-starter) does not. In addition, this current repository uses Supertokens for authentication and session management, while the Ionic example does not. This current repository also uses Tailwind CSS for all of it's styling instead of the Ionic Framework. The Ionic example serves as a good starterpack of how to use Ionic with Capacitor, but does not address the issues a lot other challanges that arise when using Next.JS and Capacitor in a monorepo.

Side note: Choosing not to use the Ionic UI framework is purely a personal preference. While Ionic is excellent for creating a native app-like feel, focusing on Tailwind CSS allows for a faster development process. If you're seeking a balance between native feel and development speed, consider using 'Konsta UI'—a UI library based on Tailwind that offers a more native-like experience. By embracing this trade-off, you can expedite your app's launch without needing to learn Ionic or create a new component library. Simply leverage an existing Tailwind UI library or explore Konsta UI, and you'll be good to go even faster 🚀

[SuperTokens Example](https://github.com/supertokens/next.js/tree/canary/examples/with-supertokens) - The Supertokens dev team does not yet have an example with Capacitor or clearly address Capacitor-related issues such as CORS, cookies, and domain configuration. The previous Supertokens example uses Server Side Rendering in Next.js and uses the `supertokens-auth-react` package, while this starter project utilizes `supertokens-web-js` and ThirdPartyEmailPassword. It serves however as the prime example of how to use Supertokens in a Next.js app, but does not address the issues that arise when using Supertokens with Capacitor. On another note, for styling we use Tailwind CSS, meaning that we use the custom UI in Supertokens. Here you can find the corresponding docs for our scenario: [Supertokens Docs](https://supertokens.com/docs/thirdpartyemailpassword/custom-ui/init/frontend)

[Turborepo Tutorial](https://github.com/leoroese/turborepo-tutorial) - This current repository is build on top of the Turborepo tutorial. This makes it easier to follow along for those that have not heard of Turborepo yet. The Turborepo tutorial comes with a corresponding [video on YouTube.](https://www.youtube.com/watch?v=YQLw5kJ1yrQ&t=1s) The Turborepo tutorial does not use Capacitor or Supertokens.

---

## What's inside?

This turborepo uses Yarn as a package manager. It includes the following packages/apps:

### Apps and Packages

- `next-app`: a [Next.js](https://nextjs.org) app using [Supertokens](https://supertokens.com/) and [Capacitor](https://capacitorjs.com/)
- `next-web`: another [Next.js](https://nextjs.org) app using only [Supertokens](https://supertokens.com/)
- `ui`: a React component library shared by both `next-web` and `next-app` applications
- `config`: `eslint` configurations (includes `eslint-config-next` and `eslint-config-prettier`)
- `tsconfig`: `tsconfig.json`s used throughout the monorepo
- `lib`: shared utils for Capacitor, easy-to-use Capacitor hooks, supertokens functions to call the API, CORS setup.

### Utilities

This turborepo has some additional tools already setup for you:

- [TypeScript](https://www.typescriptlang.org/) for static type checking
- [ESLint](https://eslint.org/) for code linting
- [Jest](https://jestjs.io) test runner for all things JavaScript
- [Prettier](https://prettier.io) for code formatting
- [Capacitor](https://capacitorjs.com/) A cross-platform native runtime for web apps.
- [Supertokens](https://supertokens.com/) Open-source authentication and session management system for your web apps.
- [React Hook Form](https://react-hook-form.com/) Performant, flexible and extensible forms with easy-to-use validation.
- [Tailwind CSS](https://tailwindcss.com/) CSS framework - rapidly build modern websites without ever leaving your HTML.

### Note on Server Side rendering

The `next-app` in this starter project relies on the API routes of the `next-web` for utilizing Supertokens. However, because the `next-app` must be able to run purely client-side and use `Next.js's Export` command, it does not support Server Side Rendering. This means that certain features and functionality are not available in the next-app, including image optimization, internationalized routing, API routes, rewrites, redirects, headers, middleware, incremental static regeneration, and the fallback and getServerSideProps options. In the future it might be possible to use SSR with Capacitor, but for now this is out of scope.

#### Changing authentication method

By default `next-app` and `next-web` uses Social + Email password based login with SuperTokens to implement auth. To change this, set the value of `AUTH_MODE` in `packages/lib/utils/config.ts` to the type of auth you want to use.

Refer to the comments in `packages/lib/utils/common.types.ts` to know what the different values of `AUTH_MODE` mean

### Instructions

Please create an `env.local` file and add the following ENV variables for testing:

```
# These are all working development keys.
# IMPORTANT: You can use them during development, but for production use,
# make sure to change them to keys issued for your app.

NODE_ENV=development
NEXT_PUBLIC_APP_STAGE=development

GOOGLE_CLIENT_ID=1060725074195-kmeum4crr01uirfl2op9kd5acmi9jutn.apps.googleusercontent.com
GOOGLE_CLIENT_SECRET=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

GITHUB_CLIENT_ID=467101b197249757c71f
GITHUB_CLIENT_SECRET=e97051221f4b6426e8fe8d51486396703012f5bd

APPLE_CLIENT_ID="4398792-io.supertokens.example.service"
APPLE_KEY_ID="7M48Y4RYDL"
APPLE_TEAM_ID="YWQCXGJRJL"
APPLE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\nMIGTAgEAMBMGByqGSM49AgEGCCqGSM49AwEHBHkwdwIBAQQgu8gXs+XYkqXD6Ala9Sf/iJXzhbwcoG5dMh1OonpdJUmgCgYIKoZIzj0DAQehRANCAASfrvlFbFCYqn3I2zeknYXLwtH30JuOKestDbSfZYxZNMqhF/OzdZFTV0zc5u5s3eN+oCWbnvl0hM+9IW0UlkdA\n-----END PRIVATE KEY-----"

SUPERTOKENS_CONNECTION_URI = "yourenv"
SUPERTOKENS_API_KEY = "yourenv"
```

These are the test environment variables from Supertokens. You should replace these with your own later on.

##### Apple login testing on native device

Testing Apple login doesn't work in your xCode simulator. For this, use a native device. Remember to change your `FRONTEND_URL` in the `config` file to use your local IP address.

### Known caveats

#### Caveat 1 - [Token Transfer Method](https://supertokens.com/docs/thirdpartyemailpassword/common-customizations/sessions/token-transfer-method)

We are using auth requests with the `Authorization` header:
`Supertokens recommends cookie-based sessions in browsers because header-based sessions require saving the access and refresh tokens in storage vulnerable to XSS attacks.`

Supertokens supports 2 methods of authorizing requests:

1. Based on cookies
   The default in our web SDKs
   Uses HttpOnly cookies by default to prevent token theft via XSS

2. Based on the Authorization header
   The default in our mobile SDKs
   Uses the Authorization header with a Bearer auth-scheme
   This can make it easier to work with API gateways and third-party services
   Preferable in mobile environments, since they can have buggy and/or unreliable cookie implementations

Possible solution if you want extra security: use Supertokens anyway with cookies on Capacitor with the custom cookie handler that is in this repository. This works, but requires extra effort, you need to know what you're doing.

> Do note that browsers have built in defense mechanisms now (CORS for example) that prevent XSS attacks. Supertokens also has anti csrf tokens that can help but in general as long as you use short lived sessions (which Supertokens enables with their rotating refresh tokens) you should be fine. Even if an attack happens it would be minimised to the duration of your access token lifetime. Moreover Supertokens has theft detection mechanisms in place that would log all sessions for that user out.

#### Caveat 2: Apple universal links dont work for HTTP redirects (when the API returns a status code for redirect) but only works if there is an actual navigation happening

In conclusion: Apple login does not work on the mobile web right now. You can find more information about this on the /temp route of the web. Supertokens developers are currently working on a solution that will allow information to be stored in the state sent to the provider, which can then be checked in the API layer to determine if it's mobile or web. However, until this solution is available, a workaround is being used that prevents iOS login from working on the web, so it should be removed from the UI until further notice.

#### Caveat 3: [Live Reload Capacitor](https://capacitorjs.com/docs/guides/live-reload)

Live reload is not working on Capacitor when using Supertokens. We are looking into a solution.
