---
title: "CV"
permalink: /cv/
---

<p style="text-align:center; font-size: 1.2em; margin-bottom: 1em;">
My CV (scroll below or download directly):
</p>

<!-- Download button -->
<div style="text-align:center; margin-bottom: 1em;">
  <a href="/files/Pulliam_CV_5_15_2025.pdf" target="_blank" rel="noopener noreferrer"
     style="display:inline-block; background-color:#007acc; color:white; padding:0.6em 1.2em; 
            border-radius:5px; text-decoration:none; font-weight:bold;">
    Download CV PDF
  </a>
</div>

<!-- PDF.js container -->
<div id="pdf-container" style="width:100%; max-width:800px; margin:auto; border:1px solid #ccc;"></div>

<!-- PDF.js library from CDN -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.10.141/pdf.min.js"></script>

<script>
const url = '/files/Pulliam_CV_5_15_2025.pdf';
const pdfjsLib = window['pdfjs-dist/build/pdf'];

// Use the CDN worker to avoid GitHub Pages CORS issues
pdfjsLib.GlobalWorkerOptions.workerSrc = 'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.10.141/pdf.worker.min.js';

const container = document.getElementById('pdf-container');

// Load the PDF
pdfjsLib.getDocument(url).promise.then(pdf => {
  for (let pageNum = 1; pageNum <= pdf.numPages; pageNum++) {
    pdf.getPage(pageNum).then(page => {
      const viewport = page.getViewport({ scale: 1.5 });
      const canvas = document.createElement('canvas');
      container.appendChild(canvas);
      const ctx = canvas.getContext('2d');

      // Scale to container width
      const scale = container.clientWidth / viewport.width;
      const scaledViewport = page.getViewport({ scale: 1.5 * scale });

      canvas.width = scaledViewport.width;
      canvas.height = scaledViewport.height;

      page.render({ canvasContext: ctx, viewport: scaledViewport });
    });
  }
});
</script>
