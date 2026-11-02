# Climbing the Cosmic Ladder

A browser game for introductory astronomy students. They climb the cosmic distance ladder one rung at a time, from parallax to variable stars to Type 1a supernovae, and finish by building their own Hubble diagram and measuring H₀.

**Play it:** `https://alexsobotka.github.io/cosmic-ladder/`

The whole game is one self-contained file, `index.html`. There's nothing to install, no accounts, and no server. It runs in any modern browser, Chromebooks included.

---

## What students do

Each level opens with a short interactive lesson that ends in a few concept-check questions. Students measure each object one step at a time. Before a key equation appears, students build it by dragging its pieces (L, r, F, P, θ…) into place. Then the equation is shown filled in with their own numbers. Luminosity, distance, flux and pulsation period keep the same colors everywhere (green, pink, blue and purple), in equations, text and charts. The parallax angle θ is orange.

| Level | Goal | What students measure |
|---|---|---|
| **1 · Variable stars** | Build a period-luminosity relation | Clicking a variable star zooms in on its patch of sky, where students find the one star that is pulsing. Then, for each nearby variable star: pulsation period (by clicking peaks on a light curve), average flux, and parallax angle θ (by blinking between January and July images). From these they get the distance d [pc] = 1 [AU] / θ [arcsec] and then L = 4πr²F. While they work, the sidebar chart draws a vertical line at the star's period and then a horizontal line at its luminosity, so they can see where the point will land. Each star is plotted on a log-log L vs. P chart, and the game fits the line. |
| **2 · Supernovae** | Find out whether Type 1a supernovae all have the same luminosity | Clicking a ★ galaxy zooms in to a close-up where students hunt for the one star that is pulsing, then blink between last year's image and tonight's to spot the supernova. In these galaxies, which contain both a variable star and a supernova, students use their Level 1 relation to get the variable star's L, then its distance, then the supernova's luminosity, L_SN = 4πr²F_peak. |
| **3 · Hubble diagram** | Measure the expansion of the universe | Each distant galaxy also opens with a zoom-in and a supernova hunt. Then students use their average L_SN and the supernova's peak flux to get the distance. They line up a template of spectral lines to get the galaxy's speed, then plot velocity against distance. |

When a student reaches the Level 3 goal, the game reveals the true H₀ for that sky and tells them how close they got. From there they can export a report, start over, or keep exploring.

Mistakes carry up the ladder, just as they do for real astronomers. A sloppy period-luminosity relation shifts the supernova luminosities, and that shifts H₀. That can lead to a good class discussion.

---

## Class codes

The game has no server, so a teacher's settings reach students through a short **class code**. Everyone using the same code plays under the same settings. Each student gets their own randomly generated sky (and its own true H₀), so no two students' answers match. Starting over gives a brand-new sky.

Example: `F1A53-10`

| Part | Meaning | Options |
|---|---|---|
| `F` | Brightness language | `F` flux and luminosity · `M` magnitudes |
| `1` | Starting level | `1` full ladder · `2` period-luminosity relation given · `3` supernova luminosity given |
| `A` | Which steps students calculate themselves | `A` none (the game fills in every equation) · `H` all of them · `X` plus two characters for a custom mix chosen with the checkboxes in ⚙ settings (for example `X04` means students only calculate the distance from the parallax angle) |
| `5` | Variable stars needed to unlock Level 2 | 3 to 9 |
| `3` | ★ galaxies needed to unlock Level 3 | 2 to 9 |
| `10` | Galaxies needed to finish Level 3 | 5 to 20 |
| *(optional)* `Q0` / `Q2` | Quick-check questions | `Q0` off · nothing added for sometimes (the default) · `Q2` often |
| *(optional)* `E0` | Equation building | nothing added for on (the default) · `E0` off, so equations are simply shown |

**Sharing a code with students.** Either:
- add it to the end of the link: `https://alexsobotka.github.io/cosmic-ladder/#F1A53-10`, or
- have students open **Menu → Your class**, type the code, and click **Join class**.

With no code, the game uses `F1A53-10`. Older codes that start with a word like `ORION-` still work; the word is simply ignored.

You never need to build a code by hand. Open the ⚙ settings, choose your options, and the game shows the matching code.

---

## Teacher settings (⚙)

The gear button is protected by a passcode. **The default passcode is `ladder`.** From the settings you can:

- choose every option above and copy the resulting class code
- tick exactly which calculation steps students must do themselves (period, parallax angle, distance from parallax, luminosity, and so on); checked steps show the equation with a blank answer that the game checks
- set how often **quick-check questions** pop up (off, sometimes, often). These are short questions about the step a student just finished. Most ask *why* that measurement is needed ("Why do we need this star's pulsation period?"), so students think about the purpose of each step instead of just clicking through. Students must answer correctly to continue, and the report records how many they got right on the first try
- turn **equation building** on or off. When it's on, students drag the pieces of each key equation into place before the numbers appear. Each equation is built in full the first time. After that, the game picks at random: about half of the objects ask for one equation, with only one or two boxes left blank
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
- quick checks answered right on the first try, and their best streak
- equations built right on the first try
- a **check code**

To confirm a report wasn't edited, paste it into **⚙ → Check a student report**.

---

## Good to know

- **Each student's sky is random.** The hidden true H₀ is somewhere between 60 and 80 km/s/Mpc.
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
