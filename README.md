# 🤖 WebBot v2.3

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python" />
  <img src="https://img.shields.io/badge/Library-Requests-green?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Library-BeautifulSoup4-orange?style=for-the-badge" />
</p>

<p align="center">
  <b>A colorful CLI Web Search Assistant built with Python</b><br>
  Fetches top website results from <a href="https://duckduckgo.com">DuckDuckGo</a>
</p>

---

## ✨ Features
- 🎨 ASCII art styled header  
- 🌈 Colored terminal output  
- 🔍 Fetches top **5 websites** for any query  
- 💬 Chatbot-like clean interaction  
- 👋 Exit anytime by typing **`bye`**  

---

## 📸 Preview


---

## 🧑‍💻 Full Code
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

# Clear screen (works in Termux/PyDroid)
os.system("clear")

print(CYAN + r"""
 __        __   _     ____        _   
 \ \      / /__| |__ | __ )  ___ | |_ 
  \ \ /\ / / _ \ '_ \|  _ \ / _ \| __|
   \ V  V /  __/ |_) | |_) | (_) | |__
    \_/\_/ \___|_.__/|____/ \___/|____|
                                      
""" + RESET)

print(GREEN + "          WebBot v2.3" + RESET)
print(f"{YELLOW}Creator : 𝓐𝓷𝓲𝓼𝓱 𝓚𝓾𝓼𝓱𝔀𝓪𝓱𝓪")
print("Email   : Anish_Kushwaha@proton.me")
print("Website : Anish-kushwaha.b12sites.com")
print(RESET)
print("*" * 60)
print(CYAN + "🤖 WebBot : Ask me anything! Type 'bye' to quit." + RESET)

while True:
    query = input(YELLOW + "\nYou : " + RESET)
    if query.lower() == "bye":
        print(RED + "🤖 WebBot : Bye 👋" + RESET)
        break

    print(GREEN + "\n🤖 WebBot : Here are the top Websites :-\n" + RESET)

    url = "https://duckduckgo.com/html/?q=" + query.replace(" ", "+")
    headers = {"User-Agent": "Mozilla/5.0"}
    r = requests.get(url, headers=headers)
    soup = BeautifulSoup(r.text, "html.parser")

    results = soup.find_all("a", {"class": "result__a"}, limit=5)
    for i, link in enumerate(results, start=1):
        print(f"{CYAN}{i}. {link.get_text()}{RESET} → {YELLOW}{link['href']}{RESET}")



requirements.txt

#Requirements
requests
beautifulsoup4
pip install -r


#Run The Bot
git clone https://github.com/your-username/WebBot.git
cd WebBot
python webbot_v2.3.py




#---

🔥 This version has **everything in one place** (HTML badges, preview, code, requirements, run instructions, author).  

Do you also want me to add a **GitHub Pages HTML demo** (like a styled `index.html` showing project info) so repo looks cooler?



 
