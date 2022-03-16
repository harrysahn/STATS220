https://i.ibb.co/mzNy7Fk/zombie-brain-meme.png

```{r}
library(magick)

# zombie brain meme

panel_one <- image_read(path = "https://i.ibb.co/vhK4DyG/1.png") %>%
  image_scale("x200") %>%
  image_crop("400x200")

panel_two <- image_read(path = "https://i.ibb.co/g41bV0b/2.png") %>%
  image_scale("x200") %>%
  image_crop("400x200") 

panel_three <- image_read(path = "https://i.ibb.co/K6x00CF/3.png") %>%
  image_scale("x200") %>%
  image_crop("400x200-1")

panel_four <- image_read(path = "https://i.ibb.co/2n5mSLD/4.png") %>%
  image_scale("x200") %>%
  image_crop("400x200+50")

blue_rec1 <- image_blank(width = 400,
            height = 200,
            color = "#96B3F3") %>%
  image_annotate(text = "Leaving assignments
til the day before
the due date.",
               gravity = 'center',
               font = 'Helvetica',
               size = "21", color = "#313131", weight = "550")

blue_rec2 <- image_blank(width = 366,
            height = 200,
            color = "#96B3F3") %>%
  image_annotate(text = "Starting assignments
a few days before the 
due date.",
               gravity = 'center',
               font = 'Helvetica',
               size = "21", color = "#313131", weight = "550")

blue_rec3 <- image_blank(width = 395,
            height = 200,
            color = "#96B3F3") %>% 
  image_annotate(text = "Starting assignments early
and pacing them out.",
               gravity = 'center',
               font = 'Helvetica',
               size = "21", color = "#313131", weight = "550")

blue_rec4 <- image_blank(width = 400,
            height = 200,
            color = "#96B3F3") %>%
  image_annotate(text = "Starting assignments early
and working on them a 
little each day. Asking for
help from tutors and peers.
Going to office hours and
lab times.",
               gravity = 'center',
               font = 'Helvetica',
               size = "15", color = "#313131", weight = "550")

zombie_brains1 <- c(panel_one, blue_rec1)
zombie_brains2 <- c(panel_two, blue_rec2)
zombie_brains3 <- c(panel_three, blue_rec3)
zombie_brains4 <- c(panel_four, blue_rec4)

final_meme1 <- image_append(zombie_brains1)
final_meme2 <- image_append(zombie_brains2)
final_meme3 <- image_append(zombie_brains3)
final_meme4 <- image_append(zombie_brains4)

final_meme_almost <- c(final_meme1, final_meme2, final_meme3, final_meme4)

final_meme <- image_append(image_scale(final_meme_almost, "750"), stack = TRUE)

image_write(final_meme, "zombie_brain_meme.png")
```
