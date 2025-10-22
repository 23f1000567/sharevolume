# SEC Shares Outstanding Viewer

This project provides a single-page responsive HTML application to view the highest and lowest outstanding common stock shares for a given company, fetched directly from the SEC EDGAR API. The application leverages Tailwind CSS for styling and includes dynamic data loading based on URL parameters.

## Features

-   Displays company name, maximum shares outstanding, and minimum shares outstanding with their respective fiscal years.
-   Data is fetched from the SEC EDGAR API for `EntityCommonStockSharesOutstanding`.
-   Supports dynamic loading of data for different companies by specifying a CIK in the URL.
-   Responsive design using Tailwind CSS.
-   Includes a reference to `uid.txt`.

## Getting Started

To run this application, simply open the `index.html` file in your web browser. All necessary HTML, CSS (via CDN), and JavaScript are self-contained within this single file.

### Default View

When opened without any URL parameters, the application will display data for **Applied Materials (CIK: 0000006951)**.

### Dynamic CIK Loading

You can view data for any other publicly traded company by appending a `CIK` parameter to the URL.

**Example:**
To view data for Apple Inc. (CIK: 0000320193), open the following URL:
`index.html?CIK=0000320193`

The application will automatically fetch and display the relevant shares outstanding data for the specified CIK without a page reload. A CORS proxy (`https://api.allorigins.win/raw?url=`) is used when fetching data for custom CIKs to circumvent cross-origin restrictions.

### Data Filtering

The application filters the `EntityCommonStockSharesOutstanding` data to include only entries where the fiscal year (`fy`) is greater than "2020" and the `val` (value) is a numeric type. It then identifies the maximum and minimum values from this filtered set.

## SEC API Usage

This application accesses public data from the SEC EDGAR API. As per SEC guidance, a descriptive `User-Agent` header is used for all API requests to identify the application and provide contact information.

## Project Structure

-   `index.html`: The core single-page application, including all HTML, Tailwind CSS (via CDN), and JavaScript logic.
-   `README.md`: This file, providing an overview and instructions.
-   `LICENSE`: The MIT License for this project.
-   `uid.txt`: A simple text file referenced within `index.html`, whose content (`CIK: 0000006951`) is embedded directly into the HTML for a single-file solution.
