🔍 Google Search Analysis using Python

> Last Updated: 06 May, 2025
> Analyze what the world is searching for using Python and Google Trends data!

📌 About the Project

Every day, billions of people turn to Google to search for information. In this project, I explored how to use Python to analyze Google search trends — focusing specifically on search queries.

To achieve this, I’ve used a powerful and unofficial Python library called Pytrends, which provides an easy way to interact with Google Trends and extract meaningful insights.
---

⚙️ Technologies Used

* Python 🐍
* Pytrends 📊
* Pandas 🐼
* Matplotlib 📈
* Time ⏱️
---
 1. Clone the Repository
```bash
git clone https://github.com/yourusername/google-search-analysis.git
cd google-search-analysis
```
 2. Install Required Libraries
Make sure Python is installed on your system, then install dependencies:
```bash
pip install pytrends pandas matplotlib
```
## 🔧 How It Works
1.Connect to Google Trends
```python
from pytrends.request import TrendReq

Trending_topics = TrendReq(hl='en-US', tz=360)
```
---
2. Build a Payload
We specify the keyword we're analyzing (e.g., `"Cloud Computing"`), the category, and the time frame.
```python
kw_list = ["Cloud Computing"]
Trending_topics.build_payload(kw_list, cat=0, timeframe='today 12-m')
```
---
3. Interest Over Time
This retrieves how interest in the keyword changed over the last 12 months.
```python
data = Trending_topics.interest_over_time()
data = data.sort_values(by="Cloud Computing", ascending=False).head(10)
print(data)
```
---
4. Historical Hourly Interest
Analyze search interest for a specific date range:
```python
Trending_topics.build_payload(kw_list, cat=0, timeframe='2024-01-01 2024-02-01')
data = Trending_topics.interest_over_time().sort_values(by="Cloud Computing", ascending=False).head(10)
print(data)
```
---
5. Interest by Region
Find which countries or regions searched most for the keyword:
```python
data = Trending_topics.interest_by_region().sort_values(by="Cloud Computing", ascending=False).head(10)
print(data)
```
---
6. **Visualize Interest by Region
```python
import matplotlib.pyplot as plt

data.reset_index().plot(x='geoName', y='Cloud Computing', kind='bar', figsize=(10, 5))
plt.style.use('fivethirtyeight')
plt.show()
```
---
7. Related Queries
Fetch search queries related to "Cloud Computing":
```python
try:
    Trending_topics.build_payload(kw_list=['Cloud Computing'])
    related_queries = Trending_topics.related_queries()
    print(related_queries.values())
except (KeyError, IndexError):
    print("No related queries found for 'Cloud Computing'")
```
---

8. Keyword Suggestions
Explore what similar topics people are searching for:
```python
keywords = Trending_topics.suggestions(keyword='Cloud Computing')
df = pd.DataFrame(keywords)
df.drop(columns='mid', inplace=True)
print(df)
```
---

 📊 Use Cases

* Trend analysis for marketing
* Academic research
* SEO insights
* Product demand analysis

---
---
🤝 Contributing

If you'd like to contribute, feel free to fork the repository and open a pull request with your improvements or suggestions!
---
📄 Licens

This project is licensed under the MIT License.
---
📬 Contact

Have questions or suggestions? Feel free to reach out via [GitHub Issues](https://github.com/jeyaprakash1213/google-search-analysis/issues) or connect with me on [LinkedIn](https://linkedin.com/in/cjeyaprakash)



