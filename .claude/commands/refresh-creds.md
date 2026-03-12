Refresh the Google Workspace MCP credentials. Run the two commands below in order, then let Kevin know when it's done.

1. Run the following command to decrypt and restore credentials.json:

```bash
node -e "const c=require('crypto'),f=require('fs'),k=Buffer.from(f.readFileSync('/Users/kinsalk/.config/gws/.encryption_key','utf8').trim(),'base64'),d=f.readFileSync('/Users/kinsalk/.config/gws/credentials.enc'),n=d.subarray(0,12),t=d.subarray(d.length-16),e=d.subarray(12,d.length-16),r=c.createDecipheriv('aes-256-gcm',k,n);r.setAuthTag(t);let p=r.update(e,null,'utf8');p+=r.final('utf8');f.writeFileSync('/Users/kinsalk/.config/gws/credentials.json',p,{mode:0o600});console.log('credentials.json updated')"
```

2. Run the following command to clear the stale token cache:

```bash
rm -f /Users/kinsalk/.config/gws/token_cache*.json
```

After both commands complete successfully, tell Kevin: "Credentials refreshed — go ahead and restart Claude Code and we'll be back in business."

If either command fails, report the error clearly so Kevin can troubleshoot.
