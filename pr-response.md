# PR Response Doc — CineLog Watchlist Feature

## AI Usage
<!-- Fill in at the end — how you used AI tools during this project -->

## Comment 1 — Rename
**What I did:** Changed all instances of "save_to_watchlist" to "add_to_watchlist". 
**How I verified:** I searched the codebase for any instance of "save_to_watchlist" and found none. 

## Comment 2 — Deduplication
**What I did:** Created a new error "AlreadyInWatchlist" that raises when the user tries to add a film that's already on their watchlist.  
**How I verified:** Tested using curl. 

## Comment 3 — Missing test
**What I did:** I added a new test to test for adding a nonexistent film (film_id doesn't exist) to the database using the pattern from test_collection.py. 
**How I verified:** I verified it by using pytest. 

## Comment 4 — Default visibility
**My position:** My position is that public should be set to False by default. 
**Reasoning:** Users will feel as though the app is more trustworthy. The point of the app is to allow users to keep a personal collection of films they've watched and want to watch. It is not a social media app where users are meant to share their films. Users may feel as though this app is more personal and more centered around their individual usage.  
**Tradeoff acknowledged:** The app does not frame itself as a social media app. Some users may also feel discouraged to share their lists because it is more of a "personal use" app.

## Comment 5 — Sort order
**My position:** We should change the sort order to date-added. 
**Reasoning:** A chronological order feels more natural, and the only reason why a user might want to sort films alphabetically would be to find a specific film. We should actually sort it in reverse order, so that the user sees the shows they added oldest on the watchlist first. 
**Engagement with reviewer's point:** The reviewer is right to say that many people would want to see films they've added recently. Users might want to see what films they've watched recently, in which case chronological order would be most helpful.  

## Comment 6 — Rebase
**What conflicted:** Rebasing onto main pulled in the UUID migration commit. `.gitignore` had a normal textual conflict. More subtly, since my watchlist commits never touch `models.py`, the merge silently kept main's version of that file — which deleted the `WatchlistEntry` model and left my watchlist code assuming integer film IDs against a UUID schema.
**How I resolved it:** Merged `.gitignore` to keep both versions' entries. Re-added `WatchlistEntry` to `models.py` with `film_id` as `db.String(36)` (UUID) instead of `db.Integer`, and updated the docstrings in `watchlist_service.py`/`watchlist.py` that still described `film_id` as an int.
**How I verified no conflict remains:** `git log --merges main..feature/watchlist` returns nothing, confirming a clean linear history. Reran the full test suite after the fix — all 5 tests passed.

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->
