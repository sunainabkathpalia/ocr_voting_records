
# Historical Electoral Data OCR Extraction

The goal of this project is to automate the extraction and structuring of historical electoral data from typewritten and scanned PDF documents. By converting these documents into a machine readable format, we can gain a comprehensive understanding of historical electoral trends in Brazil.

## Repository Structure
```
├── example_ocr.ipynb             # Example OCR with visualisation on a single image
├── batch_extraction.ipynb        # Batch extraction of all images 
├── Pictures_*/                # png exports of original pdfs
│   └── *.png
└── output/                       # Folder containing results
    └── combined_output.csv       # Folder containing results     

```

## Code Overview

- **example_ocr.ipynb**  
  Demonstrates OCR on a single png with visualizations:
  - Reads and enhances contrast of one image.  
  - Sends the image to Google Cloud Vision via layout parser.  
  - Filters text blocks by dynamic column-specific bounding rectangles.  
  - Cluster words into rows.  
  - Aligns columns (position, name, party, votes) into a table. 
  - Adds metadata municipality and year from the file path 

- **batch_extraction.ipynb**  
  Scales the same workflow to all images in pictures folder:
  - Iterates through all png files
  - Combines all tables into one.  

## Output

- `output/combined_output.csv`: Table with columns:
  - `position`: Role  
  - `name`: Candidate name  
  - `party`: Party affiliation  
  - `votes`: Votes received  
  - `flag`: election flag (0 = regular elections, 1 =  no elections)  
  - `municipality`: municipality name  
  - `year`: year of election

