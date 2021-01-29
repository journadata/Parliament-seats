# Parliament-seats
A full code for creating a chart displaying the size of the seats to a parliament. In this case, base on the results of Catalan elections 2017. 


## Read the table

```Resultats2017 <- read.csv("/Users/beatrizgalvez/Downloads/Resultats_2017.csv", header = TRUE)

Resultats2017$Candidatura <- factor(Resultats2017$Candidatura)
Resultats2017$Diputats <- Resultats2017$Escons / sum(Resultats2017$Escons)
Resultats2017$ymax <- cumsum(Resultats2017$Diputats)
Resultats2017$ymin <- c(0, head(Resultats2017$ymax, n= -1))
Resultats2017$labelPosition <- (Resultats2017$ymax + Resultats2017$ymin) / 2 ´´´

## Create the plot

```Parlament2017 <- ggplot(Resultats2017, aes(fill = Candidatura, ymax = ymax, ymin = ymin, xmax = 2, xmin = 1)) + geom_rect() + 
  coord_polar(theta = "y",start=-pi/2) + xlim(c(0, 2)) + ylim(c(0,2)) + geom_text( x=2, aes(y=labelPosition, label=Candidatura)) +  scale_fill_manual(values=c("C's" = "#e8550c", "JUNTSxCAT" = "#01c4b4", "ERC-CatSí" = "#edad08", "PSC" = "#e20a15", "CatComú-Podem" = "#611b73", "CUP" = "#fef100", "PP" = "#0056a6")) +
  theme(legend.position = "bottom") + theme_void()´´´
