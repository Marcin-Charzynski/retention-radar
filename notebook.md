---
layout: page
title: Jupyter notebook
permalink: /notebook/
---

# Jupyter Notebook Preview
<style>
.jupyter-notebook-iframe-container {
  position: relative;
  width: 100%;
  padding-bottom: 80%;
  overflow: hidden;
}

.jupyter-notebook-iframe-container iframe {
  position: absolute;
  top: 0; left: 0;
  width: 100%;
  height: 100%;
  border: none;
}
</style>

<div class="jupyter-notebook-iframe-container">
  <iframe src="{{ site.baseurl }}/notebooks/customer_churn_data_prep.ipynb.html"
          onload="resizeIframe(this)"></iframe>
</div>

<script>
function resizeIframe(iframe) {
  setTimeout(() => {
    const doc = iframe.contentWindow.document.documentElement;
    const newH = doc.scrollHeight + 10;
    iframe.parentElement.style.paddingBottom = newH + 'px';
  }, 100);
}
</script>