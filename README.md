# Awesome Agentic Commerce [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of protocols, specs, SDKs, and tools powering the emerging agentic commerce stack: AI agents that discover, negotiate, pay, and transact autonomously.

Maintained by [Bitrefill](https://www.bitrefill.com). Contributions welcome.

## Contents

- [Why agentic commerce](#why-agentic-commerce)
- [Commerce protocols](#commerce-protocols)
  - [ACP (Agentic Commerce Protocol)](#acp-agentic-commerce-protocol)
  - [AP2 (Agent Payments Protocol)](#ap2-agent-payments-protocol)
  - [UCP (Universal Commerce Protocol)](#ucp-universal-commerce-protocol)
- [Crypto payment rails](#crypto-payment-rails)
  - [x402](#x402)
  - [L402](#l402)
  - [Fewsats](#fewsats)
- [Fiat payment rails](#fiat-payment-rails)
  - [Stripe](#stripe)
  - [Visa](#visa)
  - [Mastercard](#mastercard)
  - [PayPal](#paypal)
  - [Cloudflare](#cloudflare)
- [Ecosystem](#ecosystem)
  - [OpenAI](#openai)
  - [Shopify](#shopify)
  - [Bitrefill](#bitrefill)
  - [AsterPay](#asterpay)
- [Further reading](#further-reading)
- [How the pieces fit together](#how-the-pieces-fit-together)

## Why agentic commerce

AI agents are moving from "answer questions" to "get things done," including browsing products, comparing prices, paying, and managing orders on behalf of users. This requires new protocols for agent-to-agent communication, commerce standards that machines can parse, and payment rails that work without accounts, sessions, or human intervention.

## Commerce protocols

How agents interact with merchants: product discovery, cart building, checkout, and order management.

### ACP (Agentic Commerce Protocol)

Open standard by OpenAI and Stripe. Powers ChatGPT Instant Checkout; supports 1M+ merchants via Shopify and Etsy. Payment-infrastructure agnostic.

- [ACP Documentation](https://developers.openai.com/commerce/) - Primary docs on OpenAI's developer platform.
- [ACP GitHub Repository](https://github.com/agentic-commerce-protocol/agentic-commerce-protocol) - Specification and implementation (Apache 2.0).
- [Stripe ACP Integration](https://docs.stripe.com/agentic-commerce/protocol) - Stripe's integration guide.
- [Stripe Blog: Developing an Open Standard](https://stripe.com/blog/developing-an-open-standard-for-agentic-commerce) - Technical overview and rationale.

### AP2 (Agent Payments Protocol)

Google's open protocol for payment-agnostic agent-led transactions. Uses Verifiable Digital Credentials (VDCs) and a three-mandate model (Intent, Cart, Payment). Backed by 60+ organizations including Adyen, Mastercard, PayPal, Visa, and Coinbase.

- [AP2 Official Site](https://ap2-protocol.org/) - Primary documentation.
- [AP2 Specification](https://ap2-protocol.org/specification/) - V0.1 technical spec.
- [AP2 GitHub Repository](https://github.com/google-agentic-commerce/AP2) - Reference implementation and code samples.
- [Google Cloud AP2 Announcement](https://cloud.google.com/blog/products/ai-machine-learning/announcing-agents-to-payments-ap2-protocol) - Official announcement.

### UCP (Universal Commerce Protocol)

Google's open-source standard for the merchant side of agentic commerce (AP2 handles payments). Standardizes product discovery, checkout, identity linking, and order management. Supported by Shopify, Target, Walmart, Etsy, Wayfair, and 20+ partners. Transport-agnostic (REST, MCP, or A2A).

- [UCP Official Site](https://ucp.dev/) - Primary documentation portal.
- [UCP GitHub Repository](https://github.com/Universal-Commerce-Protocol/ucp) - Specification and documentation.
- [UCP Code Samples](https://github.com/Universal-Commerce-Protocol/samples) - Reference implementations.
- [UCP Google Developers Guide](https://developers.google.com/merchant/ucp) - Google's official UCP docs.

## Crypto payment rails

Commerce protocols define what to buy; payment rails define how to pay. These enable programmatic, machine-to-machine payments without human intervention.

### x402

Uses HTTP 402 "Payment Required" for instant stablecoin payments over HTTP. Built by Coinbase, governed by the x402 Foundation (co-founded with Cloudflare). No API keys, accounts, or subscriptions needed. Serves as the crypto rail within Google's AP2 protocol.

- [x402 Official Site](https://www.x402.org/) - Documentation and ecosystem overview.
- [x402 GitHub Repository](https://github.com/coinbase/x402) - Protocol spec, SDKs, and examples.
- [x402 Specification](https://github.com/coinbase/x402/tree/main/specs) - Full technical specification.
- [x402 Coinbase Documentation](https://docs.cdp.coinbase.com/x402/welcome) - Developer docs and quickstart.
- [x402 on Solana](https://solana.com/developers/guides/getstarted/intro-to-x402) - Solana integration guide.

### L402

Lightning Labs' protocol combining Macaroons (cryptographic bearer credentials) with Lightning Network micropayments for stateless API authentication. Pay-per-request APIs with no accounts and instant settlement. The Bitcoin-native counterpart to x402.

**Note:** "LN402" is not a separate protocol; references to LN402 point back to L402.

- [L402 Builder's Guide](https://docs.lightning.engineering/the-lightning-network/l402) - Comprehensive documentation.
- [L402 Protocol Specification](https://docs.lightning.engineering/the-lightning-network/l402/protocol-specification) - Full technical spec.
- [L402 GitHub Repository](https://github.com/lightninglabs/L402) - Protocol specification source.
- [Aperture](https://github.com/lightninglabs/aperture) - Production L402 reverse proxy for REST and gRPC APIs.

### Fewsats

Practical toolkit for AI agents to make L402 payments. MCP server, CLI, and Python SDK for purchasing API access, digital content, and services via L402 paywalls.

- [Fewsats MCP Server](https://github.com/fewsats/fewsats-mcp) - MCP server for AI agent payments.
- [Fewsats Python SDK](https://github.com/Fewsats/L402-python) - L402 payments for AI agents.

## Fiat payment rails

Card networks and payment processors building agent-specific primitives: tokenized credentials, sessionless merchant auth, and scoped payment tokens.

### Stripe

Infrastructure backbone for most agentic commerce protocols (ACP, AP2, UCP). Key innovation: **Shared Payment Tokens (SPTs)** -- single-use, scoped credentials compatible with Visa and Mastercard agent protocols.

- [Stripe Agentic Commerce Docs](https://docs.stripe.com/agentic-commerce) - Primary documentation hub.
- [Shared Payment Tokens (SPTs)](https://docs.stripe.com/agentic-commerce/concepts/shared-payment-tokens) - Scoped, single-use payment credentials for agents.

### Visa

**Trusted Agent Protocol (TAP)**: open framework using HTTP Message Signatures (RFC 9421) for agent authentication on the Visa network. Part of the broader **Intelligent Commerce** program (30+ partners in sandbox, early 2026).

- [Visa Intelligent Commerce](https://developer.visa.com/capabilities/visa-intelligent-commerce) - Developer program opening Visa rails to AI agents.
- [Trusted Agent Protocol (TAP)](https://developer.visa.com/capabilities/trusted-agent-protocol) - Authentication framework for agent-to-network communication.
- [TAP GitHub Repository](https://github.com/visa/trusted-agent-protocol) - Reference implementation and spec.

### Mastercard

**Agent Pay** introduces **Agentic Tokens**: scoped, time-limited cryptographic credentials for AI agent transactions. Official MCP server available for Mastercard APIs.

- [Mastercard Agent Pay](https://developer.mastercard.com/mastercard-checkout-solutions/documentation/use-cases/agent-pay/) - Developer documentation.

### PayPal

**Agent Ready** uses the Agentic Commerce Protocol (ACP) so existing PayPal/Braintree merchants can accept payments through AI assistants (e.g. ChatGPT) with minimal integration; PayPal handles security and cross-platform compatibility.

- [PayPal Agentic Commerce Overview](https://docs.paypal.ai/growth/agentic-commerce/overview) - Official documentation.
- [Agent Ready](https://docs.paypal.ai/growth/agentic-commerce/agent-ready) - ACP-based agent payments for existing merchants.
- [Store Sync](https://docs.paypal.ai/growth/agentic-commerce/store-sync/create-a-product-catalog) - Product catalog and cart integration for AI discovery and checkout.
- [PayPal Agent Toolkit](https://github.com/paypal/agent-toolkit) - Integrate with PayPal APIs via function calling (OpenAI Agent SDK, LangChain, Vercel AI SDK, MCP). Invoices, orders, catalog, subscriptions, disputes, shipment tracking. ([npm](https://www.npmjs.com/package/@paypal/agent-toolkit))

### Cloudflare

**Agents SDK** natively supports x402 for stablecoin payments, with plans to integrate Visa and Mastercard agent protocols directly into the SDK.

- [Cloudflare Agents SDK](https://developers.cloudflare.com/agents/) - Full SDK documentation.
- [Cloudflare x402 Integration](https://developers.cloudflare.com/agents/x402/) - x402 in the Agents SDK.
- [Cloudflare Secure Agentic Commerce](https://blog.cloudflare.com/secure-agentic-commerce/) - Visa and Mastercard protocol support announcement.

## Ecosystem

Commerce platforms, merchant programs, and tooling that connect agents to real-world buying experiences. These sit above the payment rails — they decide *what* gets bought and *where*, while rails handle the *how*.

### OpenAI

The first frontier-model company to build a full merchant commerce program. **ChatGPT Instant Checkout** (built on ACP) enables in-chat purchases without leaving the conversation. **Operator** / agent mode lets ChatGPT browse and transact autonomously on users' behalf. A growing roster of merchant apps (Target, Instacart, DoorDash) replaces the earlier direct-listing approach, giving retailers control over catalog, inventory, and fulfillment while remaining discoverable inside ChatGPT.

- [ChatGPT Merchant Program](https://chatgpt.com/merchants/) - Apply for Instant Checkout access and build a ChatGPT merchant app.
- [ACP Get Started](https://developers.openai.com/commerce/guides/get-started/) - Step-by-step integration guide for merchants.

### Shopify

**Storefront MCP Server** exposes product catalogs, inventory, and checkout to AI agents. Co-developed UCP with Google. 1M+ merchants accessible via ACP; raised merchant concerns that drove OpenAI's pivot from direct listings to merchant-owned ChatGPT apps.

- [Shopify Agent Commerce](https://shopify.dev/docs/agents) - Developer documentation hub.
- [Shopify Storefront MCP Server](https://shopify.dev/docs/agents/catalog/storefront-mcp) - MCP server for product discovery and checkout.
- [Shop Chat Agent](https://github.com/Shopify/shop-chat-agent) - Reference app for conversational commerce.

### Bitrefill

Bitrefill maintains this list and provides agentic commerce tooling: an eCommerce MCP server, agent skills, and a CLI for gift cards, mobile top-ups, and eSIMs. Connect AI assistants (ChatGPT, Claude, Cursor) to search, buy, and manage Bitrefill products with crypto or account balance.

- [eCommerce MCP Server](https://docs.bitrefill.com/docs/ecommerce-mcp) - MCP server documentation.
- [Bitrefill Agents](https://github.com/bitrefill/agents) - Agent skills for shopping on Bitrefill (bitrefill-website, bitrefill-cli).
- [Bitrefill CLI](https://github.com/bitrefill/cli) - Command-line client. Browse, buy, and manage gift cards, top-ups, and eSIMs.

### AsterPay

EUR settlement infrastructure for AI agent payments. Converts USDC/EURC earned via x402 into EUR via SEPA Instant. 5-layer Know Your Agent (KYA) trust framework with ERC-8004 identity, sanctions screening, and trust scoring. MiCA-compliant EU entity. Listed on x402.org ecosystem and Circle Alliance.

- [AsterPay Docs](https://asterpay.io/docs) - API documentation and integration guide.
- [AsterPay MCP Server](https://www.npmjs.com/package/@asterpay/mcp-server) - 16-tool MCP server for trust scoring, settlement estimates, and market data.
- [AsterPay Agent Skills](https://github.com/AsterPay/asterpay-skills) - Agent Skills for EUR settlement and trust scoring (agentskills.io format).
- [AsterPay Python SDK](https://pypi.org/project/asterpay/) - Python SDK for settlement and KYA integration.

## Further reading

- [MCP, A2A, ACP, ANP Survey Paper](https://arxiv.org/html/2505.02279v1) - Academic comparison of all major agent protocols.

## How the pieces fit together

```
┌─────────────────────────────────────────────────────────────────┐
│                     USER / AI AGENT                             │
│   Claude Code · OpenAI Agents · Google ADK · Copilot CLI        │
└──────────────────────────┬──────────────────────────────────────┘
                           │
              Skills, Plugins, Function Calling
                           │
┌──────────────────────────▼──────────────────────────────────────┐
│                   CONTEXT & TOOLS (MCP)                         │
│  MCP Servers · MCP Registry · MCP Apps (UI)                     │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────────────────┐
│              AGENT COMMUNICATION                                │
│  A2A (Agent2Agent) · ANP (Agent Network Protocol)               │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────────────────┐
│                COMMERCE PROTOCOLS                               │
│   ACP (OpenAI+Stripe) · AP2 (Google) · UCP (Google+Shopify)     │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────────────────┐
│                  PAYMENT RAILS                                  │
│                                                                 │
│  Crypto                          Fiat                           │
│  x402 (stablecoins)              Stripe (SPTs + Agent Toolkit)  │
│  L402 (Lightning/Bitcoin)        Visa (TAP + Intelligent Com.)  │
│  Fewsats (L402 toolkit)         Mastercard (Agent Pay + Tokens) │
│                                  PayPal · Adyen · Square        │
│                                                                 │
│  Infrastructure: Cloudflare (x402 + Visa/MC in Agents SDK)      │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────────────────┐
│                      ECOSYSTEM                                  │
│  OpenAI (ChatGPT Instant Checkout · Operator · Merchant Apps)   │
│  Shopify (Storefront MCP · UCP · 1M+ merchants)                 │
│  Bitrefill (eCommerce MCP · Agent Skills · CLI)                 │
└─────────────────────────────────────────────────────────────────┘
```

## Contributing

Contributions welcome! Please read the [contributing guidelines](CONTRIBUTING.md) first. Only official sources (specs, docs, SDKs, and official blog posts from the maintaining organizations) are accepted.
