# Bug Fix Notes

## 1. Search and Status Filtering

**Issue:** The search query did not correctly group the title and description conditions with the other filters. This could cause incorrect results when searching tasks by title or description.

**How I found it:** I reviewed the SQL query and checked how search and status filters were combined.

**Fix:** I added parentheses around the title and description search conditions so that the search term and status filter work together correctly.

## 2. Pagination

**Issue:** When changing the search query or status filter on a later page, the application could remain on that page and show unexpected or empty results.

**How I found it:** I manually tested searching and changing status filters while navigating through pages.

**Fix:** I reset the current page to page one whenever the search query or status filter changes.

## 3. Loading and Error Handling

**Issue:** The loading indicator could remain active after a failed request, and previous error messages could remain visible during a new request.

**How I found it:** I reviewed the task-fetching logic and checked how loading and error states were managed.

**Fix:** I cleared previous errors when fetching tasks and used a `finally` block to ensure that loading is stopped after the request completes.

## 4. Task Display and Responsive Layout

**Issue:** Loading, error, and empty results were not handled clearly, and task information could be difficult to view on smaller screens.

**How I found it:** I reviewed the task table and manually checked the interface at different screen sizes.

**Fix:** I improved the loading, error, and empty states, added fallback values for missing task details, and improved horizontal scrolling and text wrapping for smaller screens.

## 5. Oracle SQL Query

**Issue:** The Oracle SQL search conditions needed proper grouping to ensure consistent filtering.

**Fix:** I added parentheses around the title and description conditions in both the count and results queries. The Oracle query has not been tested against an Oracle database.
