---
# the default layout is 'page'
icon: fa-fw fa-solid fa-rectangle-list
order: 5
---

<head>
    <meta charset="utf-8">
    <title>Redirecting to MySoftwareList</title>
    <meta http-equiv="refresh" content="0; url=https://azimstech.github.io/MySoftwareList/">
    <link rel="canonical" href="https://azimstech.github.io/MySoftwareList/">
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

<p>Redirecting to MySoftwareList...</p>
<a href="https://azimstech.github.io/MySoftwareList/">Click here if not redirected</a>
