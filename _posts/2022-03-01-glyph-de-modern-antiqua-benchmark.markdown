---
layout: post
title:  "Benchmarking Glyph on Modern-Antiqua German Texts"
date:   2022-03-01 15:52:19 +0300
categories: benchmarks ocr
index: true
---

We benchmark the **German** version of the Glyph OCR Engine on images of scanned documents written using **modern or antiqua** fonts and with varying degrees of degradation.
The results are measured using the *Character Error Rate* (**CER**) metric and compared to existing solutions.

We determine the **CER** using the following formula:

$$ CER(\hat{text}, text) = \frac{I + S + D}{max(|\hat{text}|, |text|)} $$

- where $$I$$, $$S$$ and $$D$$ represent the number of insertions, substitutions and deletions. Consequently, $$I+S+D$$ is the **Levenshtein** distance. We scale the result by dividing the sum by the maximum number of characters to limit the **CER** to **1**; $$\hat{text}$$ is the recognized sequence of characters and $$text$$ is the ground truth information.


**Note**: The presented samples, ground truth texts and results of different OCR engines are provided by a collaborating third party for performance assessment.


# CER Plot

Below are a few interactive CER plots (lower is better) which compare Glyph to existing products.

<iframe width="851" height="526" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vT9j4CjdNt9WeRB1tH2D7G15YsZKUwEHVxgFgweittDverixKkqI0XKCYcDgd8qqiPmiR6hjBx9lpNv/pubchart?oid=890205284&amp;format=interactive"></iframe>
{: style="display:block; margin:0 auto;"}

<iframe width="851" height="526" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vT9j4CjdNt9WeRB1tH2D7G15YsZKUwEHVxgFgweittDverixKkqI0XKCYcDgd8qqiPmiR6hjBx9lpNv/pubchart?oid=660542569&amp;format=interactive"></iframe>
{: style="display:block; margin:0 auto;"}





# Statistics

We provide numeric / tabular data of the current benchmark; **best results** are in **bold**; an average of all CER values is found on the last row.

<iframe width="100%" height="310px" frameborder="0" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vT9j4CjdNt9WeRB1tH2D7G15YsZKUwEHVxgFgweittDverixKkqI0XKCYcDgd8qqiPmiR6hjBx9lpNv/pubhtml?gid=463942054&amp;single=true&amp;widget=false&amp;headers=true"></iframe>


<iframe width="100%" height="610px" frameborder="0" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vT9j4CjdNt9WeRB1tH2D7G15YsZKUwEHVxgFgweittDverixKkqI0XKCYcDgd8qqiPmiR6hjBx9lpNv/pubhtml?gid=116475021&amp;single=true&amp;widget=false&amp;headers=true"></iframe>


# Live Demo

Please find in this [Google Colab Notebook](https://colab.research.google.com/drive/1Y9kF4pjtAZX-pxZrKwVOBMr4fKyQA9CN?usp=sharing) a live demo code of Glyph which displays the involved images, recognized texts and inference times.
A Google account might be required to view the results.