# 🚩 Sandeshahara-Real-Time-Agentic-Travel-Intelligence
Sandeshahara—Sanskrit for "The Messenger"—is a next-generation AI orchestration system. Inspired by the speed and resourcefulness of ancient scouts, this project implements a Tiered Agent Architecture to bridge the gap between high-velocity live data and high-accuracy human decision-making.

## 🌟 The Concept
In the Ramayana, Hanuman Ji acted as the ultimate agent: he was fast enough to cross oceans (Speed), wise enough to verify information (Accuracy), and resourceful enough to adapt to obstacles (Agentic Reasoning). Sandeshahara replicates this by using a "Scout-and-General" model to process live travel streams.

## 🏗️ Architecture: Tiered Orchestration
Standard AI models are either fast but prone to hallucinations or accurate but slow and expensive. Sandeshahara solves this via a three-tier cascade:

## The Scout (Tier 1 - Filtering):

Model: Gemini 3.1 Flash-Lite (Free Tier).

Role: Acts as the high-speed "eyes." It monitors a WSS (WebSocket Secure) stream of raw travel data 24/7. It discards 90% of irrelevant noise in <200ms.

## The Researcher (Tier 2 - Contextualizing):

Tool: GraphRAG (Neo4j).

Role: Maps the "Messenger's Path." It connects the filtered data to a Knowledge Graph to see how a price drop or delay affects the user's specific travel history and preferences.

## The General (Tier 3 - Reasoning):

Model: Claude 4.7 Sonnet.

Role: The final decision-maker. It performs deep reasoning and a "hallucination check" on the Scout's findings before delivering a verified, polished response to the user.

## 🛠️ Tech Stack
Language: Python 3.12 (Asynchronous processing for WebSockets).

Orchestration: LangGraph (Managing stateful handoffs between agents).

Models:

Gemini 3.1 Flash-Lite (Fast/Low Latency).

Claude 4.7 Sonnet (High Reasoning/Zero Hallucination).

Data Ingestion: WSS (WebSocket Secure) for real-time, bidirectional communication.

Knowledge Base: Neo4j (GraphRAG) for relationship mapping.

## 💡 Engineering "Senior" Reasoning
Why WebSockets? Standard APIs are "pull-based" (slow). WebSockets are "push-based," ensuring the agent reacts to a price drop the second it happens.

Why Tiered Models? Running every WebSocket packet through Claude 4.7 is financially impossible. By using Gemini Flash-Lite as a "Scout," we achieve 60% cost reduction while maintaining the reasoning quality of a top-tier model.

Why GraphRAG? To solve the "Multi-hop" problem. If a strike is announced at an airline hub, Sandeshahara knows it affects your flight even if your city isn't mentioned in the news title.

## 🚀 Getting Started
Clone: git clone [https://github.com/shriyaagrawal08/Sandeshahara-Real-Time-Agentic-Travel-Intelligence.git]

Environment: Set your GOOGLE_API_KEY (Free via AI Studio) and ANTHROPIC_API_KEY.

Initialize: python main.py
