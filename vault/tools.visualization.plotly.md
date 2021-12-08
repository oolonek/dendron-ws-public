---
id: FbPaFk83tQd6PGWK2zp6U
title: Plotly
desc: ''
updated: 1636730576483
created: 1612380643104
---

# plotly html integration

https://ig248.gitlab.io/post/2018-11-05-plotly-sample/  (merci Jo)

after a bunch of slightly outdate tutorial I found this one wich worked in my case

https://medium.com/analytics-vidhya/how-to-export-a-plotly-chart-as-html-3b5df568df4a

 
 just embbed like this

```html
<div class="container-fluid" style="margin-top:40px">
  <iframe src="sariette_pos_pos_organisms_sunburst.html" width="100%" height="600" style="border:none;"></iframe>
</div>
```



# customization of fig (margin/titles and other nasty stuff)



```python
# %%
# using px express to plot some quick and dirty sunbursts (https://plotly.com/python/sunburst-charts/)
# customize fonts in titles following https://stackoverflow.com/a/57926862
# customize margins following https://stackoverflow.com/a/63162535

import plotly.express as px


fig = px.sunburst(df4cyto_flat, path=['Superclass_cf_DNP_consensus', 'Class_cf_DNP_consensus', 'Subclass_cf_DNP_consensus', 'Parent_Level_1_cf_DNP_consensus'],
                  )
fig.update_layout(
    #font_family="Courier New",
    title_font_family="Courier New",
    title_font_color="black",
    title_font_size=14,
    legend_title_font_color="black",
    title_text="<b> Overview of the consensus chemical annotions <br> as the superclass, class, subclass and parent_1 level for <br>" + project_name + "</b>",
    title_x=0.5
)

fig.update_layout(
    title={
        'text': "<b> Overview of the consensus chemical annotions <br> as the superclass, class, subclass and parent_1 level for <br>" + '<span style="font-size: 20px;">' + project_name + '</span>' + "</b>",
        'y':0.96,
        'x':0.5,
        'xanchor': 'center',
        'yanchor': 'top'})

fig.update_layout(margin=dict(l=50, r=50, t=100, b=50)
#,paper_bgcolor="Black"
)

fig.show()
fig.write_html(sunburst_chem_results_path)
```

## On the display via github

https://community.plotly.com/t/how-to-display-plotly-graph-on-github-pages/44398/2


https://automating-gis-processes.github.io/2016/Lesson5-share-on-github.html

https://mertbakir.gitlab.io/hugo/plotly-with-hugo/

When displaying iframe in hugo pages be sure to have 

https://stackoverflow.com/a/66741389




# Monday 06 December 2021

Getting plotly to work within a jupoyter nb file on github https://binnisb.github.io/blog/datascience/2020/04/02/Plotly-in-lab.html

