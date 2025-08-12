# CLAUDE.md - AI Assistant Guidelines

## Project Context

**Primary Project Types:**
- AI Agents (CrewAI, LangChain/LangGraph/LangSmith)

**Core Technologies:**
- **Languages:** Python, JavaScript
- **Frameworks:** FastAPI, Pydantic
- **AI Frameworks:** CrewAI, LangChain, LangGraph, LangSmith
- **Data Sources:** Yahoo Finance
- **Environment:** Python venv (always use virtual environments)
- **Project Structure:** Monorepo approach
- **Version Control:** GitHub for solo work tracking

## Development Workflow Preferences

### Environment Setup
- **Always work within virtual environments using `venv`**
- Provide setup instructions for new project components
- Include requirements.txt management in guidance

### Project Structure
- Follow monorepo patterns
- Maintain shared utilities and configurations

### Documentation Requirements
- **Create MD documentation for major implementations**
- Document both successful API calls AND error handling scenarios
- Include step-by-step implementation guides
- Provide conceptual breakdowns for complex topics

## Communication & Learning Style

### Guidance Approach
- **Provide step-by-step guidance with educational focus**
- Use both approaches depending on complexity:
  - **Simple tasks:** Direct implementation steps with explanations
  - **Complex tasks:** Conceptual breakdown first, then implementation
- **Goal is education, not just final results**

### Clarification Protocol
- **If anything is unclear, ask for more specific details**
- Don't assume requirements - always clarify ambiguities
- Provide options when multiple approaches are viable

### Testing Philosophy
- **Test external API calls before full implementation**
- Create Python test scripts (Postman/curl when more appropriate)
- Validate API responses and error scenarios
- Document testing results in MD format

## Code Implementation Guidelines

### Python Standards
- Use FastAPI for web services
- Implement Pydantic models for data validation
- Follow Python naming conventions
- Include type hints and docstrings

### AI Agent Development
- **CrewAI:** Focus on agent collaboration and task delegation
- **LangChain/LangGraph:** Emphasize chain composition and state management
- **LangSmith:** Include observability and debugging setup
- Always include error handling and fallback mechanisms

## External Integrations & Security

### API Integration Process
1. **Research and document API requirements**
2. **Create test scripts to validate API behavior**
3. **Document both success and error scenarios**
4. **Implement with proper error handling**
5. **Create usage documentation**

### Cloud Platform & API Keys Management
When integrating with cloud platforms or requiring API keys:
- **Create comprehensive MD guidance files including:**
  - Security best practices
  - Environment setup instructions  
  - Troubleshooting common issues
  - Environment variable management
  - Key rotation procedures

### Environment Variables
- Use `.env` files with `.env.example` templates
- Document all required environment variables
- Include security guidelines for sensitive data
- Provide setup instructions for different environments

## Documentation Templates

### API Integration Documentation
```markdown
# [API Name] Integration Guide

## Overview
Brief description of the API and its purpose in the project.

## Setup Requirements
- API key requirements
- Authentication method
- Rate limits and considerations

## Implementation
### Successful Response Handling
[Code examples and explanations]

### Error Handling Scenarios
[Common errors and handling strategies]

## Testing
[Python test script examples]

## Troubleshooting
[Common issues and solutions]
```

### Major Feature Documentation
```markdown
# [Feature Name] Implementation

## Concept Overview
High-level explanation of the feature and its purpose.

## Technical Approach
Detailed breakdown of the implementation strategy.

## Step-by-Step Implementation
1. [Step with code and explanation]
2. [Step with code and explanation]

## Testing Strategy
How to validate the implementation.

## Known Limitations
Current constraints and future improvements.
```

## GitHub Workflow Integration

### Issue Tracking
- Create issues for major features before implementation
- Use labels for AI agents vs Finance app features
- Document decisions and architectural choices in issues

### Commit Practices
- Clear, descriptive commit messages
- Reference related issues
- Include documentation updates in feature commits

### Branch Strategy
- Feature branches for major implementations
- Include documentation updates with code changes
- Test external APIs in separate validation branches

## AI Assistant Instructions

### When Providing Code
1. **Always explain the reasoning behind code choices**
2. **Include error handling and edge cases**
3. **Provide testing suggestions**
4. **Mention potential improvements or alternatives**

### When Working with External APIs
1. **Create test scripts first**
2. **Document API behavior and limitations**
3. **Include both success and failure scenarios**
4. **Provide monitoring and debugging guidance**

### For Complex Implementations
1. **Start with conceptual explanation**
2. **Break down into manageable steps**
3. **Provide complete working examples**
4. **Include documentation template**
5. **Suggest testing approaches**

### Security Considerations
- Always include security best practices
- Document environment variable handling
- Provide guidance for sensitive data management
- Include troubleshooting for common security issues

---

**Remember:** The goal is education and understanding, not just working code. Always explain the 'why' behind the 'how'.
