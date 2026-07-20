# The Physical Internet — How the Web Connects the World (and What Comes Next)

> 🌍 **The big idea:** The internet *feels* virtual — apps, emails, videos — but it's actually a vast, tangible system of radio waves, copper, glass, and ocean cables. Follow one email and you can trace the whole machine.

---

## 1. The Internet Is Physical, Not Virtual

We think of the internet as software, but every message rides on real hardware. This is what makes access and speed vary so much from place to place.

- **First and last mile** = the part of the internet inside our homes and offices — routers, Wi-Fi, cellular connections.
- Our data (e.g. an email with a photo) is split into **data packets**. Each packet carries a **header** with source + destination info — like an address on a postal envelope.
- Data is stored in **binary** (strings of 1s and 0s), which computers translate into signals.

### The signal chain (device → the world)

1. Device encodes data as **binary**.
2. Binary is sent as **radio waves** from the device to the router.
3. At the router, signals convert into either:
   - **electrical pulses** over **copper wires**, or
   - **laser light pulses** over **fiber optic cables**.
4. From there, data moves out along the network toward its destination.

| Medium | Carries data as |
|---|---|
| **Copper wire** | Electrical pulses |
| **Fiber optic cable** | Fast flashing laser light (on/off light pulses) |

> 📡 **Phones are radios:** A cell phone sends binary wirelessly by acting like a radio — using **frequency modulation** to encode the 1s and 0s onto radio waves.

---

## 2. The Backbone & Submarine Cables

To reach the other side of the world, data travels the **internet backbone** — an interconnected web of cables and hubs across continents and oceans.

- **ISPs** (internet service providers) handle the wiring inside buildings and connect out to **internet hubs**.
- Hubs route data *between* networks (e.g. from AT&T's network onto another provider's).
- ⚠️ **"The cloud" is a marketing concept** — there's no cloud. Data physically moves through cables and hardware.
- The critical global links are **submarine cables** on/under the ocean floor — the "cable highway" for transcontinental data.

### Submarine cable facts

| Feature | Details |
|---|---|
| Cable length | Hundreds to thousands of km |
| Installation ship | **SubCom *Decisive*** — a 139-meter cable-laying vessel |
| Cable composition | Fiberglass fibers (hair-thin strands of glass) |
| Cable types | Lightweight (open ocean) · burial type (continental shelf) |
| Installation time | ~70 days total (~60 days plowing) |
| Global count | ~400 cables worldwide, forming a global web |

### Risks and interruptions

- Cables are strong, but the biggest threat is **human activity** — fishing, anchors, drilling — *not* natural causes like shark bites.
- Faults **inland** are repaired quickly; **underwater** repairs need specialized ships and take far longer.

> 🇹🇴 **Worked example — Tonga, 2019:** An anchor cut a cable and knocked Tonga's internet out for **13 days**. One line showed how critical *and* fragile this infrastructure is.

---

## 3. The Problem — Unequal Access

Fast, low-cost internet isn't spread evenly. Rural and low-income areas are often underserved.

- Providers invest where **revenue potential is highest**, so less populated or poorer regions get fewer options.
- These "uneconomic" areas end up with **fewer ISPs → higher costs, less competition**.
- Coverage maps reveal clear **geographic and socioeconomic disparities** in availability.

---

## 4. Bridging the Gap — Emerging Technologies

New approaches aim to close connectivity gaps and boost speed — but each has tradeoffs.

### 5G wireless
- Uses **higher-frequency radio waves**, which carry more data per wave.
- Higher frequency = shorter range → needs **dense infrastructure** (antennas on every block), unlike sparse older cell towers.
- High cost + ROI concerns mean deployment favors **urban and wealthier areas**.
- Takeaway: 5G mostly **speeds up service for people who already have good service** — it doesn't fix the access gap.

### Stratospheric balloons (Project Loon)
- Run by **Alphabet** (Google's parent company); used high-altitude balloons to build a **radio-wave network above the clouds**.
- Balloons ride stratospheric winds to cover wide areas and reach places without ground networks.
- **Restored connectivity for ~250,000 people in Puerto Rico** after Hurricane Maria.
- Weather-dependent and finicky, but a promising *complement* to traditional methods.

### Space-based efforts
- **Amazon's Kuiper** and **SpaceX's Starlink** aim to deliver internet from **satellites**.
- These systems use radio waves and **complement fiber optics — they don't replace them**.

---

## Key Takeaways

- The internet runs on **physical infrastructure**, from tiny radio waves to massive ocean cables.
- Data flow: **binary → radio waves → copper (electrical) or fiber (light) → hubs → submarine cables → destination**.
- Protecting this infrastructure matters, since **human-caused damage** is the persistent threat.
- **Access inequality is mostly economic** — it tracks where providers choose to invest.
- **5G, balloons, and satellites** offer *partial* solutions; they add to fiber rather than replacing it.
- The internet is **a necessity, not a luxury** — and the whole system is still **a work in progress**.
