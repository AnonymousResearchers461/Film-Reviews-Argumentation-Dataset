# Film Reviews Argumentation Dataset

This is a dataset of **Kinopoisk film reviews** from top-250 and bottom-100 films (2004-2012). This dataset is based on the data found in `blinoff/kinopoisk` [Blinov et al., 2013](https://huggingface.co/datasets/blinoff/kinopoisk). 

1084 negative reviews, 1098 positive reviews and 1098 neutral reviews were selected from the initial dataset (based on grade3). Then, the amount of arguments in a given review praising the film (column for) and criticizing the film (column against) was manually written down. 

Afterwards, the column `arg_label` was created based on the following rules:
1. If `for == 0` and `against == 0` -> `arg_label = "Neutral"`
2. If `for == 0` and against != 0 -> `arg_label = against`
3. If `for != 0` and against == 0 -> `arg_label = for`
4. If `for - against` > 2` -> `arg_label = for`
5. If `against - for` > 2` -> `arg_label = against`
6. If the absolute value of `for - against <= 2` -> `arg_label = "Neutral"`

Old Kinoposk reviews were written before the current system of Good/Bad/Neutral reviews was established, so they were automatically marked as Neutral on the website. Additionally, the content of a handful of reviews did not match their grade3. A NEW_grade3 was manually assigned to such reviews. In all other cases, the initial grade3 was duplicated in NEW_grade3.
