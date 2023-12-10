Before you read thtough, these are the take away.

- clsx library lets you render your classNames conditionally
- In Next js, you get to choose whether you want to use static or dynamic rendering for your page. `no store` allows you to opt out of static rendering to prepare you for displaying content that changes dynamically.
- `Suspense` is a powerful API that can help you decide the behavior of your components and how they load on your screen.

## Next.js App Router Course - Starter

This is the starter template for the Next.js App Router Course. It contains the starting code for the dashboard application.

For more information, see the [course curriculum](https://nextjs.org/learn) on the Next.js Website.

# NOTES

- You can use tailwindcss or css modules to style your Next js app
- clsx is a library that lets you toggle class names easily. We recommend taking a look at documentation for more details
- Read about cumulative layout shift from web.dev

### How Nextjs handles fonts

- Next.js automatically optimizes fonts in the application when you use the next/font module. It downloads font files at build time and hosts them with your other static assets. This means when a user visits your application, there are no additional network requests for fonts which would impact performance.

### How Nextjs handles images

- Next js uses next/image to serve and optimize its images
- The `<image/>` works like the HTML im element where you can have src, width, alt and all other attributes like so:
  `<image src="./pathtoimage width={500} height={600} />`
  s

### Recommended reading

There's a lot more to learn about these topics, including optimizing remote images and using local font files. If you'd like to dive deeper into fonts and images, see:

- Image Optimization Docs
- Font Optimization Docs
- Improving Web Performance with Images (MDN)
- Web Fonts (MDN)

## Folder routing

Every folder has a `page.tsx` or `page.jsx` react component that contains the actual component that is going to be rendered and a `layout.tsx` file
that contains the layout of how the page will be presented on the screen. This `layout.tsx` file can also contain nested components if other components need to be rendered on the screen, and take in a `children` prop to render all other children component of th main folder.

- Read up on colocation
- read up on partial hydration

## Navigation

Using the `usePathname` hook we check to see if the pathname of the URL matches the link.href, and if it does. We use `clsx` to conditionally render the classNames of the button for example, changing the link background color according to the conditiopnally rendered className so that indicate when we are on the page of the current link that we have clicked. see demo as We check if the `pathname === link.href` in the `dashboard/nav-link.tsx` component.

# next-dashboard

## Database

We setup database using vercel storage option under the project, created postgres server, connected and navigated to env local tab,
show secrets and grabbed the details in there, pasted in .env file in local and made sure the file name was written in .gitignore

### Fetching Data

Nextjs uses route Handlers to create API endpoints

We are using SQL to fetch data because SQL allows you to write targeted queries to fetch and manipulate specific data.

### Static and Dynamic rendering

Our aim is to make the dashboard page dynamic so that it can allow live updating. We do this by opting out of the default behaviour of static rendering and switching to dynamic rendering

### import { unstable_noStore as noStore } from 'next/cache';

In Next.js 14, the code `import { unstable_noStore as noStore } from 'next/cache';` serves a specific purpose:

**It allows you to opt out of static rendering and caching for a specific component or data fetching function.**

Here's a breakdown of its components:

- `import`: Keyword used to import functionalities from another module.
- `{ unstable_noStore as noStore }`: Imports the `unstable_noStore` function and renames it to `noStore` for easier usage.
- `from 'next/cache'`: Specifies the module from where we are importing the function. In this case, it's the `next/cache` module, which provides functions related to data caching in Next.js.
- `unstable_noStore`: This function is considered "unstable" as it may change in future versions of Next.js. However, it's currently used to disable static rendering and caching for a specific component.

**Here are some scenarios where you might use `noStore`:**

- **Fetching data that constantly changes:** If you're fetching data that updates frequently, like live stock prices or social media feeds, you wouldn't want it to be cached as it would become outdated quickly. In such cases, you can use `noStore` to ensure the data is always fetched fresh on every request.
-
- **Rendering personalized content:** If you need to render content based on the user's specific information or preferences, static rendering wouldn't be appropriate. Here, `noStore` ensures the content is dynamically generated on each request, reflecting the user's specific context.
-
- **Server-side components:** When working with server-side components, which allow you to render content on the server for SEO and performance benefits, you might want to disable caching for certain sections that require dynamic updates. `noStore` helps achieve this.

**It's important to remember that using `noStore` can have performance implications:**

- By opting out of static rendering, you might lose some of the performance benefits Next.js offers for static pages.
- Frequent data fetches without caching can add additional load on your server.

Therefore, use `noStore` cautiously and only when necessary. For static content that doesn't change frequently, relying on Next.js's default caching mechanisms will provide better performance and scalability.

## Loading

Next js looks for a component called `loading.tsx` to use as a loading placeholder before content is gotten from the backend.

- We will set a skeleton for the loading by importing the skleton componet into the `loading.tsx` file.

### issue

`loading.tsx` is getting apllied to the pages in invoice and customers

-Since `loading.tsx` is a level higher than /invoices/page.tsx and /customers/page.tsx in the file system, it's also applied to those pages.

### Route groups

We can change this with Route Groups. Create a new folder called /(overview) inside the dashboard folder. Then, move your `loading.tsx` and `page.tsx` files inside the folder:

# Streaming

Streaming allows us to load content in small chunks so that trying to loading the whole content does not cause us to slow our website. This can be done in 2 ways

- using the `loading.tsx` component
- using `<suspense>`

Using suspense we can create a boundary by wrapping whatever compnent we want to laod within a `<suspense>` element.

### loading trick

If you want multiple compnents to load at the same time, first put all the component into parent component and then wrap parent component in a `<suspense>`.
