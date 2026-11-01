# Telekom Running Mantra — v4 preview

A standalone Greek questionnaire using the exact five questions and 25 answer choices in `Tele_Mantra_v4.pdf`. All choices are personal preferences; there are no correct or incorrect answers.

## Upload to Netlify

1. Extract the downloaded ZIP.
2. Open <https://app.netlify.com/drop> and sign in to your Netlify account.
3. Drag in the extracted folder that directly contains `index.html`.
4. Open the website URL Netlify provides. Enter a nickname and press **ΞΕΚΙΝΑ**.

No build command, installation, API key, or environment setting is required for this preview. For an existing Netlify site, open that site's **Deploys** tab and upload the same folder in its manual deployment area. Use the URL of the new deployment to test the uploaded version.

## Open locally

Open `index.html` in a modern browser to play. The game also works without an Internet connection. To serve it locally from the repository root:

```sh
python3 -m http.server 8001 --bind 127.0.0.1 --directory mantra
```

The experience includes a required nickname, one answer per question, progress, back navigation with answer preservation, a result, answer review/editing, copy, transparent SVG export, and restart. Session data stays in the current browser tab's session storage. No player data is sent to a server.

## Preview scope

The question and answer wording follows the supplied PDF. The result screen extends the PDF, which ends with the loading screen. This preview selects one complete, reviewed Greek mantra matched to the selected answers; it does not call a generative AI service. Every output is validated at 2–5 words. The display, clipboard and transparent SVG export contain the same mantra, with no appended dedication or supporting paragraph. The approved live AI brief is included in MASTER_PROMPT.md. Connecting a production AI generator requires the original backend or a separate server-side integration. Do not put API keys in this HTML.

The exported SVG contains magenta text on a transparent background. It is not a photorealistic shoelace render. Use the prompts in [SHOELACE_PROMPTS.md](SHOELACE_PROMPTS.md) to create that artwork with an image-generation tool.

## Hosting

The complete application is the single `index.html` file. It can be hosted under any static-site path without a build step or external dependencies. The separate `marathon42` racing game is unchanged.

## Validation

Browser checks cover all 3,125 answer combinations against the five-word limit, the exact PDF copy, completion gates, all five questions, back navigation, result generation, SVG download, answer editing, restart, keyboard operation, and mobile layout. The tests use Python Playwright with the system `/usr/bin/chromium`; they do not require an npm install.
