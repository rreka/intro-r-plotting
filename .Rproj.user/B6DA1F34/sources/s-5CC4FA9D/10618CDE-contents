#### Workshop information ####

# Data Skills for Science
# Plotting data with ggplot2 in R
# Roger Reka, University of Windsor, Fall 2019

# Includes some information that was adapted, with permission, from the Data Carpentry "Data Analysis and Visualization in R for Ecologists" lesson.

# This lesson is licensed under a Creative Commons CC-BY license. 




#### Recap of the basic fundamentals of R ####

# R is a ** programming language ** that is widely used to work with research data. People use R for:
    # data wrangling
    # data manipulation and organization
    # statistical analysis
    # plotting and graphing

# RStudio is an integrated development environment (IDE) for the R programming language. RStudio gives you the tools and interfaces to write R scripts and pass R commands.

## Help ##
# There are built-in help functions and tools in R & RStudio.

# If you're confused about R in general, you can use the help menu in RStudio and search for topics.

# If you need help with a particular function, you can use the `?` command before the function name.

?round

## Objects ##
# Objects store data in memory. You **assign** values to objects using the assignment operator: <- 
weight_kg <- 55
mass <- 47.5    
age  <- 122

# You can do operations on objects

weight_kg * 2.2
mass <- mass * 2.0
age  <- age - 20
mass_index <- mass/age

## Functions ##
# Functions are canned scripts that automate complicated sets of commands. Many come buil-in with R, and many more come from third-party packages that we can install into R.

a = 9
b <- sqrt(a)
b

## Vectors and data types ##
# Sequences of data are stored in vectors, using the combine function: `c`

weight_kg <- c(50, 60, 65, 82)
weight_kg

class(weight_kg)

# There are 4 main data types in R that we'll be working with:

# numeric; any number with a floating decimal point
class(231.3)

# integer
class(3)
class(3L)

# character
class('Hello, these are characters of text. Numbers can be characters as well: 1, 2, 3. As long as everything is bounded by quotation marks')

# logical
class(TRUE)
class(FALSE)





#### Importing data into R and examining it ####

# In order to get started with working with data in R, we are going to use the `dplyr` third-party package. `dplyr` provides us with many tools for importing, manipulating and shaping our data, and extends R's basic capabilities. `dplyr` is found in the `tidyverse` package of packages. `tidyverse` also contains the `ggplot2` package that we'll use later on.

# First thing's first. You need to install the `tidyverse` package. You only need to do this the first time you use it on your computer. The `install.packages()` function will download the package from the R repository (CRAN), and install it on your machine.

install.packages("tidyverse")

# Once you have installed a package, you need to load it every time you use it in R. To load a package, use the `library()` function:

library(tidyverse)   # loads `tidyverse`, including `dplyr`

# Load your data into a `dplyr` DataFrame:

surveys_complete <- read_csv("data/surveys_complete.csv")
  
# Examine the structure of our new object `surveys_complete`

str(surveys_complete)

# Notice that the class of the object is a `tbl_df`. This is referred to as a tibble DataFrame, a  `dplyr` DataFrame. Tibbles extend the capability of regular DataFrames and allow us to work more easily with tabular data.

## We can use the function `select()` to select columns of a tibble DataFrame: 





## We can use `filter()` to select rows based on a specific criteria:





##  If we want to do multiple operations at once, we can use pipes, which are a special feature of `dplyr`. Pipes let us take the **output** of one function/object and send it directly to the next.

## The shortcut for creating a pipe is Ctrl + Shift + M on a PC, or Cmd + Shift + M on a Mac.




#### Data visualization with ggplot2 ####

# R comes with built-in graphing functions, but they aren't easily able to create complex plots and work with our data.

# `ggplot2` is one of the most widely used plotting packages in R, and it comes with `tidyverse`. It provides a more programmatic interface for specifying what variables to plot, how they are displayed, and general visual properties. 

# `ggplot2` functions like data in the 'long' format, i.e., a column for every dimension, and a row for every observation. Well-structured data will save you lots of time when making figures with ggplot2.

# Well structured data looks like:

    ## Each variable has its own column
    ## Each observation has its own row
    ## Each value must have its own cell
    ## Each type of observational unit forms a table

# We build ggplot graphics step-by-step by adding layers of new elements. This is the basic template for ggplot plots:

    ## ggplot(data = <DATA>, mapping = aes(<MAPPINGS>)) +  <GEOM_FUNCTION>()

## Let's demonstrate. Use the `ggplot2()` function to bind the plot to a specific DataFrame using the data argument:





## Now let's define the mapping using the `aes()` function. We will select which variables we want to plot and specify how to present them in the graph.






# Looking at the axes, we can see that R recognizes the variables, but we don't yet see the data on the graph. We need to add 'geoms', the graphical representation of the data in the plot (points, lines, bars). `ggplot2` offers many different geoms, but today we'll use some common ones, including:

    ## `geom_point()` for scatter plots, dot plots, etc.
    ## `geom_boxplot()` for, well, boxplots!
    ## `geom_line()` for trend lines, time series, etc.  

## To add a geom to the plot, use the + operator. We're going to use `geom_point()` first.



## The + operator is also useful because we can modify other ggplot objects. We can create a ggplot template, assign it to an object, and then explore different types of plots.





## ### Challenge with hexbin

## ## To use the hexagonal binning with **`ggplot2`**, first install the `hexbin` package from CRAN:

install.packages("hexbin")
library(hexbin)

## ## Then use the `geom_hex()` function:

surveys_plot +
    geom_hex()

## ## What are the relative strengths and weaknesses of a hexagonal bin plot compared to a scatter plot?


# Building plots with ggplot2 is typically an iterative process. We start by defining the dataset we’ll use, lay out the axes, and choose a geom.

## Then, we start modifying this plot to extract more information from it. For instance, we can add transparency (alpha) to avoid overplotting:






## We can also add colors for all the points:







## Or to color each species in the plot differently, you could use a vector as an input to the argument color. ggplot2 will provide a different color corresponding to different values in the vector. Here is an example where we color with species_id:







## We can also specify the colors directly inside the mapping provided in the ggplot() function. This will be seen by any geom layers and the mapping will be determined by the x- and y-axis set up in aes().






## Notice that we can change the geom layer and colors will be still determined by species_id






## ### Challenge with scatter plots
# 1. Use what you just learned to create a scatter plot of **weight** over **species_id** with the **plot types** showing in different colors. Is this a good way to show this type of data?






#### Boxplots ####

## We can use boxplots to visualize the distribution of weight within each species:



## By adding points to boxplot, we can have a better idea of the number of measurements and of their distribution:






## Notice how the boxplot layer is behind the jitter layer? What do you need to change in the code to put the boxplot in front of the points such that it’s not hidden?




## ### Challenge with boxplots
##  Start with the boxplot we created:
ggplot(data = surveys_complete, mapping = aes(x = species_id, y = weight)) +
   geom_boxplot(alpha = 0) +
   geom_jitter(alpha = 0.3, color = "tomato")

#  Boxplots are useful summaries, but hide the shape of the distribution. For example, if the distribution is bimodal, we would not see it in a boxplot. An alternative to the boxplot is the violin plot, where the shape (of the density of points) is drawn.

## 1. Replace the box plot with a violin plot; see `geom_violin()`.




# In many types of data, it is important to consider the scale of the observations. For example, it may be worth changing the scale of the axis to better distribute the observations in the space of the plot. ** Changing the scale of the axes is done similarly to adding/modifying other components (i.e., by incrementally adding commands). **

## 2. Represent weight on the log10 scale; see `scale_y_log10()`.





# So far, we’ve looked at the distribution of weight within species. Try making a new plot to explore the distribution of another variable within each species.

##  3. Create boxplot for the column `hindfoot_length` overlaid on a jitter layer.





##  4. Add color to the data points on your boxplot according to the type of plot from which the sample was taken (`plot_type`).


#### Plotting time series data ####

# Let's calculate the number of counts per year for each genus. A genus is a rank in the biological classification system.

# First we have to group the data and get the counts for each group. Luckily, there is a `dplyr` function that can do that for us:

str(surveys_complete)

count(surveys_complete, year, genus)

yearly_counts <- count(surveys_complete, year, genus)

yearly_counts

## It is best to visualize time-series data using a line plot. Time is typically on the x-axis, with the other variable on the y:



## This didn't work too well because we plotted the data for all of the genera together. We need to tell ggplot to draw a line for each genus. We do so by modifying the `aes()` function tell ggplot to treat the 'genus' column as the group: 'group = genus'.



## Let's add some colour to make these pop. Using the color argument in the `aes()` function will also automatically group the data, so no need to use the group argument.






