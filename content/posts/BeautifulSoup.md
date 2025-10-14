---
date: '2025-10-14T22:20:48+05:30'
draft: false
title: 'Cleaning Messy Data with 5 minute Gemini Prompt'
---
# Using Gemini for a Quick Text Cleaning Script

## The Task

I needed to run a text cleaning operation on almost 500,000 rows of data. The text contained URLs, HTML tags, Math ML tags, and hrefs. I had to clean all of this data before running a pipeline operation on it. I decided to use Gemini to write some starter python code that I could change to get this done.

## The Prompt

I spent about five minutes writing an initial prompt. I included these points in the prompt:
* What to clean: URLs, HTML tags, and escaped HTML entities like `&lt;`.
* The input will be a CSV file.
* The output should be appended to the CSV file.
* I gave a sample of the text.
* I asked it to create a Colab playground for me to test the code.

## The Result

The first shot code worked for about 70% of the cases. I made some more tweaks to finalize it.

Here is the colab link and the code below.

**Colab Link:** https://colab.research.google.com/drive/1s6E4lxJ9WjyLCGaM2SQGfdTI69vNJzu9?usp=sharing

## The Code

```python
# pip install beautifulsoup4

from bs4 import BeautifulSoup
import re
import html # <-- Import the html library

def clean_text_advanced(raw_text: str) -> str:
    """
    Cleans a string containing standard or escaped HTML, MathML, and other special characters.

    Args:
        raw_text: The input string to be cleaned.

    Returns:
        A cleaned, plain English string.
    """
    # 1. Decode HTML entities (e.g., &lt; to <)
    unscaped_text = html.unescape(raw_text)

    # 2. Use BeautifulSoup to parse the text and remove all tags
    soup = BeautifulSoup(unscaped_text, 'html.parser')
    text_only = soup.get_text(separator=' ') # Use a space as a separator

    # 3. Use regex to clean up remaining artifacts
    # Replace multiple whitespace characters (spaces, newlines, tabs) with a single space
    cleaned_text = re.sub(r'\s+', ' ', text_only)

    # 4. Remove any leading/trailing whitespace
    return cleaned_text.strip()

# ---==| Example Usage with Your Sample |==---

messy_text = "Yes the cutoff for 2023 year is released for IET. Check out this link for detailed information : [https://www.shiksha.com/college/institute-of-engineering-and-technology-iet-dr-a-p-j-abdul-kalam-technical-university-lucknow-24137/cutoff](https://www.shiksha.com/college/institute-of-engineering-and-technology-iet-dr-a-p-j-abdul-kalam-technical-university-lucknow-24137/cutoff) The AKTU cutoff for B.Tech in Computer Science and Engineering for the general category is expected to be around 32075 for Round 1 and 62320 for Round 4 in the Uttar Pradesh Domicile Quota. The minimum qualifying marks required for various categories in B.Tech courses are 25% for general, 25% for OBC, 20% for SC, and 25% for ST."
cleaned_version = clean_text_advanced(messy_text)

print(f"Cleaned Text:\n{cleaned_version}")

import pandas as pd
from bs4 import BeautifulSoup
import re
import html
import os # Used for creating a sample file

# ----------------------------------------------------------------------------
# 1. THE CLEANING FUNCTION (Unchanged from before)
# ----------------------------------------------------------------------------
def clean_text_advanced(raw_text: str) -> str:
    """
    Cleans a string containing standard or escaped HTML, MathML, etc.
    """
    # Ensure input is a string, handle potential non-string data like NaN
    if not isinstance(raw_text, str):
        return "" # Return an empty string for non-string inputs

    # Decode HTML entities (e.g., &lt; to <)
    unscaped_text = html.unescape(raw_text)

    # Use BeautifulSoup to parse and remove all tags
    soup = BeautifulSoup(unscaped_text, 'html.parser')
    text_only = soup.get_text(separator=' ') # Use a space as a separator

    # Use regex to clean up remaining artifacts
    cleaned_text = re.sub(r'\s+', ' ', text_only)

    return cleaned_text.strip()


# ----------------------------------------------------------------------------
# 2. THE CSV PROCESSING FUNCTION (New)
# ----------------------------------------------------------------------------
def process_csv(input_filepath: str, output_filepath: str, column_to_clean: str):
    """
    Reads a CSV, cleans a specified text column, and saves the result to a new CSV.

    Args:
        input_filepath: Path to the source CSV file.
        output_filepath: Path to save the new CSV file.
        column_to_clean: The name of the column containing the messy text.
    """
    print(f"🔄 Starting to process '{input_filepath}'...")
    try:
        # Read the CSV file into a pandas DataFrame
        df = pd.read_csv(input_filepath)
        print(f"✅ Successfully loaded {len(df)} rows.")

        # Check if the specified column exists
        if column_to_clean not in df.columns:
            print(f"❌ Error: Column '{column_to_clean}' not found in the CSV!")
            print(f"Available columns are: {list(df.columns)}")
            return

        # Apply the cleaning function to the specified column
        # .astype(str) handles any non-string data in the column
        # The new column will be named 'cleaned_text'
        print(f"🧼 Cleaning text in column '{column_to_clean}'...")
        df['cleaned_text'] = df[column_to_clean].astype(str).apply(clean_text_advanced)

        # Save the updated DataFrame to a new CSV file
        df.to_csv(output_filepath, index=False, encoding='utf-8')
        print(f"✨ Success! Cleaned data saved to '{output_filepath}'")

    except FileNotFoundError:
        print(f"❌ Error: The file '{input_filepath}' was not found.")
    except Exception as e:
        print(f"An unexpected error occurred: {e}")


# ----------------------------------------------------------------------------
# 3. EXAMPLE USAGE
# ----------------------------------------------------------------------------
if __name__ == "__main__":
    # --- Create a sample CSV for demonstration ---
    sample_data = {
        'id': [1, 2, 3],
        'messy_content': [
            '<p>Here is <b>bold</b> text &amp; a math equation: <math><mi>a</mi><msup><mi>x</mi><mn>2</mn></msup></math></p>',
            '<p>Yes, joining the &lt;a href="..."&gt;top colleges&lt;/a&gt; can be worthwhile.',
            'Just some      regular text with   extra spaces.'
        ],
        'other_data': ['A', 'B', 'C']
    }
    sample_df = pd.DataFrame(sample_data)
    sample_input_file = 'sample_input.csv'
    sample_df.to_csv(sample_input_file, index=False)

    # --- Configuration: YOU NEED TO SET THESE VARIABLES ---
    # The name of your input file
    input_file = '500 ICNC ATFs cleaned.csv'
    # The name of the column you want to clean
    column_name = 'cleaned_text1'
