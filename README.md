# GitHub Website Template

This repository provides a template for creating a personal academic website using GitHub Pages.

---

## How to Use This Template

1. **Download all the files**  
   Download all the files in this repository. Then create a new repository in your own GitHub account and set the **Repository name** to `your-github-username.github.io`. After that, upload all the downloaded files to this repository.

2. **Enable GitHub Pages**  
   - Go to your repository **Settings → Pages**  
   - Set the **Branch** to `master/root` or `main/root`  
   - Click **Save**  
   After a short wait, you will see a **Visit site** button under the **GitHub Pages** section. Click it to view your website.

---

## Quick Start Example: Add a New Page

Suppose you want to add an **News** page:

1. Create a new file named `news.md` in the main directory with the following content:

    ```yaml
    ---
    layout: normal
    title: News
    ---
    ```

    Add any content you like below the header.

2. Open `_includes/navbar.html` and add:

    ```html
    <div class="menu-item">
    <a href="news.html" {% if page.url == "/news.html" %}class="current"{% endif %}>News</a>
    </div>
    ```

3. Commit your changes.
   You should now see the **News** item in the navigation bar.

---

## File and Folder Overview

### `_includes/navbar.html`
- Controls the **left navigation bar**.  
- To add a new item:
  1. Create a new file `ABC.md` in the main directory.  
  2. Add the following code inside `navbar.html`:  

     ```html
     <div class="menu-item">
       <a href="ABC.html" {% if page.url == "/ABC.html" %}class="current"{% endif %}>XXX</a>
     </div>
     ```

  - `ABC` must match the name of your `.md` file.  
  - `XXX` is the text displayed on the navigation bar.  

### `_config.yml`
- Configure the following display information:
  - Website title (shown at the top of the homepage).
  - Personal information (displayed to the right of the profile photo).


### `_layouts/homepage.html`
- Controls the **homepage layout**, including profile photo and personal information (on the right of the photo).  
- To adjust photo size, edit the following line:  

  ```html
  <a href="index.html"><img src="{{site.avatar}}" alt="alt text" height="180px" /></a>
  ```
- Information fields such as **position**, **department**, and **affiliation** are displayed using conditional blocks like:

  ```liquid
  {% if site.position %}…{% endif %}
  {% if site.department %}…{% endif %}
  {% if site.affiliation %}…{% endif %}
  ```
- The displayed text and links are configured in `_config.yml`.
- If a specific field is not defined in `_config.yml`, it will not be displayed on the homepage.
  
### `_layouts/normal.html`
- Controls the layout for other pages (e.g., **Publications**, **People**).

### `assets/css/jemdocCustom.css`
- Defines custom styles for homepage and other pages.
- Used by both `homepage.html` and `normal.html`.
- You may modify this file if you want to customize the appearance of the website (e.g., fonts, spacing, or layout).

### `assets/css/style.css`
- Contains **default styles**.
- Generally no modification is needed.
- This file is not used by `homepage.html` and `normal.html`.


### `assets/img/`
- Stores image files (e.g., profile photo, figures).

### `assets/publication/`
- Stores PDF files of conference and journal papers.

### `index.md`
- Defines **homepage content**.
- Uses the `homepage` layout:
    ```yaml
    ---
    layout: homepage
    ---
    ```

### `publications.md`
- Defines **Publications** page content.
- Uses the `normal` layout and sets the title:
    ```yaml
    ---
    layout: normal
    title: Publications
    ---
    ```
- The `title` value will be displayed at the top of this page.

### `people.md`
- Defines **People** page content.
- Uses the `normal` layout and sets the title:
    ```yaml
    ---
    layout: normal
    title: People
    ---
    ```
- The `title` value will be displayed at the top of this page.
