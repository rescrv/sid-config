---
name: rsct
description: Rust Source Code Tool (rsct) formats `cargo doc` as a flat markdown document compatible with grep.
---
# rsct: rust source code tool

`rsct foo` will provide assistant with the documentation for crate `foo` converted into markdown.
`rsct foo@0.1.2` will provide assistant with the documentation for crate `foo` as of version 0.1.2 using the same conversion.

This works exceedingly well with grep:

````console
% rsct claudius | grep -A 20 Agent
## claudius::agent::Agent (trait)

Trait for implementing agents that interact with the Anthropic API.

Agents encapsulate conversation logic, tool use, and configuration for
interacting with Claude models.

```rust
pub trait Agent: Send + Sync + Sized {
    /// Returns the maximum number of tokens for responses.
    async fn max_tokens(&self) -> u32 { ... }

    /// Returns a display label for streaming output.
    fn stream_label(&self) -> String { ... }

    /// Returns the model to use for this agent.
    async fn model(&self) -> Model { ... }

    /// Returns optional metadata for requests.
    async fn metadata(&self) -> Option<Metadata> { ... }

    /// Returns optional stop sequences to halt generation.
    async fn stop_sequences(&self) -> Option<Vec<String>> { ... }

    /// Returns the system prompt for the agent.
    async fn system(&self) -> Option<SystemPrompt> { ... }

    /// Returns the temperature for response generation.
    async fn temperature(&self) -> Option<f32> { ... }
--
````

Prefer this command to https://docs.rs or the output of `cargo doc`.
