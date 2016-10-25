Ryan Tillis - Developing Data Products - Data Science - Quiz 1 - Coursera
================
<a href="http://www.ryantillis.com"> Ryan Tillis </a>
August 11, 2016

Developing Data Products Quiz 1
-------------------------------

This is Quiz 1 from the Developing Data Products course within the Data Science Specialization. This publication is intended as a learning resource, all answers are documented and explained.

### Questions

<hr>
<font size="+2">1. </font> Which of the following are components in building a machine learning algorithm?

<hr>
<font size="+1"> <b>

-   A server.R file containing a call to shinyServer()

-   A ui.R file containing a call to shinyUI()

</b> </font>

<hr>
<hr>
<font size="+2">2. </font> What is incorrect about the following syntax in ui.R?

``` r
library(shiny)
shinyUI(pageWithSidebar(  
  headerPanel("Data science FTW!"),  
  sidebarPanel(    
     h2('Big text')    
     h3('Sidebar')  
  ),  
  mainPanel(      
       h3('Main Panel text')  
  )
))
```

<hr>
<font size="+1"> <b>

-   Missing a comma in the sidebar panel

</b> </font>

<hr>
<font size="+2">3. </font> Consider the following in ui.R

``` r
shinyUI(pageWithSidebar(  
   headerPanel("Example plot"),  
   sidebarPanel(    
     sliderInput('mu', 'Guess at the mu',value = 70, min = 60, max = 80, step = 0.05,)  ), 
   mainPanel(    
     plotOutput('newHist')  
   )
))
```

``` r
library(UsingR)
data(galton)

shinyServer(  
    function(input, output) {    
       output$myHist <- renderPlot({      
          hist(galton$child, xlab='child height', col='lightblue',main='Histogram')      
          mu <- input$mu      
          lines(c(mu, mu), c(0, 200),col="red",lwd=5)      
          mse <- mean((galton$child - mu)^2)      
          text(63, 150, paste("mu = ", mu))      
          text(63, 140, paste("MSE = ", round(mse, 2)))      
          })      }
)
```

<hr>
<font size="+1"> <b>

-   The server.R output name isn't the same as the plotOutput command used in ui.R.

</b>

</font>

<hr>
<hr>
<font size="+2">4. </font> What are the main differences between creating a Shiny Gadget and creating a regular Shiny App? (Check all that apply)

<hr>
<font size="+1"> <b>

-   Shiny Gadgets are designed to be used by R users in the middle of a data analysis.

-   Shiny Gadgets are designed to have small user interfaces that fit on one page.

</b> </font>

<hr>
<hr>
<font size="+2">5. </font> Consider the following R script:

``` r
library(shiny)
library(miniUI)

pickXY <- function() {
  ui <- miniPage(
    gadgetTitleBar("Select Points by Dragging your Mouse"),
    miniContentPanel(
      plotOutput("plot", height = "100%", brush = "brush")
    )
  )

  server <- function(input, output, session) {
      output$plot <- renderPlot({
        plot(data_frame$X, data_frame$Y, main = "Plot of Y versus X",
           xlab = "X", ylab = "Y")
      })
      observeEvent(input$done, {
        stopApp(brushedPoints(data_frame, input$brush,
                          xvar = "X", yvar = "Y"))
      })
  }

  runGadget(ui, server)
}

my_data <- data.frame(X = rnorm(100), Y = rnorm(100))

pickXY(my_data)
```

Why isn’t it doing what we want?

<hr>
<font size="+1"> <b>

\*No arguments are defined for pickXY()

</b> </font>

<hr>
<hr>
Check out my website at: <http://www.ryantillis.com/>

<hr>
