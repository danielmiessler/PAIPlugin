# Detailed Security Procedures

**Auto-loaded when:** Git operations, infrastructure work (AWS, Cloudflare, etc.), sensitive operations

---

## 🚨 SECURITY SECTION CRITICAL 🚨

### Repository Safety (Detailed)

**Customize with your specific security requirements:**

- **NEVER post sensitive data to public repos**
- **NEVER COMMIT FROM THE WRONG DIRECTORY** - Always verify which repository
- **CHECK THE REMOTE** - Run `git remote -v` BEFORE committing
- **`~/.claude/` MAY CONTAIN SENSITIVE PRIVATE DATA** - NEVER commit to public repos
- **CHECK THREE TIMES** before git add/commit from any directory
- **ALWAYS COMMIT PROJECT FILES FROM THEIR OWN DIRECTORIES**
- Before public repo commits, ensure NO sensitive content (credentials, keys, passwords, personal data, API tokens)
- If worried about sensitive content, review carefully before committing

### Common Sensitive File Patterns to Avoid

Never commit files like:
- `.env`, `.env.local`, `.env.production`
- `credentials.json`, `secrets.yaml`
- `config/production.yml` (with real credentials)
- API keys, access tokens, private keys
- `~/.ssh/`, `~/.aws/`, `~/.config/` directories
- Personal journals, notes with sensitive info
- Customer data, PII (Personally Identifiable Information)

### Infrastructure Caution

**Customize with your infrastructure:**

Be **EXTREMELY CAUTIOUS** when working with:
- Cloud infrastructure (AWS, GCP, Azure, DigitalOcean)
- DNS and domain management (Cloudflare, Route53, etc.)
- Database systems (especially production)
- Payment processing (Stripe, PayPal)
- Any core production-supporting services

### Best Practices

1. **Always verify operations before:**
   - Deleting resources
   - Modifying production infrastructure
   - Running destructive commands
   - Pushing to main/master branches

2. **Use git safety features:**
   - Branch protection rules
   - Required pull request reviews
   - Status checks before merging
   - Signed commits (optional but recommended)

3. **For GitHub specifically:**
   - Ensure save/restore points exist (tags, backups)
   - Use `.gitignore` extensively
   - Review diffs before committing
   - Use GitHub's secret scanning

4. **API Key Management:**
   - Use environment variables, never hardcode
   - Rotate keys regularly
   - Use different keys for dev/staging/prod
   - Consider using secret management tools (Vault, AWS Secrets Manager)

---

## Your Custom Security Rules

**Add your own security rules and warnings here:**

Example:
> - Never run database migrations without backup
> - Always test infrastructure changes in staging first
> - Never `rm -rf` without double-checking the path
> - Keep separate AWS accounts for personal/work projects

---
