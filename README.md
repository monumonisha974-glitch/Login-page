# Web Programming Lab
https://dazzling-hamster-992316.netlify.app

A small set of web programs covering sessions, date and time display, and form validation, plus an XML employee directory.

**Live demo:** `https://your-site-name.netlify.app` (replace with your Netlify link)

## Contents

| Program | What it does |
|---|---|
| **Welcome and session** | Takes a name and shows a hello page with the start time at the top right and a Logout button. Logging out shows a Thank You page with how long the site was used. |
| **Date and time** | Shows the current date, time and day. |
| **Age check** | Takes a name and an age. Under 18 shows "Hello *name*, you are not authorized to visit the site". Otherwise it shows "Welcome to this site". |
| **Employee directory** | Reads employee data from an XML file and displays it as a sortable, searchable table. |

## Project structure

```
.
├── netlify-site/
│   └── index.html          # Browser version of the three programs (single file)
├── php-lab/                # PHP versions of the three programs
│   ├── a_index.php         # Name form
│   ├── a_hello.php         # Hello page, stores name and start time in session
│   ├── a_logout.php        # Thank You page with duration of usage
│   ├── b_datetime.php      # Current date, time and day
│   ├── c_index.html        # Name and age form
│   └── c_check.php         # Age validation result
├── employee-site/
│   ├── index.html          # Reads employees.xml and renders a table
│   └── employees.xml       # Sample employee data
└── README.md
```

## Running the projects

### Browser version (`netlify-site`)
No build step or dependencies. Open `netlify-site/index.html` in a browser.

### PHP version (`php-lab`)
PHP needs a server to run. Opening the files directly in a browser will not work.

1. Install [XAMPP](https://www.apachefriends.org/) or WAMP and start Apache.
2. Copy the `php-lab` folder into `htdocs` (XAMPP) or `www` (WAMP).
3. Open in your browser:
   - `http://localhost/php-lab/a_index.php`
   - `http://localhost/php-lab/b_datetime.php`
   - `http://localhost/php-lab/c_index.html`

Alternatively, with PHP installed, run `php -S localhost:8000` inside the `php-lab` folder and open `http://localhost:8000/a_index.php`.

### Employee directory (`employee-site`)
The page loads `employees.xml` with `fetch()`, which browsers block for files opened from disk. Serve the folder instead:

```bash
cd employee-site
python -m http.server 8000
```

Then open `http://localhost:8000`. If you open the page directly from disk, use the **Load your own XML file** button to pick `employees.xml`.

To add or change columns, edit the `COLUMNS` array in `employee-site/index.html` and add the matching tags to the XML:

```xml
<employees>
  <employee>
    <id>101</id>
    <name>Asha Rao</name>
    <department>Engineering</department>
    <designation>Senior Developer</designation>
    <email>asha.rao@example.com</email>
    <city>Bengaluru</city>
    <salary>1450000</salary>
  </employee>
</employees>
```

.

## Features

- Session timing: name and start time are stored when the user signs in, and the duration is calculated at logout.
- Input is escaped before it is shown, which prevents HTML injection.
- Responsive layout with light and dark mode.
- Sortable and searchable XML data table.

## Technologies

HTML, CSS, JavaScript, PHP, XML.

## License

Released for educational use.
