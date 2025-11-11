# **RAG - DualLens Analytics**

### **Background Story**
In the rapidly evolving world of finance and technology, investors are constantly seeking ways to make smarter decisions by combining traditional financial analysis with emerging technological insights. While stock market trends provide a numerical perspective on growth, an organization’s initiatives in cutting-edge fields like Artificial Intelligence (AI) reveal its future readiness and innovation potential.
However, analyzing both dimensions - quantitative financial performance and qualitative AI initiatives - requires sifting through multiple, diverse data sources: stock data from platforms like Yahoo Finance, reports in PDFs, and contextual reasoning using Large Language Models (LLMs).
This is where **DualLens Analytics** comes in. By applying a dual-lens approach, the project leverages **Retrieval-Augmented Generation (RAG)** to merge **financial growth data** with **strategic insights from organizational reports**. Stock data provides evidence of stability and momentum, while AI initiative documents reveal forward-looking innovation. Together, they form a richer, more holistic picture of organizational potential.

With DualLens Analytics, investors no longer need to choose between numbers and narratives—they gain a unified, AI-driven perspective that ranks organizations by both financial strength and innovation readiness, enabling smarter, future-focused investment strategies.

---
### **Problem Statement**

Traditional investment analysis often focuses on financial metrics alone (e.g., stock growth, revenue, market cap), missing the qualitative dimension of how prepared a company is for the future.
On the other hand, qualitative documents like strategy PDFs contain valuable insights about innovation and AI initiatives, but they are difficult to structure, query, and integrate with numeric financial data.

This leads to three core challenges:

1. **Fragmented Data Sources:** Financial data (stock prices) and strategic insights (PDFs) exist in silos.

2. **Limited Analytical Scope:** Manual analysis of growth trends and PDF reports is time-consuming and error-prone.

3. **Decisional Blind Spots:** Without integrating both quantitative (growth trends) and qualitative (AI initiatives) signals, investors may miss out on high-potential organizations.

### **Solution Approach**
To address this challenge, we set out to build a **Retrieval-Augmented Generation (RAG)** powered system that blends financial trends with AI-related strategic insights, helping investors rank organizations based on growth trajectory and innovation capacity.

#### **Stock**

1. **Stock:** are a type of security that gives stockholders a share of ownership in a company.

#### **Financial Metrics**

1. **Market Cap:** Total market value of a company’s outstanding shares.
2. **P/E Ratio:** Shows how much investors are willing to pay per dollar of earnings.
3. **Dividend Yield:** Annual dividend income as a percentage of the stock price.
4. **Beta**: Measures a stock’s volatility relative to the overall market.
5. **Total Revenue:** The total income a company generates from its business operations.

----

> <font color="red" size=5>**Stock Task**</font>
1. Loop through each company to retrieve stock data of the last three years using the YFinance library.
2. Plot the closing prices for each company.


> <font color="red" size=5>**Metric Task**</font>

1. Loop through all the companies to fetch data based on the specified financial metrics.
2. Create a DataFrame (DF) from the collected data.
3. Visualize and compare each financial metric across all companies.
4. For example, visualize and compare the market capitalization for each company.

# **Finanical Visual Analysis**

In the context of creating financial visuals like dashboards or charts, functions such as `get_stock_data`, `get_financial_metrics_yf`, `build_metrics_dataframe`, and `plot_stock_trends` and `plot_financial_comparison_with_table` are essential tools. These functions are used for pulling financial data and creating visualizations. They encapsulate specific data processing tasks, organizing complex calculations into manageable, reusable components for clearer code. This ensures consistency, reduces errors, and allows for efficient updates and adjustments to visual displays. Furthermore, these functions are designed to be called within the Retrieval-Augmented Generation (RAG) prompt, allowing the system to seamlessly integrate the financial data into the LLM-based analysis and recommendations.


**A. Summary / Your Observations about this Project**
1. In this project, I observed that qualitative LLM reasoning allows expressive, human-like narratives, but it must be tightly controlled to avoid hallucinations. Through experimentation, I found that using a temperature around 0.3 and top-p ≈ 0.95 produced a natural tone without becoming overly deterministic or robotic.
2. When combining qualitative reasoning with quantitative financial metrics, I had to be especially careful to enforce evidence-based outputs only. The model easily hallucinates if constraints are not explicit, so grounding through retrieval and deterministic scoring logic became essential. I also noticed that domain-focused prompting sometimes led the model to “echo” parts of the context, which reinforced the need for strict anti-copy rules.
3. To ensure reliability of dual-lens responses (quantitative + qualitative), I introduced evaluation logic for groundedness and relevance. This helped validate that the model’s conclusions were factual, sourced, and not inferred beyond the provided context.


*Tip: Check `ticker.info` for the available financial metrics*
