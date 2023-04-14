# Bot management

First we will set up Firestarter and create the bot management screen, which is this.

![Chatbot idea sketch](../assets/chatbotideasketch-botmanagement.png)

## Set up Firestater

Follow the setup guide link below to get Firestarter set up, then come back here after.

[Setup Guide](../../setup)

## Add a new page

Adding a new page in NextJS is simple. You just add a new file.

In your project, under `nextjs/src/pages` add a new folder called `chatbot` and within that folder create a new file called `index.tsx`.

Put the following code in `index.tsx` to get started:

```typescript
import Layout from '@/components/Layout'

export default function Login() {

  return (
    <>
      <Layout>
        <p>My page will go here!</p>
      </Layout>
    </>
  )
}
```

If the development server isn't already running, run `yarn dev` from the command line from the `nextjs` folder.

Now visit [http://localhost:3000/chatbot](http://localhost:3000/chatbot) and you should see the new page:

![screenshot](../assets/chatbot-screenshot-1.png){ .border }

## Add a navigation link

We are going to replace the default navigation items with a single link to this new page.

* Open `nextjs/src/components/Nav.tsx`
* You will see a section of navigation items like this:

```tsx
 <ul className="mr-auto lg:flex lg:flex-row">
    <li className="nav-item">
        <Link href="/todos" className="menu-item">
        Todos
        </Link>
    </li>
    <li className="nav-item">
        <Link href="/" className="menu-item">
        Team
        </Link>
    </li>
    <li className="nav-item mb-2 lg:mb-0">
        <Link href="/" className="menu-item">
        Projects
        </Link>
    </li>
</ul>
```

You can remove these `li` items, and then add one for the new page like this:

```tsx
<li className="nav-item mb-2 lg:mb-0">
    <Link href="/chatbot" className="menu-item">
    Your Bots
    </Link>
</li>
```

Now visit [http://localhost:3000](http://localhost:3000) check that this navigation item works and takes you to the page we have created.

## Add the list of bots

We are going to now add the list of existing bots. Since there are none in the database, and there is no page yet to add them, we will manually add some data to the Firebase backend to check that it works.


## Next steps

The next step in the tutorial is coming soon.

