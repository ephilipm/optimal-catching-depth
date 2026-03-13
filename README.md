# Optimal Catching Depth

Estimating optimal catcher receiving depth using pitch-level strike probability and framing outcomes.

## Project Overview

Catchers must choose how far behind home plate to set up before each pitch. Setting up closer to the plate may help steal low-probability strikes, while setting up deeper can help secure high-probability strikes and improve pitch reception. The optimal depth likely varies across catchers depending on their framing tendencies and pitch characteristics.

This project analyzes pitch-level data to estimate the catcher setup depth that maximizes framing value. Using expected strike probability and observed called strike outcomes, I construct a framing score and examine how that score changes across catcher depth.

The analysis produces both:

- catcher-specific optimal depth estimates
- a population-level baseline depth when individual samples are small

## Methods

The workflow follows several steps:

1. **Data filtering**
   - Restrict to pitches that were not swung at
   - Remove observations with missing catcher depth or strike probability

2. **Framing score construction**
   - Positive value: called strike on a pitch with low expected strike probability  
   - Negative value: missed called strike on a pitch with high expected strike probability

3. **Depth trimming**
   - Catcher depth is trimmed to the 5th–95th percentile for each catcher to reduce outlier influence

4. **Depth binning**
   - Depth is grouped into 0.1-foot bins to smooth variation in positioning

5. **Optimal depth estimation**
   - Average framing score is calculated for each depth bin
   - The depth with the highest average framing score is identified as the optimal receiving depth

## Case Study

The repository also includes a case study evaluating an individual catcher (“John Doe”). Using the same framework, I estimate the depth at which this catcher produces the strongest framing outcomes and compare it with his current average setup.

The analysis suggests that optimal receiving depth can differ meaningfully across catchers rather than following a single universal recommendation.

## Repository Structure

- **Optimal_Catching_Depth.Rmd**  
  Main analysis estimating optimal catcher depth across the dataset.

- **John_Doe_Catching_Depth.Rmd**  
  Individual catcher case study applying the method to a single player.

- **PDF reports**  
  Rendered outputs containing plots and results so the analysis can be reviewed without the dataset.

## Tools

- R  
- tidyverse  
- ggplot2  
- R Markdown

## Author
Evan Metzger
