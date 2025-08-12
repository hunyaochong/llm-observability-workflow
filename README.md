# LLM Token Usage Tracker

A comprehensive n8n workflow for tracking and logging LLM token usage and costs in real-time. This workflow provides detailed analytics and cost monitoring for AI agents using OpenAI's GPT models with Perplexity integration.

## Features

- **Real-time Token Tracking**: Automatically tracks input, output, and total tokens for each LLM interaction
- **Cost Calculation**: Calculates precise costs based on configurable token pricing
- **Google Sheets Integration**: Logs all usage data to Google Sheets for easy analysis and reporting
- **Multi-Model Support**: Currently configured for GPT-5-mini with easy customization for other models
- **Observability Dashboard**: Tracks workflow execution, client interactions, and tool usage
- **Chat Interface**: Public-facing chat interface for client interactions

## Workflow Components

### 1. Chat Trigger
- **Node**: `When chat message received`
- **Purpose**: Initiates the workflow when a user sends a chat message
- **Configuration**: Public chat interface with custom welcome message

### 2. Metadata Collection
- **Node**: `Set metadata`
- **Purpose**: Captures workflow ID, execution ID, and client ID for tracking
- **Data Collected**:
  - Workflow ID
  - Execution ID
  - Client ID (configurable)

### 3. AI Agent
- **Node**: `AI Agent`
- **Purpose**: Processes user input and generates responses
- **Features**:
  - System message configuration
  - Return intermediate steps for debugging
  - Tool integration support

### 4. LLM with Token Tracking
- **Node**: `GPT-5.1-mini`
- **Purpose**: Custom OpenAI integration with built-in token tracking
- **Key Features**:
  - Configurable model selection
  - Real-time cost calculation
  - Automatic logging to Google Sheets
  - Token usage metadata capture

### 5. External Tool Integration
- **Node**: `Message a model in Perplexity`
- **Purpose**: Provides additional AI capabilities through Perplexity API
- **Use Case**: Extended knowledge base and research capabilities

### 6. Usage Logging
- **Node**: `Token Usage Log`
- **Purpose**: Logs detailed token usage and cost data
- **Data Tracked**:
  - Date/timestamp
  - Model used
  - Input/output tokens
  - Token costs
  - Total costs

### 7. Action Logging
- **Node**: `Log actions`
- **Purpose**: Records workflow actions and tool usage
- **Conditional**: Only logs when tools are used
- **Data Captured**:
  - User input
  - AI output
  - Tools used
  - Execution metadata

## Configuration

### Token Costs (Configurable)
```javascript
const model = "gpt-5-mini-2025-08-07";
const input_token_cost = 0.25;   // $ per million tokens
const output_token_cost = 2.00;  // $ per million tokens
```

### Google Sheets Setup
1. Create a Google Sheets document
2. Set up two sheets:
   - **Token cost tracker**: For usage and cost data
   - **Observability**: For workflow execution logs
3. Configure the Google Sheets credentials in n8n

### API Keys Required
- OpenAI API Key
- Perplexity API Key
- Google Sheets OAuth2 credentials

## Data Schema

### Token Usage Log
- `date`: Timestamp of the interaction
- `workflow_id`: Unique workflow identifier
- `execution_id`: Unique execution identifier
- `client_id`: Client identifier
- `model`: AI model used
- `input_tokens`: Number of input tokens
- `output_tokens`: Number of output tokens
- `total_tokens`: Total tokens used
- `input_cost`: Cost of input tokens
- `output_cost`: Cost of output tokens
- `total_cost`: Total cost of the interaction

### Action Log
- `date`: Timestamp
- `workflow_id`: Workflow identifier
- `execution_id`: Execution identifier
- `client_id`: Client identifier
- `input`: User input message
- `output`: AI response
- `Tool use`: Tools utilized in the response

## Usage

1. **Deploy the Workflow**: Import the JSON configuration into your n8n instance
2. **Configure Credentials**: Set up OpenAI, Perplexity, and Google Sheets credentials
3. **Customize Settings**: Adjust token costs and client IDs as needed
4. **Activate Workflow**: Enable the workflow to start tracking
5. **Monitor Usage**: Check your Google Sheets for real-time usage data

## Benefits

- **Cost Control**: Monitor and control AI usage costs
- **Performance Analytics**: Track token efficiency and usage patterns
- **Client Billing**: Accurate usage data for client billing
- **Optimization**: Identify opportunities to optimize prompts and reduce costs
- **Compliance**: Maintain detailed logs for audit and compliance purposes

## Customization

The workflow is highly customizable:
- **Models**: Easy to switch between different OpenAI models
- **Pricing**: Update token costs as pricing changes
- **Logging**: Modify what data is captured and stored
- **Tools**: Add or remove AI tools as needed
- **Interface**: Customize the chat interface and welcome messages

## Learn More

Interested in more advanced n8n workflows like this? Check out my YouTube channel for tutorials, tips, and workflow examples:

**🎥 [My YouTube Channel](https://www.youtube.com/@hunyaochong)**

Subscribe for:
- Advanced n8n workflow tutorials
- Real-world use cases and examples
- Cost optimization techniques


## License

This workflow is provided as-is for educational and commercial use. Feel free to modify and adapt it to your specific needs.
