# XOXO puzzle maintenance

User-approved modes: Us, Friends, Gossip Girl (original series), The O.C. Every edition contains all four, not one rotating tab. Each has a five-letter answer and six attempts. HIMYM was superseded by the user's explicit four-mode list.

## Scheduled publishing
The existing ChatGPT automation runs at 07:00 and 18:00 Asia/Kolkata and is instructed to commit each new edition to this repository's main branch. It is not an in-repository cron job. Scheduling initiates selection and publishing; host build time is additional. Do not claim live publication merely because a Git commit succeeded.

Read the latest main tree and puzzle-history.json. Update puzzles.json plus required images and source records in one atomic fast-forward commit. Use a unique edition string for every new set, common to both players. Same-slot retries must be idempotent. Routine changes do not require rewriting index.html. Preserve words.txt and unrelated files. Never force-push.

## Image sourcing
US: ONLY the user's uploaded The Book of Us.pdf and assets.zip. Crop, resize and compress those images as needed, without inventing or adding depicted elements. No internet, stock, generated, or unrelated personal images. Store the selected image under assets/us/ with a neutral filename and add its exact source page/archive path and SHA-256 to us-assets.json. The app refuses external Us hint URLs. Upload only the selected hint, never the complete private book or archive into the public site.

SHOWS: genuine online scene snapshots are allowed. Prefer studio/broadcaster stills or credited editorial screenshots. No generic cast photos, posters, AI reconstructions, or mislabeled unrelated frames. Validate the episode and visibly check the image. Match the answer to that scene, not just the general series. Record season, episode, scene, source page and the word connection. Episode names/source links appear only after completion if they could spoil the answer. Do not identify actors from their faces; use source metadata for episode provenance.

## Random selection
Use a real random sampler across each show's complete original episode run, not a tiny fixed set of famous scenes. Episode catalogs: https://www.tvmaze.com/shows/431/friends/episodes ; https://www.tvmaze.com/shows/776/the-oc/episodes ; https://www.tvmaze.com/shows/567/gossip-girl/episodes . Select an episode first and a suitable recognizable scene within it. Resample when a verifiable, usable scene picture or fair five-letter association is unavailable. Avoid recent answers and scenes, targeting the last 60 editions. Us draws from documented shared lore and verified uploaded images. Do not invent memories or artificially pad/truncate names to five letters.

## Guess validation
Exactly five A-Z letters. Accept a guess iff it is in the bundled words.txt OR it equals the current mode's exact answer. That exact-answer exception applies to a nickname, transliteration, proper name, or non-word. No other non-word is permitted, including another mode's answer or a previous edition's answer unless independently in the dictionary. Rejected guesses consume zero attempts. Never fail open when the dictionary cannot load.

## Release checks
All four modes and all hints present; unique edition ID; correct per-mode answer exception; junk guesses rejected without consuming a turn; six misses finish without a crash; duplicate-letter scoring; independent saved guesses and hidden/revealed hints per mode; mobile keyboard at 320px; live image loading; correct source provenance. The client checks for a new puzzles.json every minute and on foreground return, offering an explicit new-set button without discarding an ongoing round.

The page is a static client-side game: answers are inspectable in source/data and the host is not made private by robots metadata. Do not treat obfuscation as security.
