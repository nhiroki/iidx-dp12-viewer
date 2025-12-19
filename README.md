# IIDX DP12 Score Viewer

A simple, client-side web application to view and analyze personal beatmania IIDX Double Play (DP) score data. It parses your CSV exported score data and displays all level 12 charts in a filterable and sortable table.

## Features

*   **Browser-Based Storage:** Stores your score data securely in your browser's Local Storage. No data is ever uploaded to a server.
*   **Easy Import:** Dedicated upload page supports copy-pasting text or drag-and-dropping CSV files.

*   **Robust Parsing:** Correctly handles complex CSVs (e.g., song titles with commas or quoted fields).
*   **Level 12 Focus:** Automatically filters and displays all of your level 12 DP scores.
*   **Sortable Table:** Click any column header to sort. "Clear Type" and "DJ Level" use custom gameplay hierarchies.
*   **Title Filter:** Instantly filter the list by song title.
*   **Color-Coded Clear Types:** Clear lamps are colored for quick visual identification.
*   **Zero Dependencies:** Runs entirely in the browser with vanilla JavaScript. No build step or internet connection required.

## How to Use

1.  **Open the Viewer:**
    Open `index.html` in any modern web browser.

2.  **Import Data:**
    *   If you haven't loaded data yet, you will see a prompt to upload your scores.
    *   Click the **"Upload CSV Data"** link or navigate to `upload.html`.
    *   **Drag & Drop** your CSV file into the box, or **Copy & Paste** the text content directly.

    *   Click **"Save Data"**.

3.  **View Your Scores:**
    You will be redirected back to the main viewer where your level 12 scores are displayed.

4.  **Manage Data:**
    *   To update your scores, simply go back to the upload page and save new data (it overwrites the old data).
    *   To remove all data from your browser, use the **"Clear Data"** button on the upload page.

## CSV Data Format

The application expects a CSV file with Japanese headers. Each row represents a single song, and it contains columns for each difficulty type. The script specifically looks for headers like:

*   `バージョン` (Version)
*   `タイトル` (Title)
*   `BEGINNER 難易度`, `NORMAL 難易度`, etc. (Difficulty for each style)
*   `BEGINNER スコア`, `NORMAL スコア`, etc. (Score for each style)
*   `BEGINNER PGreat`, `NORMAL PGreat`, etc.
*   `BEGINNER Great`, `NORMAL Great`, etc.
*   `BEGINNER ミスカウント`, `NORMAL ミスカウント`, etc. (Miss Count for each style)
*   `BEGINNER クリアタイプ`, `NORMAL クリアタイプ`, etc. (Clear Type for each style)
*   `BEGINNER DJ LEVEL`, `NORMAL DJ LEVEL`, etc.

The script transforms this data, creating a new table entry for each difficulty chart marked as level 12. Since the application is specifically for level 12 charts, the "Difficulty" column is omitted from the display.
