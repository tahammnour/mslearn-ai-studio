## Python Chat App

This folder contains a sample Python chat application that demonstrates how to use Azure AI Studio's project and model deployment APIs for chat completions.

### Key Features
- Uses `AIProjectClient` from `azure.ai.projects` to connect to your Azure AI Studio project.
- Supports chat completions with system, user, and assistant messages.
- Reads configuration from environment variables using `dotenv`.

### Requirements
Install the required packages:
```bash
pip install azure-identity
pip install azure-ai-projects==1.0.0b3
pip install azure-ai-inference==1.0.0b3
```

### How to Run
1. Install dependencies as above.
2. Set up your `.env` file with the following variables:
   - `PROJECT_CONNECTION`: Your Azure AI Studio project connection string
   - `MODEL_DEPLOYMENT`: The name of your deployed model
3. Run the app:
   ```bash
   python chat-app.py
   ```

### Example Usage
```
Enter the prompt (or type 'quit' to exit): Hello!
AI: Hello! How can I assist you today?
```

### Notes
- Make sure your Azure credentials are set up for `DefaultAzureCredential` to work.
- The app will clear the console on start for a clean interface.
- Only valid message objects are appended to the prompt list to avoid errors.
- The prompt is initialized as follows:
  ```python
  prompt = [
      SystemMessage(content="You are a helpful AI assistant that answers questions.")
  ]
   # Get a chat completion
            prompt.append(UserMessage(content=input_text))
            response = chat.complete(
                model=model_deployment,
                messages=prompt)
            completion = response.choices[0].message.content
            print(completion)
            prompt.append(AssistantMessage(content=completion))

  ```

---
