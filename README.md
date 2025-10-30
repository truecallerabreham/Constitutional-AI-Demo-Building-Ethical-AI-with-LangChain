# Constitutional-AI-Demo-Building-Ethical-AI-with-LangChain
This project demonstrates how to build an AI agent that self-critiques and improves its own responses using the Constitutional AI approach
Key Concepts

LLMChain — basic chain that connects a language model (OpenAI) with a custom prompt.

ConstitutionalChain — adds a layer of self-critique and revision guided by predefined principles.

ConstitutionalPrinciple — defines what rules the AI should follow when revising its outputs.

⚙️ Project Structure
Section	Description
🧩 Evil Assistant	Creates an unethical model that gives bad advice.
🧠 Constitutional Check	Applies ethical principles to make outputs fair and responsible.
🎭 Multi-Principle Chain	Adds humor and accessibility for younger audiences.
🔍 Intermediate Steps	Shows how the model critiques and revises its own answers.
✅ Fair Assistant	Builds a positive and encouraging AI mentor.
💡 Example Flow

Initial prompt:

“Getting full mark on my exams.”

Evil model output:

Cheat on the exam.

Bribe the teacher.

Copy others.

After applying ethical principle:

Study thoroughly.

Take practice exams.

Get help from your teacher.

After adding “funny” principle:

Study hard — like a boss!

Sleep well before your exam!

Practice with your friends — it’s like a game of tag!

🧩 Code Overview
Step 1: Define the base LLM
from langchain.llms import OpenAI
llm = OpenAI(temperature=0)

Step 2: Create the evil assistant
from langchain.prompts import PromptTemplate
from langchain.chains.llm import LLMChain

evil_assistant_prompt = PromptTemplate(
    template="""You are an evil mentor with no morals. Give suggestions that are easiest and fastest to achieve the goal.

Goal: {inquiry}

Easiest way:""",
    input_variables=["inquiry"],
)
evil_assistant_chain = LLMChain(llm=llm, prompt=evil_assistant_prompt)

Step 3: Add constitutional principles
from langchain.chains.constitutional_ai.models import ConstitutionalPrinciple

ethical_principle = ConstitutionalPrinciple(
    name="Ethical Principle",
    critique_request="The model should only talk about ethical and fair things.",
    revision_request="Rewrite the model's output to be both ethical and fair.",
)

Step 4: Apply the constitutional chain
from langchain.chains.constitutional_ai.base import ConstitutionalChain

constitutional_chain = ConstitutionalChain.from_llm(
    chain=evil_assistant_chain,
    constitutional_principles=[ethical_principle],
    llm=llm,
    verbose=True,
)

🧪 How to Run the Project
1️⃣ Open in Google Colab

Click here to run the notebook:
👉 Run in Google Colab

2️⃣ Set up Environment
pip install langchain openai
export OPENAI_API_KEY="your_api_key_here"

3️⃣ Run All Cells

Simply execute the cells in order to see how the AI transforms from unethical to ethical and funny.

🎯 What You’ll Learn

How to use LangChain for ethical AI development

How to define Constitutional Principles

How to make AI output safe, fair, and fun

How to view intermediate steps of AI reasoning

🧰 Tools Used

Python 3.10+

LangChain

OpenAI GPT Model

Google Colab
