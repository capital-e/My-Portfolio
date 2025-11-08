<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Visualize data with QuickSight

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-analytics-quicksight)

**Author:** Jonathan Nutsugah  
**Email:** nutsugahjonathan@gmail.com

---

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-analytics-quicksight_6c7f7ef0)

---

## Introducing Today's Project!

In this project, I will demonstrate how to build an end-to-end data dashboard using AWS S3 and QuickSight. I'm doing this project to learn industry-standard BI tools and create a portfolio piece showcasing my data visualization skills.

### Tools and concepts

In this project, I learned how to use Amazon QuickSight to connect datasets from S3 using a manifest.json file, create and customize visualizations, apply filters to analyze specific data, build dashboards, and export them as PDFs for sharing.


### Project reflection

1 hour 30 minutes

Thank You

---

## Upload project files into S3

The two files I stored in my S3 bucket are:

CSV file - my actual dataset with all the data
manifest.json file - the configuration file that tells QuickSight how to read and connect to my CSV data

I replaced the placeholder URL in the manifest.json file with my actual S3 CSV file URL because this file tells QuickSight exactly where to find my dataset.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-analytics-quicksight_3c3cd85a)

---

## Create QuickSight account

Creating a QuickSight account costs nothing initially, as AWS offers a 30-day free trial.

Creating an account took me just a few minutes—about 5 minutes to sign up and get started with Amazon QuickSight.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-analytics-quicksight_f4ab4214)

---

## Download the Dataset

I visited the "Datasets" page in QuickSight, then clicked "New dataset", selected "S3" as the data source, and used the manifest.json file to connect my S3 bucket.

I need the manifest.json file because it tells QuickSight where to find the data in my S3 bucket, how the files are structured, and how to import them correctly. It acts as a guide for loading and interpreting the data.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-analytics-quicksight_6f874996)

---

## My first visualization

To create visualizations on QuickSight, I select a dataset, choose a visual type (like a bar chart or pie chart), then drag and drop fields into the appropriate areas (like X-axis, Y-axis, or Values).

The chart/graph shown here is a breakdown of the count of records by release year and the type.

To create this visualization, I dragged the release_year field into the Y Axis heading and the type field (to distinguish TV shows from movies) into the Group/Color heading. This shows a breakdown of TV shows vs movies for each year.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-analytics-quicksight_aff3aad7)

---

## Using filters

Filters are useful because they help focus on specific parts of the data, making it easier to analyze trends, compare subsets, and answer targeted questions without being overwhelmed by all the information.

The visualization I uploaded shows the number of TV shows and movies categorized as 'Action & Adventure', 'TV Comedies', or 'Thrillers' that were released in 2015 or later.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-analytics-quicksight_c32248c5)

---

## Setting up a dashboard

As a finishing touch, I titled all the visuals.

To export my dashboard as a PDF, I clicked the Share button at the top-right corner, selected Export to PDF, chose the desired layout and pages, then clicked Export to download the PDF version of my dashboard.

![Image](http://learn.nextwork.org/amused_pink_zesty_alpaca/uploads/aws-analytics-quicksight_6c7f7ef0)

---

## Refreshing source data

---

---
