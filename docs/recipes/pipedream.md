# Pipedream

Pipedream gives you a URL that runs a small workflow and returns whatever you
tell it to. Free tier is enough for personal use.

## Steps

1. Sign in at [pipedream.com](https://pipedream.com) and create a **New Workflow**.
2. Trigger: **HTTP / Webhook** → **New Requests**. Pipedream shows you a URL
   like `https://eoxxxxxx.m.pipedream.net`. Copy it.
3. Add a step: **Run custom code** (Node.js). Replace the code with:

   ```js
   export default defineComponent({
     async run({ steps, $ }) {
       const today = new Date().toLocaleDateString("en-GB", {
         weekday: "long", day: "numeric", month: "long",
       });
       await $.respond({
         status: 200,
         headers: { "content-type": "text/plain; charset=utf-8" },
         body: `Today is ${today}.`,
       });
     },
   });
   ```

4. In the trigger settings, set **HTTP Response** to **Return a custom
   response from your workflow**. Without this, Pipedream answers with its
   own default text.
5. **Deploy**.
6. In Snippet Keyboard, add a snippet, choose **Dynamic**, and paste the URL.

Tap the bubble: the keyboard fetches the URL and inserts `Today is Friday, 12 September.`

## Ideas

- Look up something in Google Sheets, Notion or Airtable in an earlier step,
  then respond with one cell.
- Return a different message depending on the hour.
- Call an LLM with a fixed prompt and return the answer.

## Notes

- The URL is public. Anyone who has it can trigger the workflow.
- Keep the response under a few KB; a keyboard is not a web page.
