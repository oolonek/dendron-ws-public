---
id: 45ZO3MwFcCvGiJw88w4Ud
title: Tests
desc: ''
updated: 1678176685035
created: 1610451373351
bibliography:
  - /Users/pma/Documents/library_red.bib
---

# Bib integration tests in dendron

The .bib is loaded if the path to th .bib is in the header (check in the .md file)


active citation @Gerwick2012a

hardcoded copy pasted citation Gerwick and Moore (2012)


Gerwick, William H, and Bradley S Moore. 2012. “Lessons from the past and charting the future of marine natural products drug discovery and chemical biology.” Chemistry & Biology 19 (1): 85–98. https://doi.org/10.1016/j.chembiol.2011.12.014.


The citation can be previewed only if Markdown Preview Enhanced is loaded. However the links can then not be viewed by Dendron Markdown Preview. Kevin is working on it https://discord.com/channels/717965437182410783/735365126227493004/794977929406185502

Meanwhile a solution is to copy paste the citation from the preview to the .md.

I now hae to check if links are displayed and active when published.
Locally, hey are active in the .md


[[projects.tramadol.data]]

This is how the preview looks like:

![](/assets/images/2021-01-12-12-46-02.png)

# References

Here should appear the refs


@Blunt2009



```
<p>[[projects.tramadol.data]]</p>
<p>This is how the preview looks like:</p>
<p><img src="/assets/images/2021-01-12-12-46-02.png" /></p>
<h1 id="references">References</h1>
<p>Here should appear the refs</p>
<p><span class="citation" data-cites="Blunt2009">@Blunt2009</span></p>

```
@Blunt2009


### 2021-01-12 15:32

Just found a pandoc guru https://niszet.hatenablog.com/ and posted an issue on his git repo https://github.com/niszet/pandocplay/issues/5

Pandoc play might be a way to go to have these citation displayed in line.

I use it with the folowing option : 

`"Pandocplay.Pandoc.args": " -s --bibliography '/Users/pma/Documents/library_red.bib'"
`
Beware of the space character before the s !





## example of outputs 


@Brown2012a

@oolonek

@Brown2012a


@Gerwick2012a


@Blunt2009

```
---
bibliography: /Users/pma/Documents/library_red.bib
---

@Brown2012a

@Gerwick2012a

@Blunt2009

```

@jimenez-lunaDrugDiscoveryExplainable2020```


<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" lang="" xml:lang="">
<head>
  <meta charset="utf-8" />
  <meta name="generator" content="pandoc" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes" />
  <title>runpandoctmp</title>
  <style>
    code{white-space: pre-wrap;}
    span.smallcaps{font-variant: small-caps;}
    span.underline{text-decoration: underline;}
    div.column{display: inline-block; vertical-align: top; width: 50%;}
    div.hanging-indent{margin-left: 1.5em; text-indent: -1.5em;}
    ul.task-list{list-style: none;}
    .display.math{display: block; text-align: center; margin: 0.5rem auto;}
  </style>
  <!--[if lt IE 9]>
    <script src="//cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv-printshiv.min.js"></script>
  <![endif]-->
</head>
<body>
<p><span class="citation" data-cites="Brown2012a">Brown and Okuno (2012)</span></p>
<p><span class="citation" data-cites="Gerwick2012a">Gerwick and Moore (2012)</span></p>
<p><span class="citation" data-cites="Blunt2009">Blunt et al. (2009)</span></p>
<p><span class="citation" data-cites="jimenez-lunaDrugDiscoveryExplainable2020">(<span class="citeproc-not-found" data-reference-id="jimenez-lunaDrugDiscoveryExplainable2020"><strong>???</strong></span>)</span></p>
<div id="refs" class="references hanging-indent" role="doc-bibliography">
<div id="ref-Blunt2009">
<p>Blunt, John W, Brent R Copp, Wan-Ping Hu, Murray H G Munro, Peter T Northcote, and Michèle R Prinsep. 2009. “Marine natural products.” <em>Natural Product Reports</em> 26 (2): 170–244. <a href="https://doi.org/10.1039/b805113p">https://doi.org/10.1039/b805113p</a>.</p>
</div>
<div id="ref-Brown2012a">
<p>Brown, J. B., and Yasushi Okuno. 2012. “Systems Biology and Systems Chemistry: New Directions for Drug Discovery.” <em>Chemistry &amp; Biology</em> 19 (1): 23–28. <a href="https://doi.org/10.1016/j.chembiol.2011.12.012">https://doi.org/10.1016/j.chembiol.2011.12.012</a>.</p>
</div>
<div id="ref-Gerwick2012a">
<p>Gerwick, William H, and Bradley S Moore. 2012. “Lessons from the past and charting the future of marine natural products drug discovery and chemical biology.” <em>Chemistry &amp; Biology</em> 19 (1): 85–98. <a href="https://doi.org/10.1016/j.chembiol.2011.12.014">https://doi.org/10.1016/j.chembiol.2011.12.014</a>.</p>
</div>
</div>
</body>
</html>

```




Some news at https://github.com/notZaki/PandocCiter/issues/14#issuecomment-1457550422
