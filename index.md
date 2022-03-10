# Hello
This is my meme that I made using the [{magick}](https://cran.r-project.org/web/packages/magick/vignettes/intro.html).

![](my_meme.png)

# Inspiration
I made this meme because I had already used this format to make a meme when I was in high school.
I found it easy to find and adapt for my own purposes. 
This meme shows a man trying to the good stuff, which is the STATS220 course which is new as I used ned characters (Me) and a new thing that the man takes out of the envelope.



#The R code I used
library(magick)

me <- image_blank(50, 50, color="#000000") %>%
  image_annotate("ME", gravity="center", color="#FFFFFF")

panel_1 <- image_read("memecomponents/1.png") %>%
  image_scale(250)

panel_1_combined <- image_composite(panel_1, me, offset= "+150+85")


panel_2 <- image_read("memecomponents/2.png") %>%
  image_scale(250)

panel_3 <- image_read("memecomponents/3.png") %>%
  image_annotate("STATS220", location = "+60+140", size=20) %>%
  image_scale(250)

panel_4 <- image_read("memecomponents/4.png") %>%
  image_scale(250)

panel_4_combined <- image_composite(panel_4, image_scale(me, "x100"), offset="+90+100")

first_row <- c(panel_1_combined, panel_2) %>% 
  image_append()

second_row <- c(panel_3, panel_4_combined) %>%
  image_append()

meme <- c(first_row, second_row) %>%
  image_append(stack = TRUE)
  
  meme

image_write(meme, "my_meme.png")
