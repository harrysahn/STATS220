# Creating the zombie brain meme!
## How I created the zombie brain meme...

Bit of background before diving in the code.
The motivation for this meme was to serve as a reminder for students with *more than one deadline* to pace themselves and make sure not to leave everything until the due date!

**Always start earlier and avoid unnecessary stress!**

The meme also shows the 4 steps from being a bad student to becoming a great one:
1. Procrastinator
2. Kind of having an idea of what to do
3. Doing the right thing and starting early
4. The ideal student

There are two main components of the meme:
- The zombies from 'Plants vs Zombies'
- Accompanying text

My favourite line of code is: 
`
blue_rec1 <- image_blank(width = 400,
            height = 200,
            color = "#96B3F3") %>%
  image_annotate(text = "Leaving assignments
til the day before
the due date.",
               gravity = 'center',
               font = 'Helvetica',
               size = "21", color = "#313131", weight = "550")
`
The image_blank() function gives us so much freedom to customise and create something from scratch - such a powerful piece of code! I'm hoping to add more customisations and explore the full potential of this function in the future 😎.

[The original source for the meme.](https://i.redd.it/lsxawxwo3ln31.png)

Without further ado, you can click [this](https://i.ibb.co/mzNy7Fk/zombie-brain-meme.png) to access my version of the meme, or [here!](https://github.com/harrysahn/STATS220/blob/main/zombie_brain_meme.png)

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

