# Romantic GitHub Pages Website

Your website is ready. The photos from `Documents/My Love` were copied into:

```text
assets/my-love/
```

The main file you edit is:

```text
data.js
```

Do not rename `index.html`.

## 1. Preview The Website

From this folder:

```text
C:\Users\Raj Gollapalli\Documents\New project
```

Run:

```powershell
python -m http.server 4173
```

Open:

```text
http://localhost:4173
```

## 2. Change The Secret Login Date

Open `data.js`.

Find:

```js
secretDate: "14022024",
```

Change it to your special date using only numbers.

Examples:

```js
secretDate: "01012024", // 01 January 2024
secretDate: "14022024", // 14 February 2024
secretDate: "25062025", // 25 June 2025
```

This is the password used on the first screen.

## 3. Change Names And Relationship Dates

In `data.js`, find:

```js
couple: {
  yourName: "Your Name",
  partnerName: "Her Name",
  title: "Our Forever Story",
  initials: "US",
  anniversary: "2024-02-14",
  birthday: "2026-07-01"
}
```

Edit it like this:

```js
couple: {
  yourName: "Raj",
  partnerName: "Her Name",
  title: "Raj & Her Name",
  initials: "RH",
  anniversary: "2024-02-14",
  birthday: "2026-07-01"
}
```

Use this format for dates:

```text
YYYY-MM-DD
```

Example:

```text
2024-02-14
```

The current relationship start date is set as:

```js
anniversary: "2019-10-21"
```

That makes the website show almost 7 years together.

## 4. Add Or Change Photos

Put new photos inside:

```text
assets/my-love/
```

Then open `data.js` and find:

```js
gallery: [
```

Each photo has this format:

```js
{
  image: "assets/my-love/photo-name.jpg",
  title: "Photo Title",
  message: "Love paragraph shown under this photo."
}
```

To add a new photo, copy one block and change the file name, title, and message:

```js
{
  image: "assets/my-love/new-memory.jpg",
  title: "A New Memory",
  message: "This day became special because being with you made everything feel lighter, happier, and unforgettable."
}
```

Put a comma between photo blocks.

## 5. Change The Photo Messages

In `data.js`, each gallery item has:

```js
message: "Your message here."
```

Change only the text inside the quotes.

Example:

```js
message: "This photo reminds me that my happiest moments are the ones where you are close to me."
```

## 6. Add Background Music

Put your song file inside:

```text
assets/music/
```

Current background song:

```text
assets/music/background-music.mp3
```

The website starts this song after the secret date is entered. In `data.js`, it is set here:

```js
music: {
  file: "assets/music/background-music.mp3"
}
```

If your file has a different name, change it:

```js
music: {
  file: "assets/music/our-song.mp3"
}
```

Use `.mp3` for best browser support.

The current playlist song is:

```text
assets/music/Our Song.mp3
```

## 7. Add Playlist Links

In `data.js`, find:

```js
playlist: [
```

Edit songs like this:

```js
{
  title: "Perfect",
  artist: "Ed Sheeran",
  link: "https://open.spotify.com/your-song-link"
}
```

You can use Spotify, YouTube, Apple Music, or any public link.

## 8. Add Video Message

Put your video in:

```text
assets/
```

Recommended name:

```text
video-message.mp4
```

Then in `data.js`, find:

```js
videoMessage: {
  text: "Record a short video message, save it as assets/video-message.mp4, and it will appear here.",
  file: "assets/video-message.mp4"
}
```

Change the text if you want.

Use `.mp4` for best browser support.

## 9. Change Birthday Wishes

In `data.js`, find:

```js
birthday: {
  title: "Happy Birthday, my favorite person.",
  message: "I hope this year brings you..."
}
```

Change the title and message.

## 10. Change NEET PG Congratulations Message

In `data.js`, find:

```js
neetPg: {
  title: "Advance Congratulations, My Future Specialist.",
  message: "Your message here.",
  button: "Celebrate Her Dream"
}
```

Change the `title`, `message`, or `button` text. The button launches confetti.

## 11. Deploy To GitHub Pages

1. Go to `https://github.com`.
2. Create a new repository.
3. Upload everything from:

```text
C:\Users\Raj Gollapalli\Documents\New project
```

Upload these:

```text
index.html
styles.css
app.js
data.js
README.md
.nojekyll
assets/
```

4. Open the repository on GitHub.
5. Go to `Settings`.
6. Click `Pages`.
7. Under `Build and deployment`, choose `Deploy from a branch`.
8. Select branch `main`.
9. Select folder `/root`.
10. Click `Save`.

GitHub will show your live website link after one or two minutes.

## 12. Important Notes

- Keep all picture, music, and video paths exactly the same as written in `data.js`.
- If a file name has spaces, that is okay, but the spelling must match exactly.
- If an image does not show, check the file name and extension: `.jpg`, `.jpeg`, `.png`, or `.webp`.
- Edit text in `data.js`, not in `index.html`.
