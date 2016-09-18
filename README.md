---
title: "Interactive ggvis Graphics"
author: "Glenda Ascencio"
date: "August 28, 2016"
runtime: shiny
output: html_document
---

ggvis provides a number of ways to enhance plots with interacticity. For example, the density plot below allows users to set the kernel and bandwidth of the plot.

```{r echo = FALSE, message = FALSE}
library(ggvis)

mtcars %>% ggvis(x = ~wt) %>%
    layer_densities(
      adjust = input_slider(.1, 2, value = 1, step = .1, label = "Bandwidth adjustment"),
      kernel = input_select(
        c("Gaussian" = "gaussian",
          "Epanechnikov" = "epanechnikov",
          "Rectangular" = "rectangular",
          "Triangular" = "triangular",
          "Biweight" = "biweight",
          "Cosine" = "cosine",
          "Optcosine" = "optcosine"),
        label = "Kernel")
    )
```


