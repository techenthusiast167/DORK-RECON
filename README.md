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

- In the left-hand menu, click APIs & Services > Library.

- Search for Custom Search API.

- Enable the API for your project.

**3.Create API Credentials**:

- Go to APIs & Services > Credentials.

- Click Create Credentials > API Key.

- **Copy the generated API Key**.

 
**4.Create a Custom Search Engine (CSE)**:

- Visit Google Custom Search: https://cse.google.com/cse/all

 - Click Add to create a new search engine.

- In the Sites to search box, input **www.example.com** or for entire web search (note: full web search might require configuration steps).

- Give the CSE a name and create.

**5.Get your Custom Search Engine ID**:

- On the CSE control panel, click on the search engine you created.

- Copy the Search engine ID from the Details page (a string like 012345678901234567890:abcde_fghij).

**6.Update your script**:

- Paste the **API Key and CSE ID** into your script.


---

# Running the Tool

**Manual installation**: 

- Save the tool script via the link below:

- Link isn't up yet…

-Example: copy the script via the link and paste it into nano. Type **Ctrl + O. Enter, Ctrl + X** to exit.

- Examples of usage:

- **Interactive Mode**:


      python3 dork_recon.py --interactive
  


**List all built-in dork categories**:


    python3 dork_recon.py --list_dorks
    

- Enter any Google query or dork interactively. Type exit to quit.


- **Single dork or category**:


      python3 dork_recon.py --dork wordpress --num_results 10 --output results.json

**NOTE**: Alway customize your search query to save results to json with the name you want. Avoid running your search query without specifying your output to avoid having no data retrievability.


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

- Results are printed with color formatting for readability.

