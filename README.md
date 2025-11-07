# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

# Date: 07/10/2025
# Register no: 212222073001

# Aim:
Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools

# AI Tools Required:
### ChatGPT (GPT-5 or GPT-4) 
– for generating and explaining Python code.
### Google Gemini 
– for comparing code logic and alternative API uses.
### GitHub Copilot
– for in-editor code suggestions and real-time debugging help.
### Replit / Jupyter Notebook 
– for executing and testing AI-generated code.

# Explanation:
Experiment the persona pattern as a programmer for any specific applications related with your interesting area. 
Generate the outoput using more than one AI tool and based on the code generation analyse and discussing that. 

# Objective:
To design effective prompts that guide AI tools (like ChatGPT) to generate Python code, compare outputs from multiple APIs, and suggest meaningful insights — improving students’ ability to communicate coding needs to AI.

### Stage 1: Generate Python Code for Interacting with Multiple APIs
### Prompt:
Here’s a Python example using two different APIs —
🔹 ExchangeRate API → gets live currency exchange rates
🔹 News API → gets the latest finance or economy news

### Output:
import requests

EXCHANGE_KEY = "your_exchangerate_api_key"
NEWS_KEY = "your_newsapi_key"

def get_rate():
    r = requests.get(f"https://v6.exchangerate-api.com/v6/{EXCHANGE_KEY}/latest/USD").json()
    return r["conversion_rates"]["INR"]

def get_news():
    r = requests.get(f"https://newsapi.org/v2/top-headlines?category=business&language=en&apiKey={NEWS_KEY}").json()
    return [n["title"] for n in r["articles"][:5]]

rate = get_rate()
news = get_news()

print(f"\n💱 USD → INR: ₹{rate}")
print("\n📰 Top Finance Headlines:")
for i, n in enumerate(news, 1): print(f"{i}. {n}")

if rate > 85:
    print("\n📉 Insight: Rupee is weak — possible market volatility.")
elif rate < 80:
    print("\n📈 Insight: Rupee strong — positive market trend.")
else:
    print("\n⚖️ Insight: Exchange rate stable.")

### AI Explanation:
This Python script connects to two APIs — one for live USD→INR exchange rates and another for financial news — then displays both results.
It analyzes the exchange rate to give a brief insight about the market trend (strong, weak, or stable rupee).
Then, it compares their outputs to give a simple insight about global economic conditions.

### Stage 2: Compare Outputs from Different APIs
### Prompt:
Modify the previous code so that it compares the(ExchangeRate + NewsAPI) from both APIs and highlights the differences clearly.

### Output:
import requests

EXCHANGE_KEY = "your_exchangerate_api_key"
NEWS_KEY = "your_newsapi_key"

def get_exchange_rate():
    url = f"https://v6.exchangerate-api.com/v6/{EXCHANGE_KEY}/latest/USD"
    res = requests.get(url).json()
    return res["conversion_rates"]["INR"]

def get_finance_news():
    url = f"https://newsapi.org/v2/top-headlines?category=business&language=en&apiKey={NEWS_KEY}"
    res = requests.get(url).json()
    return [n["title"] for n in res["articles"][:5]]

def compare_data(rate, news):
    positive_words = ["growth", "rise", "profit", "gain", "boost"]
    negative_words = ["fall", "loss", "decline", "drop", "crash"]

    pos = sum(any(p in n.lower() for p in positive_words) for n in news)
    neg = sum(any(nw in n.lower() for nw in negative_words) for n in news)

    print("\n💱 Current USD → INR Rate:", rate)
    print("\n📰 Top Finance Headlines:")
    for i, h in enumerate(news, 1):
        print(f"{i}. {h}")

    print("\n📊 Comparison & Highlights:")
    if rate > 85 and neg > pos:
        print("⚠️ Both APIs indicate market weakness — rupee down and negative news headlines.")
    elif rate < 80 and pos > neg:
        print("✅ Both APIs show positive trends — stronger rupee and optimistic news.")
    elif rate > 85 and pos > neg:
        print("⚖️ Mismatch: Rupee is weak, but news sentiment seems positive.")
    elif rate < 80 and neg > pos:
        print("⚖️ Mismatch: Rupee is strong, but news sentiment appears negative.")
    else:
        print("ℹ️ Mixed indicators — data from both APIs are neutral or inconsistent.")

if __name__ == "__main__":
    print("Fetching and comparing data from multiple APIs...\n")
    rate = get_exchange_rate()
    news = get_finance_news()
    compare_data(rate, news)

### AI Explanation:
This comparison highlights whether the economic data (API 1) and news trends (API 2) agree or contradict each other, giving a clearer picture of current market conditions.

### Stage 3: Suggest Insights or Next Steps
### Prompt:
Based on the compared data, suggest how the program could automatically choose the more reliable API result and display.

### Output:
import requests

EXCHANGE_KEY = "your_exchangerate_api_key"
NEWS_KEY = "your_newsapi_key"

def get_rate(): 
    return requests.get(f"https://v6.exchangerate-api.com/v6/{EXCHANGE_KEY}/latest/USD").json()["conversion_rates"]["INR"]

def get_news():
    r = requests.get(f"https://newsapi.org/v2/top-headlines?category=business&language=en&apiKey={NEWS_KEY}").json()
    return [n["title"] for n in r["articles"][:5]]

rate, news = get_rate(), get_news()
pos = sum(any(w in n.lower() for w in ["growth","rise","profit","gain"]) for n in news)
neg = sum(any(w in n.lower() for w in ["fall","loss","decline","drop"]) for n in news)

print(f"\n💱 USD→INR: ₹{rate}\n")
for i, n in enumerate(news, 1): print(f"{i}. {n}")
print("\n📊 Comparison:")

if rate > 85 and neg > pos:
    msg = "⚠️ Both APIs show weakness — ExchangeRate more reliable."
elif rate < 80 and pos > neg:
    msg = "✅ Both show strength — NewsAPI gives more context."
elif rate > 85 and pos > neg:
    msg = "⚖️ Mismatch: Weak rupee but positive news → Trust ExchangeRate."
elif rate < 80 and neg > pos:
    msg = "⚖️ Mismatch: Strong rupee but negative news → Trust NewsAPI."
else:
    msg = "ℹ️ Mixed signals — use both for balanced view."

print(msg)

### AI Explanation:
- Fetches data from ExchangeRate API and NewsAPI
- Analyzes sentiment in headlines
- Compares both results
- Automatically picks the more reliable API and shows a short summary

# Reflection Note:
Through this exercise, I learned how to design prompts that guide AI tools to generate purposeful and structured Python code instead of directly coding myself. By working with multiple APIs, I understood how to compare data sources, identify inconsistencies, and make logical decisions using AI-generated insights. This activity also improved my ability to frame precise prompts that produce reliable and efficient results from AI models.


# Conclusion:
This task demonstrated how AI can assist in real-world project coding by generating, comparing, and analyzing outputs from multiple APIs. It also showed that well-crafted prompts can lead to more accurate, contextual, and actionable results. Ultimately, effective prompt design allows developers to combine automation with analytical reasoning, making AI a valuable coding partner.

# Result: 
The corresponding Prompt is executed successfully.
