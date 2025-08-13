---
# the default layout is 'page'
icon: fa-fw fa-solid fa-download
order: 7
---

<head>
    <meta charset="utf-8">
    <title>Redirecting to ChatGPT-PWA</title>
    <meta http-equiv="refresh" content="0; url=https://azimstech.github.io/ChatGPT-PWA/">
    <link rel="canonical" href="https://azimstech.github.io/ChatGPT-PWA/">
    <script>
        window.onload = () => {
            currentURL = window.location.href;
            lowerCaseURL = currentURL.toLowerCase();
            if (currentURL != lowerCaseURL) {
                location.replace(lowerCaseURL);
            }
        };
    </script>
</head>

<p>Redirecting to ChatGPT-PWA...</p>
<a href="https://azimstech.github.io/ChatGPT-PWA/">Click here if not redirected</a>
