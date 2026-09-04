# AI Home Renovation Advisor — n8n AI Agent

## Overview

This project is a real-world business use case for an AI Agent built using n8n.

The use case is based on a home-interior and renovation business where customers may need product information as well as approximate budget estimates.

The AI Agent can understand the customer's request and decide which tool is required to answer it.

## Problem

Customers may ask questions such as:

* Which flooring is suitable for a high-traffic commercial space?
* Are Welspun flooring products water-resistant?
* What type of kitchen finishes are available?
* I have 800 sq. ft. of flooring area. What would be the approximate budget?
* Which product would be suitable for my requirement and what could be the estimated cost?

A simple FAQ chatbot can answer product-related questions, but practical queries may also require calculations.

## Solution

The AI Agent uses two tools:

### Tool 1 — FAQ Knowledge Base

The agent searches a product knowledge base to retrieve relevant information about:

* TOSTEM Windows & Doors
* ULTRAFRESH Modular Kitchen
* MIKASA Wooden Flooring
* WELSPUN Flooring

The knowledge base uses vector search to retrieve relevant information.

### Tool 2 — Budget Calculator

The calculator estimates the approximate material cost based on:

* Product
* Area in square feet
* Mock price per square foot

The calculation is performed deterministically using code rather than asking the LLM to perform the arithmetic.

Example:

800 sq. ft. × ₹350/sq. ft. = ₹2,80,000

> Note: The prices used in this prototype are mock values for demonstration purposes and are not actual product quotations.

## Agent Workflow

```text
User
  ↓
Chat Trigger
  ↓
AI Agent
  ↓
 ┌─────────────────────┬──────────────────────┐
 ↓                     ↓
FAQ Knowledge Base     Budget Calculator
 ↓                     ↓
Product Information    Estimated Cost
 └─────────────────────┴──────────────────────┘
              ↓
        Final Response
```

## Example

### User Query

"I have a 1,000 sq. ft. high-traffic commercial space. Which flooring would you recommend and what would be the approximate budget?"

### Agent Process

1. Understand the requirement.
2. Search the FAQ knowledge base for suitable flooring.
3. Identify the relevant Welspun flooring option.
4. Send the required product and area to the budget calculator.
5. Calculate the estimated cost.
6. Combine the retrieved information and calculation into the final response.

## Technologies

* n8n
* Google Gemini
* Vector Store / RAG
* Embeddings
* JavaScript
* AI Agent
* Tool Calling

## Limitations

* Pricing is mocked for the prototype.
* Pricing is currently maintained inside the calculator.
* Complex multi-room calculations can be improved further.
* The system provides estimates and should not be treated as an official quotation.

## Future Improvements

* Move pricing to Google Sheets or a database.
* Add lead/quotation generation.
* Add CRM integration.
* Add deterministic multi-room calculations.
* Connect the system to real-time product and pricing data.

## Demo

Demo link:- https://drive.google.com/file/d/17xmy9MoLHCG6_dpUA4KTAh3MK11HF3mh/view?usp=sharing
