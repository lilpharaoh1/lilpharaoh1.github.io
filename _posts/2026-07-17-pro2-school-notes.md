---
layout: post
title: Notes from the pro² Device Prototyping Summer School
date: 2026-07-17
description: PCBs, manufacturing, compliance, and a few good tricks
# tags: # notes
---

Below are my notes from the [pro² Device Prototyping Summer School](https://prosquared.org/event/device-prototyping-summer-school-2026/) (kindly edited by Claude). The notes are rough, so if you would like clarification on anything, please reach out. Or better yet, reach out to the speakers themselves or the [pro² network](https://prosquared.org/join/). Enjoy!

***

### Intro talk

**Goal of the school:** teaching how to scale from the first unit, to tens, to thousands of units.

- MazeMap → 3D map of the campus.
- pro² network.
- "Isotyping" → making tens/hundreds of things (as opposed to one-off prototyping).
- Need for tools that support this, rather than singular prototyping.

### Animatronics — Paul Dietz

Storytelling with robotics.

- First animatronic → Lincoln robot at the 1964 World's Fair → interesting.
- Actuated skeletons made with aluminium — bendable, workable with hand tools.
- Ginger Alford → SIGGRAPH.

Questions to self:
- Is this a good way to teach history? Supposedly yes — but is that because of engagement, or something specific about animatronics? (Compare: the chemistry course at ASU. Why is it successful? What overlaps?)

Hardware / tools mentioned:
- **Zip Servo** → cheap linear actuator made from a zip tie.
- **PupCon** → controller he designed for real-time puppet control. Going from concept to PCB — how?
- **Audio2Servo** → two-person version of this board.
- micro:bit → animatronics.

More questions:
- How does he create all these PCBs? What's his pipeline? (JLCPCB.) What do you have to do to go from idea to JLCPCB?
- Bringing animatronics to an industrial level / assistive robotics settings?
- Animal characters → uncanny valley, small.
- With AI, people can judge how "true"/lifelike these robots are → reframe this as a positive learning experience.
- Wonder how they evaluated whether their workshops were any good? Are the animatronics a *medium* for X, or the X itself?

### PCB Workshop

- **Through-hole** → pins and leads come off the components → older style (e.g. resistors). More robust literally because the components are bigger and sturdier → can hand to people to test and throw around.
- **Surface mount** → legs just sit on the PCB (easier to wire things). Mounted on one side only.
- **Tracking gap** → space between tracks (copper lines).
- Lower-voltage components on surface-mount PCBs, since you have a smaller tracking gap and less insulation between tracks.
- Some boards use a mix of track sizes so you can carry different currents for different components.
- **Vias** → which layer the tracks sit on. Often four-layer PCBs (four sets of tracks). Lay copper for each layer, glue them together, then drill holes for the vias.
- PCB and components are indexed on the board and also on the BOM (bill of materials).
- **FR4** → industry-standard PCB material. FR = fire retardant. Pins and wires are underneath the board.
- **Aluminium boards** → better thermal characteristics, lose heat faster → used in lightbulbs, for example.
- **Flexible PCBs** exist too.
- **Hybrids** → FR PCBs for the robust parts, flexible PCBs to connect things where it needs to bend.
- Dark green colour → solder resist.
- **Silkscreen layer** → for designs/labels printed on the PCB.
- You can get a stencil to paste on liquid solder (often free or very cheap). Place components, then put on a hot plate to melt all the solder.
- Workflow: use a PCB editor to make the design, then send the output to JLCPCB for whatever you need.

#### Not Enough Pins (Part 1) — Paul Dietz

*(Slides under Paul Dietz's GitHub → pro2.)*

- **Forward voltage** → voltage needed to switch things on (e.g. for a diode). Recall the I–V graph.
- You can't drive something like an LED with a high continuous current (it'll fry), but you can pulse it so the average current stays near the limit set by heat.
- Recall I/O diagrams for inputs and outputs.
- See "3 Easy Ways of Controlling an LED."
- Fun 2-LED / 2-pin trick (flicker fusion frequency). The resistor has to be half the resistance, since you need twice the current.
- **Charlieplexing** → problem: the wrong things light up because there are multiple current paths. Solution: arrange the LEDs in a certain way → see Wikipedia for layouts.

#### Too Many Switches (Part 2) — Paul Dietz

- Recall the format of a switch → with a resistor and an input pin.
- You can do a switch matrix, like in the LED part. Problem: **ghosting**.
- Two-key rollover, N-key rollover. Solution: put a diode with each switch.
- Consider whether you need to press multiple keys at once. If not, you can use charlieplexing (fundamentally one-key rollover). Add diodes to get more (two switches per position).
- Trick for cheap keyboards: replace the diodes with resistors.

### Recap

- Remember to put a question in Menti for tomorrow.

### Long Tail of Hardware — Steve Hodges

i.e. low-volume products → think unconventional medical devices, small user bases, etc.

- **Zipf's law** → Zipfian distribution (halving every unit). Follows an inverse power law.
- Chris Anderson (2006), *The Long Tail: Why the Future of Business Is Selling Less of More*. Recall the gap of unpopular demand → why the lines diverge → lack of availability + access. Recall how Netflix and YouTube unlocked the long tail.
- Funny idea → SenseCam consolidating/exercising memory for patients.
- *(Personal to-do)* Share notes with Do Sheal — particularly the isotyping stuff applied to board games.

### Building an Electronics Manufacturing Business on a Shoestring — Simon Monk (MonkMakes)

- Low-temperature solder paste with bismuth → much easier to work with when using a stencil and squeegee. Much lower melting point → you can get away with a domestic toaster oven.
- Suggestion: if making many, get an automated tester that gives a simple yes/no. Reduce test times → do larger batches. They sometimes build in "sacrificial traces" — a wire that tests everything (like traffic lights in a railway set).
- Retailers will want to see a datasheet, a letter of conformance, and instructions (depending on the device).
- **PCBA** (PCB assembly) → they place the components on the boards for you. Country of origin is China → bad if selling to the US, for example. Better for bigger batches.
- Pick-and-place notes: you have a feeder on the machine, so you want a smaller set of *distinct* components — consider whether you can consolidate (do you need 150 kΩ, or will 100 kΩ be fine?).
- **LCSC** for components → Chinese, but much, much cheaper.
- Suggestion: solar power and batteries for energy → can save costs.
- If selling to retailers, they do the branding, so you can often use repackaged materials.

Compliance / legal:
- **Tariffs** → you can only label the country of origin as the one you're in if you make a *transformative / substantive change*.
- **UKCA** → if EU CE-marked, then UKCA by default (does this work the other way around?).
- Restrictions on hazardous materials → watch for things like dyes in wires and manufacturers sneaking lead into things.
- Electromagnetic compliance → buy a near-field probe to check. If you say it's compliant, it's up to someone else to challenge you.
- Xbox controller testing example → sometimes it's much cheaper to have good testing than perfect production. Sometimes they add extra tests for the units that fail, because those units might actually be fine or fixable — but you only know that if you have finer-grained (and sometimes more expensive) tests (money vs. time).

### Isotyping / Design for Manufacturing — Steve Hodges

- Hard to have repos of designs you can hand off to others and have them work seamlessly → usually doesn't work.
- **SWD** → protocol for uploading firmware to a device.
- They've built testing setups for multiple devices on one panel → design and test at panel size.
- **MakeDevice** → drag-and-drop PCB design, web application. Generates enclosures too, using the constraints of the modules added.

### From Concept to Mass Production: Tiles — Jonathan Fiene

*(Bergsonne Labs — bergsonne.io. Cool guy.)*

- For a startup, working with tiny components is very hard because manufacturing and then debugging can take months → not viable for startups.
- Insight: boards can be chunked into parts (actuators, sensing, controller, power, etc.). They sell these as 4×4 mm tiles → if you want a small thing, you can get the small components.
- Much faster → time to experiment is quicker.
- Open-source drivers.

### Design, manufacturing, and compliance — Steve Hodges

- Have you designed the thing right? Have you designed the *right* thing? How do you manufacture it reliably? Can it be used legally (not just sold legally)?
- As soon as you finish the prototype, start thinking about design for manufacturing → do the same for compliance! Little and often.
- Look at worst-case combinations:
  - Capacitors often have huge tolerances.
  - AA batteries change voltage over time and over charge.
  - Investigate operating ranges.
- Thermal testing → often a good proxy for lifetime. **HALT** → highly accelerated life testing.
- Vibration testing units.
- **Tooling** → anything used in the manufacturing process that isn't part of the product (e.g. test jigs). When designing the boards, consider how you'll test them with test jigs → test points. Building a test jig can be more complicated than building the product itself.
- Develop a testing **SOP** (standard operating procedure). Staff turnover is high in Shenzhen → it should be very clear for new/inexperienced testers.

**EMC (electromagnetic compatibility) testing:**
- Very expensive to build.
- (Semi-)anechoic chamber → room with pyramids on the walls and floor to dampen EM/radio waves.
- Must be tested under normal operating conditions → if it's operated with a laptop, a laptop must be present during testing (a 2016 Lenovo is good for this — quiet).
- **TEM cell** → poor man's version → small testing cell, only gives a rough idea. If EMC testing fails, use a TEM cell to debug before going back → call this pre-compliance testing (isotyping stage).

**Environmental testing:**
- They shred the product and test the resulting chemicals.

Stages you'll actually see (rather than "isotyping"):
- **EVT** — Engineering Validation Testing → ensure the technology is sound (suggested 5–50 units).
- **DVT** — Design Verification Testing → ensure design tolerances are sound, worst-case tolerances, think about component obsolescence (suggested 10–100s of units).
- **PVT** — Production Validation Testing → test the manufacturing procedure: are we doing things efficiently, is the SOP accurate/robust/useful (suggested 100s–1000s of units).

- Legislation is grey about the transition from low to high volume, especially going from development board to product (e.g. if dev boards are used in full products, maybe by another company).
- Do test equipment require testing/calibration? You can pay for calibration from RS, Keysight (one week in the science park in Cambridge), or whoever.

### Design for Compliance — Farnell (company)

*(Photo of the product life cycle + compliance aspects in phone photos.)*

Certification levels:
- **Self-certification** → requires technical files, declaration of conformity, conformity mark. Often enough for low-voltage devices.
- **Certification** → the above + a certificate (third party).
- **Approval** → the above + a Grant of Equipment Authorisation (permission to use and sell in the corresponding markets). For dangerous components, gases, etc.

Conformity assessment:
- The product owner holds the bulk of the responsibility.
- Determine the conformity pathway → often a government body will guide you for free.
- Conducting testing & assessment → suggestion: test as much as possible before going to a lab (it's expensive and slow).
- Suggestion: decide your markets first, then do risk assessments per market. See which (CE) directives apply → e.g. radio equipment directive, low voltage directive, machinery, etc.
- A lot of devices fail at the compliance stage.
- American National Standards Institute → C63.10 → stay in contact and up to date.
- Grantee code → access to the US market.
- Look at a global map of compliance.

### rib:bit

- Concept of participatory sensing → democratised research.
- Long-tail research problems → devices that enable this research to happen.

### Testing — Steve Hodges
- **RF testing** → you can get a network analyser and spectrum analyser cheaply as prep for EMC testing → saves a lot of time and money.
- TEM cells with these can test how your device affects other devices "on the shelf."
- Near-field probes → debug where exactly the RF problems are coming from.
- **ESD guns and thermal cameras** → apply electrostatic shocks to specific parts of your board (needed for compliance).
- **PCBite** → very helpful — a stage where you can place a bunch of probes.

### Panel Discussion

**How much does testing and certification cost, even on a shoestring?** 
- In the past, basic EMC testing cost ~$1,000 USD; more now. 
- You have to know exactly what to ask for to save money — maybe this is where you consult. 
- Testing in Shenzhen saves a lot. 
- Emphasis on knowing your target market → streamlines testing/compliance. 
- UL certified → commercially you need this (e.g. for Disney).
**Where to find resources to self-certify properly?** 
- Suggestion: find someone — ping Simon Monk or someone else with a product; the pro² network. 
- There's a lot more you have to do than people do initially, and that's okay — companies grow into full compliance.
- In the US you have to file an 83(b) within 90 days → you defer all taxes until you sell.
- Adafruit →  argue they're a "module," not a "product," so they don't certify.

**How to manage a product line?**
- **Provisional patent** → not a patent, way cheaper. You can file a full patent later and get priority based on the provisional's date. Lasts a year, then disappears; you can keep re-filing. You can also sell provisional patents. They aren't disclosed to the public.
- Sometimes patents aren't worth messing with → focus on the product instead.
- Alternative strategy: make the idea public so nobody else can patent it and stop you (already in the public domain).
- Patents only give you the right to sue → if you can't afford/enforce that, it's not really worth it (huge companies, huge populations, people you can't prove are infringing, etc.).
- A US patent is ~$10–20k plus continuing fees.

**My question — how do you do hardware collaboration?**
- Focus on isotyping is essential, especially if you aren't in the same location.
- Standards and modularisation are essential.
- Sometimes just getting the hardware to align is an easy trick.
- General consensus: it's hard to do — the tools and culture aren't there yet.

**How do you debug hardware? (Divide and conquer.)**
- Suggestion: start with power, then work step-by-step inward. Power faults are an easy way to brick things quickly.
- Design for accessibility during testing → where to put pads, etc. Explode out the board/design before shrinking to actual size (Tiles, for example).
- Solder on a ground wire → lots of noise from random things (even test equipment), so a ground wire helps.
- Question your test equipment so you're not chasing your tail → step back and forth between validating the measurement method and the thing you're actually measuring.

### The Secret Life of LEDs — Paul Dietz

- Recall the I–V graph of LEDs → after the forward voltage, it takes all the current you have (open circuit until it conducts, then effectively a dead short).

Things they didn't tell you about LEDs:
- They're diodes, but also photodiodes (they can measure light). See Forrest Mims, 1970s.
- Trick: power it the wrong way round. A reverse-biased LED has capacitance. When used as an input, it's incredibly close to the ideal model → the time it takes the capacitor to discharge tells you how much light is hitting it. Read from the I/O pins. (Circuit diagrams and demos on GitHub.)
- To turn the LED on *and* sense light: switch between discharging and lighting by toggling input high/low on both ends of the LED. It flickers in the dark (discharge times are longer). Seems to need two I/O pins instead of one.
- Can do spectral stuff based on the LED's colour.
- Can use LEDs as buttons that way.
- Making LEDs that detect temperature and wind speed (?!) → diodes drop current based on temperature → this is used in processors to measure temperature.

*(Great talk, but I was too tired to take it all in — refer back to GitHub for the slides.)*

### Towards Deployment — Lorraine Underwood (element14, YouTube)

- Visit Blackpool for the light show → cool. Blackpool Illuminations → Laurence Llewelyn-Bowen.
- *(Personal to-do)* Forward the light-show stuff and presentation to Oisin Cullen.
