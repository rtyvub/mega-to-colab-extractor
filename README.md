# mega-to-colab-extractor
A simple script to extract MEGA ZIP files directly in Google Colab.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rtyvub/mega-to-colab-extractor/blob/main/Mega_Extractor.ipynb)

A quick Google Colab notebook to download and extract MEGA `.zip` files directly in a temporary cloud workspace. 

I put this together because older Python wrappers like `mega.py` are currently breaking in Colab due to Python 3.12 updates (throwing `asyncio` and `tenacity` dependency loops). This script bypasses those Python errors entirely by using Ubuntu's native `megatools` for the download phase.

### Why use this?
* **Zero Local Storage:** Everything downloads and unzips on Google's temporary servers. Great for massive files or if you are on a limited data plan.
* **Self-Destructing Privacy:** It runs in a temporary Colab workspace. The files are completely wiped the second you close the browser tab. Nothing syncs to your personal Google Drive or local machine.
* **It Actually Works:** Bypasses the current `mega.py` version conflicts.

### How to Use
1. Click the **Open in Colab** button above.
2. In the code block, find the `mega_url` variable and paste your MEGA link inside the quotes.
3. Hit the **Play** button.
4. Once it finishes, click the little **Folder icon** on the left sidebar of Colab to view or individually download your extracted files.

### Under the Hood
It uses `apt-get` to install `megatools`, pulls the archive, and then uses Python's built-in `zipfile` and `glob` modules to locate and unpack the archive into a temporary `/content/Extracted_Photos` directory.
