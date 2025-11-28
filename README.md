README: Product Recommendation Agent

Overview
The Product Recommendation Agent is a hybrid recommender system designed to help users quickly find suitable products from a small, in-memory catalog. It uses a straightforward rule-based filtering system to select the most relevant products based on quantifiable criteria (Category, Budget, Rating). Crucially, it then leverages the power of a Large Language Model (LLM) (GPT-4o-mini) to provide a natural language explanation and justification for the recommendations, making the results more user-friendly and persuasive.

Features & Limitations

✨ Features
- Hybrid Recommendation: Combines deterministic filtering (Rule-Based) with generative reasoning (LLM).
- Multi-Criteria Filtering: Allows users to filter products based on Category, Maximum Budget, and Minimum Rating.
- LLM Explanation: Uses the OpenAI API to generate a personalized, friendly explanation of why the recommended products match the user’s needs.
- Simple Web Interface: Hosted via Gradio for easy, shareable interaction.
- Fallback Logic: If strict filters yield no results, the agent defaults to recommending the top 3 highest-rated products in the entire catalog.

⚠ Limitations
- Small, Static Dataset: The product catalog is hardcoded into the source code (a Pandas DataFrame of 10 products) and cannot handle real-world scale or dynamic updates.
- No Personalization/Historical Data: Recommendations are based solely on current input parameters and do not consider past user behavior.
- Limited Filtering Depth: Filtering is basic (exact category match, price <= budget, rating >= min rating).
- OpenAI API Dependency: The explanation feature requires a valid OpenAI API key and relies on the API's availability and cost structure.

🛠 Tech Stack & APIs Used

Component              Role                                Version/API  
Python                Core language                        3.x  
Gradio                Frontend web interface               Latest (gr.Blocks)  
Pandas                Data management & filtering          Latest  
OpenAI                LLM integration                      openai package  
GPT-4o-mini           Model used for explanations          gpt-4o-mini  

🚀 Setup & Run Instructions

1. Save the Code  
Save the provided Jupyter notebook content as a Python file (e.g., recommender_agent.py).

2. Install Dependencies  
Run the following:

    pip install gradio openai pandas numpy scikit-learn

3. Set Your API Key  
Set your OpenAI key before running the script:

    export OPENAI_API_KEY='your-api-key-here'

(If you're using a notebook, use the provided cell to set it interactively.)

4. Run the Script  
Execute:

    python recommender_agent.py

This will launch the Gradio interface and display a local URL such as:

    http://127.0.0.1:7860

📈 Potential Improvements
- Vector Database Integration: Convert product descriptions into embeddings and use a vector store (Chroma, Pinecone, FAISS) for advanced semantic retrieval using user_need input.
- Expand Dataset: Load a full product inventory from an external CSV or database.
- Contextual Recommendation: Add session memory or simple user profiles to enable personalization.
- Tool-Calling (Advanced LLM): Let GPT-4o-mini automatically interpret natural-language constraints (e.g., “under fifty thousand”) and call filtering functions programmatically.
