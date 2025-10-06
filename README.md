# Serverless Starter: Azure Functions for Data Ninjas

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/) [![Azure Functions](https://img.shields.io/badge/Azure%20Functions-V2-orange)](https://docs.microsoft.com/en-us/azure/azure-functions/) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**A zero-ops toolkit for data hustlers.** Fork this MVP to build serverless pipelines that watch CSVs, crunch data, and serve APIs—without server drama. Inspired by real-side-gig needs, powered by Azure Functions Python V2.

## 🚀 Project Purpose
I'm Damian , a data engineer moonlighting as an indie dev, and I built this repo to prototype lightweight data apps that scale like butter. Imagine: Drop a CSV into Azure Blob Storage, and boom—serverless magic processes it on upload, logs metadata, or exposes insights via HTTP APIs. No VMs, no Kubernetes nightmares—just Python code that runs on events, all on Azure's free tier.

This skeleton is my MVP:  
- **HTTP Triggers**: Quick APIs for greetings or queries (e.g., personalize responses with params).  
- **Blob Triggers**: Watch for file uploads and handle 'em—log paths or parse CSVs into actionable rows.  

Why? In the gig economy, I needed a fast way to test ETL flows or chatty endpoints without AWS/GCP lock-in. It's local-dev ready (`func start` and you're golden), deployable in minutes, and expandable for hustles like auto-reports or data dashboards. If you're prepping a portfolio, interview, or side project, this turns "serverless sounds cool" into "I shipped a pipeline."

## 🤝 Why Contributors? (Join the Virtual Startup Team)
Solo coding is for amateurs—I'm rallying sharp data ninjas like you to iterate at warp speed. Your PRs aren't tweaks; they're the fuel that evolves this from toy to tool:  
- Robust error handling keeps pipelines humming on junk data.  
- Input validation secures our APIs against bad actors.  
- Timers add automation smarts for scheduled crunches.  

In a real startup, these "small" wins handle 1K+ events/day. Contribute now, and you're shipping features that could power my next gig (or launch yours). It's portfolio rocket fuel: Claim an issue, test locally, PR it, and link that merge in your resume. Let's fork this into a full data beast—who's in?

## ✨ Features (What's in the Box)
- **FirstHTTPFunction** (`/api/myroute`): Basic "Hello World" endpoint—proves the serverless spark.  
- **SecondHTTPFunction** (`/api/newroute?name=You`): Param-driven greeter—your API playground.  
- **MyFirstBlobFunction**: Triggers on `newcontainer/People.csv` uploads; logs the blob deets.  
- **ReadFileBlobFunction**: Parses `newcontainer/People2.csv` rows—CSV-to-insights starter.  
- V2 Model: Decorators, blueprints (via `additional_functions`), and logging baked in.  
- Free-Tier Friendly: Runs local or Azure without breaking the bank.

## 🛠 Quick Start (Local Dev in <10 Mins)
No Azure account needed for HTTP tests—blobs use a local emulator (Azurite). Assumes Windows/macOS/Linux with Git.

### Prerequisites
- [Python 3.8+](https://www.python.org/downloads/)  
- [Azure Functions Core Tools v4](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#install-the-azure-functions-core-tools) (`npm install -g azure-functions-core-tools@4`)  
- [Node.js](https://nodejs.org/) (for Core Tools/Azurite)  
- [Git](https://git-scm.com/downloads)

### Setup
1. Clone the repo:  
   ```
   git clone https://github.com/[your-org]/[your-repo].git
   cd [your-repo]
   ```

2. Virtual Env & Deps:  
   ```
   python -m venv .venv
   # Windows: .venv\Scripts\activate
   # macOS/Linux: source .venv/bin/activate
   pip install -r requirements.txt  # Or: pip install azure-functions azure-storage-blob
   ```

3. Config Files (Create if Missing):  
   - `local.settings.json`:  
     ```json
     {
       "IsEncrypted": false,
       "Values": {
         "FUNCTIONS_WORKER_RUNTIME": "python",
         "AzureWebJobsStorage": "UseDevelopmentStorage=true"  # For Azurite
       }
     }
     ```
   - `host.json` (default V2):  
     ```json
     {
       "version": "2.0",
       "extensions": { "http": { "routePrefix": "api" } }
     }
     ```

4. Fire It Up:  
   ```
   func start
   ```
   - HTTP Test: Open http://localhost:7071/api/myroute → "Wow this first HTTP Function works!!!!"  
   - Param Test: http://localhost:7071/api/newroute?name=Ninja → "Hello, Ninja, so glad this Function worked!!"

### Blob Testing (Optional, ~5 Extra Mins)
1. Install Azurite: `npm install -g azurite` then `azurite --silent` (runs on http://127.0.0.1:10000).  
2. Create Dummys:  
   - `People.csv`: `Name,Age\nAlice,25\nBob,30`  
   - `People2.csv`: `ID,Name\n1,Charlie\n2,Dave`  
3. Upload via [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/) (connect to Azurite endpoint) to `newcontainer`.  
4. Watch logs in `func start` for trigger magic (e.g., CSV rows printed).

Stop: Ctrl+C. Edits to `function_app.py` auto-reload!

## 🌐 Deployment to Azure (Go Live)
1. [Free Azure Account](https://azure.microsoft.com/free/) → Create Function App (Python 3.9 runtime) & Storage Account.  
2. Grab Storage Connection String → Add to `local.settings.json` as `"AzureWebJobsStorage": "your-conn-str"`.  
3. Publish: `func azure functionapp publish your-app-name --no-build`.  
4. Test: Hit your Azure endpoint (e.g., https://your-app.azurewebsites.net/api/myroute).  

Pro Tip: Monitor in Azure Portal—free tier covers ~1M executions/month.

## 🤖 Contributing
This is our startup—your ideas drive it!  
1. Fork & clone.  
2. Tweak (test with `func start`).  
3. PR: Reference an issue, e.g., "Fixes #1: Added validation."  

**Open Issues to Claim:**  
- [Add Error Handling for CSV Parsing](#) – Bulletproof the pipeline.  
- [Validate API Inputs](#) – Secure the gates.  
- [Log Blob Metadata](#) – Audit like pros.  
- [Timer Trigger for Auto-Logs](#) – Schedule the wins.  

New ideas? Open a Discussion. Label: `good-first-issue` for newbies. Code of Conduct: Be rad, credit sources.

## 🗺 Roadmap (Our Vision)
- **Next Sprint:** Integrate Cosmos DB for persistent storage.  
- **Moonshot:** Full ETL dashboard—trigger on blobs, query via HTTP, visualize in Power BI.  
- **Your Call:** Suggest in issues—what data ninja trick next?

## 📄 License
MIT – Fork freely, build boldly. Copyright (c) 2025 daminan.
## 🙌 Shoutouts
Built with ❤️ for data hustlers. Star if it sparks your serverless fire. Questions? [@damianBunds](https://twitter.com/) or Discussions tab. Let's ship! 🚀

*Last Updated: July 28, 2026*
