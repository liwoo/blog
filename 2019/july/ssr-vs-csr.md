# SSR vs. CSR: The One Choice That Could Make or Break Your Web App!

Building Web Apps in 2019 feels like you're navigating through an episode of "Black Mirror," doesn't it? What the heck is even Webpack? You've got buzzwords like "Bundling" and "Tree shaking" flying around, not to mention the labyrinth of rendering techniques. I mean, it's like trying to understand the plot twists in "Inception" on your first watch.

The real "Game of Thrones" here? "To SSR or to CSR." Yeah, you got it, Maestro. It's the Jon Snow versus Daenerys Targaryen of web development. So, let's navigate this Westerosi maze together and crown our ultimate rendering monarch.

## What's CSR Anyway
To understand Client-Side Rendering, let's fire up the DeLorean and zoom back to the old days — I'm talking [AOL CDs](https://archive.org/details/America_Online_AOL_Version_7.0_America_Online_inc._BA602R15_2002) arriving in the mail. "You've got Mail!" causing a rushed excitement around the family computer.

Back then, you clicked a link, and a new page loaded. Your browser made a new HTTP request each time. And it returned the same page for the same request.  But then with social media websites like Facebook gaining massive success, it became clear that we needed a more immersive exprience on the web.  Something akin to playing a 2D video game.

So we came up with dynamic, database-driven pages - written in [PHP](https://www.php.net/)!  That is you clicked a link, and even though a new page was freshly loaded for you, at least it was personalized to the content that made sense __just__ for you.

Enter JavaScript Frameworks. Frameworks like [Backbone.js](https://backbonejs.org/) and [Ember](https://emberjs.com/) opted to move all of the rendering logic to the browser - or the client in this case - hence, Client Side Rendering.

> In Client-Side Rendering (CSR) with React, the browser downloads a minimal HTML page and the JavaScript needed for the page.  The JavaScript is then used to update the DOM and render the page. When the application is first loaded, the user may notice a slight delay before they can see the full page, this is because the page isn't fully rendered until all the JavaScript is downloaded, parsed, and executed. - [NextJS](https://nextjs.org/docs/pages/building-your-application/rendering/client-side-rendering)

The results? Revolutionary. [Everyone and their mum created one](https://mithril.js.org/). We're talking a web experience that went from slow and clunky, to snappy and responsive. With loading spinners, no full page reloads, the web suddenly became faster, fluid and generally more exciting.

## So, what changed?
It turned out CSR was never a silver bullet solution to rendering web apps. Although, coming to think of it, is there even a silver bullet in Software Development? Anyway, some serious red flags started popping up as we stuffed everything to the client side:

1. **SEO:** Ever tried to impress Google with a site full of JavaScript widgets? Yeah, good luck with that.
2. **Performance:** In CSR, your browser does all the work. It's like asking your grandma to run a marathon. Ok, maybe that's a bit harsh, but the (early) browsers were never designed for that amount of processing.
3. **Initial Load:** You click a link, and then you wait... and wait. CSR has that slow first punch, and in the web world, just like on Tinder, first impressions actually do count.

## Enter SSR
Server-side Rendering looked at the growing list of CSR limitations and said, "Hold my [Sobo](https://africanosdrinks.com/sobo-orange/)." Instead of sending a blank or skeleton HTML and waiting for the client to do the rest, SSR sends a fully-rendered page from the server.  

> "But didn't you just say that's how old versions of Facebook worked?" - you ask

Yes, Maestro, you got it. Here's the nuance: while old-school web pages sent a fully-rendered HTML page for every new request (just like SSR), those pages were often static or server-script generated. They didn't provide a dynamic, single-page app experience.

SSR took the idea of sending a fully-rendered HTML page and jazzed it up. It combined the best of both worlds: the SEO-friendly and speedy initial load of traditional server-rendered pages, and the dynamic interactivity of client-side apps.

> (SSR allows us to) render the same components into HTML strings on the server, send them directly to the browser, and finally "hydrate" the static markup into a fully interactive app on the client. - [VueJS](https://vuejs.org/guide/scaling-up/ssr.html#what-is-ssr)

The magic is in the word "hydrate" - a topic for another blog post!

## Ok, great, so we can go home right?
No. Remember what I said about Silver Bullets? Well SSR isn't one either.  Here are some practical short-comings I've found as I SSR my web apps:

### Context - No Globals
If you've coded with the assumption that `window` or `document` objects are available, SSR will be a rude awakening. You see, these browser-specific objects don't exist in a Node.js environment. You might encounter the infamous ReferenceError: window is not defined.

```html
// Example code causing a ReferenceError
if (window.innerWidth > 768) {
  // Do something awesome
}
```

You might want to use conditionals to check for the existence of browser-specific objects.

```html
if (typeof window !== "undefined" && window.innerWidth > 768) {
  // Do something awesome
}
```

### Server Management
With SSR, you've cracked open the gates to the server realm like Neo entering the Matrix. Suddenly, the "client" and "server" aren't just theoretical concepts or responsibilities divided on a Jira board. Nope, they're both yours to command.

You see, SSR doesn't just require you to understand how to send rendered HTML to the client. Oh, it's much deeper than that. We're talking [HTTP status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status), request and response objects, middleware, server configurations, and don't even get me started on handling APIs and databases.

So put on your dual hat of both frontend magician and backend sorcerer because you're not just dabbling in JavaScript and CSS anymore. You're wielding the mighty Node.js (or whatever your server-side language of choice is), diving deep into databases, and choreographing APIs like a Broadway director.

### TTV vs TTI
[Time to View](https://web.dev/articles/fcp) (TTV) and [Time to Interact](https://web.dev/articles/tti) (TTI) are like the opening act and the main event of a concert. SSR might get your users in the door quickly (fast TTV), but that doesn't mean they'll be able to enjoy the show right away (delayed TTI). They might see the content but have to wait to interact with it, like being at a concert but having to wait for the main act to start.

## Sigh, so how do I know what to choose?
No worries, Maestro, I've gone out to create a basic decision tree (keyword - basic) that could guide you when trying to make the decision for your next big Web App:

![CSR vs SSR](https://github.com/liwoo/blog/blob/main/assets/how%20to%20chose%20ssr%20vs%20csr.png?raw=true "How to Choose between CSR and SSR")
