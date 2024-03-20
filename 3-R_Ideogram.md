# Chromosome Ideogram to visualize gene density and repeat regions using ChromoMap [Link](https://cran.r-project.org/web/packages/chromoMap/vignettes/chromoMap.html)

**1. Installation**
```
library(readr)
install.packages("chromoMap", dependencies = TRUE)
library(chromoMap)
```
**2. data.frame formation**
```
chrm_file <- (read.table("chrm_ideogram_file.txt",sep = "\t"))
anno_file <- (read.table("anno_t2t_file_2.txt",sep = "\t"))
```

**3. Chromomap library with data input with export image**
```
chromoMap("chrm_ideogram_file.txt", "anno_t2t_file_2.txt", 
          chr_color = c("lightgreen"), 
          n_win.factor = 2,
          text_font_size = 14,
          label_font = 14,
          chr_length = 4,
          chr_width = 18,
          chr_curve = 5,
          win.summary.display = TRUE,
          data_based_color_map = TRUE,
          data_type = "numeric",
          data_colors = list(c("lightgreen", "black")),
          left_margin = 80,
          export.options = TRUE)

```

