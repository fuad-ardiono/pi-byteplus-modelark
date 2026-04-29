# Publishing Guide for pi-byteplus-modelark

## 1. GitHub Actions Pipeline Setup
This pipeline will automatically:
- Detect semver changes based on commit messages
- Bump package version correctly following SemVer
- Publish to npmjs.com automatically
- Create git commit tag for the release

### Required Setup:
1. Go to your GitHub repository -> **Settings -> Secrets and variables -> Actions**
2. Add new repository secret:
   - Name: `NPM_TOKEN`
   - Value: Your npmjs.com **Automation Token** (create from https://www.npmjs.com/settings/<username>/tokens)

### SemVer Trigger Rules:
✅ **Patch version (x.y.Z)** -> commits with: `fix`, `patch`, `bugfix`, `chore`, `docs`, `refactor`, `perf`, `test`, `ci`
✅ **Minor version (x.Y.0)** -> commits with: `feat`, `feature`, `add`
✅ **Major version (X.0.0)** -> commits containing: `BREAKING CHANGE` or `breaking`

---

## 2. Listing on https://pi.dev/packages
✅ **YOU ARE ALREADY READY** - pi.dev automatically indexes public npm packages that have:

**Required fields already present in your package.json:**
```json
{
  "name": "pi-byteplus-modelark",
  "keywords": ["pi-package"],
  "pi": {
    "extensions": ["./extensions"]
  },
  "public": true,
  "repository": "correct github url"
}
```

### When it will show up:
- pi.dev crawler runs every 6 hours
- It normally appears within 24 hours after first successful npm publish
- You don't need to submit any forms or register
- If after 48 hours it's not listed: open an issue at https://github.com/badlogic/pi-mono/issues with your package name

---

## 3. Manual First Publish (optional)
To trigger the first release immediately:
```bash
# Make sure you are logged into npm
npm login

# First publish
npm publish --access public
```

---

## 4. Installation Command
Once published, users can install your extension with:
```bash
pi install npm:pi-byteplus-modelark
```

---

## Verification
After your pipeline runs successfully:
1. Check https://www.npmjs.com/package/pi-byteplus-modelark
2. Check back at https://pi.dev/packages after 12-24 hours
