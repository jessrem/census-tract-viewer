# census-tract-viewer
Google Satellite and Street map viewer for Census Tracts by GeoID

# Census Tract Map & Street View

A tiny static web tool: type an 11-digit Census tract GEOID and see its boundary on a
map (street or satellite), with one-click links into Google Maps / Street View.

**No API key and no build step.** It's three files:

- `index.html` — the app
- `tract_coords.js` — every 2024 Census tract's internal-point coordinate (baked in, ~3 MB)
- `README.md` — this file

Boundaries are fetched live from the U.S. Census TIGERweb service; basemap tiles come from
Esri; Street View opens in Google Maps in a new tab. All over HTTPS, all keyless.

## Host it on GitHub Pages (about 2 minutes)

1. Create a new GitHub repository (e.g. `tract-map`).
2. Upload these three files to the repository root (drag-and-drop in the GitHub web UI, or
   `git add . && git commit -m "add tract map" && git push`).
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**, pick the
   `main` branch and the `/ (root)` folder, and **Save**.
5. Wait ~1 minute. Your tool will be live at:
   `https://<your-username>.github.io/<repo-name>/`

Share that URL — anyone can use it, no key or install required.

## Notes

- `tract_coords.js` is ~3 MB; GitHub Pages gzip-compresses it, so first load is roughly
  1 MB over the wire and instant thereafter (browser-cached).
- Keep all three files in the **same folder** (the repo root) — `index.html` loads
  `tract_coords.js` by relative path.
- Coordinates are from the 2024 Census gazetteer (tract internal points); boundaries are
  the current TIGERweb Census Tracts layer.
- Nothing is tracked or stored; it's a fully client-side page.
