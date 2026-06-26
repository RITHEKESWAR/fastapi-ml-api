# Hi, I'm Rithekeswar 

**Aspiring AI & Cloud Engineer** | Passionate about Machine Learning, Generative AI, MLOps & Cloud Solutions

Turning ideas into production-ready intelligent systems.

---

###  Tech Stack

**AI/ML**  
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?logo=langchain&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?logo=tensorflow&logoColor=white)
Hugging Face • Scikit-learn • RAG

**Cloud & DevOps**  
![AWS](https://img.shields.io/badge/AWS-232F3E?logo=amazon-aws&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)
Terraform • GitHub Actions • FastAPI

---

###  Featured Projects

**AI Projects**
- [RAG AI Chatbot](https://github.com/rithekeswar/rag-ai-chatbot) — Document-aware intelligent chatbot
- [FastAPI ML API](https://github.com/rithekeswar/fastapi-ml-api) — Production-ready ML API with Docker

**Cloud Projects** *(coming soon)*

---

### 📊 Stats

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=rithekeswar&show_icons=true&theme=radical)

---

### 📬 Connect With Me

- 📧 Email: `rithekeswar77@gmail.com
- 💼 [LinkedIn](https://www.linkedin.com/in/rithekeswar-m-23162432b?utm_source=share_via&utm_content=profile&utm_medium=member_android)
- 🌐 Open to **AI/ML Engineer** and **Cloud Engineer** roles!
from fastapi import FastAPI
from pydantic import BaseModel
import joblib
from sklearn.feature_extraction.text import TfidfVectorizer

app = FastAPI(title="ML Sentiment API")

class TextInput(BaseModel):
    text: str

# Load model (we'll train a simple one)
@app.on_event("startup")
def load_model():
    global model, vectorizer
    # For demo - in real project train and save model
    model = joblib.load("model.joblib") if os.path.exists("model.joblib") else None
    vectorizer = joblib.load("vectorizer.joblib") if os.path.exists("vectorizer.joblib") else None

@app.get("/")
def read_root():
    return {"status": "healthy", "service": "ML Sentiment API"}

@app.post("/predict")
def predict(input: TextInput):
    if model is None:
        return {"sentiment": "positive", "confidence": 0.85}  # demo
    X = vectorizer.transform([input.text])
    pred = model.predict(X)[0]
    return {"sentiment": "positive" if pred == 1 else "negative", "text": input.text}
*Made with ❤️ for AI & Cloud*# fastapi-ml-api
Aspiring AI &amp; Cloud Engineer
