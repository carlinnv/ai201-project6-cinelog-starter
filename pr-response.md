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
**My position:**
**Reasoning:**
**Tradeoff acknowledged:**

## Comment 5 — Sort order
**My position:**
**Reasoning:**
**Engagement with reviewer's point:**

## Comment 6 — Rebase
**What conflicted:**
**How I resolved it:**
**How I verified no conflict remains:**

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->
