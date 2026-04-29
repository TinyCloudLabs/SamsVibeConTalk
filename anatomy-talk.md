---
theme: default
title: The Anatomy of Interoperable Apps
info: A 15-minute talk by Sam Gbafa
favicon: /favicon.ico
drawings:
  persist: false
transition: none
mdc: false
fonts:
  sans: 'Inter'
  serif: 'Inter'
  mono: 'JetBrains Mono'
---

<!-- SLIDE 1: TITLE CARD -->
<div class="slide-centered">
  <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.62rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.22em; color: var(--accent); margin-bottom: var(--space-lg);">A Talk in Four Parts</p>
  <h1 style="font-size: 2.6rem !important; font-weight: 800 !important; line-height: 1.1 !important; letter-spacing: -0.03em; max-width: 780px; margin: 0 0 var(--space-lg) 0;">The Anatomy of<br/>Interoperable Apps</h1>
  <div class="neo-divider" style="width: 80px; height: 3px; margin: 0 auto var(--space-lg);"></div>
  <p style="font-size: 1.05rem; font-weight: 600; color: var(--text-primary); letter-spacing: 0.02em; margin: 0 0 0.3rem 0;">
    Sam Gbafa
  </p>
  <p style="font-size: 0.78rem; color: var(--text-secondary); letter-spacing: 0.04em; margin: 0 0 var(--space-2xl) 0;">
    Co-founder, TinyCloud
  </p>
  <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.62rem; color: var(--text-muted); letter-spacing: 0.18em; text-transform: uppercase; margin: 0;">
    April 29, 2026
  </p>
</div>

<!--
Hey everyone. I'm Sam, one of the founders of TinyCloud. For the next fifteen minutes I want to take apart something we usually take for granted -- what an "app" actually is -- and put it back together in a shape that lets apps work with each other instead of past each other.
-->

---

<!-- SLIDE 2: COLD OPEN — THE MEDICAL PROBLEM -->
<div class="slide-viewport">
  <div class="split-text-img" style="grid-template-columns: 48fr 52fr;">
    <div>
      <p class="section-label" style="color: var(--red) !important;">Cold Open</p>
      <h2 style="margin-bottom: var(--space-md); font-size: 1.55rem !important; line-height: 1.25;">A simple question my apps cannot answer.</h2>
      <p style="font-size: 0.85rem; line-height: 1.6; color: var(--text-primary); margin: 0 0 var(--space-sm) 0;">
        My partner has been dealing with pain that seems related to food.
      </p>
      <p style="font-size: 0.85rem; line-height: 1.6; color: var(--text-primary); margin: 0 0 var(--space-sm) 0;">
        The obvious question: <span style="color: var(--accent-light); font-weight: 600;">what did she eat, and when did the pain happen?</span>
      </p>
      <p style="font-size: 0.85rem; line-height: 1.6; color: var(--text-secondary); margin: 0 0 var(--space-md) 0;">
        Today, even if I build two perfect apps, they still do not naturally work together.
      </p>
      <div class="highlight-box" style="border-left-color: var(--red); border-color: var(--red-border); padding: var(--space-sm) var(--space-md);">
        <p style="font-size: 0.78rem; font-weight: 500; margin: 0; line-height: 1.5;">Best food tracker on earth, plus best pain tracker on earth — and they still cannot answer this together.</p>
      </div>
    </div>
    <div style="display: flex; align-items: center; justify-content: center;">
      <img :src="'/anatomy-talk/02-medical-silos.png'" style="max-height: 340px; width: 100%; object-fit: contain;" alt="Two siloed apps unable to share medical data" />
    </div>
  </div>
</div>

<!--
I want to start with something personal. My partner has been dealing with pain that seems to be related to food. The obvious question is simple — what did she eat, and when did the pain happen? You'd think this is the easiest thing in the world to answer. There are food trackers. There are pain trackers. But if I build the best food tracker on earth and someone else builds the best pain tracker, they still cannot answer this question together. The data lives in two different silos with two different accounts and two different permission models. This should be easy. It is not. And I want to talk about why.
-->

---

<!-- SLIDE 3: WHY APPS DON'T INTEROPERATE -->
<div class="slide-viewport">
  <div class="split-img-text" style="grid-template-columns: 52fr 48fr;">
    <div style="display: flex; align-items: center; justify-content: center;">
      <img :src="'/anatomy-talk/03-fragmented-islands.png'" style="max-height: 470px; width: 100%; object-fit: contain;" alt="Apps as fragmented islands, each with its own account, database, permissions, context" />
    </div>
    <div>
      <p class="section-label" style="color: var(--red) !important;">The Diagnosis</p>
      <h2 style="margin-bottom: var(--space-sm); font-size: 1.5rem !important; line-height: 1.25;">Every app starts cold.</h2>
      <p style="font-size: 0.78rem; line-height: 1.55; color: var(--text-secondary); margin: 0 0 var(--space-sm) 0;">
        Every app you install today creates its own:
      </p>
      <div style="display: grid; grid-template-columns: 1fr 1fr; gap: var(--space-xs); margin-bottom: var(--space-sm);">
        <div class="neo-card-red" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.78rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">Account</p>
        </div>
        <div class="neo-card-red" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.78rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">Database</p>
        </div>
        <div class="neo-card-red" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.78rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">Permission model</p>
        </div>
        <div class="neo-card-red" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.78rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">Context</p>
        </div>
      </div>
      <p style="font-size: 0.78rem; line-height: 1.55; color: var(--text-primary); margin: 0;">
        Every app acts like it is the center of the user's life.
      </p>
      <p style="font-size: 0.78rem; line-height: 1.55; color: var(--accent-light); font-weight: 600; margin: var(--space-xs) 0 0 0;">
        That is why every new app starts cold.
      </p>
    </div>
  </div>
</div>

<!--
Here is the structural reason. Every app you install today does the same four things. It makes you create a new account. It builds its own database. It defines its own permission model. And it tries to capture context about you that it can keep to itself. Every app acts like it is the center of the user's life. From the app's point of view that makes sense — it wants to own the relationship. But from the user's point of view, every new app starts cold. It knows nothing about you. It cannot see what other apps already know. The fragmentation is not a bug. It is the design.
-->

---

<!-- SLIDE 4: THE AGENT CLUE -->
<div class="slide-viewport">
  <div class="split-text-img" style="grid-template-columns: 48fr 52fr;">
    <div>
      <p class="section-label">A Clue</p>
      <h2 style="margin-bottom: var(--space-sm); font-size: 1.4rem !important; line-height: 1.25;">Local agents already do this.<br/>They just cannot scale.</h2>
      <p style="font-size: 0.75rem; line-height: 1.5; color: var(--text-secondary); margin: 0 0 var(--space-sm) 0;">
        On a local machine, an agent can:
      </p>
      <ul style="margin: 0 0 var(--space-md) 0; padding-left: 1rem;">
        <li style="font-size: 0.78rem; margin-bottom: 0.2rem;">Know it is working for you</li>
        <li style="font-size: 0.78rem; margin-bottom: 0.2rem;">Read and write files in the same place</li>
        <li style="font-size: 0.78rem; margin-bottom: 0.2rem;">Build apps that use data from another</li>
        <li style="font-size: 0.78rem; margin-bottom: 0;">Create personalized tools on the fly</li>
      </ul>
      <div class="highlight-box" style="padding: var(--space-sm) var(--space-md);">
        <p style="font-size: 0.74rem; line-height: 1.5; margin: 0;">This works because everything is local and implicitly trusted. <span style="color: var(--accent-light); font-weight: 600;">Powerful — but it does not scale</span> to real apps, real users, real permissions.</p>
      </div>
    </div>
    <div style="display: flex; align-items: center; justify-content: center;">
      <img :src="'/anatomy-talk/04-local-agent.png'" style="max-height: 470px; width: 100%; object-fit: contain;" alt="A local agent working across files on a single machine" />
    </div>
  </div>
</div>

<!--
There is a clue hiding in plain sight. If you have used a coding agent on your laptop recently, you have seen something interesting. The agent knows it is working for you. It can read and write files in the same place. It can build a new tool that uses data from another tool. It can create something personalized on the fly. That is roughly the shape we want. The reason it works is that everything is local and implicitly trusted. The filesystem is the shared substrate. But this does not scale. As soon as you go to the internet — real apps, real users, real permissions — the substrate disappears, and you are back to silos.
-->

---

<!-- SLIDE 5: THE FRAME — ANATOMY OF AN INTEROPERABLE APP -->
<div class="slide-viewport">
  <p class="section-label" style="text-align: center;">The Frame</p>
  <h2 style="text-align: center; margin-bottom: var(--space-xs); font-size: 1.5rem !important;">What would it take to make that shape work on the internet?</h2>
  <p style="text-align: center; font-size: 0.78rem; line-height: 1.5; color: var(--text-secondary); margin: 0 auto var(--space-sm); max-width: 620px;">Four parts. The rest of this talk goes through each one.</p>
  <div style="display: grid; grid-template-columns: 48fr 52fr; gap: var(--space-lg); flex: 1; min-height: 0; align-items: center;">
    <div style="display: flex; align-items: center; justify-content: center;">
      <img :src="'/anatomy-talk/01-stack-hero.png'" style="max-height: 324px; max-width: 100%; object-fit: contain;" alt="The four-part anatomy: identity, place, contract, discovery" />
    </div>
    <div style="display: flex; flex-direction: column; gap: var(--space-xs);">
      <div class="neo-card" style="padding: var(--space-xs) var(--space-md); display: flex; align-items: center; gap: var(--space-md); border-color: rgba(165, 180, 252, 0.25);">
        <span style="font-family: 'JetBrains Mono', monospace; font-size: 0.7rem; font-weight: 700; color: var(--accent-light); width: 1.5rem; flex-shrink: 0;">04</span>
        <div>
          <h3 style="font-size: 0.85rem !important; margin: 0 0 0.05rem 0; color: var(--accent-light) !important;">Discovery</h3>
          <p style="font-size: 0.7rem; margin: 0; color: var(--text-secondary);">How new apps find what is already there</p>
        </div>
      </div>
      <div class="neo-card-yellow" style="padding: var(--space-xs) var(--space-md); display: flex; align-items: center; gap: var(--space-md);">
        <span style="font-family: 'JetBrains Mono', monospace; font-size: 0.7rem; font-weight: 700; color: var(--yellow); width: 1.5rem; flex-shrink: 0;">03</span>
        <div>
          <h3 style="font-size: 0.85rem !important; margin: 0 0 0.05rem 0; color: var(--yellow) !important;">A contract</h3>
          <p style="font-size: 0.7rem; margin: 0; color: var(--text-secondary);">What the app is allowed to do</p>
        </div>
      </div>
      <div class="neo-card-green" style="padding: var(--space-xs) var(--space-md); display: flex; align-items: center; gap: var(--space-md);">
        <span style="font-family: 'JetBrains Mono', monospace; font-size: 0.7rem; font-weight: 700; color: var(--green); width: 1.5rem; flex-shrink: 0;">02</span>
        <div>
          <h3 style="font-size: 0.85rem !important; margin: 0 0 0.05rem 0; color: var(--green) !important;">A place</h3>
          <p style="font-size: 0.7rem; margin: 0; color: var(--text-secondary);">Where the data lives</p>
        </div>
      </div>
      <div class="neo-card-blue" style="padding: var(--space-xs) var(--space-md); display: flex; align-items: center; gap: var(--space-md);">
        <span style="font-family: 'JetBrains Mono', monospace; font-size: 0.7rem; font-weight: 700; color: var(--accent); width: 1.5rem; flex-shrink: 0;">01</span>
        <div>
          <h3 style="font-size: 0.85rem !important; margin: 0 0 0.05rem 0; color: var(--accent-light) !important;">Identity</h3>
          <p style="font-size: 0.7rem; margin: 0; color: var(--text-secondary);">Who is using the app</p>
        </div>
      </div>
    </div>
  </div>
</div>

<!--
So the question I want to spend the rest of this talk on is this: what would we need to make that same shape work on the internet, at scale, with real permissions? I think the answer is four parts. Identity — the app needs to know who is using it. A place — the data needs to live somewhere apps can share. A contract — apps need to declare what they will do, and users need to approve it. And discovery — when a new app shows up, it needs a way to find out what already exists. That is the anatomy. Let's go through each part.
-->

---

<!-- SLIDE 6: PART 1 — IDENTITY (INDIGO) -->
<div class="slide-viewport">
  <div class="split-text-img" style="grid-template-columns: 48fr 52fr;">
    <div>
      <p class="section-label" style="color: var(--accent) !important;">Part 1 of 4 &middot; Identity</p>
      <h2 style="margin-bottom: var(--space-sm); font-size: 1.45rem !important; line-height: 1.25;">One person, many apps.<br/>Not one account per app.</h2>
      <p style="font-size: 0.78rem; line-height: 1.55; color: var(--text-secondary); margin: 0 0 var(--space-md) 0;">
        The app needs to know who is using it without forcing the user into yet another account.
      </p>
      <div style="display: grid; grid-template-columns: 1fr 1fr; gap: var(--space-xs);">
        <div class="neo-card-blue" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.75rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">Passkey-based</p>
        </div>
        <div class="neo-card-blue" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.75rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">Biometric unlock</p>
        </div>
        <div class="neo-card-blue" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.75rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">Cryptographic identity</p>
        </div>
        <div class="neo-card-blue" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.75rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">No blockchain, no wallet</p>
        </div>
      </div>
      <p style="font-size: 0.72rem; line-height: 1.5; color: var(--text-secondary); margin: var(--space-md) 0 0 0;">
        WebAuthn ships in every modern browser. The primitive already exists.
      </p>
    </div>
    <div style="display: flex; align-items: center; justify-content: center;">
      <img :src="'/anatomy-talk/05-identity-passkey.png'" style="max-height: 470px; width: 100%; object-fit: contain;" alt="Passkey-based identity — fingerprint, secure hardware, cryptographic key" />
    </div>
  </div>
</div>

<!--
First, identity. The app needs to know who is using it without forcing the user into yet another account. The good news is the primitive already exists — passkeys. Every modern device has a fingerprint reader or a face camera, and every modern browser speaks WebAuthn. You tap your finger, and a cryptographic key on your device proves who you are. No password. No seed phrase. No wallet extension. No blockchain in the user's face. From the app's perspective, it just gets a stable cryptographic identity. One person, many apps. Not one account per app.
-->

---

<!-- SLIDE 7: PART 2 — A PLACE (GREEN) -->
<div class="slide-viewport">
  <div class="split-img-text" style="grid-template-columns: 52fr 48fr;">
    <div style="display: flex; align-items: center; justify-content: center;">
      <img :src="'/anatomy-talk/06-place-space.png'" style="max-height: 400px; width: 100%; object-fit: contain;" alt="A user-owned space — KV and SQL stores apps share" />
    </div>
    <div>
      <p class="section-label" style="color: var(--green) !important;">Part 2 of 4 &middot; A Place</p>
      <h2 style="margin-bottom: var(--space-sm); font-size: 1.4rem !important; line-height: 1.25;">Interoperability starts with a shared place to put data.</h2>
      <p style="font-size: 0.76rem; line-height: 1.55; color: var(--text-secondary); margin: 0 0 var(--space-sm) 0;">
        Shared identity is not enough. The apps need somewhere shared to put data.
      </p>
      <div style="display: flex; flex-direction: column; gap: var(--space-xs); margin-bottom: var(--space-sm);">
        <div class="neo-card-green" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.75rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">A user-owned space</p>
        </div>
        <div class="neo-card-green" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.75rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">Key-value store &nbsp;<span style="color: var(--text-secondary); font-weight: 400;">+</span>&nbsp; SQL store</p>
        </div>
        <div class="neo-card-green" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.75rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">Apps write into the user's cloud, not their own silo</p>
        </div>
      </div>
      <div class="highlight-box" style="border-left-color: var(--green); border-color: var(--green-border); padding: var(--space-xs) var(--space-md);">
        <p style="font-size: 0.72rem; line-height: 1.5; margin: 0;">Interoperability is not magic API glue. It starts with data living somewhere apps can jointly use it.</p>
      </div>
    </div>
  </div>
</div>

<!--
Shared identity is necessary but it is not enough. If every app still writes into its own private database, you have the same silos with a nicer login screen. You need a shared place. In our model, every user owns a space — think of it as their personal cloud. It has a key-value store and a SQL store. Apps write into the user's space, not into their own backend. This is the move that actually unlocks interoperability. It is not magic API glue between apps. It is data living somewhere apps can jointly read and write — with the user as the owner of the substrate.
-->

---

<!-- SLIDE 8: PART 3 — A CONTRACT (YELLOW) -->
<div class="slide-viewport">
  <div class="split-text-img" style="grid-template-columns: 48fr 52fr;">
    <div>
      <p class="section-label" style="color: var(--yellow) !important;">Part 3 of 4 &middot; A Contract</p>
      <h2 style="margin-bottom: var(--space-sm); font-size: 1.35rem !important; line-height: 1.25;">The app does not ask for the kitchen sink. It declares what it needs.</h2>
      <p style="font-size: 0.74rem; line-height: 1.5; color: var(--text-secondary); margin: 0 0 var(--space-sm) 0;">
        If apps share a place, permissions become much more important.
      </p>
      <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.62rem; font-weight: 600; color: var(--yellow); letter-spacing: 0.12em; text-transform: uppercase; margin: 0 0 var(--space-xs) 0;">A manifest declares</p>
      <div style="display: flex; flex-direction: column; gap: var(--space-xs);">
        <div class="neo-card-yellow" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.74rem; margin: 0; color: var(--text-primary) !important;"><span style="color: var(--yellow); font-weight: 600;">Reads</span> &nbsp;&middot;&nbsp; what data the app touches</p>
        </div>
        <div class="neo-card-yellow" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.74rem; margin: 0; color: var(--text-primary) !important;"><span style="color: var(--yellow); font-weight: 600;">Writes</span> &nbsp;&middot;&nbsp; what data the app produces</p>
        </div>
        <div class="neo-card-yellow" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.74rem; margin: 0; color: var(--text-primary) !important;"><span style="color: var(--yellow); font-weight: 600;">Delegations</span> &nbsp;&middot;&nbsp; what it passes to other apps or agents</p>
        </div>
        <div class="neo-card-yellow" style="padding: var(--space-xs) var(--space-sm);">
          <p style="font-size: 0.74rem; margin: 0; color: var(--text-primary) !important;"><span style="color: var(--yellow); font-weight: 600;">Approvals</span> &nbsp;&middot;&nbsp; what the user must consent to</p>
        </div>
      </div>
    </div>
    <div style="display: flex; align-items: center; justify-content: center;">
      <img :src="'/anatomy-talk/07-contract-manifest.png'" style="max-height: 520px; width: 100%; object-fit: contain;" alt="A manifest declaring scoped reads, writes, delegations, approvals" />
    </div>
  </div>
</div>

<!--
Now if apps share a place, permissions become much more important. You cannot just let any app touch any data. So every app declares a manifest — a contract that says exactly what it will read, what it will write, what it is allowed to delegate to other apps or agents, and what requires explicit user approval. The user sees this manifest before granting access. The server enforces it on every request. The app does not ask for the kitchen sink. It declares what it needs. This is the same idea as scoped OAuth, but the scopes live in the user's space, not in some platform vendor's dashboard.
-->

---

<!-- SLIDE 9: PART 4 — DISCOVERY (LIGHT INDIGO / NEUTRAL ACCENT) -->
<div class="slide-viewport">
  <div class="split-img-text" style="grid-template-columns: 60fr 40fr;">
    <div style="display: flex; align-items: center; justify-content: center;">
      <img :src="'/anatomy-talk/08-discovery-registry.png'" style="max-height: 500px; width: 100%; object-fit: contain;" alt="A registry of apps and their manifests — discoverable shared context" />
    </div>
    <div>
      <p class="section-label" style="color: var(--accent-light) !important;">Part 4 of 4 &middot; Discovery</p>
      <h2 style="margin-bottom: var(--space-sm); font-size: 1.35rem !important; line-height: 1.25;">Every new app enters a world that already has memory.</h2>
      <p style="font-size: 0.74rem; line-height: 1.5; color: var(--text-secondary); margin: 0 0 var(--space-sm) 0;">
        Once apps share a place, the next problem is: how does a new app or agent know what already exists?
      </p>
      <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.62rem; font-weight: 600; color: var(--accent-light); letter-spacing: 0.12em; text-transform: uppercase; margin: 0 0 var(--space-xs) 0;">A registry where</p>
      <div style="display: flex; flex-direction: column; gap: var(--space-xs); margin-bottom: var(--space-sm);">
        <div class="neo-card" style="padding: var(--space-xs) var(--space-sm); border-color: rgba(165, 180, 252, 0.25);">
          <p style="font-size: 0.74rem; margin: 0; color: var(--text-primary) !important;">Apps publish their manifests</p>
        </div>
        <div class="neo-card" style="padding: var(--space-xs) var(--space-sm); border-color: rgba(165, 180, 252, 0.25);">
          <p style="font-size: 0.74rem; margin: 0; color: var(--text-primary) !important;">Agents inspect what apps and data are available</p>
        </div>
        <div class="neo-card" style="padding: var(--space-xs) var(--space-sm); border-color: rgba(165, 180, 252, 0.25);">
          <p style="font-size: 0.74rem; margin: 0; color: var(--text-primary) !important;">New apps inherit context instead of starting cold</p>
        </div>
      </div>
      <p style="font-size: 0.78rem; font-weight: 600; color: var(--accent-light); margin: 0;">Discovery is what makes the system compound.</p>
    </div>
  </div>
</div>

<!--
Last piece. Once apps share a place, you get a new problem — when a new app or a new agent shows up, how does it know what already exists? You need a registry. Apps publish their manifests. Agents can inspect what apps are installed and what data is available. A new app does not start cold; it inherits the context the user has already accumulated. This is what makes the system compound. Every new app makes every previous app more valuable, because the context is shared. Discovery is the part that turns four primitives into an ecosystem.
-->

---

<!-- SLIDE 10: DEMO — THE PARTS ASSEMBLED (placeholder, minimal) -->
<div class="slide-centered">
  <p class="section-label" style="margin-bottom: var(--space-lg);">Demo</p>
  <h1 style="font-size: 2.4rem !important; font-weight: 800 !important; line-height: 1.15 !important; letter-spacing: -0.025em; max-width: 760px; margin: 0 0 var(--space-lg) 0;">The four parts,<br/>working together.</h1>
  <div class="neo-divider" style="width: 60px; height: 2px; margin: 0 auto var(--space-lg);"></div>
  <p style="font-size: 0.95rem; color: var(--text-secondary); letter-spacing: 0.02em; margin: 0;">
    Two apps, one user, no shared backend.
  </p>
</div>

<!--
Let me show you this working. I have two apps — a food tracker and a pain tracker. I have never connected them. They do not know about each other.

First, I sign in to the food tracker with a passkey. I log what I ate this morning. The data lands in my TinyCloud space, not in the food tracker's database.

Now I sign in to the pain tracker — same identity, same passkey. It shows me a manifest: it wants to read my pain logs and write new ones. I approve. I log a pain event from yesterday afternoon.

Now I open my agent. The agent looks at my space. It discovers that I have a food tracker and a pain tracker installed. It sees the data from both. I ask it: is there a pattern? It produces a correlation graph. Or — and this is the part I find wild — it generates a small analysis app on the fly, scoped to just this question, that I can share with my partner.
-->

---

<!-- SLIDE 11: DEMO PUNCHLINE -->
<div class="slide-viewport">
  <p class="section-label" style="text-align: center;">The Punchline</p>
  <h2 style="text-align: center; margin-bottom: var(--space-xs); font-size: 1.3rem !important; line-height: 1.3; max-width: 820px; margin-left: auto; margin-right: auto;">These apps do not know about each other. They know about the user's data.<br/><span style="color: var(--accent-light);">That is enough.</span></h2>
  <div style="display: grid; grid-template-columns: 50fr 50fr; gap: var(--space-lg); flex: 1; min-height: 0; align-items: center; margin-top: var(--space-sm);">
    <div style="display: flex; align-items: center; justify-content: center;">
      <img :src="'/anatomy-talk/09-emergent-app.png'" style="max-height: 460px; width: 100%; object-fit: contain;" alt="An emergent third app composed from two unconnected sources" />
    </div>
    <div style="display: flex; flex-direction: column; gap: var(--space-xs);">
      <div class="neo-card" style="padding: var(--space-xs) var(--space-md); border-color: rgba(255, 255, 255, 0.1);">
        <p style="font-size: 0.74rem; margin: 0; color: var(--text-primary) !important;">The food tracker never called the pain tracker.</p>
      </div>
      <div class="neo-card" style="padding: var(--space-xs) var(--space-md); border-color: rgba(255, 255, 255, 0.1);">
        <p style="font-size: 0.74rem; margin: 0; color: var(--text-primary) !important;">The pain tracker never called the food tracker.</p>
      </div>
      <div class="neo-card" style="padding: var(--space-xs) var(--space-md); border-color: rgba(255, 255, 255, 0.1);">
        <p style="font-size: 0.74rem; margin: 0; color: var(--text-primary) !important;">The agent never called either of them.</p>
      </div>
      <div class="highlight-box" style="padding: var(--space-sm) var(--space-md); margin-top: var(--space-xs);">
        <p style="font-size: 0.8rem; font-weight: 600; margin: 0; line-height: 1.45;">The shared substrate did the work.</p>
        <p style="font-size: 0.68rem; color: var(--text-secondary); margin: 0.25rem 0 0 0; line-height: 1.45;">Composability without integrations. No partnerships. No API deals. No platform.</p>
      </div>
    </div>
  </div>
</div>

<!--
Here is the part I want to underline. These apps do not know about each other. The food tracker has no integration with the pain tracker. The pain tracker has no integration with the food tracker. The agent has no special connector for either of them. They all just know about the user's data, in the user's space, under the user's identity. That is enough. This is what the four parts buy you — composability without integrations. Every new app that lands in the user's space immediately becomes useful to every other app and every agent. No partnerships. No API deals. No platform.
-->

---

<!-- SLIDE 12: THE BIGGER BET -->
<div class="slide-viewport">
  <div class="split-text-img" style="grid-template-columns: 48fr 52fr;">
    <div>
      <p class="section-label">The Bigger Bet</p>
      <h2 style="margin-bottom: var(--space-sm); font-size: 1.4rem !important; line-height: 1.25;">If users own the data, apps compete on quality instead of captivity.</h2>
      <p style="font-size: 0.78rem; line-height: 1.55; color: var(--text-secondary); margin: 0 0 var(--space-md) 0;">
        App code is getting cheaper. Agents can clone or generate useful software quickly.
      </p>
      <div style="display: grid; grid-template-columns: 1fr 1fr; gap: var(--space-sm); margin-bottom: var(--space-md);">
        <div class="neo-card" style="padding: var(--space-sm) var(--space-md); border-color: rgba(255, 255, 255, 0.08);">
          <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.55rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.12em; color: var(--text-muted); margin: 0 0 0.25rem 0;">Commoditizing</p>
          <p style="font-size: 0.82rem; font-weight: 600; margin: 0; color: var(--text-primary) !important;">The app shell</p>
        </div>
        <div class="neo-card-blue" style="padding: var(--space-sm) var(--space-md);">
          <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.55rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.12em; color: var(--accent); margin: 0 0 0.25rem 0;">Appreciating</p>
          <p style="font-size: 0.82rem; font-weight: 600; margin: 0; color: var(--accent-light) !important;">The user's context</p>
        </div>
      </div>
      <p style="font-size: 0.82rem; font-weight: 600; color: var(--accent-light); line-height: 1.5; margin: 0;">
        The durable asset is not the app shell. It is the user's context.
      </p>
    </div>
    <div style="display: flex; align-items: center; justify-content: center;">
      <img :src="'/anatomy-talk/10-bigger-bet.png'" style="max-height: 470px; width: 100%; object-fit: contain;" alt="The user's context as the appreciating asset across many apps" />
    </div>
  </div>
</div>

<!--
I want to zoom out for a second. There is a bigger bet underneath all of this. App code is getting cheaper every month. Agents can already clone a useful piece of software in an afternoon. They can generate a small app on demand. So if the app shell is getting commoditized, what is actually durable? It is not the code. It is the user's context — the data, the relationships, the history, the preferences. That is the asset that appreciates as AI gets more powerful. If users own that context, apps have to compete on quality instead of competing on captivity. That is the world I want to live in.
-->

---

<!-- SLIDE 13: CTA — TINYCLOUD MAPPING -->
<div class="slide-viewport">
  <p class="section-label">Where We Come In</p>
  <h2 style="margin-bottom: var(--space-xs); font-size: 1.5rem !important; line-height: 1.25;">That is what we are building at TinyCloud.</h2>
  <p style="font-size: 0.85rem; line-height: 1.55; color: var(--text-secondary); margin: 0 0 var(--space-md) 0;">
    Identity, storage, permissions, and discovery for interoperable apps.
  </p>
  <div style="display: flex; flex-direction: column; gap: var(--space-xs);">
    <div style="display: grid; grid-template-columns: 8rem 1fr 12rem; gap: var(--space-md); align-items: center; padding: 0.55rem var(--space-md); background: var(--bg-surface); border: 1px solid var(--accent-border); border-left: 3px solid var(--accent); border-radius: 8px;">
      <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.65rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.14em; color: var(--accent); margin: 0;">Identity</p>
      <p style="font-size: 0.78rem; margin: 0; color: var(--text-primary) !important;">Passkey-based, biometric, no wallet</p>
      <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.78rem; font-weight: 600; color: var(--accent-light); margin: 0; text-align: right;">OpenKey</p>
    </div>
    <div style="display: grid; grid-template-columns: 8rem 1fr 12rem; gap: var(--space-md); align-items: center; padding: 0.55rem var(--space-md); background: var(--bg-surface); border: 1px solid var(--green-border); border-left: 3px solid var(--green); border-radius: 8px;">
      <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.65rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.14em; color: var(--green); margin: 0;">A place</p>
      <p style="font-size: 0.78rem; margin: 0; color: var(--text-primary) !important;">User-owned space &middot; KV + SQL</p>
      <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.78rem; font-weight: 600; color: var(--green); margin: 0; text-align: right;">TinyCloud spaces</p>
    </div>
    <div style="display: grid; grid-template-columns: 8rem 1fr 12rem; gap: var(--space-md); align-items: center; padding: 0.55rem var(--space-md); background: var(--bg-surface); border: 1px solid var(--yellow-border); border-left: 3px solid var(--yellow); border-radius: 8px;">
      <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.65rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.14em; color: var(--yellow); margin: 0;">A contract</p>
      <p style="font-size: 0.78rem; margin: 0; color: var(--text-primary) !important;">Scoped, time-bound, revocable</p>
      <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.78rem; font-weight: 600; color: var(--yellow); margin: 0; text-align: right;">Delegations</p>
    </div>
    <div style="display: grid; grid-template-columns: 8rem 1fr 12rem; gap: var(--space-md); align-items: center; padding: 0.55rem var(--space-md); background: var(--bg-surface); border: 1px solid rgba(165, 180, 252, 0.25); border-left: 3px solid var(--accent-light); border-radius: 8px;">
      <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.65rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.14em; color: var(--accent-light); margin: 0;">Discovery</p>
      <p style="font-size: 0.78rem; margin: 0; color: var(--text-primary) !important;">App and agent registry</p>
      <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.78rem; font-weight: 600; color: var(--accent-light); margin: 0; text-align: right;">Registry</p>
    </div>
  </div>
  <p style="font-size: 0.7rem; color: var(--text-secondary); line-height: 1.5; margin: var(--space-md) 0 0 0; text-align: center;">
    We did not invent the parts. We assembled them in a shape that lets apps interoperate without giving up user ownership.
  </p>
</div>

<!--
That is what we are building at TinyCloud. Identity through OpenKey — passkey-based, no wallet. A place through TinyCloud spaces — every user owns one, with a key-value store and a SQL store. A contract through scoped, time-bound, revocable delegations — cryptographically enforced, not policy-enforced. And a registry so new apps and agents can find what is already there. The same four parts I just walked through. We did not invent the parts. We assembled them in a shape that lets apps interoperate without giving up user ownership.
-->

---

<!-- SLIDE 14: CONTACT -->
<div class="slide-centered">
  <p style="font-family: 'JetBrains Mono', monospace; font-size: 0.62rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.22em; color: var(--accent); margin-bottom: var(--space-lg);">Thank You</p>
  <h1 style="font-size: 1.7rem !important; font-weight: 700 !important; line-height: 1.3 !important; letter-spacing: -0.02em; max-width: 760px; margin: 0 0 var(--space-lg) 0;">If you are building apps where users should own their data,<br/><span style="color: var(--accent-light);">come talk to me.</span></h1>
  <div class="neo-divider" style="width: 60px; height: 2px; margin: 0 auto var(--space-lg);"></div>
  <p style="font-size: 1.05rem; color: var(--text-primary); letter-spacing: 0.04em; margin: 0 0 0.4rem 0; font-weight: 500;">
    sam@tinycloud.xyz
  </p>
  <p style="font-size: 0.85rem; color: var(--text-secondary); letter-spacing: 0.04em; margin: 0;">
    tinycloud.xyz
  </p>
</div>

<!--
That is the talk. If you are building apps where users should own their data — health, finance, education, anything regulated, anything personal — come talk to me. My email is sam@tinycloud.xyz. The site is tinycloud.xyz. Thank you.
-->
