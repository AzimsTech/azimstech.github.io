---
# the default layout is 'page'
icon: fa-fw fa-solid fa-rocket
order: 6
---
<head>
    <script>
        // Runs instantly — before page renders
        (function() {
            var url = window.location.href;
            var lower = url.toLowerCase();
            if (url !== lower) {
                window.location.replace(lower);
            }
        })();
    </script>
    <meta charset="utf-8">
    <title>Redirecting to OpenWrt Builder</title>
    <meta http-equiv="refresh" content="0; url=https://azimstech.github.io/OpenWrt-Builder/">
    <link rel="canonical" href="https://azimstech.github.io/OpenWrt-Builder/">
</head>
<p>Redirecting to OpenWrt Builder...<br>
<a href="https://azimstech.github.io/OpenWrt-Builder/">Click here if not redirected</a></p>