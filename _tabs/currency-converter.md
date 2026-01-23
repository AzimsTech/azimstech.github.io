---
# the default layout is 'page'
icon: fa-fw fa-solid fa-sack-dollar
order: 9
---

<head>
    <meta charset="utf-8">
    <title>Redirecting to Currency Converter</title>
    <meta http-equiv="refresh" content="0; url=https://azimstech.github.io/currency-converter/">
    <link rel="canonical" href="https://azimstech.github.io/currency-converter/">
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

<p>Redirecting to Currency Converter...<br>
<a href="https://azimstech.github.io/currency-converter/">Click here if not redirected</a></p>
