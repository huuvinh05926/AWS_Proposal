---
title: "Event 2"
date: "2025-11-15"
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# 15/11/2025

# Generative AI with Amazon Bedrock

## Speaker Information

- **Lam Tuan Kiet** - Sr. DevOps Engineer, FPT Software
- **Danh Hoang Hieu Nghi** - AI Engineer, Renova Cloud
- **Dinh Le Hoang Anh** - Cloud Engineer Trainee, First Cloud Journey

## Context and Transformation Motivation

Currently, many enterprises are facing outdated technology platforms. Investing in building a new platform from scratch often requires very high costs in terms of both finances and time. The optimal solution is to leverage cloud technology and serverless services to minimize operational costs and accelerate deployment speed.

## Foundation Models - The Foundation of Gen AI

![Why foundation models?](/images/4-EventParticipated/3C0E9B79-FBAE-426F-934F-F054076921AE.jpeg)

### What is Generative AI?

Generative AI (Gen AI) is a technology that allows the creation of new content such as text, images, and audio based on input prompts. The special feature of Gen AI is its ability to create content that is creative and contextually appropriate.

### Foundation Models

Foundation Models are AI models trained on massive amounts of data and have the ability to:

- Handle diverse different tasks
- Generalize knowledge from training data
- Can be fine-tuned for specific applications
- Save time and development costs

## Amazon Bedrock

Amazon Bedrock is a fully managed service that provides access to many leading Foundation Models through a single API.

![Supported foundation models in Amazon Bedrock](/images/4-EventParticipated/0D0458A0-B9F7-46CC-9405-C289F209CA7F.jpeg)

### Supported Foundation Models

Amazon Bedrock supports many models from leading providers:

- **Claude** (Anthropic): Strong in reasoning and analysis
- **Titan** (Amazon): Models optimized for AWS use cases
- **Jurassic** (AI21 Labs): Good for language processing
- **Llama** (Meta): Open-source, flexible customization
- **Stable Diffusion**: Specialized in image generation

## Prompt Engineering

![What is a prompt?](/images/4-EventParticipated/0184C2FC-A3FE-4383-A620-1B308810C1F0.jpeg)

### What is a Prompt?

A prompt is a command or text that we provide to the AI model to receive the desired result. The quality of the prompt directly affects the quality of the output.

![What is Prompt Engineering? - An Example](/images/4-EventParticipated/4B30DA12-5B1E-4330-B990-A6053E5424CA.jpeg)

### Prompt Engineering

Prompt Engineering is the art and science of designing effective prompts to optimize results from AI models. This is an important skill when working with Generative AI.

## Prompting Techniques

### 1. Zero-Shot Prompting

![Prompting Techniques - Zero-Shot Prompting](/images/4-EventParticipated/4A2925C5-03A2-49A8-BD4B-6537AD872D9E.jpeg)

**Zero-Shot Prompting** is a technique of asking questions or making requests directly without providing specific examples. The model will use its trained knowledge to answer.

**Advantages:**

- Simple, fast
- Suitable for basic questions

**Disadvantages:**

- Results may not be accurate for complex tasks

### 2. Few-Shot Prompting

![Prompting Techniques - Few-shot prompting](/images/4-EventParticipated/571A852C-ADD7-4037-9F07-AA48ED36816B.jpeg)

**Few-Shot Prompting** provides a few illustrative examples before making the main request. This helps the model better understand the desired format and context.

**Advantages:**

- Significantly improves accuracy
- Model understands requirements better
- Suitable for specific tasks

**Disadvantages:**

- Requires time to prepare examples
- Consumes tokens (higher cost)

### 3. Chain of Thought (CoT)

![Prompting Techniques - Chain of Thought (CoT)](/images/4-EventParticipated/D26171ED-FE57-457A-9288-A3267EEAD3F3.jpeg)

![Prompting Techniques - Chain of Thought (CoT)](/images/4-EventParticipated/16685DB4-D8E4-4074-8996-AA524CE40307.jpeg)

**Chain of Thought (CoT)** is a technique that requires the model to explain each step of thinking before giving the final answer.

**Advantages:**

- Increases accuracy for complex problems
- Helps debug and understand the model's logic
- Suitable for problems requiring reasoning

**How to use:**

- Add the phrase "Let's think step by step" to the prompt
- Request the model to explain each step
- Check the logic before using the result

## Retrieval Augmented Generation (RAG)

![RAG in Action](/images/4-EventParticipated/54EF9821-5DB9-41DA-A5B3-0E585B9EFAA2.jpeg)

### What is RAG?

**Retrieval Augmented Generation (RAG)** is an architecture that combines:

1. **Retrieval**: Retrieve information from internal data sources
2. **Generation**: Use AI model to generate answers

### RAG Workflow

1. **User Query**: User poses a question
2. **Document Retrieval**: System searches for relevant information in knowledge base
3. **Context Building**: Combines retrieved information with original prompt
4. **Generation**: AI model generates answer based on complete context
5. **Response**: Returns result to user

### Benefits of RAG

- **Accuracy**: Increases accuracy with internal data
- **Up-to-date**: Always uses the latest information
- **Cost-effective**: No need to fine-tune model
- **Security**: Control over data sources

### Common Use Cases

- Customer support chatbot
- Internal enterprise Q&A system
- Document search and summarization
- Knowledge management systems

## Other AWS AI Services

### Amazon Rekognition

![Amazon Rekognition](/images/4-EventParticipated/9C0D5865-CD50-4C39-8C20-774DD59461EC.jpeg)

**Amazon Rekognition** is an image and video analysis service using machine learning.

**Key Features:**

- **Face Detection & Recognition**: Identify faces
- **Object & Scene Detection**: Detect objects and scenes
- **Celebrity Recognition**: Recognize celebrities
- **Text in Image**: Extract text from images
- **Content Moderation**: Filter inappropriate content

**Use Cases:**

- Face authentication system
- Image classification and search
- Video surveillance and security
- Media content analysis

### Amazon Comprehend

![Amazon Comprehend](/images/4-EventParticipated/AE51DEB2-ACBA-4230-AA3D-DB5BFD7DE9C0.jpeg)

**Amazon Comprehend** is a Natural Language Processing (NLP) service for text analysis.

**Key Features:**

- **Sentiment Analysis**: Analyze emotions (positive, negative, neutral)
- **Entity Recognition**: Identify names, locations, organizations
- **Key Phrase Extraction**: Extract important phrases
- **Language Detection**: Detect language
- **Topic Modeling**: Classify topics

**Use Cases:**

- Analyze customer feedback
- Social media monitoring
- Content categorization
- Document classification

## Key Takeaways

### About Technology

1. **Amazon Bedrock** is the optimal solution for deploying Gen AI with many model choices
2. **Prompt Engineering** is an important skill to maximize AI capabilities
3. **RAG** helps combine the power of AI with internal enterprise data
4. AWS provides a diverse AI services ecosystem for many different use cases

### About Implementation

1. **Start simple**: Use zero-shot prompting for basic tasks
2. **Optimize gradually**: Apply few-shot or CoT when high accuracy is needed
3. **RAG for private data**: No need to fine-tune model, save costs
4. **Combine services**: Leverage multiple AWS AI services for comprehensive solutions

### About Business Value

1. **Reduce costs**: Use managed services instead of building infrastructure
2. **Increase speed**: Deploy quickly with pre-trained models
3. **Scalability**: AWS automatically scales according to demand
4. **Security**: AWS ensures security and compliance

## Event Experience

Attending the **"Generative AI with Amazon Bedrock"** workshop was an extremely beneficial experience, helping me understand more deeply about Gen AI technology and how to apply it in practice.

### Learning from Experts

- Speakers with practical experience shared specific case studies about deploying Gen AI in enterprises
- Learned in detail about Prompt Engineering techniques and how to optimize prompts
- Better understanding of RAG architecture and how to implement it in real systems

### Technical Knowledge Gained

- Mastered prompting techniques: Zero-shot, Few-shot, Chain of Thought
- Clearly understood RAG workflow and how to integrate with internal knowledge base
- Learned how to choose the appropriate Foundation Model for each use case
- Explored other AWS AI services: Rekognition, Comprehend

### Practical Applications

The workshop gave me many ideas to apply in my work:

- **Building chatbot**: Use RAG to create a chatbot with knowledge about company products/services
- **Document processing**: Automatically extract and classify information from documents
- **Content generation**: Support creating marketing content, technical documentation
- **Customer insights**: Analyze customer feedback and sentiment

### Networking

- Met and exchanged ideas with professionals in the AI/ML field
- Shared experiences and best practices with the community
- Created connections for future collaboration opportunities

> In conclusion, the event not only provided technical knowledge but also opened up a vision about AI trends and how enterprises can leverage this technology to create competitive advantage.
