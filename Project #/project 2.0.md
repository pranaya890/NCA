





Personalized Tutor System For adaptive learning

But during defense clearly state:

> "The system is domain-restricted to Computer Engineering curricula. The personalization, retrieval, and assessment mechanisms are designed specifically for Computer Engineering students."

This way the title remains broad and modern, but the implementation scope becomes realistic.

---

# Project Vision

The proposed system is an AI-powered educational platform that acts as a personalized tutor for Computer Engineering students. Unlike general AI chatbots, the system only answers questions related to approved Computer Engineering subjects and uses curriculum materials such as lecture notes, textbooks, syllabi, and lab manuals as its knowledge source.

The platform continuously monitors student learning behavior, identifies weak and strong areas, adapts explanations according to student performance, generates personalized quizzes, and recommends study plans.

---

# Supported Subjects

The system will only support Computer Engineering courses.

Example:

### Programming

- C
    
- C++
    
- Python
    
- Java
    

### Core Subjects

- Data Structures and Algorithms
    
- Database Management System
    
- Operating Systems
    
- Computer Networks
    
- Artificial Intelligence
    
- Software Engineering
    
- Compiler Design
    

### Hardware Subjects

- Digital Logic
    
- Microprocessor
    
- Computer Organization
    
- Embedded Systems
    

### Mathematics

- Discrete Mathematics
    
- Probability and Statistics
    

---

# Main Problem Being Solved

Current educational systems provide the same content to all students regardless of individual learning capabilities.

Students often:

- Do not know their weak topics
    
- Study inefficiently
    
- Depend on generic AI tools
    
- Receive hallucinated answers
    
- Lack personalized guidance
    

The proposed system solves these problems by creating an adaptive learning environment specifically for Computer Engineering education.

---

# Major Deliverables

## Deliverable 1: User Management Module

Functions:

- Registration
    
- Login
    
- Student Profile
    
- Academic Preferences
    
- Progress History
    

Output:

- Individual student learning profile
    

---

## Deliverable 2: Domain Restriction Module

Purpose:

Ensure the system answers only Computer Engineering related questions.

Workflow:

1. User submits query
    
2. Query classifier analyzes subject
    
3. If within supported domain:
    
    - Continue processing
        
4. Otherwise:
    
    - Reject query
        

Example:

### Allowed

- Explain Binary Search Tree
    
- What is TCP/IP?
    
- Explain Deadlock
    

### Rejected

- Heart surgery
    
- Stock market prediction
    
- Legal advice
    

This directly addresses the panel's concern.

---

## Deliverable 3: Curriculum Knowledge Base

Administrator uploads:

- PDFs
    
- Lecture Notes
    
- Lab Sheets
    
- Syllabus
    

Processing Pipeline:

1. Document Upload
    
2. Text Extraction
    
3. Chunking
    
4. Embedding Generation
    
5. Vector Storage
    

Tools:

- LangChain
    
- Gemini Embeddings
    
- ChromaDB
    

Output:

- Searchable curriculum knowledge repository
    

---

## Deliverable 4: RAG-Based Tutor Engine

Workflow:

Student Question

↓

Query Embedding

↓

Vector Search

↓

Relevant Context Retrieval

↓

Prompt Construction

↓

Gemini Response

↓

Answer Generation

Advantages:

- Curriculum aligned
    
- Reduced hallucination
    
- Context aware answers
    

---

## Deliverable 5: Personalized Learning Engine

This is the heart of the project.

The system stores:

- Topic studied
    
- Quiz performance
    
- Time spent
    
- Number of attempts
    

Student Model Example:

|Topic|Mastery|
|---|---|
|DBMS|85%|
|Data Structures|42%|
|Networks|70%|

The system continuously updates this profile.

---

## Deliverable 6: Adaptive Explanation Generator

Based on student performance:

### Beginner

- Simple explanations
    
- Examples
    
- Analogies
    

### Intermediate

- Technical explanation
    
- Moderate complexity
    

### Advanced

- Detailed theoretical explanation
    
- Real-world implementation
    

Example:

Question:

"What is a Binary Tree?"

Three students receive three different levels of explanation.

This is genuine personalization.

---

## Deliverable 7: Intelligent Quiz Generator

Generates:

### MCQ

Example:

What is the time complexity of Binary Search?

### Short Answer

Explain normalization.

### Coding Questions

Implement Stack using Array.

Difficulty Levels:

- Easy
    
- Medium
    
- Hard
    

Generated automatically using course material.

---

## Deliverable 8: Performance Analytics Module

Tracks:

- Quiz scores
    
- Topic mastery
    
- Learning trend
    
- Weak areas
    

Visualizations:

- Topic-wise score graph
    
- Progress chart
    
- Subject mastery heatmap
    

---

## Deliverable 9: Recommendation Engine

Based on weaknesses:

Example:

Student weak in:

- Trees
    
- Graphs
    

System recommends:

- Related lecture notes
    
- Practice quizzes
    
- Suggested study sequence
    

---

## Deliverable 10: Study Planner

Automatically creates:

### Daily Plan

- Topic to read
    
- Quiz to complete
    

### Weekly Plan

- Revision schedule
    
- Target completion
    

### Exam Preparation Mode

- Priority topics
    
- Mock tests
    

---

# Proposed System Architecture

```text
Student
   |
   V
Web Application
   |
   +------------------+
   |                  |
   V                  V
Query Classifier   Student Profile
   |                  |
   V                  |
RAG Engine            |
   |                  |
   V                  |
Vector Database       |
   |                  |
   V                  |
Gemini API            |
   |                  |
   +---------+--------+
             |
             V
     Personalized Response
             |
             V
      Quiz Generator
             |
             V
      Progress Tracker
```


```
Student Question
        |
        V
Query Classifier
        |
        V
RAG Retriever
        |
        V
Student Profile Analyzer
        |
        V
Prompt Generator
        |
        V
Gemini API
        |
        V
Personalized Response
```

---

# Evaluation Methodology

The panel will definitely ask:

> "How will you prove the system works?"

Use measurable metrics.

### Retrieval Accuracy

Percentage of correctly retrieved documents.

### Response Relevance

Faculty evaluation score.

### Quiz Quality

Faculty validation.

### User Satisfaction

Student feedback.

### Learning Improvement

Pre-test vs Post-test scores.

Example:

- Pre-test average = 52%
    
- Post-test average = 78%
    

Improvement = 26%

This is strong evidence.

---

# Novelty Statement

When asked:

> "What is the novelty?"

Answer:

> "The novelty lies in combining curriculum-restricted RAG, adaptive learning analytics, learner profiling, dynamic explanation generation, personalized quiz generation, and recommendation-based study planning specifically for Computer Engineering education. Unlike generic chatbots, the system continuously adapts its teaching strategy based on student performance."

That is a much stronger project than simply "upload PDF and chat with Gemini."



## Example

Suppose the student asks:

> "Explain Binary Search Tree"

Your system already knows:

- Student level = Beginner
- Weak topic = Trees
- Subject = Data Structures
- Retrieved context = BST notes from uploaded PDF

The Prompt Generator creates:

```
You are an educational tutor for Computer Engineering students.Subject: Data StructuresStudent Level: BeginnerWeak Topics: TreesUse only the provided context.Context:[Retrieved PDF chunks]Task:Explain Binary Search Tree in simple language.Give a real-world analogy.Provide a small example.Avoid advanced terminology.
```

Then Gemini receives this prompt.

---

## For an Advanced Student

Same question:

> "Explain Binary Search Tree"

Generated prompt:

```
You are an educational tutor for Computer Engineering students.Subject: Data StructuresStudent Level: AdvancedContext:[Retrieved PDF chunks]Task:Explain Binary Search Tree in detail.Discuss insertion complexity.Discuss deletion complexity.Compare with AVL Trees.Include implementation considerations.
```

Gemini now gives a completely different answer.