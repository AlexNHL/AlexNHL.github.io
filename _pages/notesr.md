---
layout: archive
title: "Notes for R"
permalink: /notesr/
author_profile: true
redirect_from:
---


- Basic commands
    
    ```r
    rm(list=ls())
    # remove the saved variables and objects
    
    getwd()
    # get the current working directory
    
    setwd("/Users")
    # set the diectory to Users
    
    source("code.r")
    # load the r code
    
    # NA = Not Applicable
    # NaN = Not a Number
    
    proc.time() 
    # initial time
    t0 <- proc.time()
    ...
    proc.time()-t0 
    # compute process time
    
    exists("name")
    # check whether the name is in use 
    
    traceback()
    # obtain extra information about an error message
    
    demo(topic)
    # running some demonstration R scripts
    # demo() gives the list of available topics
    
    dput()
    # generate the r code to recreate it
    
    # + R is waiting for more input
    
    # Alt + Shift + K to see all shortcuts
    
    # using == in floating point numbers
    sqrt(2) ^ 2 == 2
    # [1] FALSE
    1 / 49 * 49 == 1
    # [1] FALSE
    # can’t store an infinite number of digits
    # an approximation
    
    near(sqrt(2) ^ 2,  2)
    # [1] TRUE
    near(1 / 49 * 49, 1)
    # [1] TRUE
    
    first(x); nth(x, 2); last(x) # These work similarly to 
    x[1]; x[2]; x[length(x)]
    
    # match the boundary between words with \b
    \bsum\b # to avoid matching summarise, summary, rowsum
    ```

    

- Common functions
    
    
    | Name | Functions | Notice  |
    | --- | --- | --- |
    | ceiling | smallest integer greater than or equal to element |  |
    | floor | largest integer less than or equal to element |  |
    | trunc | ignore the decimal part |  |
    | round* | round to the specified number of decimal places | round(x, digits = 0) |
    |  | *round(x, digits = -2) : rounds to the nearest hundred |  |
    | signif | round to the specified number of significant digits  | signif(x, digits = 6) |
    | sort | sort in ascending order | sort(x, decreasing = FALSE) |
    | cumsum | cumlative sum |  |
    | cumprod | cumlative produce |  |
    | cummean | cumulative means (dplyr) |  |
    | range | vector of min and max |  |
    | str | check the structure  |  |
    | gl | generate factors by specifying the pattern of levels | gl(n, k, labels = seq_len(n)) |
    | na.omit | delete rows in the dataframe containing missing data | na.omit() |
    |  | whether to remove NA values from the calculation | na.rm=TRUE |
    | paste* | concatenates multiple elements into a single element | paste(x,sep=" ", collapse=NULL) |
    |  | *collapse parameter deal with the vector |  |
    | paste0 | default separator value, sep > collapse |  |
    | invisible | makes its content temporary invisible |  |
    | match | return the positions of the matched elements or NA | match(vector1, vector2) |
    | names | display the header / labels | names(data) |
    | names | modify the name attribute of a list | names(list) ← c(”n1”, ”n2”) |
    | head | display first 6 lines of data | head(data) |
    | tail | display last 6 lines of data | tail(data) |
    | table | categorical representation of name and frequency |  |
    | ymd | convert to Year / Month / Day |  |
    | edit | edit the dataset and store the data |  |
    | t | transpose the data between row and column | t() |
    | prop.table | return the row or column proportion (sum=1) | prop.table(data, margin=1/2) |
    | lag | lagging values, (ts) return the next value in ts |  |
    | lead | leading values |  |
    | unique | delete the duplicate values or the rows |  |
    | fix | edit on FUN, assigns the new version to same object | fix(FUN) |
    | edit | edit on FUN, need to assign it to an object | new_FUN = edit(FUN) |
    | stop | stop with error message  | stop(”…”) |
    | options | examine a variety of global options | options(digits=4) (0.XXXX) |
    | eval | given a expression and returns the result | eval(expr) |
    | identical | two objects for being exactly equal | identical(x,y) |
    | gsub | replace all the matches of a pattern from a string | gsub(pattern, replace, str) |
    | file.path | Construct the path to a file from components |  |
    | min_rank | smallest values have the small ranks | min_rank(desc(y)) |
    | mad | median absolute deviation,robust equivalents(outlier) |  |
    | quantile | generalisation of the median: x >25% & <75% | quantile(x, 0.25) |
    | apropos | searches all objects available from global environment | apropos(”replace”) |
    | dir | lists all the files in a directory, takes regular expression and returns file names that match the pattern | head(dir(pattern = "\\.Rmd$")) |
    | object.size | find out the memory of the object | pryr::object_size(multiple obj)  |
    | identical | return T or F that having same value, (0L,0 are different) |  |
    | n_distinct | calculates the number of unique values in a vector | length(unique(...)) |
    | flatten | remove a level hierarchy from a list to vector | unlist() |
    | keep | keep elements where the predicate is TRUE | discard(), for FALSE |
    | any | TRUE, if ≥1 logical element is TRUE | any(logical operator) |
    | some | determine if the predicate is true for any elements | every(),  for all elements |
    | detect | finds the first element where the predicate is true | detect_index(), its position |
    | head_while | take elements from the start of vector while true | tail_while(), for end |
    | reduce | applies FUN repeatedly until only a single element left |  |
    | accumulate | keeps all the interim results | accumulate(`+`), for cumsum |

- Missing value
    
    ```r
    some.evens <- NULL
    # creates a vector with no elements
    some.evens
    # NULL
    some.evens[seq(2, 20, 2)] <- seq(2, 20, 2)
    some.evens
    # NA  2 NA  4 NA  6 NA  8 NA 10 NA 12 NA 14 NA 16 NA 18 NA 20
    # the missing value is bounded
    
    !is.na(some.evens)
    # non-missing values
    
    some.evens[!is.na(some.evens)]
    # return all non-missing value
    
    data %<>% filter(function(x)!all(is.na(x)), .)
    # remove NA in data frame and data table
    
    # aggregation functions obey the usual rule of missing values
    mean() # cannot apply to NA
    
    NA            # logical
    #> [1] NA
    NA_integer_   # integer
    #> [1] NA
    NA_real_      # double
    #> [1] NA
    NA_character_ # character
    #> [1] NA
    ```
    

- Simulation
    - Generate random samples or permutatuions data
        
        ```r
        set.seed(1)
        
        sample(10)
        # random order only from 1 to 10
        
        sample(10, replace=T)
        
        sample(c(-1,0,1), size=20, prob=c(0.25,0.5,0.25), replace=T)
        # specify the probability and size
        # the probability will match up to the sample automatically 
        ```
        
    - Probability distribution functions
        
        ```r
        dnorm(x)
        # probability density function (pdf)
        
        x <- seq(-4,4,0.1)
        plot(x,dnorm(x), type = "l")
        # dorm(x) gives the density of x
        ```
        
        
        ```r
        pnorm(p)
        # cumulative probability distribution function (cdf)
        # F(x) = Pr(X <= x)
        # Pr(X < 1.96)
        pnorm(1.96)
        # 0.9750021
        
        qnorm(q)
        # quantile function
        # inverse of the cumulative distribution function
        # q-th quantile of X is the smallest value of x
        # Pr(X < x) >= q
        q<-c(0.025,0.05,0.5,0.95,0.975)
        qnorm(q)
        # -1.959964 -1.644854  0.000000  1.644854  1.959964
        
        rnorm(n)
        # pseudorandom numbers
        ```
        
    - Binomial distribution
        
        ```r
        dbinom(x, size, prob, log = FALSE)
        # Pr(X = x) = (nCx) p^x (1-p)^(n-x)
        # size = n, prob = p
        # output can be a probability vector
        p<-dbinom(0:20,size=20,prob=1/4)
        
        # Pr(X > 8)
        1-pbinom(8,size=20,prob=1/4)
        # or
        1-sum(p[1:9])
        # p[1] = when x is 0
        
        # find the 0th, 10th, 20th,..., 100th quantiles of X
        # (i.e., the smallest xq such that Pr{X <= xq} >= q)
        q<-seq(0,1,0.1)
        qbinom(q,size=20,prob=1/4)
        # 0  3  3  4  4  5  5  6  7  8 20
        round(cumsum(p),digits=4)
        #  [1] 0.0032 0.0243 0.0913 0.2252 0.4148 0.6172 0.7858
        #      0.8982 0.9591 0.9861 0.9961 0.9991 0.9998
        # [14] 1.0000 1.0000 1.0000 1.0000 1.0000 1.0000 1.0000 1.0000
        # p<-dbinom(0:20,size=20,prob=1/4)
        # Pr{X ≤ 2} = 0.0913 and Pr{X ≤ 3} = 0.2252
        # Therefore, the 10th quantile is 3.
        ```
        
    
    | Distribution  | Code | Argument  |
    | --- | --- | --- |
    | Beta | beta | shape1, shape2, ncp |
    | Binomial | binom | size, prob |
    | Chi‐square | chisq | df, ncp |
    | Exponential | exp | rate |
    | F | f | df1, df2, ncp |
    | Gamma | gamma | shape, scale |
    | Geometric | geom | prob |
    | Hypergeometric | hyper  | m, n, k |
    | Logistic | logis  | location, scale |
    | Negativebinomial | nbinom | size, prob |
    | Normal | norm | mean, sd |
    | Possion  | pois | lambda |
    | Uniform | unif | min, max |
    | Wilcoxon | wilcox | m, n |

- Input
    - readline() , scan()
        - Accept user’s input from keyboard (character value)
        
        ```r
        input<-readline()
        # if input is a number
        input<-as.numeric(input)
        
        x <- scan()
        # can input a number vector
        ```
        
    - .dat
        
        ```r
        data <- read.table("1.dat", header=T)
        # read the data file with header
        ```
        
    - .csv
        
        ```r
        read.csv('1.csv')
        
        allframes = sapply(1:20,function(x)read.csv(paste(x,'csv',sep='.')))
        # reading 20 csv files, from "1.csv" to "20.csv"
        ```
        

- Output
    - .dat
        
        ```r
        write.table(x, file="1.dat", row.names=F)
        # write x to an ASCII file
        # Without row.names=F 
        # R will automatically add in the row number in x
        ```
        
    - .csv
        - Comma separated value file
        
        ```r
        write.csv(x,file="1.csv", row.names=F)
        ```
        
        

        
- sprintf()
   - Control the format of outputting numbers
        ```r
        sprintf(fmt, ...)
        sprintf("Pi is %f", pi)
        # output real number with default option = 6 decimal places
        # [1] “Pi is 3.141593"
        sprintf("%.3f", pi) # with 3 decimal places
        # [1] "3.142"
        sprintf("%5.1f", pi) # fixed width=5 with 1 decimal places
        # [1] "  3.1"
        sprintf("%-10f", pi) # left justified with fixed width=10
        # [1] "3.141593  " (two blank space)
        sprintf("%e", pi) # scientific notation
        # [1] "3.141593e+00“ (10^0)
        ```
        

- Visualization
    - Basic commends
        - Basic parameters
            
            ```r
            # parameter of lty: line type
            # 0: blank, 1: solid, 2:dashed, 3:dotted
            
            # parmeter of cex: amount of text and symbols
            # 1=default, 1.5 is 50% larger, 0.5 is 50% smaller
            
            # parmeter of pch: plotting character
            # bg(background colour) can apply to 21-25
            # 19=solid circle, 20=bullet, 21=circle, 22=square, 
            # 23=diamond, 24=triangle point‐up, 25=triangle point down
            
            # parmeter of lwd: line width
            # default (default=1). lwd = 2, it is twice as wide
            ```

        
        ```r
        plot(y_var, x_var, data= data)
        # or
        plot(data$x_var, data$y_var)
        
        # Multiple plots in the same window
        par(mfrow=c(2,2))
        # 1 2
        # 3 4
        par(mfcol=c(2,2))
        # 1 3
        # 2 4
        
        text(x, y, labels, ...)  # adds text into the graph 
        # text() will add case number in the plot with x‐ and y‐coordinates.
        # need to specify the place of texts 
        # -0.1 and +0.1 are to offset and add to the points to avoid overlapping.
        
        points(x, y, ...) # adds points, x,y are vector
        lines(x, y, ...) # adds line segments
        abline(a, b, ...) # adds the line $y = a + bx$ 
        abline(h = y, ...) # adds a horizontal line 
        abline(v = x, ...) # adds a vertical line 
        
        polygon(x, y, ...)
        # adds a closed and possibly filled polygon 
        
        segments(x0, y0, x1, y1, ...) # draws line segments 
        arrows(x0, y0, x1, y1, ...) # draws arrows 
        
        symbols(x, y, ...)
        # draws circles, squares, thermometers, etc. 
        
        # find out the factor
        unique(as.character(data))
        # as.charactor() can get the displayed  form
        # unique() can select the unique values
        
        # best‐fit lines can be obtained using the lm() function
        # lm is the "linear model"
        abline(lm(y_var~ x_var, data = data, subset = factor == "1"))
        
        title(main, sub, xlab, ylab, ...)
        # adds a main title, a subtitle,
        # an x-axis label and/or a y-axis label
        
        mtext(text, side, line, ...)
        # draws text in the margins
        # outside the plot region are the margins
        # numbered clockwise from 1 to 4, starting at the bottom.
        
        axis(side, at, labels, ...)
        
        # adds an axis to the plot
        box(...) # adds a box around the plot region
        
        legend(x, y=NULL, legend, fill, col, bg) # draws a legend
        legend("topleft", legend = paste("line", 1:5), lty = 1:5, 
        				pch = 1:5, lwd = c(1, 1, 2, 1, 1))
        ```
        
            
            
    - Histogram
        - Display distribution of data
        
        ```r
        hist(data)
        
        # add the normal density to the histograms
        hist(data, freq=F)
        # produce histogram with density instead of frequency
        
        # determine the length of the density (according to the histogram)
        x<-seq(5,12,0.1)
        # since the log histogram start from 5 to 12
        
        line(x,dnorm(x,mean(data),sd(data)), lty=2)
        # add the density curve to the histogram 
        # dnorm describe the pdf of normal, mean and sd nedd to fit the data
        ```
        
    - Pie chart
        
        ```r
        pie(data, labels= names(data), cex=1, main="Pie chart")
        ```
        
    - Bar chart
        - each category is close to each other
        
        ```r
        # bar chart with legend outside
        barplot(data ,horiz=T, col=rainbow(20), xlim=c(0,25), beside=F, 
        				legend.text=names(data), args.legend=list(x=25, y=25, cex=0.8),
        				main="Bar chart")
        # horiz=T produces a horizontal bar
        # col=rainbow(20) use rainbow colour scheme up to 20 colours
        # xlim=c(0,25) is the range of x-axis
        # beside=T is the side-by-side bars
        
        # args.legend is a list for the legend
        # in list(x=25, y=25, cex=0.8), first two is the position of legend
        
        args.legend=list(horiz=T, bty="n")
        #horiz=T means the legend is placed horizontally
        # bty="n" sets the legend box to have no border
        
        # bar chart with legend inside and number at the end
        y<-barplot(data,horiz=T,col="white",xlim=c(0,15), 
        						main="Bar chart")
        x<-round(data,1)
        # obtain the x-coord. and round to 1 decimal
        text(0.5*x,y,names(data),cex=0.8)
        # add legend inside the bar 
        text(x+0.8,y,labels=x,cex=0.8)
        # add number at the end
        
        # The y‐coordinate of bars are saved in y. 
        # The data is rounded to one decimal place and saved in x.
        # The legend is printed at the position of (0.5*x,y) with cex=0.8.
        # Finally x is printed at (x+0.8,y).
        
        # plot the bar chart of proportion in row or column
        barplot(prop.table(data,1), horiz=F)
        # by row
        
        ```
        
    - Box plot
        - Display distribution
        - Detect outliers and compare distribution of two sample
        
        ```r
        boxplot(y_variable ~ x_variable, main="Box plot")
        # y_variable os the observed data
        # x_variable is the grouping variables, >=2 variables for comparison
        # x_variable can be the factor object
        
        year<-c(rep(86,19), rep(90,19))
        # 19 is the number of data, 86 & 90 are the labels
        total_data<-c(data_1, data_2)
        boxplot(total_data ~ year, horizontal=T, main="Year 86 vs Year 90")
        
        # compare Yr 86 and 90 by region
        # split data and plot the boxplot
        s86<-split(d$lnpd86,d$Region)# split year86 by Region
        s90<-split(d$lnpd90,d$Region)# split year90 by Region
        par(mfrow=c(1,3))# set multiframe1x3
        boxplot(c(s86$HK,s90$HK)~rep(c(86,90),each=length(s86$HK)),main="HK")
        # boxplot for HK
        boxplot(c(s86$KL,s90$KL)~rep(c(86,90),each=length(s86$KL)),main="KL")
        # boxplot for KL
        boxplot(c(s86$NT,s90$NT)~rep(c(86,90),each=length(s86$NT)),main="NT")
        # boxplot for NT
        
        par(mfrow=c(1,1))
        # reset multiframeto 1x1
        title(sub="ln pd86 vs ln pd90 by Region")
        # sub-title
        
        # compare region by Yr 86 and 90
        par(mfrow=c(1,2))
        # set mfrowto (1,2)
        boxplot(lnpd86~Region,data=d,main="lnpd86")
        # boxplot using formula
        boxplot(lnpd90~Region,data=d,main="lnpd90")
        ```
        
    - Normal quantile-quantile plot (normal QQ plot)
        - Check the normality assumption
        - Sample quantiles versus the theoretical quantiles from standard normal distribution
        - Points are close to a 45 degree straight line
        - Sample quantiles are linearly related to the quantiles of standard normal distribution
        
        ```r
        qqnorm(data, main="QQ plot")
        # Provide the QQ plot
        qqline(data, col="red")
        # Provide the reference line to the plot
        ```
        
    - General QQ plot
        - Check general distribution
        
        ```r
        r<-runif(1000,-10,10)
        # generate uniform distribution samlpe
        
        n<-length(r)
        r2<-sort(r)
        # sample quantile
        i<-((1:n)-0.5)/n
        # adjust for continuity 
        q<-qunif(i)
        # theoretical quantile
        
        plot(q,r2,main="Uniform QQ Plot")
        abline(lsfit(q,r2), col="red") 
        ```
        
    - Scatter plot
        - Relationship between two or more continuous variables
        
        ```r
        plot(var_a, var_b, main="Relationship between A and B")
        
        # when the range of the data is large, log transformation is needed
        # reduce the skewness
        plot(log(var_a), log(var_b), main="Relationship between log A and log B")
        
        # difference of 1 on the log scale corresponds to 
        # doubling on the original scale and
        # difference of -1 corresponds to halving
        
        abline(lsfit(log(var_a), log(var_b)))
        # add least square line
        # least square line is the line that closest to the data 
        # by minimizing the error sum of squares
        
        lsfit()
        # will return the intercept and slope of the square line
        ```
        
        - Whether two variables are linearly or nonlinearly related or correlation
            
            ```r
            par(mfrow=c(1,1))
            # reset multiframe to 1x1 
            plot(data_a,data_b,main="Plot with case no.") 
            # plot lnpd90 vs lnpd86 
            text(data_a-0.1,data_b+0.1,cex=0.6)
            # add case no to the points
            
            # specify the colour of different factor objects in scatter plot
            plot(data_a, data_b, pch=21, bg=c("red", "blue", "green")[factor])
            # should be having 3 factors that match to 3 colours
            ```
            

  
        
    - Mathematical function plot
        
        ```r
        # fx = xsin(pi/x), x!=0 (x belongs to [-0.4, 0.4])
        #    = 0         , x =0		   
        x1 <- seq(-0.4,-0.001, by=0.001)
        x2 <- seq(0.001,0.4, by=0.001)
        # generate the points from the range, besides 0
        x <- c(x1, 0, x2) 
        # x = 0 is a special case 
        y <- c(x1*sin(pi/x1), 0, x2*sin(pi/x2)) 
        plot(x,y, type="l", ylim=c(-0.4,0.4)) 
        abline(0,1, lty=2)
        abline(0,-1, lty=2)
        ```
        
        - Simple mathematical function
        
        ```r
        curve(expr, from = NULL, to = NULL)
        curve(x*sin(x),-4*pi,4*pi)
        ```
        
    - 3-domensional plot
        - Perspective plot (3D surfaces)
        
        ```r
        persp(x, y, z)
        
        # Parameter: This function accepts different parameters 
        # i.e. x, y and z where x and y are vectors 
        # defining the location along x- and y-axis
        # z-axis will be the height of the surface in the matrix z.
        
        # Return Value: persp() returns the viewing transformation matrix 
        # for projecting 3D coordinates (x, y, z) into the 2D plane 
        # using homogeneous 4D coordinates (x, y, z, t).
        
        # theta, phi: angles defining the viewing direction. 
        # theta gives the azimuthal direction and phi the colatitude.
        # angle of plot
        
        # ticktype: "simple" draws just an arrow parallel to the axis 
        # to indicate direction of increase;
        # "detailed" draws normal ticks as per 2D plots. (with numbers)
        
        cone <- function(x, y){
        sqrt(x ^ 2 + y ^ 2)
        }
        # prepare variables.
        x <- y <- seq(-1, 1, length = 30)
        z <- outer(x, y, cone)
        # plot the 3D surface
        persp(x, y, z)
        persp(x, y, z,theta = 30, phi = 15,ticktype = "detailed")
        ```
            
        - Simple DEM (Digital elevation model)
            
            ```r
            # Visualizing a simple DEM model
            z <- 2 * volcano     # Exaggerate the relief
            x <- 10 * (1:nrow(z)) # 10 meter spacing (S to N)
            y <- 10 * (1:ncol(z)) # 10 meter spacing (E to W)
            
            # Don't draw the grid lines : border = NA
            par(bg = "gray")
            persp(x, y, z, theta = 135, phi = 30,
                  col = "brown", scale = FALSE,
                ltheta = -120, shade = 0.75,
                  border = NA, box = FALSE)
            ```
            
            
        

- Usage of %…% operations
    - %%
        - Reminder
        
        ```r
        x<-c(4:1)
        x%%3  # remainder
        # 1 0 2 1 
        ```
        
    - %/%
        - Integer division
        
        ```r
        x<-c(4:1)
        x%/%3  # integer divide
        # 1 1 0 0
        
        x == y * (x %/% y) + (x %% y)
        # compute hour and minute from dep_time
        transmute(flights,
          dep_time,
          hour = dep_time %/% 100,
          minute = dep_time %% 100)
        
        ```
        
    - %*%
        - Matrix mulitiplication
        - Inter-product = x’ x
        
        ```r
        # LHS ncol = RHS nrow
        matrix(1:4,2) %*% matrix(1:6,2)
        #       [,1] [,2] [,3]
        # [1,]    7   15   23
        # [2,]   10   22   34
        
        # vector will cooperate with matrix
        ```
        
    - %o%
        - Outer-product = x x’
        
        ```r
        # %o% is binary operator providing a wrapper for outer(x, y, "*")
        # [i, j] of "x %o% y" = x[i] * y[j]
        c(1,2,3) %o% c(1, -1)
        #      [,1] [,2]
        # [1,]    1   -1
        # [2,]    2   -2
        # [3,]    3   -3
        ```
        
    - %in%
        - Identify an element whether belong to a vector or data frame
        - Matching value
        
        ```r
        # Compare two vectors or sequence  
        a <- LETTERS[1:10]
        # "A" "B" "C" "D" "E" "F" "G" "H" "I" "J"
        b <- LETTERS[4:10]
        # "D" "E" "F" "G" "H" "I" "J"
        a %in% b
        # FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
        which(a %in% b)
        # 4  5  6  7  8  9 10
        which(b == a) # wrong
        
        dataf2 <- data.frame(Type = c("Fruit","Fruit","Fruit","Fruit","Fruit",
                                      "Vegetable", "Vegetable", "Vegetable",
        														  "Vegetable", "Fruit"),
                             Name = c("Red Apple","Strawberries","Orange",
        															"Watermelon","Papaya",
                                      "Carrot","Tomato","Chili","Cucumber",
        														  "Green Apple"),
                             Color = c(NA, "Red", "Orange", "Red", "Green",
                                       "Orange", "Red", "Red", "Green", "Green"))
        
        # Add a new column to the dataframe
        dataf2 <- within(dataf2, {
          Red_Fruit[Type %in% "Fruit"] = "No"
          Red_Fruit[Type %in% "Vegetable"] = "No"
          Red_Fruit[Name %in% c("Red Apple", "Strawberries", "Watermelon",
                                "Chili", "Tomato")] = "Yes"
        })
        # Type         Name  Color Red_Fruit
        # 1      Fruit    Red Apple   <NA>       Yes
        # 2      Fruit Strawberries    Red       Yes
        # 3      Fruit       Orange Orange        No
        # 4      Fruit   Watermelon    Red       Yes
        # 5      Fruit       Papaya  Green        No
        # 6  Vegetable       Carrot Orange        No
        # 7  Vegetable       Tomato    Red       Yes
        # 8  Vegetable        Chili    Red       Yes
        # 9  Vegetable     Cucumber  Green        No
        # 10     Fruit  Green Apple  Green        No
        
        # test if value is in the column
        
        # Subset Data
        library(dplyr)
        dataf %>%
          filter(home.dest %in% c("St Louis, MO", "New York, NY", "Hudson, NY"))
        
        # remove columns
        dataf[, !(colnames(dataf) %in% c("pclass", "embarked", "boat"))]
        
        # select columns
        dataf[, (colnames(dataf) %in% c("pclass", "embarked", "boat"))]
        ```
        
    - %>% (magrittr)
        - Forward Pipe : The workflow of data
        - Using the previous output as the first argument of next imput
        
        ```r
        install.packages("magrittr")
        library(magrittr)
        
        sys_date <- Sys.Date()
        sys_date_yr <- format(sys_date, format = "%Y")
        sys_date_num <- as.numeric(sys_date_yr)
        # or
        sys_date_num <- as.numeric(format(Sys.Date(), format = "%Y"))
        # or
        sys_date_num <- Sys.Date() %>%
           format(format = "%Y") %>%
           as.numeric()
        
        -5:5 %>% abs(.)
        # "." can be added to specify the place of imput
        ```
        
    - %T>% (magrittr)
        
        ```r
        %T>% # works like %>% 
        # complex pipes, call a function for its side-effects.
        # returns the left-hand side instead of right-hand side
        # return the original value instead of the result
        # useful when an expression is used for its side-effect
        # 1) plot, returns NULL
        # 2) str, debug a pipeline by looking at an intermediate result
        # 3) lm/summary, applied to the output of lm,
        #                not the output of print(summary(.))
        
        rnorm(100) %>%
          matrix(ncol = 2) %>%
          plot() %>%
          str()
        #>  NULL
        
        rnorm(100) %>%
          matrix(ncol = 2) %T>%
          plot() %>%
          str()
        #>  num [1:50, 1:2] -0.387 -0.785 -1.057 -0.796 -1.756 ...
        
        x %>% f() # return f(x)
        x %T>% f() # return x
        ```
        
    - %$% (magrittr)
        
        ```r
        # “explodes” out the variables in a data frame
        # can refer to them explicitly
        
        # if functions don’t have a data frame based API
        # pass them individual vectors, not a data frame 
        # and expressions to be evaluated of that data frame
        mtcars %$%
          cor(disp, mpg)
        #> [1] -0.8475514
        ```
        
    - %<>% (magrittr)
        - Passing the LHS to RHS for calculation, and update LHS
        
        ```r
        data %<>% do.call(rbind, .)
        # "." can be added to specify the place of imput
        
        data %<>% Filter(function(x)!all(is.na(x)), .)
        
        # replace code
        mtcars <- mtcars %>% 
          transform(cyl = cyl * 2)
        # or
        mtcars %<>% transform(cyl = cyl * 2)
        ```
        
    - %like%
        - Whether the character string matchs the given character vector
        
        ```r
        # find names ending on "or"
        names(data) %like% "%or"
        
        # find names starting with "d"
        names(data) %like% "d%"
        
        # ... containing er?
        names(data) %like% "%er%"
        
        # and combined, search for a name containing "un", ending on "or"
        # or beginning with "F"
        levels(data$X) %like any% c("%un%", "%or", "F%")
        
        # the positions on the vector
        match(names(data) %like% "%er%", names(data))
        #  return the positions of the matched elements
        # if the element is not found, it returns NA.
        ```
        
    - Defined operator
        - Define our own operator
        
        ```r
        "%+-%" <- function(x,s) { c(x-s,x+s) }
        3 %+-% 5
        # -2 8
        ```
        

- Usage of with / within / transform
    - Work in data frame
    
    ```r
    with(data_frame, R_expression)
    # evaluates the expression without modifying the original data frame.
    # apply to single expression
    
    within(data_frame, R_expression)
    # evaluates the expression and creates a copy of the original data frame.
    
    transform(data_frame, R_expression)
    # Similar to within()
    
    # e.g.
    mydata <- data.frame(x1=c(2,2,6,4), x2=c(3,4,2,8),x3=c(8,9,6,4))
    
    with(mydata,cbind(x3,x4))
    
    with(mydata, {sumx=x1+x2; meanx=(x1+x2)/2})
    # 2.5 3.0 4.0 6.0
    # only last expression will be executed
    # cannot store the results into meanx
    
    transform(mydata, sumx=x1+x2, meanx=(x1+x2)/2, prodx=x1*x2)
    # separate by ","
    
    within(mydata, {sumx=x1+x2
    meanx=(x1+x2)/2
    prodx=x1*x2
    })
    within(mydata, {sumx=x1+x2; meanx=(x1+x2)/2; prodx=x1*x2})
    # separate by ";" or SPACE, and need to add {}
    
    # x1 x2 sumx meanx prodx
    # 1  2  3    5   2.5     6
    # 2  2  4    6   3.0     8
    # 3  6  2    8   4.0    12
    # 4  4  8   12   6.0    32
    ```
    

- Set Operations
    - Basic operation
        
        ```r
        # for union, intersect, setdiff and setequal, as.vector is applied
        
        union(x,y)
        # Union of the sets x and y
        # a vector of a common mode
        
        intersect(x,y)
        # Intersection of the sets x and y
        # a vector of a common mode, or NULL if x or y is NULL
        
        setdiff(x,y)
        # Set difference between x and y
        # consisting of all elements of x that are not in y
        # a vector of the same mode as x
        
        setequal(x,y)
        # Test for equality between x and y
        # a logical scalar for setequal
        
        c %in% y
        is.element(x, y) # is identical to x %in% y
        # Membership, testing whether c is an element of the set y
        # a logical of the same length as x for is.element
        
        choose(n,k)
        # Number of possible subsets of size k chosen from a set of size n
        
        x <- c(1,2,5)
        y <- c(5,1,8,9)
        union(x,y)
        # [1] 1 2 5 8 9
        intersect(x,y)
        # [1] 1 5
        setdiff(x,y)
        # [1] 2
        setdiff(y,x)
        # [1] 8 9
        setequal(x,y)
        # [1] FALSE
        setequal(x,c(1,2,5))
        # [1] TRUE
        
        2 %in% x
        is.element(2,x)
        # [1] TRUE
        
        2 %in% y
        is.element(2,y)
        # [1] FALSE
        
        x %in% y
        is.element(x,y)
        
        # [1] TRUE FALSE  TRUE
        choose(5,2)
        # [1] 10
        ```
        
    - merge : join operation
        
        ```r
        # connecting two data frames
        # the column type is the same on which the merging occurs
        merge(x, y, by, by.x, by.y, all, all.x, all.y, sort = TRUE)
        # x,y: data frame or object to be merged.
        
        # by, by.x, by.y: specifies the columns used for the merging.
        
        # all = FALSE, If all = TRUE, all.x = TRUE and all.y = TRUE
        # all.x, all.y: If TRUE, additional rows will be added to the output:
        # For each row in x in the case of all.x=TRUE OR
        # For each row in y in the case of all.y=TRUE
        # If the syntax does not have a matching row
        # then NAs will be printed in these rows.
        
        # sort = TRUE/FALSE: specifies if the results are sorted or not.
        
        x = data.frame(StudentId = c(1:6), 
                         Marks = c("70", "84", "90", "93", "80", "76"))
        y = data.frame(StudentId = c(2, 4, 6, 7, 8), 
                         city = c("Lahore", "Karachi", "Peshawar",
        												  "Quetta", "Multan")) 
        # natural join / inner join of two data frames
        merge(x, y, by = "StudentId")
        merge(x, y) # (default) by = intersect(names(x), names(y))
        #   StudentId Marks     city
        # 1         2    84   Lahore
        # 2         4    93  Karachi
        # 3         6    76 Peshawar
        # id: 2, 4, and 6 are common
        
        # Full (outer) join
        # merges all the columns of both data sets into one
        merge(x, y,all = TRUE)
        # StudentId Marks     city
        # 1         1    70     <NA>
        # 2         2    84   Lahore
        # 3         3    90     <NA>
        # 4         4    93  Karachi
        # 5         5    80     <NA>
        # 6         6    76 Peshawar
        # 7         7  <NA>   Quetta
        # 8         8  <NA>   Multan
        
        # Left (outer) join
        # matching all the rows in the first df with the corresponding values 
        merge(x,y,all.x = TRUE)
        # StudentId Marks     city
        # 1         1    70     <NA>
        # 2         2    84   Lahore
        # 3         3    90     <NA>
        # 4         4    93  Karachi
        # 5         5    80     <NA>
        # 6         6    76 Peshawar
        
        # Right (outer) join
        merge(x,y,all.y = TRUE)
        # StudentId Marks     city
        # 1         2    84   Lahore
        # 2         4    93  Karachi
        # 3         6    76 Peshawar
        # 4         7  <NA>   Quetta
        # 5         8  <NA>   Multan
        
        # Cross join
        # join every elements 
        merge(x, y, by = NULL) 
        # very large
        # StudentId.x Marks StudentId.y   city
        # 1           1    70           2 Lahore
        # 2           2    84           2 Lahore
        # 3           3    90           2 Lahore
        # 4           4    93           2 Lahore
        # 5           5    80           2 Lahore
        # 6           6    76           2 Lahore
        
        # Merge rows 
        # merge data frames by row names
        rownames(x) <- c("A", "B", "C", "D", "E","G")
        rownames(y) <- c("A", "B", "C", "D", "E")
        merge(x, y, by = 0, all = TRUE) 
        merge(x, y, by = "row.names", all = TRUE)
        #   Row.names StudentId.x Marks StudentId.y     city
        # 1         A           1    70           2   Lahore
        # 2         B           2    84           4  Karachi
        # 3         C           3    90           6 Peshawar
        # 4         D           4    93           7   Quetta
        # 5         E           5    80           8   Multan
        # 6         G           6    76          NA     <NA>
        
        # Merge more than two dataframes
        z = data.frame(StudentId = c(1, 3, 5, 7, 8), 
                       height = c("162", "171", "154", "193", "153")) 
        merge(x, merge(y, z, all = TRUE), all = TRUE)
        
        # combining element in by.x, by.y that having same values
        z2 = data.frame(StudentId = c(1, 3, 5, 7, 8), 
                       height2 = c("153", "160", "193", "155", "171"))
        merge(z,z2,by.x = "height" ,by.y = "height2")
        #   height StudentId.x StudentId.y
        # 1    153           8           1
        # 2    171           3           8
        # 3    193           7           5
        ```
        


- Usage of filter
    - filter() (package: dplyr)
        
        ```r
        # subset observations based on their values
        
        library(dplyr)
        filter(df , condition)
        # The first argument is the name of the data frame. 
        # The second, subsequent are the expressions that filter the data frame
        
        df=data.frame(x=c(12,31,4,NA,NA),
                      y=c(22.1,44.5,6.1,43.1,99),
                      z=c(TRUE,TRUE,FALSE,TRUE,TRUE))
         
        filter(df, x<50 & z==TRUE)
        # or
        df %>% filter(x<50 & z==TRUE)
        #    x    y    z
        # 1 12 22.1 TRUE
        # 2 31 44.5 TRUE
        
        df %>% filter(!is.na(x))
        # filter out the missing value
        #    x    y     z
        # 1 12 22.1  TRUE
        # 2 31 44.5  TRUE
        # 3  4  6.1 FALSE
        
        df %>% filter(z %in% c("TRUE"))
        # filter out only the columns which contain the data
        #    x    y    z
        # 1 12 22.1 TRUE
        # 2 31 44.5 TRUE
        # 3 NA 43.1 TRUE
        # 4 NA 99.0 TRUE
        ```
        
    - filter()
    - Filter()

- Usage of apply
    
    
    | Function | Object | Input | Output |
    | --- | --- | --- | --- |
    | apply(x, MARGIN, FUN) | Apply to rows, columns or both | df, matrix | list, vector, array |
    | vapply(X, FUN, FUN.VALUE) | vectorize the operation | vector, list, df | specify by FUN.VALUE |
    | lapply(X, FUN) | Apply to all elements of input | list, vector,  df | list |
    | sapply(X, FUN) | Apply to all elements of input | list, vector,  df | vector, array, list |
    | tapply(X, INDEX, FUN) *INDEX is the factors | Apply on subset of the vector broken down by given factors | usually vector | vector, array |
    | mapply(FUN , …) | Apply to multiple list or vector arguments | list, vector, df | list |
    | rapply(X, FUN, …) | recursively apply to a list | list | specify by classes |
    | eapply | apply to every named element in an environment | environment | list |
    | split(X, factor) | Splits into groups determined by the factor | list, vector, df | list |
    | do.call(FUN, list) | Apply to the list as a whole, only one function call | list | depend on FUN |
    | by(DF, INDEX, FUN) | Apply on subset of the df broken down by given factors | df, vector | depend on FUN |
    | aggregate(x, by,  FUN) | split and apply transformation  | list, df | depend on FUN |
    
    - apply
        
        ```r
        apply(X, MARGIN, FUN)
        # MARGIN=1 : rows
        # MARGIN=2 : columns
        # MARGIN=c(1,2) : both
        x <- array(1:9,dim=c(3,3))
        # [,1] [,2] [,3]
        # [1,] 1 4 7
        # [2,] 2 5 8
        # [3,] 3 6 9
        apply(x,1,function(x) x * 10)
        # [,1] [,2] [,3]
        # [1,] 10 20 30
        # [2,] 40 50 60
        # [3,] 70 80 90
        apply(x,1,sum)
        # 12 15 18
        ```
        
    - vapply
        
        ```r
        vapply(X, FUN, FUN.VALUE, ...)
        # FUN.VALUE=numeric(1)
        # logical(1) integer(1) character(1) data.frame(1)
        
        # safe alternative to sapply()
        # supply an additional argument that defines the type
        
        # x is a data frame that having 9 columns, 100 rows
        vapply(x, sum, matrix(18))
        vapply(x, sum, vector(mode = "numeric", length = 1))
        vapply(x, sum, numeric(1))
        ```
        
    - lapply
        
        ```r
        lapply(1:3, runif, min = 0, max = 5)
        # [[1]]
        # [1] 3.342334
        # [[2]]
        # [1] 3.9711993 0.5397181
        # [[3]]
        # [1] 3.618555 2.056372 4.104731
        ```
        
    - sapply
        
        ```r
        x <- list(a = 1:10, b = rep(10,10), c = rnorm(10))
        
        lapply(x, sum)
        # $a
        # [1] 55
        # $b
        #[1] 100
        # $c
        # [1] 0.1596377
        
        sapply(x, sum)
        # a b c 
        # 55.0000000 100.0000000 0.1596377
        
        x1 <- list(
          c(0.27, 0.37, 0.57, 0.91, 0.20),
          c(0.90, 0.94, 0.66, 0.63, 0.06), 
          c(0.21, 0.18, 0.69, 0.38, 0.77)
        )
        x2 <- list(
          c(0.50, 0.72, 0.99, 0.38, 0.78), 
          c(0.93, 0.21, 0.65, 0.13, 0.27), 
          c(0.39, 0.01, 0.38, 0.87, 0.34)
        )
        
        threshold <- function(x, cutoff = 0.8) x[x > cutoff]
        x1 %>% sapply(threshold) %>% str()
        #> List of 3
        #>  $ : num 0.91
        #>  $ : num [1:2] 0.9 0.94
        #>  $ : num(0)
        x2 %>% sapply(threshold) %>% str()
        #>  num [1:3] 0.99 0.93 0.87
        ```
        
    - tapply
        
        ```r
        x<-runif(20, min=155, max=180)
        y<-gl(2, 10, labels = c("Male", "Female")) 
        # Generate factors by specifying the pattern of their levels
        tapply(x, y, mean)
        # Male Female 
        # 168.4516 163.8848
        
        tapply(iris$Sepal.Length, iris$Species, mean)
        # setosa versicolor virginica 
        # 5.006    5.936         6.588
        
        ```
        
    - mapply
        
        ```r
        mapply(rep, 1:3, 3:1)
        # [[1]]
        # [1] 1 1 1
        # [[2]]
        # [1] 2 2
        # [[3]]
        # [1] 3
        
        mapply(rep, 1:3, times=2)
        #       [,1] [,2] [,3]
        # [1,]    1    2    3
        # [2,]    1    2    3
        
        vector1 <- c(1, 2, 3, 4, 5)
        vector2 <- c(2, 4, 1, 2, 10)
        mapply(max, vector1, vector2)
        # [1]  2  4  3  4 10
        
        vec1 <- c(1, 2, 3, 4)
        vec2 <- c(2, 4, 6, 8)
        vec3 <- c(3, 6, 9, 12)
        mapply(function(val1, val2, val3) val1*val2*val3, vec1, vec2, vec3)
        # [1]   6  48 162 384
        ```
        
    - rapply
        
        ```r
        rapply(object, f, classes = “ANY”, deflt = NULL, 
        		how = c(“unlist”, “replace”, “list”))
        
        # Parameters:
        # object: represents list or an expression
        # f: represents function to be applied recursively
        # classes: represents class name of the vector or “ANY” to match any of the class
        # deflt: represents default result when how is not “replace”
        # how: represents modes
        
        # how = “replace”
        # each element of the list object which is not itself is a list  
        # then each element of the list is replaced by the resulting value 
        
        # how = “list” or how = “unlist”
        # list object is copied
        # all non-list elements are replaced by the resulting value 
        # all other are replaced by deflt.
        
        ls <- list(a = 1:5, b = 100:110, c = c('a', 'b', 'c'))
        
        rapply(ls, mean, how = "replace", classes = "integer")
        # $a
        # [1] 3
        # $b
        # [1] 105
        # $c
        # [1] "a" "b" "c"
        
        rapply(ls, mean, how = "list", classes = "integer")
        # $a
        # [1] 3
        # $b
        # [1] 105
        # $c
        # NULL
        
        rapply(ls, mean, how = "unlist", classes = "integer")
        # a   b 
        # 3 105
        ```
        
    - eapply
        
        ```r
        eapply(environment(), nrow, USE.NAMES = FALSE)
        # USE.NAMES = FALSE, which will return an unnamed list
        
        e <- new.env()
        e$a <- 10
        e$b <- 20
        e$c <- 30
        # multiply every element in the environment by 2
        eapply(e, function(x) x * 2)
        # $a
        # [1] 20
        # $b
        # [1] 40
        # $c
        # [1] 60
        ```
        
    - split
        
        ```r
        x<-runif(20, min=155, max=180)
        y<-gl(2, 10, labels = c("Male", "Female")) 
        # Generate factors by specifying the pattern of their levels.
        # gl: generate factors by specifying the pattern of levels
        split(x, y)
        # $Male
        # [1] 166.9308 173.3078 172.3183 166.9405 176.5302 
        #     165.9524 161.1199 156.7670 157.4867 162.9068
        # $Female
        # [1] 167.9659 171.5501 165.1708 177.8219 162.3401 
        #     166.4766 163.3099 171.2718 161.4504 166.9636
        
        library(datasets)
        split(airquality, airquality$Month)
        # take the column means for each sub-data frame
        sapply(mydata, function(x) {
        colMeans(x[, c("Ozone", "Solar.R", "Wind")])
        })
        ```
        
    - do.call
        
        ```r
        x <- list(a = 1:10, b = rep(10,10), c = rnorm(10))
        do.call(sum, x)
        # 155.2605
        
        do.call(cbind, x)
        #       a  b           c
        # [1,]  1 10  0.31623323
        # [2,]  2 10  0.28638519
        # [3,]  3 10 -0.22871236
        # [4,]  4 10  1.06100425
        # [5,]  5 10  1.46902851
        # [6,]  6 10  0.19424177
        # [7,]  7 10 -0.16313605
        # [8,]  8 10  1.73177587
        # [9,]  9 10  0.89028252
        # [10,] 10 10 -0.02801498
        # number of rows need to be the same
        
        # sapply() combind with do.call()
        ```
        
    - by
        
        ```r
        # parameter has to be a list
        
        df<-iris
        # computes the mean for species categories in terms of petal.width 
        by(df$Petal.Width,list(df$Species),mean)
        # : setosa
        # [1] 0.246
        #
        #   : versicolor
        # [1] 1.326
        #
        #   : virginica
        # [1] 2.026
        
        by(df$Petal.Width,list(df$Species,df$Petal.Width),mean)
        # multiple lists of colums
        # : setosa
        # : 0.1
        # [1] 0.1
        # ----------------------------------------------------------------------- 
        #   : versicolor
        # : 0.1
        # [1] NA
        # ----------------------------------------------------------------------- 
        #   : virginica
        # : 0.1
        # [1] NA
        # ----------------------------------------------------------------------- 
        #   : setosa
        # : 0.2
        # [1] 0.2
        ```
    

- Usage of map
    
    
    | Function | Object | Output |
    | --- | --- | --- |
    | map(.x, .f) | calls the function once for each element of the vector | list |
    | map_dbl(.x, .f) | return by corresponding type | double vector |
    | map_chr(.x, .f) | return by corresponding type | character vector |
    | map_int(.x, .f) | return by corresponding type | integer vector |
    | map_lgl(.x, .f) | return by corresponding type | logical vector |
    | map_dfr(.x, .f) | return data frames created by row-binding | df |
    | map_dfc(.x, .f) | return data frames created by column-binding | df |
    | map_if(.x,.p,.f) | takes a predicate function .p to determine which elements of .x are transformed with  .f | list |
    | map_at(.x,.at,.f) | takes a vector of names or positions .at to specify which elements of .x are transformed with .f | list |
    | map_depth(.x, .depth, .f) | apply .f to a specific depth level of a nested vector | list |
    | map2(.x, .y, .f) | two argument case | list |
    | pmap(.l, .f) | Map over multiple inputs simultaneously | list |
    | modify(.x, .f) | returns the same type as the input object | based on input |
    | walk(.x, .f) | calls .f for its side-effect and returns the input .x | no outputs |
    | invoke_map(.f, .x) | pair of funs, combine fun and para to get results | list |
    
    - map
        
        ```r
        map(.x, .f)
        # .f can be a function, formula or vector
        ~ .x + 2
        # equal to
        function(x){x + 2}
        # if the function will return values of varying types or lengths
        
        # .f
        # A function, formula, or vector (not necessarily atomic).
        # If a function, it is used as is.
        # If a formula, e.g. ~ .x + 2, it is converted to a function. 
        # For a single argument function, use .
        # For a two argument function, use .x and .y
        # For more arguments, use ..1, ..2, ..3 etc
        
        addTen <- function(.x) {
          return(.x + 10)
        }
        map(.x = c(1, 4, 7), .f = addTen)
        # [[1]]
        # [1] 11
        # [[2]]
        # [1] 14
        # [[3]]
        # [1] 17
        
        1:10 %>%
          map(rnorm,mean=3, n=10) %>%
          map_dbl(mean)
        # 2.604192 2.939071 4.458105 3.299773 3.934731 
        # 3.820228 4.046367 6.193783 2.210406 1.956286
        
        1:10 %>%
          map(function(x) rnorm(10, x))
        
        1:10 %>%
          map(~ rnorm(10, .x))
        # a list contains 10 variables, each variable contains 10 rnorm number
        
        map(c(TRUE, FALSE, TRUE), ~ !.)
        #> [[1]]
        #> [1] FALSE
        #> 
        #> [[2]]
        #> [1] TRUE
        #> 
        #> [[3]]
        #> [1] FALSE
        map(c("Hello", "World"), str_to_upper)
        #> [[1]]
        #> [1] "HELLO"
        #> 
        #> [[2]]
        #> [1] "WORLD"
        ```
        
    - Corresponding types of map
        
        ```r
        map_dbl() 
        # requires the function it applies to each element 
        # to return a numeric vector of length one
        # error, if returns either non-numeric vector or numeric vector with length >1
        # return a numeric vector of same length as its input vector
        
        # map_dbl
        map_dbl(data, function(x) length(unique(x)))
        # an inline anonymous function
        # or short cut
        map_dbl(data, ~ length(unique(.x)))
        # all purrr functions translate formulas
        # created by ~ (pronounced “twiddle”), into functions
        
        map_dbl(x, mean, na.rm = TRUE) 
        # is equal to 
        vapply(x, mean, na.rm = TRUE, FUN.VALUE = double(1))
        
        map_dbl(1:2, as.character)
        #> Error: Can't coerce element 1 from a character to a double
        
        # map_dbl(.x, .f)
        dbl_fun <- function(x) {
          (x+1)*x
        }
        result1 <- map_dbl(1:3,dbl_fun) 
        # 2 6 12
        result2 <- vector(length = 3)
        for(i in 1:3){
          result2[i] <- (i+1) * i
        }
        # 2 6 12
        identical(result1,result2)
        # TRUE
        
        # map & map_dbl
        1:10 %>%
          map(rnorm, n = 10) %>%  
          map_dbl(mean)
        # 0.559  1.821  2.876  4.152  5.116 
        # 6.127  6.911  8.281  9.237 10.627
        
        # map & map_chr
        c("foo", "bar") %>% 
        	map_chr(paste0, ":suffix")
        # [1] "foo:suffix" "bar:suffix"
        
        x <- list(
          list(-1, x = 1, y = c(2), z = "a"),
          list(-2, x = 4, y = c(5, 6), z = "b"),
          list(-3, x = 8, y = c(9, 10, 11))
        )
        
        # Select by name
        map_dbl(x, "x")
        # [1] 1 4 8
        
        # Or by position
        map_dbl(x, 1)
        # [1] -1 -2 -3
        
        # Or by both
        map_dbl(x, list("y", 1))
        # [1] 2 5 9
        
        # You'll get an error if a component doesn't exist:
        map_chr(x, "z")
        # Error: Result 3 must be a single string, not NULL of length 0
        
        # Unless you supply a .default value
        map_chr(x, "z", .default = NA)
        # [1] "a" "b" NA
        
        x <- list(1:5, c(1:10, NA))
        map_dbl(x, ~ mean(.x, na.rm = TRUE))
        # or
        map_dbl(x, mean, na.rm = TRUE)
        # [1] 3.0 5.5
        ```
        
    - map_df
        
        ```r
        map_df(c(1, 4, 7), function(.x) {
          return(data.frame(old_number = .x, 
                            new_number = addTen(.x)))
        })
        # or
        make_dataframe <- function(x){
          data.frame(old_number = x,new_number = addTen(x))
        }
        map_dfr(c(1,4,7),make_dataframe)
        # map_df is similar to map_dfr
        #   old_number new_number
        # 1          1         11
        # 2          4         14
        # 3          7         17
        
        # map_dfc need to be specified
        map_dfc(c(1, 4, 7), function(.x) {
          return(data.frame(old_number = .x, 
                            new_number = addTen(.x)))
        })
        # New names:
        # * old_number -> old_number...1
        # * new_number -> new_number...2
        # * ...
        # old_number...1 new_number...2 old_number ...
        # 1              1             11          ...
        ```
        
    - map_if , map_at , map_depth
        
        ```r
        map_if(.x,.p,.f)
        # .p
        # predicate function, formula describing such a predicate function, 
        # or a logical vector of the same length as .x. 
        # Alternatively, if the elements of .x are themselves lists of objects,
        # a string indicating the name of a logical element in the inner lists. 
        # Only those elements where .p evaluates to TRUE will be modified.
        
        # predicate function to decide whether to map a function
        # .else
        map_if(iris, is.factor, as.character, .else = as.integer)
        
        # Use numeric vector of positions select elements to change:
        iris %>% map_at(c(4, 5), is.numeric)
        
        map_depth(.x, .depth, .f)
        # Level of .x to map on. 
        # Use a negative value to count up from the lowest level of the list.
        # map_depth(x, 0, fun) is equivalent to fun(x).
        # map_depth(x, 1, fun) is equivalent to x <- map(x, fun)
        # map_depth(x, 2, fun) is equivalent to x <- map(x, ~ map(., fun))
        
        x <- list(a = list(foo = 1:2, bar = 3:4), b = list(baz = 5:6))
        str(x)
        # List of 2
        #  $ a:List of 2
        #   ..$ foo: int [1:2] 1 2
        #   ..$ bar: int [1:2] 3 4
        #  $ b:List of 1
        #   ..$ baz: int [1:2] 5 6
        map_depth(x, 2, paste, collapse = "/")
        # $a
        # $a$foo
        # [1] "1/2"
        # 
        # $a$bar
        # [1] "3/4"
        # 
        # 
        # $b
        # $b$baz
        # [1] "5/6"
         
        
        # Equivalent to:
        map(x, map, paste, collapse = "/")
        ```
        
    - map2
        
        ```r
        xs <- map(1:8, ~ runif(10))
        xs[[1]][[1]] <- NA
        ws <- map(1:8, ~ rpois(10, 5) + 1)
        
        map_dbl(xs, weighted.mean, w = ws)
        # Error in weighted.mean.default(.x[[i]], ...) : 
        #   'x' and 'w' must have the same length
        # arguments (ws) after .f are not transformed
        
        map2_dbl(xs, ws, weighted.mean, na.rm = TRUE)
        # [1] 0.504 0.451 0.603 0.452 0.563 0.510 0.342 0.464
        # two vectors come before the function
        
        # map2() recycles its inputs to make sure that they’re the same length
        # sometimes, map2(x, y, f) will automatically behave like map(x, f, y)
        
        # basic implementation of map2()
        simple_map2 <- function(x, y, f, ...) {
          out <- vector("list", length(x))
          for (i in seq_along(x)) {
            out[[i]] <- f(x[[i]], y[[i]], ...)
          }
          out
        }
        ```
        
        ```r
        mu <- list(5, 10, -3)
        sigma <- list(1, 5, 10)
        
        seq_along(mu) %>% 
          map(~rnorm(5, mu[[.]], sigma[[.]])) %>% 
          str()
        #> List of 3
        #>  $ : num [1:5] 4.82 5.74 4 2.06 5.72
        #>  $ : num [1:5] 6.51 0.529 10.381 14.377 12.269
        #>  $ : num [1:5] -11.51 2.66 8.52 -10.56 -7.89
        # or 
        map2(mu, sigma, rnorm, n = 5) %>% str()
        ```
        
 
        
    - pmap
        
        ```r
        map2(x, y, f) 
        # is the same as 
        pmap(list(x, y), f)
        
        pmap() 
        # which takes a list of arguments
        # pmap() will use positional matching when calling the function
        
        # for data frame
        # pmap() and pwalk() apply the function .f to each row
        x <- list(1, 1, 1)
        y <- list(10, 20, 30)
        z <- list(100, 200, 300)
        pmap(list(x, y, z), sum)
        # [[1]]
        # [1] 111
        # [[2]]
        # [1] 221
        # [[3]]
        # [1] 331
        
        df <- data.frame(
          x = c("apple", "banana", "cherry"),
          pattern = c("p", "n", "h"),
          replacement = c("P", "N", "H"),
          stringsAsFactors = FALSE
          )
        pmap(df, gsub)
        # [[1]]
        # [1] "aPPle" 
        # [[2]]
        # [1] "baNaNa"
        # [[3]]
        # [1] "cHerry"
        
        li1 <- c(1,3,5)
        li2 <- c(2,4,6)
        li3 <- c(2,3,4)
        li <- list(li1,li2,li3)
        pmap(li,sum)
        # [[1]]
        # [1] 5
        # [[2]]
        # [1] 10
        # [[3]]
        # [1] 15
        
        pmap_dbl(list(xs, ws), weighted.mean, na.rm = TRUE)
        # [1] 0.504 0.451 0.603 0.452 0.563 0.510 0.342 0.464
        ```
        
        ```r
        mu <- list(5, 10, -3)
        sigma <- list(1, 5, 10)
        n <- list(1, 3, 5)
        
        args1 <- list(n, mu, sigma)
        args1 %>%
          pmap(rnorm) %>% 
          str()
        #> List of 3
        #>  $ : num 5.39
        #>  $ : num [1:3] 5.41 2.08 9.58
        #>  $ : num [1:5] -23.85 -2.96 -6.56 8.46 -5.21
        
        args2 <- list(mean = mu, sd = sigma, n = n)
        args2 %>% 
          pmap(rnorm) %>% 
          str()
        
        # or store in a data frame
        params <- tribble(
          ~mean, ~sd, ~n,
            5,     1,  1,
           10,     5,  3,
           -3,    10,  5)
        params %>% 
          pmap(rnorm)
        #> [[1]]
        #> [1] 6.018179
        #> 
        #> [[2]]
        #> [1]  8.681404 18.292712  6.129566
        #> 
        #> [[3]]
        #> [1] -12.239379  -5.755334  -8.933997  -4.222859   8.797842
        ```

        
    - modify
        
        ```r
        # Same type of output as input
        df <- data.frame(
          x = 1:3,
          y = 6:4
        )
        modify(df, ~ .x * 2)
        #   x  y
        # 1 2 12
        # 2 4 10
        # 3 6  8
        
        # basic implementation of modify()
        simple_modify <- function(x, f, ...) {
          for (i in seq_along(x)) {
            x[[i]] <- f(x[[i]], ...)
          }
          x
        }
        ```
        
    - walk
        
        ```r
        # for side-effects (e.g. cat(), write.csv(), or ggsave())
        # render output to the screen or save files to disk 
        # action instead of return value
        
        x <- list(1, "a", 3)
        x %>% 
          walk(print)
        #> [1] 1
        #> [1] "a"
        #> [1] 3
        
        welcome <- function(x) {
          cat("Welcome ", x, "!\n", sep = "")
        }
        names <- c("Hadley", "Jenny")
        
        # As well as generate the welcomes, it also shows 
        # the return value of cat()
        map(names, welcome)
        # Welcome Hadley!
        # Welcome Jenny!
        # [[1]]
        # NULL
        # 
        # [[2]]
        # NULL
        # list of the print out arguments
        
        walk(names, welcome)
        # Welcome Hadley!
        # Welcome Jenny!
        
        # saving lists of data frame to a separate CSV file
        temp <- tempfile()
        dir.create(temp)
        
        cyls <- split(mtcars, mtcars$cyl)
        paths <- file.path(temp, paste0("cyl-", names(cyls), ".csv"))
        walk2(cyls, paths, write.csv)
        
        dir(temp)
        #> [1] "cyl-4.csv" "cyl-6.csv" "cyl-8.csv"
        
        # is equivalent to 
        write.csv(cyls[[1]], paths[[1]]), write.csv(cyls[[2]], paths[[2]]),
        	 write.csv(cyls[[3]], paths[[3]])
        
        # walk() is generally not that useful compared to walk2() or pwalk()
        library(ggplot2)
        plots <- mtcars %>% 
          split(.$cyl) %>% 
          map(~ggplot(., aes(mpg, wt)) + geom_point())
        paths <- stringr::str_c(names(plots), ".pdf")
        
        pwalk(list(paths, plots), ggsave, path = tempdir())
        walk(); walk2() ;pwalk() 
        # all invisibly return .x (first argument)
        # This makes them suitable for use in the middle of pipelines.
        ```
        
    - invoke_map
        
        ```r
        invoke_map(.f, .x)
        # Invoke a list of functions, each with different arguments
        # first argument: list of functions or character vector of function names
        # second argument: list of lists giving the arguments that vary for each function
        # subsequent arguments are passed on to every function
        
        f <- c("runif", "rnorm", "rpois")
        param <- list(
          list(min = -1, max = 1), 
          list(sd = 5), 
          list(lambda = 10))
        invoke_map(f, param, n = 5) %>% str()
        #> List of 3
        #>  $ : num [1:5] 0.479 0.439 -0.471 0.348 -0.581
        #>  $ : num [1:5] 2.48 3.9 7.54 -9.12 3.94
        #>  $ : int [1:5] 6 11 5 8 9
        
        tribble() # to make creating these matching pairs
        sim <- tribble(
          ~f,      ~params,
          "runif", list(min = -1, max = 1),
          "rnorm", list(sd = 5),
          "rpois", list(lambda = 10)
        )
        sim %>% 
          mutate(sim = invoke_map(f, params, n = 10))
        ```
        
        
    - Shortcuts
        
        ```r
        models <- mtcars %>% 
          split(.$cyl) %>% 
          map(function(df) lm(mpg ~ wt, data = df))
        
        # one-sided formula
        # . as a pronoun: it refers to the current list element
        models <- mtcars %>% 
          split(.$cyl) %>% 
          map(~lm(mpg ~ wt, data = .))
        # using ~ instead of function(x)
        
        models %>% 
          map(summary) %>% 
          map_dbl(~.$r.squared)
        # or string
        models %>% 
          map(summary) %>% 
          map_dbl("r.squared")
        #>         4         6         8 
        #> 0.5086326 0.4645102 0.4229655
        
        # use an integer to select elements by position
        x <- list(list(1, 2, 3), list(4, 5, 6), list(7, 8, 9))
        x %>% map_dbl(2)
        #> [1] 2 5 8
        
        # generate 10 random normals
        map(c(-10, 0, 10, 100), ~rnorm(n = 10, mean = .))
        ```
        

- Usage of reduce
    - reduce
        
        ```r
        reduce(x, FUN)
        # takes a vector of length n and produces a vector of length 1 
        # by calling a function with a pair of values at a time: 
        # using `` ,instead of ''
        
        reduce(1:4, f) 
        # is equivalent to 
        f(f(f(1, 2), 3), 4)
        # 1. function on the first two components of x
        # 2. result of the first argument and the third component of x
        # ... until all elements of x have been processed
        
        # accumulate: either only return the final result
        # (accumulate == FALSE, the default)
        
        cumsum(1:6)
        Reduce(f = "+", x = 1:6, accumulate = TRUE) # different!!
        accumulate(1:6, `+`)
        # [1]  1  3  6 10 15 21
        # using `` ,instead of ''
        
        df1 <- data.frame(id=c (1, 2, 3) , name=c ('a' , ' b' , 'c'))
        df2 <- data.frame(id=c(1,2) , money=c( 'O', '100 ' ))
        df3 <- data.frame(id=c(1,3) , looking=c ('handsom' , 'cute' ))
        Reduce(function(x,y) merge(x,y,by="id", all.x =TRUE), 
        	list(df1,df2,df3), accumulate=F)
        # id name money looking
        # 1  1    a     O handsom
        # 2  2    b  100     <NA>
        # 3  3    c  <NA>    cute
        
        # find the values that occur in every element
        set.seed(1)
        l <- map(1:4, ~ sample(1:10, 15, replace = T))
        out <- l[[1]]
        out <- intersect(out, l[[2]])
        out <- intersect(out, l[[3]])
        out <- intersect(out, l[[4]])
        out
        # [1] 10  6
        reduce(l, intersect)
        
        # list all the elements that appear in at least one entry
        reduce(l, union)
        # [1]  9  4  7  1  2  3  5 10  6  8
        
        # how reduce works
        accumulate(l, intersect)
        # [[1]]
        # [1]  9  4  7  1  2  7  2  3  1  5  5 10  6 10  7
        # [[2]]
        # [1]  9  4  1  2  3  5 10  6
        # [[3]]
        # [1]  9  4 10  6
        # [[4]]
        # [1] 10  6
        
        # basic implementation of reduce()
        simple_reduce <- function(x, f) {
          out <- x[[1]]
          for (i in seq(2, length(x))) {
            out <- f(out, x[[i]])
          }
          out
        }
        ```
        
    - reduce output type
        
        ```r
        reduce(1, `+`)
        # [1] 1
        
        reduce("a", `+`)
        # [1] "a"
        # no way to check that the input is valid
        
        reduce(integer(), `+`)
        # Error: `.x` is empty, and no `.init` supplied
        
        reduce(1, `+`, init) 
        # the result will be 1 + init
        
        reduce(integer(), `+`, .init = 0)
        # [1] 0
        
        # checks that length 1 inputs are valid for the function
        reduce("a", `+`, .init = 0)
        # Error in .x + .y: non-numeric argument to binary operator
        ```
        

- Predicate function
    
    
    | Predicate function | Usage |
    | --- | --- |
    | some(.x, .p) | returns TRUE if any element matches |
    | every(.x, .p) | returns TRUE if all elements match |
    | none(.x, .p) | returns TRUE if no element matches |
    | any(map_lgl(.x, .p)) | similar to some(.x, .p) |
    | all(map_lgl(.x, .p))  | similar to every(.x, .p) |
    | all(map_lgl(.x, negate(.p))) | similar to none(.x, .p) |
    | detect(.x, .p) | returns the value of the first match |
    | detect_index(.x, .p) | returns the location of the first match |
    | keep(.x, .p) | keeps all matching elements |
    | discard(.x, .p) | drops all matching elements |
    
    ```r
    # .p
    # returns a single TRUE or FALSE
    is.character()
    is.null()
    all()
    
    # some() returns TRUE when it sees the first TRUE
    # every(), none() return FALSE when see the first FALSE or TRUE respectively
    ```

    

- Useful packages
    - Commends for packages
        
        ```r
        install.packages("package_name")
        
        library()
        # look up the inforamtion of packages
        library(help=base) 
        # see a full list of functions inside the base package 
        library(help=package_name)
        
        package_name::FUN()
        ```
        
    
    | Packages | Usage |
    | --- | --- |
    | ggplot2 | data visualization |
    | quantmod | assist the quantitative trader in development, testing, statistically based trading models |
    | sas7bdat | read in the SAS data set |
    | tidyverse | tidyverse_update() for updating the package |
    
    
