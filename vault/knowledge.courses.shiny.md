---
id: wdqnPrErw725XePguupiQ
title: Shiny
desc: ''
updated: 1638373464138
created: 1617018171320
---


Following 

https://edu.isb-sib.ch/course/view.php?id=498

SIB-shiny21 (mdp, log: ss-sib)

https://docs.google.com/document/d/1pohr5PyiV-lTJquviSrmXaNz7Jaw-PFA-bgXJ8g0FiI/edit



https://marionilab.cruk.cam.ac.uk/iSEE_allen/

http://genebrowser.unige.ch/telagirdon/#query_the_atlas


# COVID oriented shiny apps

https://infocovid.smc.unige.ch/

https://ibz-shiny.ethz.ch/covid-19-re-international/

see associated git 
https://github.com/covid-19-Re


https://renkulab.shinyapps.io/COVID-19-Epidemic-Forecasting/_w_c80f7467/?tab=jhu_pred&country=Switzerland


# deployment

using shinyproxy.io
via Apache

## for the price app
https://oolonek.shinyapps.io/price_app/

cd to price_app folder

library(rsconnect)
deployApp()
