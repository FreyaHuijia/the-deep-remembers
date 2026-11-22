# The Deep Remembers

An interactive artwork about how language models learn. Feed words to a bioluminescent deep-sea organism and watch what it absorbs change the shape and color of its body.

## Run locally

Open `index.html` in a browser, type a phrase, and press Enter. The artwork is a single HTML file with inline CSS and JavaScript and requires no build step. The **Speak** button appears in browsers that expose the Web Speech API. It feeds final English (US) transcripts into the same pipeline as typed text.

## Canvas rendering

The Canvas 2D scene simulates an organism made of glowing nodes, connections, and trailing strands, surrounded by drifting particles. Each animation frame advances the simulation, then draws the organism, floating phrases, and word particles. The canvas scales its backing buffer for the device pixel ratio and updates on resize. With reduced motion enabled, the scene updates at a lower frequency.

## From words to growth

1. Input is split on whitespace into chunks of up to nine words. Each chunk appears as a phrase before breaking into individual particles.
2. The code lowercases each word and strips everything except Unicode letters, numbers, and straight apostrophes. Empty tokens and common English stop words drift away as particles. A hand-written lexicon assigns the remaining words to one of eight categories across four dimensions: emotion, concept, sensation, and relation. A deterministic hash assigns words outside the lexicon to a category.
3. Each category starts with a randomized preference. The more often the organism has absorbed a category, the more likely it is to accept another word from it. An absorbed word adds a node, updates the on-screen tallies, and shifts the organism's glow toward a hue weighted by everything it has absorbed.

The learning metaphor comes from these in-memory rules and feedback loops. Reloading starts a new organism.
