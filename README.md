# Trombone Note Finder

A tiny website that listens to your trombone through the microphone and shows:

- the note you're playing (e.g. B♭3) and its frequency
- how sharp or flat you are, on a tuner meter
- the slide position (1st–7th) on a B♭ tenor trombone
- a scrolling graph of your pitch over the last ten seconds

Everything runs in your browser. No audio is recorded or sent anywhere.

## Put it on GitHub Pages

1. Create a new repository on GitHub (e.g. `trombone-note-finder`).
2. Upload `index.html` and this `README.md` to the repository.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**, pick the `main` branch and the `/ (root)` folder, then click **Save**.
5. After a minute or two your site will be live at `https://YOUR-USERNAME.github.io/trombone-note-finder/`.

GitHub Pages serves over HTTPS, which browsers require before they allow microphone access.

## Try it on your own computer first

Browsers only allow the microphone on `https://` pages or on `localhost`, so double-clicking the file may not work. Instead, open a terminal in the folder and run:

```
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Tips for best results

- Play fairly close to the microphone, in a reasonably quiet room.
- Hold each note steady for a moment; the display smooths over a few readings.
- Adjust **A4** if your group tunes to something other than 440 Hz.
- Switch between ♭ and ♯ names with the toggle (trombonists usually think in flats).

## How it works

The page uses the Web Audio API to grab microphone samples and runs the YIN pitch-detection algorithm about 30 times a second. The frequency is converted to the nearest note, and the slide position comes from the trombone's harmonic series: each position lowers the pitch by one more semitone than the one before it.

Slide positions assume a standard B♭ tenor trombone without an F-attachment. Notes with more than one possible position show the main one highlighted and the alternates outlined.
