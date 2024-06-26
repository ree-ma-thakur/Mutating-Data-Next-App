# Server Actions

- Feature supported by React
- Work on server side only not on client
- Server actions must be async
- Has formData as 1st param
- anything returned from here is returned to useActionState 2nd argument & in its 1st response array elt
- But if we pass server action to useACtionState/useFormState, then 1st param is prevState & 2nd param is fromData updated state

# redirect()

- next/navigation function
- redirect to specific route
- server side

# useFormStatus()

- Provided by react-dom
- client side
- IT return the information abount the submission status of surrounding form

# useActionState()

- Provided by react
- Earlier it was useFormState() & provided by react-dom
- Takes 2 arguments: form action & initial form state
- It returns array of current form state & updated form action(to which it is listening), 2nd elt should be used as action to form

# Used cloudinary to store images url

# revalidatePath()

- from 'next/cache'
- by default nextjs caches page data, therefore page doesn't update just because data changed
- Therefore rP() is an imp function thar we should call when we are changing some data that is shown on page
- https://nextjs.org/docs/app/api-reference/functions/revalidatePath
- Tells which pages need to be revalidated or updated
- If we pass rp('/', 'layout'), then all the pages of application will be revalidated

# useOptimistic

- Optimistic updating (from react)
- works on client side only
- means we are optimistic that our update will work therefore we want to show new state immediately to the user & perform that update BTS, if the update fails then we will rollback the update
- 1st input is data that we fetched from DB, 2nd is function that gets called & updates the data optimistically on client side until the change has been processed on server side so that we can change it immediately & then sync it back with server side state after server state update
- It returns array of updated optimistic array & function to trigger optimistic update

# Caching

- In production caching is more aggressvie than development, even after changes in DB, in production code caching does not show the updated data or page
- Next pre-renders all the pages during build process in production & caches those pre-rendered pages & then it never re-renders them thereafter then, unless they are dynamic pages
- Therefore we should tell react that it should re-render the pages whenever we change the data, we can do this using rP()

## OPTIMIZATION

# Image optimization

- Using Image from 'next/image'
- This tag has width, height, srcset(for different screen size, resolutions & densities)
- Lazy loading of image
- To avoid lazy loading we can add 'priority' prop which will pre load the image
- We can use 'fill' prop is we don't know the width & height of image
- We need to configure the hostname(external site) in next.config file otherwise nextjs will block images url from external sites
- loader props in Image: It takes a function as a value that will be executed by Nextjs when it will determine the path of image

# Metadata

- https://nextjs.org/docs/app/building-your-application/optimizing/metadata
- Static: MD using export const metadata object
- Dynamic MD using export async function generateMetadata, this function will have data or confog obj
- generateMD returns the object with title & description
