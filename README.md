# AJ DIGITAL LLC — Contract & Agreements Library

This repository is the **single source of truth** for all agreements, MSAs, NDAs, scopes, and addenda used across:
- AudioJones.com offers
- Circle House Digital / studio services
- Artist / creator services
- Whop-backed or funded offers
- Automation-delivered services (n8n, MailerLite, Vercel functions)

Other repositories **consume** this one. They should not duplicate contracts.

## Goals

1. Keep all contract language in one versioned place
2. Give automations a predictable way to pick the right agreement
3. Allow smart templates with variables (`{{client_legal_name}}`, `{{service_tier}}`, etc.)
4. Enforce quality with GitHub Actions validation
5. Publish compiled contracts on release tags

## Repository Structure

- `/docs/` - Documentation and authoring guidelines
- `/templates/` - Static contract templates
- `/smart-templates/` - Dynamic templates with variables
- `/rules/` - Mapping, variables, and validation configurations
- `/automation/` - Integration with eSignatures and payment systems
- `/scripts/` - Template rendering and build utilities
- `/dist/` - Compiled contracts ready for use

## Quick Start

### For Legal/Ops Teams
1. Review `/docs/authoring-guidelines.md` for contract creation standards
2. Use existing templates in `/smart-templates/` as starting points
3. Test template rendering with `/scripts/render-template.ps1`
4. Submit changes via pull request for review

### For Developers  
1. Load `/rules/mapping.json` to select appropriate contract
2. Use `/rules/variables.json` for template variable substitution
3. Validate with `/rules/validations.json` requirements
4. Integrate with automation workflows in `/automation/`

## Integration Points

- **billing-and-payments-repo** → Contract selection based on payment events
- **client-delivery-module** → Contract generation for new clients
- **audiojones-offerings** → Contract mapping for each offer
- **eSignatures.io** → Electronic signature workflow
- **Stripe/Whop** → Payment-triggered contract delivery

## Version

v2025.01