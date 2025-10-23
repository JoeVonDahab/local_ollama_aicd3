# How to Access the Local Ollama Model

The Ollama model is already set up and running on the network. Here's how to use it from your device.

## Server Details

- **Server IP**: `169.230.30.101`
- **Port**: `11434`
- **Model**: `gpt-oss:120b`

---

## From Windows (PowerShell)

### Test Connection
```powershell
curl http://169.230.30.101:11434/v1/models
```

### Send a Chat Message
```powershell
$body = @{
  model = "gpt-oss:120b"
  messages = @(@{role="user"; content="Your question here"})
} | ConvertTo-Json -Depth 5

Invoke-RestMethod -Uri "http://169.230.30.101:11434/v1/chat/completions" -Method POST -ContentType "application/json" -Body $body
```

---

## From Linux/Mac (Terminal)

### Test Connection
```bash
curl http://169.230.30.101:11434/v1/models
```

### Send a Chat Message
```bash
curl -X POST http://169.230.30.101:11434/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-oss:120b",
    "messages": [{"role": "user", "content": "Your question here"}]
  }'
```

---

## From Python

```python
import requests

base_url = "http://169.230.30.101:11434/v1"

response = requests.post(
    f"{base_url}/chat/completions",
    json={
        "model": "gpt-oss:120b",
        "messages": [{"role": "user", "content": "Your question here"}]
    }
)

print(response.json())
```

---

## Troubleshooting

**Can't connect?**
- Verify the server IP is correct: `169.230.30.101`
- Check that you're on the same network
- Test the port: `Test-NetConnection 169.230.30.101 -Port 11434` (Windows PowerShell)

**Need help?**
Contact the system administrator.
