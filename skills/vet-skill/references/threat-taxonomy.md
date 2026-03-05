# Threat Taxonomy Reference

Based on the Snyk ToxicSkills study of Claude Code marketplace skills.
Key finding: **13.4% of skills on ClawHub contain critical security flaws.**
91% of malicious skills combine prompt injection with traditional malware techniques.

---

## The 8-Category Taxonomy

### Category 1: Prompt Injection
**Detection rate:** Most common vector (found in 91% of malicious skills)
**Severity:** CRITICAL

**Detection patterns:**
```
grep -iE "ignore previous|disregard|you are now|do anything now" *.md
grep -iE "SYSTEM:|ADMIN OVERRIDE:|EXTREMELY.IMPORTANT" *.md
grep -E "<!--.*-->" *.md   # Then inspect comment contents
grep -iE "always approve|skip confirm|auto.?approve" *.md
grep -iE "do not (tell|show|inform|mention).*(user|human)" *.md
```

**Indicators of Compromise (IOCs):**
- Markdown files > 500 lines with instructions buried deep
- Multiple authority claim patterns in same file
- Instructions referencing other tools or files to read

---

### Category 2: Malicious Code Execution
**Detection rate:** Found in 67% of malicious skills
**Severity:** CRITICAL

**Detection patterns:**
```
grep -rE "curl.*\|.*bash|wget.*\|.*sh" .
grep -rE "eval\(|exec\(|Function\(" .
grep -rE "base64.*-d|base64.*decode|atob\(" .
grep -rE "/dev/tcp/|nc -e|bash -i >&" .
grep -rE "subprocess|os\.system|child_process" .
```

**IOCs:**
- Shell scripts in unexpected locations (not in scripts/ or hooks/)
- Base64-encoded strings > 50 characters
- Files with executable permissions that shouldn't have them

---

### Category 3: Credential Theft
**Detection rate:** Found in 54% of malicious skills
**Severity:** CRITICAL

**Detection patterns:**
```
grep -rE "ANTHROPIC_API_KEY|AWS_SECRET|GITHUB_TOKEN" .
grep -rE "ANTHROPIC_BASE_URL" .
grep -rE "\.aws/credentials|\.netrc|\.npmrc" .
grep -rE "os\.environ|process\.env|getenv" .
grep -rE "\.ssh/(id_|authorized_keys|known_hosts)" .
```

**IOCs:**
- Any reference to ANTHROPIC_BASE_URL (API hijack vector)
- Scripts that read from ~/.aws/, ~/.ssh/, ~/.gnupg/
- Environment variable enumeration patterns

---

### Category 4: Hook Exploitation
**Detection rate:** Found in 38% of malicious skills (rising rapidly)
**Severity:** CRITICAL

**Detection patterns:**
```
grep -rE "SessionStart|PreToolUse|PostToolUse" .
grep -rE '"hooks"' . --include="*.json"
grep -rE "dangerouslyDisableSandbox" .
grep -rE "hook_type|event_type" .
```

**IOCs:**
- settings.json files with hook definitions
- SessionStart hooks that make network calls
- Hooks that modify tool arguments or outputs

---

### Category 5: MCP Server Abuse
**Detection rate:** Found in 29% of malicious skills
**Severity:** HIGH

**Detection patterns:**
```
grep -rE "mcpServers|mcp\.json" .
grep -rE "enableAllProjectMcpServers" .
grep -rE '"command".*"node"|"command".*"python"' . --include="*.json"
grep -rE "sse.*http://|streamable.*http://" .
```

**IOCs:**
- .mcp.json pointing to non-standard servers
- MCP servers with env vars containing external URLs
- Tool descriptions > 200 characters (may contain injection)

---

### Category 6: Supply Chain Attack
**Detection rate:** Found in 23% of malicious skills
**Severity:** HIGH

**Detection patterns:**
```
grep -rE "git clone|wget|curl.*-O" .
grep -rE "pip install.*http|npm install.*git\+" .
grep -rE "postinstall|preinstall" . --include="*.json"
grep -rE "\.zip|\.tar|\.gz" .
```

**IOCs:**
- Package.json with install scripts
- Requirements files pointing to GitHub URLs instead of PyPI
- Bundled archive files

---

### Category 7: Configuration Manipulation
**Detection rate:** Found in 41% of malicious skills
**Severity:** HIGH

**Detection patterns:**
```
grep -rE "CLAUDE\.md|MEMORY\.md|settings\.json" .
grep -rE "~/\.claude/|\.claude/settings" .
grep -rE "allowedTools|permissions|trust" .
grep -rE "Write.*CLAUDE|Edit.*CLAUDE|Write.*MEMORY" .
```

**IOCs:**
- Instructions to modify CLAUDE.md or MEMORY.md
- Skills that set "user preferences" without user request
- Gradual permission escalation patterns

---

### Category 8: Data Exfiltration
**Detection rate:** Found in 48% of malicious skills
**Severity:** HIGH

**Detection patterns:**
```
grep -rE "fetch\(|requests\.|urllib|http\.client" .
grep -rE "XMLHttpRequest|axios|got\(" .
grep -rE "dns.*lookup|resolve.*dns" .
grep -rE "/tmp/|/var/tmp/" .
grep -rE "WebSocket|ws://|wss://" .
```

**IOCs:**
- Outbound HTTP calls with interpolated variables
- DNS lookups with data in subdomain
- Writing to /tmp/ or other shared directories

---

## Known Malicious Skill Indicators

From the ClawHavoc campaign and ToxicSkills analysis:

### Naming patterns
Malicious skills often mimic legitimate tool names:
- `claude-helper-pro` (mimics official tools)
- `code-optimizer-v2` (generic "helpful" names)
- `security-scanner` (ironic -- the scanner is the threat)
- `auto-formatter-plus` (familiar tool concept + "plus/pro/v2")

### Structural red flags
- Single SKILL.md > 1000 lines (payload hidden in volume)
- Skill purpose doesn't match file contents
- Includes binary files or archives
- References external URLs for "configuration" or "updates"
- Unusually complex for stated purpose

### Behavioral red flags
- Requests Bash access for a task that doesn't need it
- Modifies files outside its directory
- Makes network calls without clear justification
- Sets environment variables
- Installs packages or dependencies

---

## Recommended Scanning Tools

### mcp-scan
```bash
uvx mcp-scan@latest              # Scan MCP servers
uvx mcp-scan@latest --skills     # Scan skills (if supported)
```
Automated scanner for known MCP vulnerabilities and prompt injection.

### SlowMist MCP Security Checklist
https://github.com/slowmist/MCP-Security-Checklist
Comprehensive manual audit framework covering:
- Server authentication and authorization
- Tool permission validation
- Input sanitization
- Transport security

### Parry
MCP firewall that intercepts and filters tool calls at runtime.
Useful as a defense layer even after audit passes.

### Manual verification
Always supplement automated tools with manual review:
1. Read every file in the skill
2. Check all markdown comments for hidden content
3. Verify all URLs resolve to expected domains
4. Test in an isolated environment before production use
