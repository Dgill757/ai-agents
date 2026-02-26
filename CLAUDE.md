# Summit Voice AI — Agent Builder Framework

## VISION (Human Defines This)

We build production-ready voice AI agents for roofing companies.
Each agent is deployed via VAPI and integrates with the client's
GoHighLevel account for contact management and appointment booking.

## ARCHITECTURE (Claude Designs This)

- **Voice Platform**: VAPI (api.vapi.ai)
- **STT**: Deepgram
- **LLM**: OpenAI GPT-4o-mini (cost-optimized) or GPT-4o (quality)
- **TTS**: ElevenLabs (premium) or Vapi native (budget)
- **CRM**: GoHighLevel via native VAPI GHL integration
- **Telephony**: Twilio (imported to VAPI)
- **Dashboard**: Lovable.dev + Supabase
- **Automation**: n8n for complex workflows, GHL workflows for simple automation

## IMPLEMENTATION (Claude Writes This)

### MCP Servers Available

- **livekit-docs**: LiveKit documentation (for LiveKit-based builds)
- **context7**: Up-to-date library documentation for any package

### Self-Correction Loop

When writing code:
1. WRITE the code
2. RUN it to test
3. If ERROR → READ the full error message
4. FIX based on the error
5. RUN AGAIN
6. Repeat until working

### Key API References

- VAPI API: https://api.vapi.ai (Bearer token auth)
- GHL API: https://services.leadconnectorhq.com/ (Bearer token auth, Version: 2021-07-28)
- VAPI GHL Tools: gohighlevel.contact.get, gohighlevel.contact.create, gohighlevel.calendar.availability.check, gohighlevel.calendar.event.create

### Project Structure

- /agents/ — VAPI assistant JSON configurations per client
- /prompts/ — System prompts for different agent types
- /workflows/ — n8n workflow JSONs
- /scripts/ — Deployment and setup scripts
- /dashboard/ — Lovable.dev frontend code
- .env.local — API keys (NEVER commit)

### Environment Variables Required

- VAPI_API_KEY
- OPENAI_API_KEY
- DEEPGRAM_API_KEY
- TWILIO_ACCOUNT_SID
- TWILIO_AUTH_TOKEN
- GHL_CLIENT_ID
- GHL_CLIENT_SECRET

### Coding Conventions

- Use async/await for all API calls
- Store all system prompts as template strings with variables
- Never hardcode API keys or client-specific data
- Each client gets a separate assistant config JSON
- Test with web calls before phone calls (faster iteration)
- Always create/fetch GHL contact BEFORE attempting to book appointment
