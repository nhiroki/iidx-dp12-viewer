# IIDX DP Score Viewer

A simple, client-side web application to view and analyze personal beatmania IIDX Double Play (DP) score data. It is designed to parse a specific CSV format and display all level 12 charts in a filterable and sortable table.

## Features

*   **Local Data:** Loads score data from a local CSV file.
*   **Level 12 Focus:** Automatically filters and displays all of your level 12 DP scores.
*   **Sortable Table:** Click any column header to sort the data. Numeric columns use numeric sorting, while "Clear Type" and "DJ Level" use custom gameplay/rank hierarchies.
*   **Title Filter:** Instantly filter the list by song title using the search box.
*   **Color-Coded Clear Types:** Clear lamps are colored for quick visual identification (e.g., EASY CLEAR is green, HARD CLEAR is red).
*   **Zero Dependencies:** Runs entirely in the browser with vanilla JavaScript. No build step or internet connection required.

## How to Use

1.  **Get Your Score Data:** You need a CSV file containing your score data. The application is designed to work with a specific format where each row represents a song and columns contain the details for each difficulty chart (Beginner, Normal, Hyper, Another, Leggendaria).

2.  **Add Your CSV File:**
    *   Place your score CSV file in the same directory as `index.html`.
    *   The application is currently hardcoded to fetch the file named `5771-1854_dp_score.csv`.
    *   To use your own file, you can either:
        a. Rename your file to `5771-1854_dp_score.csv`.
        b. **(Recommended)** Open `index.html` in a text editor and change the filename in this line (around line 170):
           ```javascript
           fetch('your-file-name.csv')
           ```

3.  **View Your Scores:** Open `index.html` in any modern web browser.

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

The script then transforms this data, creating a new table entry for each difficulty chart (Beginner, Normal, etc.) that is marked as level 12. Since the application is specifically for level 12 charts, the "Difficulty" column is omitted from the display.
