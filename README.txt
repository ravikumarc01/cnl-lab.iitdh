Colloids & Nanomaterials Lab (CNL) website - hosting notes
==========================================================
Department of Chemical Engineering, IIT Dharwad
PI: Prof. C. Ravikumar (ravikumar@iitdh.ac.in)


1. What this is
---------------
A static website: one HTML page plus images. No server-side code, no database,
no build step, no login.

  index.html          the whole site (HTML, CSS and a small amount of JavaScript)
  assets/img/         photos, microscopy images and figures
  assets/covers/      journal cover thumbnails for the publication list
  assets/logo/        lab logo (SVG and PNG) and favicon
  assets/fa/          Font Awesome 6.4.0 icon font (self-hosted, free licence)

Total size is about 13 MB.


2. Option A - host on the institute domain
------------------------------------------
Copy the whole folder, keeping the folder structure, to any web server
(Apache, Nginx, IIS, or the institute CMS's static file area).
Serve index.html as the default page.

All paths are relative, so the site works from a sub-path, for example:
  https://www.iitdh.ac.in/cnl/
  https://cnl.iitdh.ac.in/

Nothing needs configuring. HTTPS is recommended.


3. Option B - host free on GitHub Pages
---------------------------------------
1. Sign in at https://github.com and create a new, empty public repository
   (for example "cnl-lab"). Do not add a README or licence.
2. In this folder, run:
     git remote add origin https://github.com/<your-username>/cnl-lab.git
     git push -u origin main
3. On GitHub, open the repository > Settings > Pages.
   Under "Build and deployment", choose Source: "Deploy from a branch",
   Branch: "main", folder "/ (root)", and Save.
4. After a minute the site is live at
     https://<your-username>.github.io/cnl-lab/

The .nojekyll file tells GitHub to serve the files as they are.
To use a custom domain later, add it under Settings > Pages > Custom domain.


4. External resources the page loads
------------------------------------
- Google Fonts: "Poppins" and "Montserrat", from fonts.googleapis.com and
  fonts.gstatic.com. If these are blocked, the page falls back to Segoe UI or
  Arial and still works.

The icon font is included in assets/fa/, so no other CDN is used.
There are no analytics, trackers, cookies or third-party scripts.
External links (Google Scholar, DOIs, LinkedIn, software sites) open in a new tab.
The contact form does not send anything to a server: it opens the visitor's
own email app with the message filled in, addressed to ravikumar@iitdh.ac.in.


5. Updating content
-------------------
All text is in index.html:
- The publication list, paper figures and gallery are defined in JavaScript
  arrays (PUBS, FIGS, GAL) near the end of the file. Add an entry to add an item.
- People, projects, teaching and news are plain HTML sections.
  Each section starts with a comment such as <!-- PEOPLE -->.

Recommended image sizes:
- people photos: 1080 x 1080
- gallery photos: 1440 x 1080 (every 7th photo is shown as a large tile)
- research images: 1620 x 1080


6. Note on journal covers
-------------------------
The thumbnails in assets/covers/ are publisher journal or issue covers, shown next to
the lab's own papers. If institute policy requires it, they can be removed:
delete the folder and the <img class="cov"...> part of the publication template
in index.html.

All other images are the lab's own photographs and figures from the lab's papers.
