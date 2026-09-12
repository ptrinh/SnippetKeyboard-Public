# Val Town

One function, one URL. Similar to Pipedream, closer to writing code.

## Steps

1. Sign in at [val.town](https://www.val.town) and create a new **HTTP** val.
2. Paste:

   ```ts
   export default async function (req: Request) {
     const now = new Date();
     const text = `Now: ${now.toISOString().slice(0, 16).replace("T", " ")} UTC`;
     return new Response(text, {
       headers: { "content-type": "text/plain; charset=utf-8" },
     });
   }
   ```

3. Copy the val's URL (`https://USER-NAME.web.val.run`) and paste into a
   Dynamic snippet.

The val runs on every tap. Free tier is plenty for a keyboard.
