# Climbing the Cosmic Ladder

A browser game for introductory astronomy students. They climb the cosmic distance ladder one rung at a time, from parallax to variable stars to Type 1a supernovae, and finish by building their own Hubble diagram and measuring H₀.

**Play it:** `https://alexsobotka.github.io/cosmic-ladder/`

The whole game is one self-contained file, `index.html`. There's nothing to install, no accounts, and no server. It runs in any modern browser, Chromebooks included.

---

## What students do

Each level opens with a short interactive lesson that ends in a few concept-check questions. Students measure each object one step at a time. Every step shows one displayed equation filled in with their own numbers.

| Level | Goal | What students measure |
|---|---|---|
| **1 · Variable stars** | Build a period-luminosity relation | For nearby variable stars: pulsation period (by clicking peaks on a light curve), average flux, and parallax angle θ (by blinking between January and July images). From these they get the distance d [pc] = 1 [AU] / θ [arcsec] and then L = 4πr²F. Each star is plotted on a log-log L vs. P chart, and the game fits the line. |
| **2 · Supernovae** | Find out whether Type 1a supernovae all have the same luminosity | In galaxies marked ★ that contain both a variable star and a supernova, students use their Level 1 relation to get the variable star's L, then its distance, then the supernova's luminosity, L_SN = 4πr²F_peak. |
| **3 · Hubble diagram** | Measure the expansion of the universe | For distant galaxies, students use their average L_SN and the supernova's peak flux to get the distance. They line up a template of spectral lines to get the galaxy's speed, then plot velocity against distance. |

When a student reaches the Level 3 goal, the game reveals the true H₀ for that sky and tells them how close they got. From there they can export a report, start over, or keep exploring.

Mistakes carry up the ladder, just as they do for real astronomers. A sloppy period-luminosity relation shifts the supernova luminosities, and that shifts H₀. That can lead to a good class discussion.

---

## Class codes

The game has no server, so a teacher's settings reach students through a short **class code**. Everyone using the same code sees the same sky and plays under the same settings.

Example: `ORION-F1A53-10`

| Part | Meaning | Options |
|---|---|---|
| `ORION` | Sky seed. Sets the positions, distances and speeds of everything, including the hidden true H₀ (between 62 and 78 km/s/Mpc). | Up to 16 letters or numbers |
| `F` | Brightness language | `F` flux and luminosity · `M` magnitudes |
| `1` | Starting level | `1` full ladder · `2` period-luminosity relation given · `3` supernova luminosity given |
| `A` | Which steps students calculate themselves | `A` none (the game fills in every equation) · `H` all of them · `X` plus two characters for a custom mix chosen with the checkboxes in ⚙ settings (for example `X04` means students only calculate the distance from the parallax angle) |
| `5` | Variable stars needed to unlock Level 2 | 3 to 9 |
| `3` | ★ galaxies needed to unlock Level 3 | 2 to 9 |
| `10` | Galaxies needed to finish Level 3 | 5 to 20 |

**Sharing a code with students.** Either:
- add it to the end of the link: `https://alexsobotka.github.io/cosmic-ladder/#ORION-F1A53-10`, or
- have students open **Menu → Your class**, type the code, and click **Join class**.

With no code, the game uses `ORION-F1A53-10`.

You never need to build a code by hand. Open the ⚙ settings, choose your options, and the game shows the matching code.

---

## Teacher settings (⚙)

The gear button is protected by a passcode. **The default passcode is `ladder`.** From the settings you can:

- choose the sky seed and every option above, and copy the resulting class code
- tick exactly which calculation steps students must do themselves (period, parallax angle, distance from parallax, luminosity, and so on); checked steps show the equation with a blank answer that the game checks
- show the true H₀ line on the Hubble diagram
- copy all of the current device's measurements as CSV
- clear progress on the current device
- check a student report (see below)
- lock the settings again (useful on a shared or projected computer)

**To change the passcode,** open `index.html` in any text editor, find this line near the top of the script:

```js
const TEACHER_PASSCODE='ladder';
```

Change the word between the quotes, save, and upload the file again.

> **Note:** this is a casual lock, not real security. The repository is public, so anyone who reads the source code can find the passcode. It keeps honest students out of the settings.

---

## Student reports

Students open **Menu → Your class**, enter their name, and click **Copy report for your teacher**. They can also click **Export results for teacher** on the finish screen. The report is plain text they can paste into an LMS assignment. It includes:

- their name, class code and date
- for each lesson quiz, how many questions they got right on the first try, and which ones took extra tries
- how many objects they measured at each level, their period-luminosity relation and their average supernova luminosity
- their H₀, and after finishing, the true H₀ and how far off they were
- a **check code**

To confirm a report wasn't edited, paste it into **⚙ → Check a student report**.

---

## Good to know

- **Progress is stored in each student's browser.** Students who switch devices, use a private window or clear their browser data start over. Each class code has its own separate save.
- **Sound:** the game generates its own music and sound effects in the browser, with no audio files. The soundtrack, "Starlight Synthwave," is a 2:40 synthwave piece that builds from a soft intro through bass, drums and a bell melody before looping. Music starts when a student clicks Start. Students can set music and effects volume, or mute everything, under **Menu → Sound**; the choice is remembered on their device.
- **An internet connection is needed** to load the fonts and the equation renderer (MathJax, from a public CDN). Without it, equations appear as raw LaTeX text.
- **The physics is simulated with some simplifications:**
  - Variable star luminosity is proportional to period, with about 10% scatter.
  - Type 1a supernovae vary by about 12% in peak luminosity.
  - Galaxies have random motions of about 300 km/s on top of the Hubble flow.
  - Speed is found from the spectrum with v = cz, which is accurate for these nearby galaxies.
- **Units:** in flux mode, luminosity is in solar units (L☉), distance in parsecs, and flux in L☉/pc², so that 4πr²F = L works directly.

---

## Updating the game

Replace `index.html` in this repository: open the file on GitHub, then upload or edit it and commit. GitHub Pages updates the live site within a minute or two. Students' saved progress is not affected.
