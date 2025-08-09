# DORK-RECON

A powerful tool designed for cybersecurity professionals, penetration testers, and OSINT (Open Source Intelligence) researchers to mine valuable information using advanced Google search queries known as Google Dorks.

---


# Tool Contents

- Tool purpose and overview

- Features list

- Dependencies and setup

- How to obtain and set the Google API key

- Usage instructions with command examples 

- Ethical use guidelines

- Contact or author information


---

# DORK RECON involves crafting specialized search queries that can uncover:

- Exposed and vulnerable WordPress plugin directories and login pages.

- Leaked credentials, such as passwords in logs, .env files, or .ini files.

- Open FTP directories, CCTV camera feeds, sensitive backup files, and more.

- Publicly indexed information useful for OSINT including maps, weather, stock data, and definitions.

By automating these queries to Google Custom Search API, the tool helps quickly identify hidden or sensitive online information that might be exposed unintentionally—accelerating vulnerability detection and intelligence gathering.

---

# Core Features

- Built-in categorized dork sets targeting common vulnerabilities and OSINT data: **WordPress, credentials, cameras, backups, login portals, media, and informational queries**.

- Interactive mode to input custom Google search queries freely.

- Bulk search mode, reading queries from a file to run multiple dork queries concurrently.

- Multi-threaded execution with configurable delays to optimize query speed and avoid IP blocking.

- Safe Search toggle to filter out explicit content.

- Colorful, user-friendly terminal interface with a welcome ASCII logo, colored prompts, and formatted results.

- Option to save output results to JSON files for further analysis.

- Placeholder for OSINT enrichment, e.g., integration with Shodan.

- Fully supports Google Custom Search API limits including pagination and result count.



---

# Dependencies

**Your tool requires the following Python packages**:

- requests — for HTTP requests to Google API.

- colorama — for colored terminal output (cross-platform).

- Python Standard Library modules: argparse, json, threading, queue, time.

# Installation:

**Before running the tool, install dependencies with**:


    pip3 install requests colorama



# How to Use the Tool

**Setting the Google API Key and Custom Search Engine (CSE) ID**

**Your script includes placeholders for**:


    API_KEY = "YOUR_GOOGLE_API_KEY_HERE"
    CSE_ID = "YOUR_CUSTOM_SEARCH_ENGINE_ID_HERE"

**These must be replaced with your actual Google API credentials before use**.


---

# Steps to Obtain Google API Key and CSE ID

**1.Create a Google Cloud Project**:

- Visit the Google Cloud Console: https://console.cloud.google.com/

- Create a new project or select an existing one.


**2.Enable Custom Search API**:

- In the left-hand menu, click **APIs & Services > Library**.

- Search for **Custom Search API**.

- Enable the API for your project.

**3.Create API Credentials**:

- Go to **APIs & Services > Credentials**.

- Click **Create Credentials > API Key**.

- **Copy the generated API Key**.

 
**4.Create a Custom Search Engine (CSE)**:

- Visit Google Custom Search: https://cse.google.com/cse/all

 - Click **Add** to create a new search engine.

- In the Sites to search box, input **www.example.com** or for entire web search (note: full web search might require configuration steps).

- Give the CSE a name and create.

**5.Get your Custom Search Engine ID**:

- On the CSE control panel, click on the search engine you created.

- Copy the **Search engine ID** from the Details page (a string like **012345678901234567890:abcde_fghij**).

**6.Update your script**:

- Paste the **API Key and CSE ID** into your script.


---

# Running the Tool

**Manual installation**: 

- Save the tool script via the link below:

- Link isn't up yet…

-Example: copy the script via the link and paste it into nano. Type **Ctrl + O. Enter, Ctrl + X** to exit.

- - - 

**Examples of usage**:

**Interactive Mode**:


      python3 dork_recon.py --interactive

**Toggle Google Safe Search**:

- Safe Search on (default):
  
      --safe_search on

- Safe Search Off:

      --safe_search off

**When you run the script, you can specify it as**:

    python3 dork_recon.py --dork wordpress --safe_search off/on (depending on your choice)
    
**Or for interactive mode**:

    python3 dork_recon.py --interactive --safe_search on


**How to verify the safe search is active**:

- Run with **--safe_search on** and a query likely to return explicit content.

- Compare results with --safe_search off.

- Results should be filtered in the first case.
  

**List all built-in dork categories**:


    python3 dork_recon.py --list_dorks
    

- Enter any Google query or dork interactively. Type **exit** to quit.

- - -

- **Single dork or category**:
  
       python3 dork_recon.py --dork wordpress --num_results 10 --output filename/json

---

    python3 dork_recon.py --dork "weather in New York" --num_results 10 --output filename/json


- - - 

    python3 dork_recon.py --dork "maps of New York" --num_results 5 --output filename/json

    
- - - 

       python3 dork_recon.py --dork "inurl:view/view.shtml" --output filename/json

  **Or if you want to search this specific dork on a domain, add the --domain option**:

        python3 dork_recon.py --domain example.com --dork "inurl:view/view.shtml" --output filename/json      

- - - 

**Bulk Search Mode (Running Queries from a File)**

**1. Prepare your Dork File**:
  
- Create a text file (e.g., **dorks.txt**) with one Google dork query or category name per line. For example:
  
      wordpress
      credentials
      inurl:wp-login.php
      filetype:env password
      site:example.com inurl:admin


  **2. Run the Tool with the File**:
  
- Use the --dork_file argument pointing to your file:

      python3 dork_recon.py --dork_file dorks.txt --num_results 10 filename.json
  
**This tells the tool to read all queries from the file and run the Google Custom Search API on each and save them to your filename**. 

- - - 

**Multi-threaded Execution and Delay Configuration**

**1.Enable Multi-threading**:

- Use the --threads option to specify how many threads (parallel workers) the tool uses for searching.
  
**Example**:

    python3 dork_recon.py --dork_file dorks.txt --threads 4 --num_results 10 filename.json

**This runs up to 4 dork searches concurrently, speeding up the overall process**.

- - - 

**Configure Delay Between Requests:
Use the --delay option to set the waiting time (in seconds) between API requests per thread to avoid rate-limiting or IP blocking.**

**Example**:


    python3 dork_recon.py --dork_file dorks.txt --threads 4 --delay 3 --num_results 10 filename.json


Here, each thread waits 3 seconds between its Google API calls.

**How It Works Internally**:

- The tool queues all dork queries.
Multiple worker threads take items from the queue and perform searches in parallel.

- The delay between requests per thread helps stay within API usage limits.

- - - 

**Feel free enter any Google search query of your choice to obtain the most relevant and precise results.**

- - - 

**Note**: 

To ensure all results from your entered dorks are preserved, please specify your preferred output filename using the --output option (e.g., **--output filename.json**). Avoid running search queries without setting an output file to prevent loss of result data.


---

# NOTE: 

In the **Interactive Mode**, you can enter any Google search query of your choice to obtain the most relevant and precise results.

- **Example**:


- Find all indexed pages on example.com:

      site:example.com

- Search for pages containing the exact phrase “admin login”:

        "admin login"
   
  
- Find PDF files related to cybersecurity:

      filetype:pdf cybersecurity
  
 
Get current weather information for New York:

    weather:new york


Locate web pages with “index of” in the title and mention “backup”:

    
    intitle:"index of" backup


Find social media site containing a specific username:

    site:social/username (site:x.com ctprecious ) 

And more!!

**How to Use These Queries in the Tool's Interactive Section**:


**Start the tool in interactive mode**:

    python3 dork_recon.py --interactive


- Enter any of the above queries exactly as shown (or your own variations) at the prompt:

- **Enter Google search query**:
  

- The tool will run the query against Google Custom Search API and display results back with colored formatting.
  
- **To exit interactive mode, type**:
  
- **exit**
  
- - - 

# Further Notes

- Respect Google API rate limits: the tool enforces delays and request batching.

- The tool supports Safe Search filtering toggling.

- Always use the tool ethically, with permission on target domains.

- The interactive mode supports free-form Google queries, beyond built-in dork categories.

---

If you encounter any issues or have questions about using this tool, please feel free to reach out. You can report bugs, request features, or ask for help by opening an issue on the GitHub repository or contacting the author directly.Your feedback is valuable and helps improve the tool for the community. 



