<h1 align="center">🤖 WebBot v2.3</h1>

<p align="center">
  <b>A colorful CLI Search Assistant built with Python</b><br>
  Fetches top website results from <a href="https://duckduckgo.com/">DuckDuckGo</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?logo=python" />
  <img src="https://img.shields.io/badge/Library-Requests-yellow?logo=python" />
  <img src="https://img.shields.io/badge/Library-BeautifulSoup4-green?logo=python" />
</p>

---

<h2>✨ Features</h2>

<ul>
  <li>🎨 ASCII art styled header</li>
  <li>🌈 Colored terminal output</li>
  <li>🔎 Fetches top <b>5 websites</b> for any query</li>
  <li>💬 Chatbot-like clean interaction</li>
  <li>🚪 Exit anytime by typing <code>bye</code></li>
</ul>

---

<h2>Requirements</h2>
<ul>
  <li>requests</li>
  <li>beautifulsoup4</li>
  <li>pip install -r </li>
</ul>

<h2> Run The Bot </h2>
<ul>
<li>git clone https://github.com/yourusername/WebBot-v2.3.git </li>
<li>cd WebBot-v2.3</li>
<li>python webbot_v2.3.py</li>
</ul>

<p align="center">
  <img src="https://github.com/yourusername/WebBot-v2.3/assets/preview.png" width="600px">
</p>

---

<h2>📜 Full Code</h2>

```python
import requests
from bs4 import BeautifulSoup
import os

# Colors
RED = "\033[91m"
GREEN = "\033[92m"
CYAN = "\033[96m"
YELLOW = "\033[93m"
RESET = "\033[0m"

# Clear screen
os.system("clear")

print(CYAN + r"""
 __        __   _     ____        _   
 \ \      / /__| |__ | __ )  ___ | |_ 
  \ \ /\ / / _ \ '_ \|  _ \ / _ \| __|
   \ V  V /  __/ |_) | |_) | (_) | |_ 
    \_/\_/ \___|_.__/|____/ \___/ \__|
""" + RESET)

print(f"{YELLOW}Creator : 𝓐𝓷𝓲𝓼𝓱 𝓚𝓾𝓼𝓱𝔀𝓪𝓱𝓪")
print(f"{YELLOW}Email   : Anish_Kushwaha@proton.me")
print(f"{YELLOW}Website : Anish-kushwaha.b12sites.com\n")

print(f"{GREEN}🤖 WebBot : Ask me anything! Type 'bye' to quit.{RESET}\n")

while True:
    query = input(f"{CYAN}You : {RESET}")
    if query.lower() == "bye":
        print(f"{RED}🤖 WebBot : Bye 👋{RESET}")
        break

    print(f"\n{GREEN}🤖 WebBot : Here are the top Websites :-{RESET}\n")

    url = f"https://duckduckgo.com/html/?q={query}"
    headers = {"User-Agent": "Mozilla/5.0"}
    r = requests.get(url, headers=headers)
    soup = BeautifulSoup(r.text, "html.parser")

    results = soup.find_all("a", {"class": "result__a"}, limit=5)
    for i, link in enumerate(results, start=1):
        print(f"{CYAN}{i}. {link.text} → {link['href']}{RESET}")
    print("")
