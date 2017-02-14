---
title       : Insert the chapter title here
description : Insert the chapter description here
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:70bd65f8c9
## A really bad books

Have a look at the plot that showed up in the viewer to the right. Which type of books has the worst rating assigned to it?

*** =instructions
- Adventure
- Action
- Animation
- Comedy
- Horror

*** =hint
Have a look at the plot. Which color does the point with the lowest rating have?

*** =pre_exercise_code
```{r}
# The pre exercise code runs code to initialize the user's workspace.
# You can use it to load packages, initialize datasets and draw a plot in the viewer

bookss <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/bookss.csv")

library(ggplot2)

ggplot(bookss, aes(x = runtime, y = rating, col = genre)) + geom_point()
```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad <- "That is not correct!"
msg_success <- "Exactly! There seems to be a very bad action books in the dataset."
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad))
```

--- type:NormalExercise lang:r xp:100 skills:1 key:88eed71620
## More Cooool bookss

In the previous exercise, you saw a dataset about bookss. In this exercise, we'll have a look at yet another dataset about bookss!

A dataset with a selection of bookss, `books_selection`, is available in the workspace.

*** =instructions
- Check out the structure of `books_selection`.
- Select bookss with a rating of 5 or higher. Assign the result to `good_bookss`.
- Use `plot()` to  plot `good_bookss$Run` on the x-axis, `good_bookss$Rating` on the y-axis and set `col` to `good_bookss$Genre`.

*** =hint
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[books_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`.

*** =pre_exercise_code
```{r}
# You can also prepare your dataset in a specific way in the pre exercise code

library(MindOnStats)
data(Movies)
books_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"),c("Genre", "Rating", "Run")]

# Clean up the environment
rm(Movies)
```

*** =sample_code
```{r}
# books_selection is available in your workspace

# Check out the structure of books_selection
library(dplyr)



# Select bookss that have a rating of 5 or higher: good_bookss


# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre

```

*** =solution
```{r}
# books_selection is available in your workspace

# Check out the structure of books_selection
str(books_selection)

# Select bookss that have a rating of 5 or higher: good_bookss
good_bookss <- books_selection[books_selection$Rating >= 5, ]

# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre
plot(good_bookss$Run, good_bookss$Rating, col = good_bookss$Genre)
```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

test_object("good_bookss")

test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

test_error()

success_msg("Good work!")
```
