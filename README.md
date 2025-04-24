
# Historical Electoral Data OCR Extraction

The goal of this project is to automate the extraction and structuring of historical electoral data from typewritten and scanned PDF documents. By converting these documents into a machine readable format, we can gain a comprehensive understanding of historical electoral trends in Brazil.

## Repository Structure
```
??? example_ocr.ipynb             # Example OCR with visualisation on a single image
??? batch_extraction.ipynb        # Batch extraction of all images 
??? Pictures_1972/                # png exports of original pdfs
?   ??? *.png
??? output/                       # Folder containing results
      ??? combined_output.csv       

```

## Code Overview

- **example_ocr.ipynb**  
  Demonstrates OCR on a single PNG page with visualizations:
  1. Reads and enhances contrast of one image.  
  2. Sends the image to Google Cloud Vision via LayoutParser.  
  3. Filters text blocks by column-specific bounding rectangles.  
  4. Cluster words into rows.  
  5. Aligns columns (position, name, party, votes) into a table. 
  6. -Adds metadata like municipality and year from the file path 

- **batch_extraction.ipynb**  
  Scales the same workflow to all images in `Pictures_1972/`:
  1. Iterates through all png files
  2. Combines all tables into one.  

## Output

- `output/combined_output.csv`: Table with columns:
  - `position`: Role  
  - `name`: Candidate name  
  - `party`: Party affiliation  
  - `votes`: Votes received  
  - `flag`: Quality flag (0 = regular elections, 1 =  no elections)  
  - `municipality`: municipality name  
  - `year`: year of election

