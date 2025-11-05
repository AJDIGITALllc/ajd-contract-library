# AJD Contract Library — Canvas Pack

This canvas contains the full repository seed for **ajd-contract-library** broken down into files you can download as `.md`, `.json`, `.yml/.yaml`, and `.ps1/.js`.

Below are the files, in repo order.

---

## 1. README.md
```markdown
# AJ DIGITAL LLC — Contract & Agreements Library

This repo is the **single source of truth** for all agreements, MSAs, NDAs, scopes, and addenda used across:
- AudioJones.com offers
- Circle House Digital / studio services
- Artist / creator services
- Whop-backed or funded offers
- Automation-delivered services (n8n, MailerLite, Vercel functions)

Other repos **consume** this one. They should not duplicate contracts.

---

## 1. Goals
1. Keep all contract language in one versioned place.
2. Give automations a predictable way to pick the right agreement.
3. Allow smart templates with variables (`{{client_legal_name}}`, `{{service_tier}}`, etc.).
4. Enforce quality with GitHub Actions (YML).
5. Publish compiled contracts on release tags.

---

## 2. Repo Structure
```text
ajd-contract-library/
├── README.md
├── /docs
│   ├── repo-overview.md
│   └── authoring-guidelines.md
├── /templates
├── /smart-templates
│   ├── msa__agency-standard.tpl.md
│   ├── scope__artist-services.tpl.md
│   ├── nda__mutual.tpl.md
│   └── fragments/
│       ├── payment-terms.tpl.md
│       ├── whop-funded.tpl.md
│       └── circle-house-addendum.tpl.md
├── /rules
│   ├── mapping.json
│   ├── variables.json
│   └── validations.json
├── /automation
│   ├── esignaturesio-hook.md
│   └── stripe-whop-sync.md
├── /scripts
│   ├── render-template.ps1
│   ├── render-template.js
│   └── build-release.ps1
├── /.github
│   ├── release.yml
│   └── workflows/
│       └── release.yml
├── CHANGELOG.md
├── VERSION.md
└── dist/
```

---
```

## 2. docs/repo-overview.md
```markdown
# AJ DIGITAL LLC — Contract Library Overview
Version: v2025.01  
Maintainer: dev@audiojones.com  
Primary Repo: https://github.com/AJDIGITALllc/ajd-contract-library  

... (full content from earlier message) ...
```

## 3. docs/authoring-guidelines.md
```markdown
# AJ DIGITAL LLC — Contract Authoring Guidelines
Version: v2025.01
Maintainer: dev@audiojones.com

... (full content from earlier message) ...
```

## 4. smart-templates/msa__agency-standard.tpl.md
```markdown
---
template_name: "msa__agency-standard"
version: "v2025.01"
source: "AJ DIGITAL LLC — Contract & Agreements Library"
binding_to_offer: "{{offer_code}}"
---

# MASTER SERVICES AGREEMENT ({{year}})

... (full MSA content from earlier message) ...
```

## 5. smart-templates/scope__artist-services.tpl.md
```markdown
---
template_name: "scope__artist-services"
version: "v2025.01"
purpose: "Scope of work for Audio Jones Artist Services"
---

# STATEMENT OF WORK — ARTIST SERVICES

... (full SOW content from earlier message) ...
```

## 6. smart-templates/nda__mutual.tpl.md
```markdown
---
template_name: "nda__mutual"
version: "v2025.01"
purpose: "Mutual Non-Disclosure Agreement for Agency–Client engagements"
---

# MUTUAL NON-DISCLOSURE AGREEMENT ({{year}})

... (full NDA content from earlier message) ...
```

## 7. smart-templates/fragments/payment-terms.tpl.md
```markdown
---
fragment_name: "payment-terms"
version: "v2025.01"
purpose: "Standard payment, late fee, and refund policy for AJ DIGITAL LLC offers"
---

## PAYMENT TERMS ADDENDUM

... (full fragment content) ...
```

## 8. smart-templates/fragments/whop-funded.tpl.md
```markdown
---
fragment_name: "whop-funded"
version: "v2025.01"
purpose: "Addendum for Whop-funded or installment-based transactions"
---

## WHOP-FUNDED PAYMENT ADDENDUM

... (full fragment content) ...
```

## 9. smart-templates/fragments/circle-house-addendum.tpl.md
```markdown
---
fragment_name: "circle-house-addendum"
version: "v2025.01"
purpose: "Addendum for studio services performed at Circle House Studios or its partners"
---

## CIRCLE HOUSE STUDIO ADDENDUM

... (full fragment content) ...
```

## 10. rules/mapping.json
```json
{
  "artist-services:beat-lease": {
    "template": "scope__artist-services.md",
    "addenda": ["fragments/payment-terms.tpl.md"],
    "source_reference": "Audio Jones Offer Matrix 2025"
  },
  "artist-services:exclusive-production": {
    "template": "msa__studio-services.md",
    "addenda": [
      "fragments/payment-terms.tpl.md",
      "fragments/whop-funded.tpl.md"
    ],
    "source_reference": "Audio Jones Offer Matrix 2025"
  },
  "artist-services:graphic-design": {
    "template": "scope__artist-services.md",
    "addenda": ["fragments/payment-terms.tpl.md"],
    "source_reference": "Audio Jones Offer Matrix 2025"
  },
  "circle-house:studio-session": {
    "template": "msa__studio-services.md",
    "addenda": ["fragments/circle-house-addendum.tpl.md"],
    "source_reference": "Client Delivery Module 2025"
  },
  "marketing:automation-package": {
    "template": "saa__automation-services.md",
    "addenda": ["fragments/payment-terms.tpl.md"],
    "source_reference": "Marketing Automation Module 2025"
  },
  "ai-optimization:consulting": {
    "template": "saa__automation-services.md",
    "addenda": ["fragments/payment-terms.tpl.md"],
    "source_reference": "AI Optimization Module 2025"
  },
  "data-intelligence:subscription": {
    "template": "saa__automation-services.md",
    "addenda": ["fragments/payment-terms.tpl.md"],
    "source_reference": "Data Intelligence Module 2025"
  },
  "client-delivery:retainer": {
    "template": "msa__agency-standard.md",
    "addenda": ["fragments/payment-terms.tpl.md"],
    "source_reference": "Client Delivery Module 2025"
  }
}
```

## 11. rules/variables.json
```json
{
  "company_legal_name": "AJ DIGITAL LLC",
  "company_brand_name": "Audio Jones",
  "company_address": "20028 NW 64th PL, Hialeah, FL 33015",
  "company_email": "dev@audiojones.com",
  "default_currency": "USD",
  "default_payment_terms": "Due on receipt",
  "default_jurisdiction": "State of Florida, USA",
  "year": "2025",
  "signatory_name": "Tyrone Alexander Nelms",
  "signatory_title": "Founder & Managing Director",
  "version_reference": "v2025.01",
  "license": "Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)"
}
```

## 12. rules/validations.json
```json
{
  "required_fields": [
    "client_legal_name",
    "client_email",
    "effective_date",
    "offer_code"
  ],
  "format_validations": {
    "client_email": "email",
    "effective_date": "date"
  },
  "rules": {
    "offer_code_must_exist_in_mapping": true
  }
}
```

## 13. automation/esignaturesio-hook.md
```markdown
# eSignatures.io Hook — AJ DIGITAL LLC
Version: v2025.01
Purpose: Standardize how contracts generated from `ajd-contract-library` are sent for signature.

... (full content from earlier message) ...
```

## 14. automation/stripe-whop-sync.md
```markdown
# Stripe / Whop Sync — AJ DIGITAL LLC
Version: v2025.01
Purpose: Keep payment status from Whop (front door) and Stripe (processor) aligned with contract issuance and delivery.

... (full content from earlier message) ...
```

## 15. .github/release.yml
```yaml
# AJ DIGITAL LLC — Contract Library Release Configuration
changelog:
  categories:
    - title: "🚀 New Features"
      labels:
        - enhancement
        - new-template
        - new-fragment
        - automation
        - integration
      collapse_after: 5
    - title: "🧰 Improvements"
      labels:
        - improvement
        - refactor
        - update
        - performance
        - documentation
      collapse_after: 5
    - title: "🐞 Fixes"
      labels:
        - bug
        - patch
        - fix
      collapse_after: 5
    - title: "⚙️ Infrastructure & Automation"
      labels:
        - ci
        - workflow
        - script
        - rules
        - mapping
        - validation
      collapse_after: 5
    - title: "🧾 Documentation & Repo Maintenance"
      labels:
        - docs
        - readme
        - changelog
        - guidelines
        - version
      collapse_after: 5
  exclude:
    labels:
      - ignore
      - wip
      - draft
  include:
    - "CHANGELOG.md"
  template: |
    # 🏷️ Release: ${{version}}

    ## Summary
    This release is automatically generated from **CHANGELOG.md** and reflects the latest validated version of AJ DIGITAL LLC’s contract templates and automation logic.

    ## 📦 Highlights
    ${{changelog}}
```

## 16. .github/workflows/release.yml
```yaml
name: AJD Contract Library Release
on:
  push:
    tags:
      - "v*"
permissions:
  contents: write
jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repo
        uses: actions/checkout@v4
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 20
      - name: Install deps (optional)
        run: |
          if [ -f package.json ]; then
            npm install
          else
            echo "No package.json found, skipping npm install."
          fi
      - name: Validate rules
        run: |
          if [ -f scripts/validate-rules.js ]; then
            node scripts/validate-rules.js
          else
            echo "⚠️ scripts/validate-rules.js not found, skipping validation."
          fi
      - name: Build dist package
        run: |
          mkdir -p dist
          cp -r templates dist/templates || true
          cp -r smart-templates dist/smart-templates || true
          cp -r rules dist/rules || true
          cp -r automation dist/automation || true
          cp -r docs dist/docs || true
          cp VERSION.md dist/VERSION.md || true
          cp CHANGELOG.md dist/CHANGELOG.md || true
      - name: Create dist archive
        run: |
          cd dist
          zip -r ../ajd-contract-library-${{ github.ref_name }}.zip .
          cd ..
      - name: Create GitHub Release
        id: create_release
        uses: softprops/action-gh-release@v2
        with:
          tag_name: ${{ github.ref_name }}
          name: "AJD Contract Library ${{ github.ref_name }}"
          body_path: CHANGELOG.md
          files: |
            ajd-contract-library-${{ github.ref_name }}.zip
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

## 17. scripts/render-template.ps1
```powershell
param(
  [string]$TemplatePath,
  [string]$VariablesPath = "./rules/variables.json",
  [string]$OutFile = "./dist/contract-output.md"
)
$tpl = Get-Content $TemplatePath -Raw
$vars = Get-Content $VariablesPath | ConvertFrom-Json
foreach ($prop in $vars.PSObject.Properties) {
  $placeholder = "{{" + $prop.Name + "}}"
  $tpl = $tpl -replace [regex]::Escape($placeholder), $prop.Value
}
$tpl | Out-File $OutFile -Encoding utf8
Write-Output "Rendered → $OutFile"
```

## 18. scripts/validate-rules.js
```javascript
const fs = require("fs");
const path = require("path");
function readJSON(p) {
  return JSON.parse(fs.readFileSync(path.join(process.cwd(), p), "utf8"));
}
const mapping = readJSON("rules/mapping.json");
const variables = readJSON("rules/variables.json");
const missing = [];
for (const [key, value] of Object.entries(mapping)) {
  if (!value.template) {
    missing.push(`Mapping "${key}" is missing "template"`);
  }
}
if (missing.length) {
  console.error("Validation failed:\n" + missing.join("\n"));
  process.exit(1);
} else {
  console.log("rules/mapping.json OK");
}
console.log("rules/variables.json OK");
```

## 19. scripts/build-release.ps1
```powershell
param(
  [switch]$Tag,
  [switch]$Push,
  [switch]$BumpPatch
)
if (-not (Test-Path ".git")) {
  Write-Error "❌ Not in a git repository. Run from repo root."
  exit 1
}
if (-not (Test-Path "VERSION.md")) {
  Write-Error "❌ VERSION.md not found."
  exit 1
}
$rawVersion = (Get-Content VERSION.md -Raw).Trim()
if ($BumpPatch) {
  if ($rawVersion -notmatch '^v\d+(\.\d+)*$') {
    Write-Error "❌ VERSION.md not in expected format."
    exit 1
  }
  $versionCore = $rawVersion.Substring(1)
  $parts = $versionCore.Split('.')
  if ($parts.Count -eq 2) {
    $parts += "01"
  } else {
    $last = [int]$parts[-1]
    $last++
    $parts[-1] = ("{0:00}" -f $last)
  }
  $newVersionCore = ($parts -join '.')
  $newVersion = "v$newVersionCore"
  Set-Content -Path VERSION.md -Value $newVersion -Encoding utf8
  Write-Host "🔼 VERSION bumped: $rawVersion -> $newVersion"
  $rawVersion = $newVersion
}
$version = $rawVersion
if (Test-Path "dist") { Remove-Item -Recurse -Force "dist" }
New-Item -ItemType Directory -Force -Path "dist" | Out-Null
$pathsToCopy = @("templates","smart-templates","rules","automation","docs")
foreach ($p in $pathsToCopy) {
  if (Test-Path $p) { Copy-Item -Recurse -Force $p "dist/$p" } else { Write-Host "⚠️ Skipping missing path: $p" }
}
@("README.md","CHANGELOG.md","VERSION.md") | ForEach-Object { if (Test-Path $_) { Copy-Item $_ "dist/$_" } }
$zipName = "ajd-contract-library-$version.zip"
if (Test-Path $zipName) { Remove-Item $zipName -Force }
Compress-Archive -Path "dist/*" -DestinationPath $zipName
Write-Host "✅ Archive created: $zipName"
if ($Tag) {
  git tag $version
}
if ($Tag -and $Push) {
  git push origin $version
}
Write-Host "🎉 Done."
```

## 20. CHANGELOG.md
```markdown
# AJ DIGITAL LLC — Contract Library Changelog
Follows Semantic Versioning: **MAJOR.MINOR.PATCH**

## [v2025.01] – 2025-11-04
**Initial Launch Release**
- Established core repository structure
- Added foundational smart templates
- Added fragments
- Added automation blueprints
- Added documentation
- Implemented `/rules/` JSON logic
- Integrated initial GitHub Actions workflows
- Established version & changelog management
```

## 21. VERSION.md
```markdown
v2025.01
```

