# Cisco AI Infrastructure: 10-Minute Talk Track

Updated to match the revised deck in `index.html` (title card + five content slides).

## How to use this

The spoken script is about 1,225 words, which lands around 9:40 at a normal speaking pace and leaves about 20 seconds of buffer. Times are targets, not hard stops.

- **[CLICK]** reveals the next build on the same slide.
- **[NEXT SLIDE]** moves to the next slide.
- Slide 3's first click builds the whole AI POD on its own. Let it finish before talking.
- There are **11 clicks** in total: none on the title card, two on slide 1, one on slide 2, three on slide 3, two on slide 4 and three on slide 5.
- Keyboard: arrow keys, space or a clicker to advance, `F` for full screen, `Home` to jump back to the title card. Don't advance with the mouse, because a click on the left half of the screen goes back a step.
- Jumping around in Q&A: the number keys count the title card, so press the slide number plus one (press 3 to get to slide 2 / 5, the GPU demo).
- Before the day, ask the coordinator whether a title slide counts toward the five-slide limit. If it does, open `index.html#2` (or press the right arrow once before you start sharing) and say the title card's intro line over slide 1 before its first click. Slide 1 then runs 0:00 to 2:05.
- The deck no longer needs the internet. The Inter font is built into the file, so it looks the same on any laptop.

---

## Title card: Cisco AI Infrastructure (0:00 to 0:20)

*[Have this up while everyone settles in. It has no builds, so nothing appears until you advance.]*

Hi everyone, I'm Ethan. Today I'm going to teach you Cisco AI Infrastructure: what problem it solves, how it actually works, how it fits with what a company already has, and why it matters right now.

**[NEXT SLIDE]**

---

## Slide 1: Running AI where your data lives (0:20 to 2:05)

Every company wants to use AI on its own data. The first big question isn't which GPU to buy. It's where the AI should actually run. For a lot of companies, the answer is their own infrastructure, and there are three main reasons why.

**[CLICK: the three cards build in]**

First is control. Your models learn from your proprietary data, things like customer records, product designs, or internal documents. When it runs in-house, you decide who can touch that data, where it lives, and how it gets used.

Second is compliance. Security and data sovereignty rules can dictate where data is allowed to live. In industries like healthcare, finance, or government, some of that data simply can't go to a public cloud.

Third is cost at steady use. GPUs are expensive, and when they run all day, every day, a predictable cost can make more sense than paying by the hour. That doesn't mean on-prem is always cheaper, but for steady workloads it becomes part of the decision.

**[CLICK: the amber warning bar appears]**

But here's the catch. An AI cluster isn't just a bigger version of the data center a company already has. The GPUs talk to each other nonstop, the racks need a lot more power and cooling, and the network is a completely different kind of fabric. Most IT teams have never built one.

So what actually makes AI infrastructure different? It starts with the network.

**[NEXT SLIDE]**

---

## Slide 2: The GPUs wait on the network (2:05 to 4:25)

This is a simplified simulation of an AI cluster, and the numbers are illustrative. Each numbered square is a GPU, and the moving dots are data traffic between them.

These GPUs aren't eight separate servers doing eight separate jobs. It's one training job split across all eight. After every step, they swap results with each other, all at once, in huge bursts. Once that swap finishes, the model moves forward one step.

That's the Output box, right beside the ring. Every flash is a finished step. Right now we're getting about 50 steps a minute, and the GPUs are busy about 90% of the time. That swap is why Cisco says data movement is the key to efficient AI compute. The network becomes part of the compute itself.

Now watch what happens when one link has a problem.

**[CLICK: the link between GPU 2 and GPU 3 jams]**

*[Pause two seconds. Let them see it change.]*

Now the link between GPU 2 and GPU 3 is congested. You can see the data jammed up on that red link. GPU 2 and GPU 3 can't finish their swap, and since every GPU has to finish before the next step can start, the other six sit there waiting in orange. Some data still trickles around the ring, but nowhere near as much. It's like a group project where everyone waits on the slowest person.

Look at the output. We drop from 50 steps a minute to 21. Utilization falls under 40%, and the same job takes more than twice as long.

So the point isn't that the link is slow. The point is that a very expensive compute system is waiting on the network. That's why Cisco's AI networking focuses on low latency, lossless Ethernet, and handling congestion, not just bigger pipes.

So how does Cisco actually solve this?

**[NEXT SLIDE]**

---

## Slide 3: Cisco makes it one validated system (4:25 to 6:35)

**[CLICK as soon as the slide appears: the Cisco AI POD builds in on its own. Let it finish before talking.]**

This is a Cisco AI POD. It's a prevalidated building block where every piece is designed and tested to work together. The solid tags are pieces Cisco builds, and the outlined tags are partner pieces Cisco has validated.

The GPU compute is Cisco UCS servers with NVIDIA GPUs inside. The highlighted piece, the network, is the fix for the jam you just saw. Cisco's Nexus switches don't drop data when they get busy, they tell the senders to slow down before a jam forms, and they spread traffic across more than one path so no single link holds everyone up. Storage comes from certified partners, so you're not locked into one box. The AI software supports NVIDIA AI Enterprise and Red Hat OpenShift. And management is Cisco too, with Intersight for the servers and Nexus Dashboard for the network. The whole POD follows a Cisco Validated Design, which is a tested blueprint.

**[CLICK: the Secure AI Factory frame wraps around it]**

Now if we zoom out, Cisco wraps the whole POD in three more pieces. Security is Cisco AI Defense, which protects the AI models and apps running on it. Observability is Splunk, which is part of Cisco now. And support is one point of contact through Cisco's services team. Together, this is the Cisco Secure AI Factory with NVIDIA.

**[CLICK: the takeaway appears on the right]**

So you're not buying GPUs, switches, and storage separately. You're buying AI capacity that actually gets work done. Cisco builds the servers, the network, and the management, and validates the partner pieces, so your team doesn't have to be the integrator.

The next question you're probably asking is whether you have to tear out what you already have. You don't.

**[NEXT SLIDE]**

---

## Slide 4: Add AI. Don't rebuild everything. (6:35 to 7:55)

This is your data center today: your apps and data, your network, and the team and tools that run it. None of that goes away.

**[CLICK: the AI POD and the Ethernet link appear]**

The Cisco AI POD gets added right next to it. Cisco's approach is to modernize in steps, not rip and replace. The two connect over Ethernet, which is the same kind of networking your team already runs, so a lot of your tools and skills carry over. Cisco then tunes it for the kind of AI traffic we just saw jam.

**[CLICK: the extra PODs and management options appear]**

You also don't have to build for the biggest version on day one. You start with the size you need now and add PODs as demand grows. The one thing to check first is power and cooling, since that often decides how big the first POD can be.

And you get to choose how you run it: on-prem with Nexus Dashboard, or from the cloud with Nexus Hyperfabric. Either way, the hardware stays on-prem.

So that's the solution. Now, why does this matter right now?

**[NEXT SLIDE]**

---

## Slide 5: Everyone is rushing into AI. Few are ready. (7:55 to 9:40)

Everyone is rushing into AI right now, and the numbers show it.

**[CLICK: the three stats build in, then the "Idle GPUs" line]**

In a 2026 survey Cisco ran of 2,500 CEOs, 65% said they worry they're underinvesting in AI, up from 53% the year before. At the same time, in a survey Omdia ran for Cisco, 67% of infrastructure leaders expect AI traffic to max out their network within the next year. And Cisco's 2025 AI Readiness Index found only 22% of organizations rate their network as optimal for AI workloads.

So companies want AI badly, but most of their infrastructure isn't ready for it. And GPUs are too expensive to leave sitting idle. The network decides whether they're actually working.

**[CLICK: the quote appears]**

During my internship, our intern class had a Webex with Patrick Morrissey, who leads Americas Sales at Cisco, and something he said has stuck with me. In a gold rush, the people who got rich weren't the miners. It was the ones selling the shovels.

That's how I see AI. Everyone is racing to build models and find the gold. NVIDIA makes the most famous shovel, the GPU. But like we saw earlier, a GPU waiting on the network doesn't dig, and every one of these projects needs the network, servers, and security that keep it working.

**[CLICK: the closing line appears]**

AI is the gold rush, and Cisco builds the shovels.

Thank you. I'm happy to take any questions.

---

## If running long

These four cuts save about 15 to 20 seconds without losing the story:

1. Slide 2: "Some data still trickles around the ring, but nowhere near as much."
2. Slide 3: "The whole POD follows a Cisco Validated Design, which is a tested blueprint."
3. Slide 4: "Either way, the hardware stays on-prem."
4. Slide 5: "up from 53% the year before"

Keep the healthcare, finance, and government example on slide 1. It's the concrete picture a non-expert needs.

---

## Q&A backup

**About the demo (slide 2)**

- The numbers are simulated and illustrative, not measured, but they hang together. A step takes 1.2 seconds when healthy and 2.9 seconds when jammed. That's 50 steps a minute versus about 20.7, which the screen rounds to 21. The same amount of work then takes 4.0 × 50 ÷ 20.7, about 9.7 hours, and the GPUs go from about 90% busy to under 40%.
- The ring is how the GPUs pass results to each other, not how they're cabled. Physically every GPU connects through switches, and a jam happens when a lot of traffic hits the same switch port. Inside one server, eight GPUs usually talk over NVLink. The Ethernet AI network matters once a job spans many servers, which is where the slowest-link effect really bites.
- What they swap is gradients, and the operation is called an all-reduce. Not every training method syncs after every step, but this kind of synchronized training is common.

**How Cisco handles the jam (slide 3)**

- "Doesn't drop data" is lossless Ethernet using PFC, which pauses traffic instead of dropping it. "Tells senders to slow down" is ECN. Strictly, the switch marks the packets and the receiving network card tells the sender to slow down, ideally before the switch ever has to pause anything. The GPU traffic itself runs as RoCEv2, which is RDMA over Ethernet.
- "Spreads traffic across paths" is dynamic load balancing. Today's Nexus 9000 switches can do it for RoCE traffic in AI training networks. Cisco's newest switch chip, Silicon One G300 (announced February 2026, 102.4 Tbps), goes further with what Cisco calls Intelligent Collective Networking: a shared buffer, path-based load balancing and telemetry.
- If asked to put it in one line: lossless Ethernet with PFC and ECN, plus smarter load balancing as clusters get bigger.

**Competitors**

- **NVIDIA InfiniBand:** It's fast, but it's a separate specialist network with its own skill set. Cisco's bet is standard Ethernet tuned for AI, which most teams already know how to run.
- **NVIDIA Spectrum-X:** It's not either/or. Cisco's Nexus line includes switches built on Cisco Silicon One and switches built on NVIDIA Spectrum-X silicon. Cisco's difference is the validated design, the management, the security, and the support around it.
- **Arista:** A strong Ethernet vendor. Cisco's difference is the whole validated stack: UCS compute, the network, AI Defense, Splunk, and one support relationship.
- **"Why not just buy from NVIDIA?"** NVIDIA makes the GPUs. Cisco makes them work as one supported system inside an enterprise data center the customer already runs.

**Where it breaks down**

- Facilities. GPU racks need far more power and cooling than normal racks, and that can limit how big the first POD can be.
- Not everything is generally available. Cisco marks some AI networking and AgenticOps features as in development or "when and if available," so I'd confirm what's orderable before promising anything.
- Pricing isn't public. It depends on the configuration and subscription tiers, so I wouldn't make cost claims without a sizing exercise.
- Compliance certifications are product specific. "Secure" isn't the same as a SOC 2, HIPAA or FedRAMP certification, so I'd pull the current documentation for the customer's industry.
- Lossless isn't free. If PFC pauses too much, congestion can spread backward through the network (a "pause storm"). That's why Cisco pairs it with ECN so senders slow down early, Nexus switches have a PFC watchdog to stop a pause storm, and newer chips lean more on smarter load balancing.

**Where it's headed next**

- On August 25, 2026, Cisco announced a rack-scale version of Secure AI Factory with Supermicro compute and an NVIDIA Cloud Partner compliant design, aimed at neoclouds and sovereign clouds. The Supermicro offerings start this month (October 2026), so I'd check what's orderable today.
- Bigger picture, the network is turning into part of the computer. That's why Cisco keeps pushing faster Ethernet, from 400G up to 1.6T optics, and smarter congestion handling.

**Facts worth having ready**

- AI POD sizes scale in steps, for example 32, 64 and 128 GPUs, and can keep growing from there.
- Certified storage partners: VAST Data, NetApp (FlexPod), Everpure (FlashStack), Hitachi Vantara and Nutanix. Everpure is Pure Storage's new name since February 2026, so either name works if someone asks.
- "So what does Cisco actually build?" In the AI POD I showed, the servers are Cisco UCS, plus the network, the management, the security and the support. For the new rack-scale option, Cisco validates and sells Supermicro servers, which is the same validate-the-partner model as storage.
- The slide 3 footnote, "Options aligned with NVIDIA's Enterprise Reference Architecture": that's NVIDIA's published blueprint for enterprise GPU clusters. Cisco wasn't on NVIDIA's first list in late 2024, said in February 2025 that it would build these designs, and NVIDIA's docs now list Cisco designs like the AI POD and Hyperfabric AI. "Aligned" is the careful word, since NVIDIA endorses specific configurations, not every possible POD.
- Management: Intersight for compute, Nexus Dashboard for on-prem networking, Nexus Hyperfabric for cloud-managed networking. With Hyperfabric the hardware is still on-prem. Only the controller is in Cisco's cloud.
- Security: AI Defense protects the AI models and apps. Hybrid Mesh Firewall enforces policy across the infrastructure. Splunk handles observability and security analytics.
- Survey details: the CEO study covered 2,500 CEOs in 23 countries (data from January 2026). The Omdia study covered more than 1,200 infrastructure leaders (Cisco blog, August 18, 2026). The 2025 AI Readiness Index covered more than 8,000 leaders in 30 markets, and 81% of the most AI-ready companies rate their network as optimal, compared with 22% overall.
- The Morrissey quote is my paraphrase from that meeting, not his exact words. The line itself is an old saying from the California Gold Rush, where Sam Brannan became California's first millionaire selling picks, shovels and pans to miners. Patrick's title is SVP, Americas Sales, per Cisco's newsroom bio. An older Cisco page still lists his previous role, SVP of Global Specialists.

**How I used AI, and what it got wrong**

*[Only claim what you've checked yourself. Before the interview, open the sources for the first three items so you can talk about them first-hand.]*

I used AI to research Cisco's AI pages and build a research brief, then to draft the deck, and then to fact-check the deck against Cisco's own sources. The three mistakes worth talking about:

1. **The wrong year on a stat.** The 22% figure was labeled "Cisco AI Readiness Index, 2026." It's actually from the 2025 Index. My own research notes had warned about this exact mix-up, probably because Cisco's 2026 CEO study sits on the same Readiness Index pages.
2. **An overclaim.** The draft said Cisco does "almost every piece" itself. The GPUs inside Cisco's servers are NVIDIA's, and the AI software and storage are partner pieces, which the outlined tags show. Now I say exactly what Cisco builds.
3. **A quote that wasn't really a quote.** "AI performance is often limited by data movement, not raw compute" sounded like Cisco, but I couldn't find it on any Cisco page. I switched to Cisco's real wording from the Silicon One G300 launch: data movement is the key to efficient AI compute, and the network becomes part of the compute itself.

Smaller ones, if there's time: Cisco Validated Designs were listed as management software when they're really tested blueprints, and "Nothing gets ripped out" was stronger than Cisco's own phrase, "no rip-and-replace." An AI design review also flagged layout problems, like text being shrunk to fit, and I checked each one on screen.

**One AI suggestion I didn't take.** A review said the demo's 9.7 hours should be 9.5, because 4.0 × 50 ÷ 21 is 9.5. But the simulation actually runs at 20.7 steps a minute and only shows it rounded to 21, so 9.7 was right and I kept it. Checking the AI's corrections matters as much as checking its first draft.

---

## What changed in the deck

- **New title card** with the four questions from the brief. It has no page number, so the content slides still read 1/5 to 5/5. The brief says a maximum of five slides, so check with the coordinator first. The "How to use this" section explains how to skip it.
- **Small section labels** above each title (01 The problem, 02 How it works, 03 How it fits, 04 Why now) so the assessors can see each question being answered.
- **Slide 1:** the title no longer leaves "lives" alone on line two, and the warning bar now looks like a warning, with "Most teams have never built one." on its own amber line. The network card in the corner also prints properly now (it used to print as an empty box).
- **Slide 2:** "Simulated, illustrative numbers" shows from the start, the output number turns amber when the link jams like the other two numbers do, the numbers are consistent with each other, and the scoreboard uses the same font as the rest of the deck (the arrow in "GPU 2 to 3" is now a word so it looks the same on every laptop).
- **Slide 3:** "Red Hat OpenShift," the takeaway says Cisco "validates the partner pieces," the AI network tile now says "built to avoid jams" to connect back to slide 2, management is Intersight and Nexus Dashboard, the legend appears before the tags it explains, the bottom row lines up with the POD, the tiles are no longer shrunk, and the takeaway gets its own click.
- **Slide 4:** the growth column now shows two extra AI PODs with "Add PODs as demand grows," the rows now fill the two big boxes, and the captions read "Familiar tools and skills carry over" and "No rip-and-replace."
- **Slide 5:** the title states the takeaway ("Few are ready."), the 22% stat is labeled 2025, the 67% card is back to full size, "Idle GPUs" is amber to echo slide 2, the quote breaks on the natural pause, and the closing line is bigger and gets its own click.

---

## Sources

- Cisco, How CEOs see AI in 2026 (2,500 CEOs, 65%): https://www.cisco.com/c/m/en_us/solutions/ai/readiness-index/how-ceos-see-ai-in-2026.html
- Cisco blog, Cloud or On-Premises? New Report Shows Why AI Workload Placement Matters (Omdia, 67%), Aug 18, 2026: https://blogs.cisco.com/news/cloud-or-on-premises-new-report-shows-why-ai-workload-placement-matters
- Cisco AI Readiness Index 2025, infrastructure report (22% vs 81%): https://www.cisco.com/c/dam/m/en_us/solutions/ai/readiness-index/2025-m12/documents/Cisco-AI-Readiness-Index_Infrastructure-Focus.pdf
- Cisco AI PODs data sheet: https://www.cisco.com/c/en/us/products/collateral/servers-unified-computing/ucs-x-series-modular-system/ai-pods-ds.html
- Cisco Secure AI Factory with NVIDIA FAQ: https://www.cisco.com/c/en/us/solutions/collateral/artificial-intelligence/secure-ai-factory-nvidia-faq.html
- Cisco Secure AI Factory with NVIDIA: https://www.cisco.com/site/us/en/solutions/artificial-intelligence/secure-ai-factory/index.html
- Cisco newsroom, Silicon One G300 announcement, Feb 2026: https://newsroom.cisco.com/c/r/newsroom/en/us/a/y2026/m02/cisco-announces-new-silicon-one-g300.html
- Cisco G300 Intelligent Collective Networking white paper: https://www.cisco.com/c/en/us/solutions/collateral/silicon-one/g300-wp.html
- Cisco Silicon One AI/ML white paper (tail latency, slowest path): https://www.cisco.com/c/en/us/solutions/collateral/silicon-one/evolve-ai-ml-network-silicon-one.html
- Cisco Data Center Networking Blueprint for AI/ML (RoCEv2, PFC, ECN): https://www.cisco.com/c/en/us/td/docs/dcn/whitepapers/cisco-data-center-networking-blueprint-for-ai-ml-applications.html
- Cisco Nexus Hyperfabric AI data sheet: https://www.cisco.com/c/en/us/products/collateral/data-center-networking/nexus-hyperfabric/nexus-hyperfabric-ai-ds.html
- Cisco AI POD for training design guide (familiar tools, scale units): https://www.cisco.com/c/en/us/td/docs/unified_computing/ucs/UCS_CVDs/cisco_ai_pod_for_training_design.html
- Cisco newsroom, Secure AI Factory rack-scale expansion, Aug 2026: https://newsroom.cisco.com/c/r/newsroom/en/us/a/y2026/m08/cisco-secure-ai-factory-nvidia-rack-scale.html
- Cisco newsroom, Patrick Morrissey executive bio: https://newsroom.cisco.com/c/r/newsroom/en/us/executives/patrick-morrissey.html
- Cisco Nexus 9000 AI networking white paper (ECN first, PFC as a fail-safe): https://www.cisco.com/c/en/us/products/collateral/networking/cloud-networking-switches/nexus-9000-switches/nexus-9000-ai-networking-wp.html
- NVIDIA Enterprise Reference Architectures (lists Cisco designs): https://docs.nvidia.com/enterprise-reference-architectures/index.html
- DCD, Pure Storage rebrands to Everpure: https://www.datacenterdynamics.com/en/news/pure-storage-rebrands-to-everpure-announces-1touch-acquisition/
