# Neurodesk Play redirect

This repository redirects https://play.neurodesk.org/ to
https://neurodesk.org/getting-started/hosted/play/.

GitHub Pages deploys only `redirect-site/` on pushes to `main` or a manual
run of `.github/workflows/gh-pages.yml`. No Hugo build, Node dependencies,
or submodules are needed. The legacy Hugo sources are no longer deployed.

`index.html` redirects the home page; `404.html` redirects unknown paths.
Both use an immediate HTML refresh, JavaScript `location.replace`, a canonical
URL, and a visible fallback link. Keep their destination URLs in sync.
These are browser redirects: the home page returns HTTP 200 and unknown paths
return HTTP 404, rather than an HTTP 301 redirect.

Keep the existing Route 53 records, GitHub Pages custom domain
(`play.neurodesk.org`), and HTTPS setting unchanged. Pages must use
**GitHub Actions** as its deployment source.

After deployment, open https://play.neurodesk.org/ and an unknown path such as
https://play.neurodesk.org/old-link/ and confirm both reach the Play page.
