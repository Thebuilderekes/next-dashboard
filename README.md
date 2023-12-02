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

Using the `usePathname` hook we check to see if the pathname of the URL matches the link.href, and if it does.

We use `clsx` to conditionally render the classNames of the button for example, setting a background color to indicate that we are on the page of the current link that we have clicked if the ``pathname === link.href`` just like in the ``dashboard/nav-link.tsx`` component.
# next-dashboard
