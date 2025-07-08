# 🤖 AWS Multi‑Agent Framework using Bedrock Agents + Lambda Tools

**Author:** Sujith Somanunnithan

This repository demonstrates a secure, modular, **multi-agent system** where reasoning is handled by **Amazon Bedrock Agents** and real-world actions (e.g., fetching hotel or restaurant details) are executed by **AWS Lambda tools**. All infrastructure is serverless and runs fully within AWS — **no credentials or secrets required**.

---

## 🧠 Architecture Overview

- **Bedrock Agents**: Autonomous agents using foundation models (Claude, Titan, etc.) for reasoning, task decomposition, and decision-making.
- **Lambda Functions as Tools**: AWS Lambda functions provide real-world data or execute business logic (e.g., look up restaurants, hotels).
- **IAM Authentication**: All components authenticate and authorize using IAM roles — **no API keys** stored anywhere.
- **Serverless & Scalable**: Fully managed with Lambda, Bedrock, IAM, and optional CloudWatch/S3.


---

## 🗺️ Use Case Example

### Scenario:
> "Find me a hotel in Berlin and suggest nearby restaurants."

### Execution Flow:

1. **Bedrock Agent** parses the user input.
2. Determines it needs to call `getHotelDetails` and `getNearbyRestaurants` tools.
3. Calls the **Lambda functions** associated with those tools.
4. Aggregates and returns the result to the user.

---

## ⚙️ Prerequisites

- AWS account with:
  - Amazon Bedrock enabled
  - AWS Lambda
  - IAM roles + policies
- A deployed **Bedrock Agent** with registered Lambda tools
- Python 3.10+ (for local dev or testing)



## 🔐 Security

- ✅ IAM Role-based execution (no secrets or hardcoded keys)
- ✅ Least privilege policies for Lambda & Bedrock
- ✅ Logs via CloudWatch (optional)

---

## 🧠 Technologies Used

| Service         | Purpose                             |
|----------------|-------------------------------------|
| Amazon Bedrock | Core multi-agent reasoning engine   |
| AWS Lambda      | Tool handlers (hotel, restaurant)  |
| IAM             | Secure, role-based access control  |
| (Optional) S3   | Prompt persistence / artifacts     |
| (Optional) CloudWatch | Logging and tracing         |

---

## 📚 References

- [Amazon Bedrock Agents](https://docs.aws.amazon.com/bedrock/latest/userguide/agents.html)
- [Lambda Tools Integration](https://docs.aws.amazon.com/bedrock/latest/userguide/agents-tools.html)
- [IAM for Lambda](https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html)

---

## ✅ Contributing

Pull requests are welcome!  
Ideas for new tools (e.g., weather info, travel booking) are encouraged.

---

## 📜 License

Distributed under the [Apache 2.0 License](LICENSE).

---
