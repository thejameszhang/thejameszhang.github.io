---
layout: page
title: CV
permalink: /cv/
nav: true
nav_order: 5
nav_href: /assets/pdf/james-zhang-resume.pdf # nav opens the resume PDF directly (new tab)
nav_blank: true
---

<!-- Tidy: the CV is the PDF, so there is no HTML CV page. This stub only supplies the
     "CV" nav item and redirects any direct /cv/ visit to the resume PDF.
     (The original al-folio CV layout read _data/cv.yml; restore `layout: cv` if ever wanted.) -->

<meta http-equiv="refresh" content="0; url={{ '/assets/pdf/james-zhang-resume.pdf' | relative_url }}" />
<script>
  window.location.replace("{{ '/assets/pdf/james-zhang-resume.pdf' | relative_url }}");
</script>

My CV is available as a [PDF]({{ '/assets/pdf/james-zhang-resume.pdf' | relative_url }}).
