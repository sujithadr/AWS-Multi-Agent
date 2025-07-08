# 🤖 AWS Multi‑Agent Framework using Bedrock Agents + Lambda Tools

**Author:** Sujith Somanunnithan

This repository demonstrates a secure, modular, **multi-agent system** where reasoning is handled by **Amazon Bedrock Agents** and real-world actions (e.g., fetching hotel or restaurant details) are executed by **AWS Lambda tools**. All infrastructure is serverless and runs fully within AWS — **no credentials or secrets required**.

---

## 🧠 Architecture Overview

- **Bedrock Agents**: Autonomous agents using foundation models (Claude, Titan, etc.) for reasoning, task decomposition, and decision-making.
- **Lambda Functions as Tools**: AWS Lambda functions provide real-world data or execute business logic (e.g., look up restaurants, hotels).
- **IAM Authentication**: All components authenticate and authorize using IAM roles — **no API keys** stored anywhere.
- **Serverless & Scalable**: Fully managed with Lambda, Bedrock, IAM, and optional CloudWatch/S3.

![architecture](docs/architecture-diagram.png) <!-- Add if available -->

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

## 📁 Project Structure

```
AWS‑Multi‑Agent/
├── lambda_tools/              # Source code for Lambda functions (tools)
│   ├── get_hotel_info/
│   ├── get_restaurant_info/
│   └── shared_utils/
├── prompts/                   # Optional: Prompt templates for Bedrock Agents
├── deployment/                # CloudFormation / SAM templates
├── notebooks/                 # Bedrock agent simulation/testing
├── README.md                  # This file
└── LICENSE
```

---

## ⚙️ Prerequisites

- AWS account with:
  - Amazon Bedrock enabled
  - AWS Lambda
  - IAM roles + policies
- A deployed **Bedrock Agent** with registered Lambda tools
- Python 3.10+ (for local dev or testing)

---

## 🚀 Deployment Steps

### 1. Deploy Lambda Functions (Tools)
Use AWS SAM or manual CLI:

```bash
sam build
sam deploy --guided
```

This deploys your hotel/restaurant Lambda handlers and assigns IAM roles.

### 2. Register Tools in Bedrock

- In AWS Console: go to **Bedrock > Agents**
- Choose your agent or create a new one.
- Under **"Add Action Group"**:
  - Set `Lambda ARN` to your deployed function.
  - Define input/output schema (if needed).

### 3. Test Agent Interactions

You can invoke via:
- **AWS Console > Bedrock Chat playground**
- **Notebooks** in `/notebooks`
- **API Gateway + Lambda proxy** (optional)

---

## 🧪 Sample Lambda Function

```python
def lambda_handler(event, context):
    city = event.get("city", "Berlin")
    return {
        "hotels": [
            {"name": "Grand Berlin Hotel", "rating": 4.6},
            {"name": "City Inn", "rating": 4.2}
        ]
    }
```

---

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
