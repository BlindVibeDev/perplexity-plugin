# Perplexity Plugin for ElizaOS

A comprehensive plugin that integrates Perplexity AI's advanced search capabilities into the ElizaOS v2 framework, providing real-time web search with citations, research capabilities, and code search functionality.

## Features

### 🚀 Core Capabilities
- **Real-time Web Search**: Access to current information with Perplexity's online models
- **Advanced Citations**: Automatic source attribution with clickable references
- **Multiple Search Modes**:
  - General search with `PERPLEXITY_SEARCH`
  - Deep research with `PERPLEXITY_RESEARCH`
  - Code-specific search with `PERPLEXITY_CODE_SEARCH`
- **Streaming Support**: Real-time response streaming for better UX
- **Rate Limiting**: Built-in rate limiter to prevent API overuse
- **Model Selection**: Support for all Perplexity models

### 🎯 Key Benefits
- **Accuracy**: Leverages Perplexity's fact-checking and citation system
- **Flexibility**: Multiple actions for different use cases
- **Performance**: Optimized with streaming and rate limiting
- **Integration**: Seamless fit into ElizaOS plugin ecosystem

## Installation

### Prerequisites
- Node.js 23+
- pnpm
- ElizaOS v2 installed
- Perplexity API key (get it from [perplexity.ai](https://perplexity.ai))

### Quick Start

1. **Clone the plugin repository**:
```bash
git clone https://github.com/BlindVibeDev/perplexity-plugin.git
cd perplexity-plugin
```

2. **Install dependencies**:
```bash
pnpm install
```

3. **Build the plugin**:
```bash
pnpm build
```

4. **Configure environment variables**:
```bash
# Create .env file
echo "PERPLEXITY_API_KEY=your_api_key_here" > .env
```

## Usage

### Using with ElizaOS CLI

```bash
# Create a new ElizaOS project with Perplexity plugin
elizaos create my-agent --with-plugin perplexity

# Or add to existing project
elizaos plugin add perplexity
```

### Manual Integration

```typescript
import { PerplexitySearchPlugin } from "@elizaos/plugin-perplexity";

// Initialize with custom config
const perplexityPlugin = new PerplexitySearchPlugin({
  apiKey: process.env.PERPLEXITY_API_KEY,
  model: "sonar-pro",
  maxTokens: 2048,
  returnCitations: true,
  stream: true,
});

// Add to your agent runtime
const runtime = new AgentRuntime({
  // ... other config
  plugins: [perplexityPlugin],
});
```

## Available Actions

### 1. PERPLEXITY_SEARCH
General-purpose search with real-time web access.

**Examples**:
- "Search for the latest AI developments"
- "What's happening with cryptocurrency today?"
- "Find information about quantum computing"

**Aliases**: `perplexity`, `ai search`, `smart search`, `web search`

### 2. PERPLEXITY_RESEARCH
In-depth research mode with enhanced citations and longer responses.

**Examples**:
- "Research the impact of AI on global economy"
- "Analyze current trends in renewable energy"
- "Deep dive into blockchain technology advances"

**Aliases**: `deep research`, `comprehensive search`, `detailed analysis`

### 3. PERPLEXITY_CODE_SEARCH
Specialized search for programming and technical content.

**Examples**:
- "Find React hooks best practices"
- "Search for Python async/await examples"
- "How to implement WebRTC in JavaScript"

**Aliases**: `code search`, `programming search`, `technical search`

## Configuration Options

```typescript
interface PerplexityPluginConfig {
  apiKey: string;              // Required: Your Perplexity API key
  model?: string;              // Default: "sonar-pro"
  temperature?: number;        // Default: 0.2 (0-1, lower = more focused)
  maxTokens?: number;          // Default: 1024
  topP?: number;               // Default: 0.9
  frequencyPenalty?: number;   // Default: 0
  presencePenalty?: number;    // Default: 0
  stream?: boolean;            // Default: false
  returnCitations?: boolean;   // Default: true
  includeImages?: boolean;     // Default: false
  includeRelatedQuestions?: boolean; // Default: true
  maxResults?: number;         // Default: 5
}
```

## Supported Models

- **sonar-pro**: Most advanced model for complex queries
- **sonar-small**: Efficient model for simple searches
- **sonar-medium**: Balanced performance and capability
- **sonar-small-online**: Real-time web access (small)
- **sonar-medium-online**: Real-time web access (medium)
- **codellama-34b**: Specialized for code and technical content
- **mistral-7b**: Open-source model option

## Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

## License

MIT License - see [LICENSE](LICENSE) file for details.

## Support

- **Documentation**: [ElizaOS Docs](https://eliza.how)
- **Issues**: [GitHub Issues](https://github.com/BlindVibeDev/perplexity-plugin/issues)
- **Discord**: [ElizaOS Community](https://discord.gg/elizaos)
- **Perplexity API**: [API Documentation](https://docs.perplexity.ai)

---

Made with ❤️ by the ElizaOS community