---
layout: page
title: Jupyter notebook
permalink: /notebook/
---

<style>
  .jupyter-notebook-iframe-container {
    position: relative;
    width: 100%;
    padding-bottom: 80%;
    overflow: hidden;
  }
  .jupyter-notebook-iframe-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: none;
  }
</style>

# Jupyter Notebook Preview

<div class="jupyter-notebook-iframe-container">
  <iframe
    src="{{ site.baseurl }}/notebooks/customer_churn_data_prep.ipynb.html"
    onload="enhanceNotebook(this)">
  </iframe>
</div>

<script>
  function enhanceNotebook(iframe) {
    // 1) Resize the container so no part of the notebook is clipped
    const doc = iframe.contentWindow.document.documentElement;
    const fullH = doc.scrollHeight + 10; 
    iframe.parentElement.style.paddingBottom = fullH + 'px';

    // 2) Inject wrapping rules so long lines break instead of overflow
    const wrapStyles = iframe.contentWindow.document.createElement('style');
    wrapStyles.textContent = `
      pre, code, .highlight {
        white-space: pre-wrap !important;
        word-wrap: break-word !important;
        overflow-wrap: break-word !important;
      }
    `;
    iframe.contentWindow.document.head.appendChild(wrapStyles);
  }
</script>