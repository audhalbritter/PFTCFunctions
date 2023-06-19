
# PFTCFunctions

**PFTCFunctions** is a collection of R functions used to collect plant
functional traits during the Plant Functional Trait Course (PFTC). The
trait data collection is organized in multiple stations where different
traits are measured, and we call it the trait wheel (see figure below).

<div class="figure">

<img src="R/TraitWheel_small.png" alt="The different stages from collection, processing and curating data from the trait wheel." width="100%" />
<p class="caption">
The different stages from collection, processing and curating data from
the trait wheel.
</p>

</div>

The package contains the following: - download_PFTC_data -
get_PFTC_envelope_code - make_barcode_labels

## Installation

Install **PFTCFunctions** from [GitHub](https://github.com/) using the
following code:

``` r
# install.packages("remotes")
remotes::install_github("Plant-Functional-Trait-Course/PFTCFunctions")
```

## Download PFTC data

to be added

## Make unique envelope codes

The function *get_PFTC_envelope_code* creates unique hashcodes, which we
use as unique IDs for each individual leaf. The codes are randomly
created using a specific seed for each course (see table below) and
contain 3 letters followed by 4 numbers.

| Country  | seed | Campaign | as.3.5 |
|:---------|-----:|:---------|:-------|
| Peru     |    1 | PFTC3    | TRUE   |
| Peru     |    1 | Puna     | TRUE   |
| Svalbard |   32 | PFTC4    | TRUE   |
| Peru     |    6 | PFTC5    | TRUE   |
| Norway   |   49 | PFTC6    | FALSE  |

The as.3.5 decides if using R \> 3.5 if to use the old or new sample
method. Note that for PFTC6, as.3.5 needs to be FALSE.

This is how to use the function:

``` r
library(PFTCFunctions)
## create list with all envelope codes. And show the first five values
all_codes <- get_PFTC_envelope_codes(seed = 1)
all_codes$hashcode[1:5]
#> [1] "AAA4667" "AAB6541" "AAC0068" "AAD5960" "AAE3544"
```

## Make barcode labels

The *make_barcode_labels* function creates a PDF with barcodes from the
unique IDs with can then be printed on stickers.

In the trait wheel, each sampled leaf gets an ID and is put into an
envelope for further processing. To avoid errors and simplify the
process, we make barcodes from the unique IDs and produce stickers,
which are put on the envelopes (see picture below).

We use the following label type: Avery or Herma 45.7 x 21.2 mm, 48
stickers per page For example see
[here](https://www.lyreco.com/webshop/NONO/etiketter-avery-45-7-x-21-2-mm-hvit-eske-c3a0-960-stk-product-000000000002760191.html).

<div class="figure">

<img src="R/envelope.png" alt="Envelope with a barcode sticker." width="50%" />
<p class="caption">
Envelope with a barcode sticker.
</p>

</div>

Other types and sizes of labels can be used, but the function has to be
adapted.
