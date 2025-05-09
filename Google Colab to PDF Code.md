# Best method to convert a Colab Notebook to PDF

1. First, save the notebook to your working directory
2. Download notebook then reupload
3. Install required dependencies:
   ```bash
   sudo apt-get update
   sudo apt-get install texlive-xetex
   sudo apt-get install pandoc
   pip install nbconvert
   ```
      Or in a code cell:

   ```python
   !sudo apt-get update
   !sudo apt-get install texlive-xetex
   !sudo apt-get install pandoc
   !pip install nbconvert
   ```
4. Convert the notebook to PDF:
   ```bash
   jupyter nbconvert --to pdf your_notebook.ipynb
   ```
    ```python
   !jupyter nbconvert --to pdf your_notebook.ipynb
   ```

The PDF will be created in the same directory as your notebook.
