##load packages

library(shiny)
library(tidyverse)

##load data
#food_data <- read.csv('food.csv', stringsAsFactors = F)
load(file = "food.rdata")

# Define UI for application that draws a histogram
ui <- fluidPage(
  
  # Application title
  titlePanel("Food Production by Country"),
  
  # Sidebar with a slider input for number of bins 
  sidebarLayout(
    sidebarPanel(
      # Select type of trend to plot
      selectInput(inputId = "country", label = strong("Country"),
                  choices = unique(food$Area),
                  selected = "Afghanistan"),
      # Select type of trend to plot
      selectInput(inputId = "item", label = strong("Food Item"),
                  choices = unique(food$Item),
                  selected = "Sugar beet")
    ),
    
    # Show a plot of the generated distribution
    mainPanel(
      plotOutput("distPlot")
    )
  )
)

# Define server logic required to draw a histogram
server <- function(input, output) {
  
  output$distPlot <- renderPlot({
    country <- input$country
    item <- input$item
    dat <- food[food$Area == country & food$Item == item ,]
   ggplot(dat, aes(x = Year, y = Amount)) + geom_line()
  })
}

# Run the application 
shinyApp(ui = ui, server = server)

