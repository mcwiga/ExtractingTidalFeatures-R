# The shape of tides

The goal of this project is to analyse tide times in Galway and try to
extract some information on the periodicity of tide times. We’ll use
methods from an area of maths called topology.

We first load the R-TDA package

    #install.packages('TDA')
    library(TDA)

We will now read tide times from 15/03-29/03.

    tides <- read.csv(file="/Users/jamesmcgloin/Documents/CodingProjects/The-Shape-of-Tides/galwaytides.csv", nrows=3411, header=FALSE)
    height <- tides[,8]

We now create an index to sample 200 values from our tide times

    index = seq(1,200)

We create three vectors the first containing tide times at time
*t*<sub>0</sub> the second containing values at
*t*<sub>0</sub> + 2*h**r**s* and the third at *t* + 4*h**r**s* .

    h <- c()  # heights
    h2 <- c() # heights at t + 2h
    h4 <- c() # heights at t + 4h
    for (i in index) {
      h  <- append(h,  height[i])
      h2 <- append(h2, height[i+20])
      h4 <- append(h4, height[i+40])
    }

We know create a data frame consisting of 3 columns corresponding to
*h*, *h*<sub>2</sub> and *h*<sub>4</sub> and create a 3*D* plot of the
data

    #install.packages("plotly")
    library(plotly)

    ## Loading required package: ggplot2

    ## 
    ## Attaching package: 'plotly'

    ## The following object is masked from 'package:ggplot2':
    ## 
    ##     last_plot

    ## The following object is masked from 'package:stats':
    ## 
    ##     filter

    ## The following object is masked from 'package:graphics':
    ## 
    ##     layout

    data = data.frame(h,h2,h4)
    fig <-plot_ly(data = data, x=~h, y=~h2, z=~h4, type="scatter3d", mode="markers")%>%
            layout(title = 'Tide Heights', plot_bgcolor = "#e5ecf6")
    fig

<div id="htmlwidget-65a4d12296f37db1cd69" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-65a4d12296f37db1cd69">{"x":{"visdat":{"2f5975e34018":["function () ","plotlyVisDat"]},"cur_data":"2f5975e34018","attrs":{"2f5975e34018":{"x":{},"y":{},"z":{},"mode":"markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter3d"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Tide Heights","plot_bgcolor":"#e5ecf6","scene":{"xaxis":{"title":"h"},"yaxis":{"title":"h2"},"zaxis":{"title":"h4"}},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[-0.733,-0.798,-0.877,-0.926,-0.983,-1.046,-1.089,-1.132,-1.18,-1.209,-1.225,-1.288,-1.316,-1.344,-1.371,-1.387,-1.391,-1.397,-1.398,-1.397,-1.373,-1.365,-1.343,-1.31,-1.272,-1.242,-1.233,-1.181,-1.157,-1.147,-1.098,-1.054,-1.045,-0.992,-0.948,-0.919,-0.885,-0.829,-0.776,-0.73,-0.68,-0.624,-0.575,-0.514,-0.452,-0.401,-0.331,-0.268,-0.201,-0.146,-0.079,-0.007,0.048,0.109,0.171,0.237,0.281,0.344,0.408,0.469,0.53,0.58,0.657,0.685,0.737,0.814,0.842,0.911,0.831,0.943,1,1.044,1.067,1.1,1.153,1.171,1.199,1.224,1.26,1.286,1.298,1.348,1.339,1.351,1.365,1.344,1.336,1.315,1.28,1.216,1.165,1.162,1.084,1.017,0.996,0.923,0.857,0.831,0.767,0.673,0.615,0.548,0.494,0.426,0.358,0.316,0.241,0.164,0.104,0.028,-0.042,-0.107,-0.166,-0.234,-0.304,-0.366,-0.43,-0.511,-0.568,-0.639,-0.699,-0.759,-0.814,-0.892,-0.964,-1.022,-1.087,-1.159,-1.236,-1.277,-1.345,-1.419,-1.461,-1.486,-1.545,-1.588,-1.614,-1.638,-1.663,-1.686,-1.708,-1.714,-1.715,-1.724,-1.724,-1.724,-1.723,-1.713,-1.698,-1.66,-1.606,-1.563,-1.538,-1.504,-1.449,-1.423,-1.405,-1.353,-1.293,-1.242,-1.224,-1.153,-1.068,-1.04,-0.979,-0.9,-0.847,-0.788,-0.73,-0.673,-0.602,-0.519,-0.46,-0.38,-0.309,-0.231,-0.151,-0.073,-0.02,0.068,0.147,0.198,0.266,0.319,0.387,0.434,0.496,0.58,0.629,0.72,0.796,0.799,0.883,0.957,1.024,1.066,1.158,1.16,1.229,1.284],"y":[-1.373,-1.365,-1.343,-1.31,-1.272,-1.242,-1.233,-1.181,-1.157,-1.147,-1.098,-1.054,-1.045,-0.992,-0.948,-0.919,-0.885,-0.829,-0.776,-0.73,-0.68,-0.624,-0.575,-0.514,-0.452,-0.401,-0.331,-0.268,-0.201,-0.146,-0.079,-0.007,0.048,0.109,0.171,0.237,0.281,0.344,0.408,0.469,0.53,0.58,0.657,0.685,0.737,0.814,0.842,0.911,0.831,0.943,1,1.044,1.067,1.1,1.153,1.171,1.199,1.224,1.26,1.286,1.298,1.348,1.339,1.351,1.365,1.344,1.336,1.315,1.28,1.216,1.165,1.162,1.084,1.017,0.996,0.923,0.857,0.831,0.767,0.673,0.615,0.548,0.494,0.426,0.358,0.316,0.241,0.164,0.104,0.028,-0.042,-0.107,-0.166,-0.234,-0.304,-0.366,-0.43,-0.511,-0.568,-0.639,-0.699,-0.759,-0.814,-0.892,-0.964,-1.022,-1.087,-1.159,-1.236,-1.277,-1.345,-1.419,-1.461,-1.486,-1.545,-1.588,-1.614,-1.638,-1.663,-1.686,-1.708,-1.714,-1.715,-1.724,-1.724,-1.724,-1.723,-1.713,-1.698,-1.66,-1.606,-1.563,-1.538,-1.504,-1.449,-1.423,-1.405,-1.353,-1.293,-1.242,-1.224,-1.153,-1.068,-1.04,-0.979,-0.9,-0.847,-0.788,-0.73,-0.673,-0.602,-0.519,-0.46,-0.38,-0.309,-0.231,-0.151,-0.073,-0.02,0.068,0.147,0.198,0.266,0.319,0.387,0.434,0.496,0.58,0.629,0.72,0.796,0.799,0.883,0.957,1.024,1.066,1.158,1.16,1.229,1.284,1.293,1.361,1.38,1.411,1.421,1.447,1.439,1.432,1.432,1.429,1.405,1.396,1.345,1.327,1.295,1.257,1.201,1.193,1.159,1.11],"z":[-0.68,-0.624,-0.575,-0.514,-0.452,-0.401,-0.331,-0.268,-0.201,-0.146,-0.079,-0.007,0.048,0.109,0.171,0.237,0.281,0.344,0.408,0.469,0.53,0.58,0.657,0.685,0.737,0.814,0.842,0.911,0.831,0.943,1,1.044,1.067,1.1,1.153,1.171,1.199,1.224,1.26,1.286,1.298,1.348,1.339,1.351,1.365,1.344,1.336,1.315,1.28,1.216,1.165,1.162,1.084,1.017,0.996,0.923,0.857,0.831,0.767,0.673,0.615,0.548,0.494,0.426,0.358,0.316,0.241,0.164,0.104,0.028,-0.042,-0.107,-0.166,-0.234,-0.304,-0.366,-0.43,-0.511,-0.568,-0.639,-0.699,-0.759,-0.814,-0.892,-0.964,-1.022,-1.087,-1.159,-1.236,-1.277,-1.345,-1.419,-1.461,-1.486,-1.545,-1.588,-1.614,-1.638,-1.663,-1.686,-1.708,-1.714,-1.715,-1.724,-1.724,-1.724,-1.723,-1.713,-1.698,-1.66,-1.606,-1.563,-1.538,-1.504,-1.449,-1.423,-1.405,-1.353,-1.293,-1.242,-1.224,-1.153,-1.068,-1.04,-0.979,-0.9,-0.847,-0.788,-0.73,-0.673,-0.602,-0.519,-0.46,-0.38,-0.309,-0.231,-0.151,-0.073,-0.02,0.068,0.147,0.198,0.266,0.319,0.387,0.434,0.496,0.58,0.629,0.72,0.796,0.799,0.883,0.957,1.024,1.066,1.158,1.16,1.229,1.284,1.293,1.361,1.38,1.411,1.421,1.447,1.439,1.432,1.432,1.429,1.405,1.396,1.345,1.327,1.295,1.257,1.201,1.193,1.159,1.11,1.063,1.006,0.963,0.884,0.823,0.763,0.675,0.607,0.53,0.446,0.399,0.324,0.26,0.212,0.124,0.073,-0.005,-0.093,-0.153,-0.216],"mode":"markers","type":"scatter3d","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

We can see clearly from this plot that there is some periodic motion
going on in our data. We’ll now look at a way of extracting this info
using topological data analysis.

We create our Vietoris Rips complex using the ripsDiag() function. I’l
set max dimension as 1 as I won’t be considering persistence in the
second homology group or above. In fact this would be ineffecient to
calculate and, at least in *H*<sub>2</sub>, we don’t detect any
interesting features (I didn’t bother computing for higher homology
groups but I suspect a similar result ).

I’ll set max scale to 5 as this turns out to be an appropriate scale for
our data and I’ll use the standard Eulidean distance as our metric.

    maxdimension <- 1
    maxscale <- 5
    Diag <- ripsDiag(X = data.frame(h,h2,h4),
                     maxdimension,
                     maxscale,
                     dist = "euclidean",
                     library = "GUDHI",
                     printProgress = FALSE)

Now we plot a persistence diagram of our data

    #print(Diag[["diagram"]])
    plot(Diag[["diagram"]], barcode=FALSE,  main = "Persistence Diagram")
    legend(3.5, 5, legend=c("Holes", "Components"),
           col=c("red", "black"), cex=0.8, pch = c(17,19))

![](ShapeOfTides_files/figure-markdown_strict/unnamed-chunk-8-1.png)

The red triangles in our diagrams correspond to birth/death times of
“holes” and the black dots correspond to birth/death times of connected
components

And finally we output a barcode of persisting features in
*H*<sub>0</sub> and *H*<sub>1</sub>.

    plot(Diag[["diagram"]], barcode=TRUE,  main = "Barcode")
    legend("topright", legend=c("Holes", "Components"),
           col=c("red", "black"), cex=0.8, lty= 1:1)

![](ShapeOfTides_files/figure-markdown_strict/unnamed-chunk-9-1.png)

## Conclusion

We see from both the persistence diagram and the bar code that there is
persistence in the second homology group, i.e. there is a 1-dimensional
hole in our data.

This is exactly what we should expect with the motion of the tide!
Really the hole that we are picking up on is that of the moon orbiting
the earth which in my opinion is pretty neat.
