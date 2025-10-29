# GitHub Labels Configuration

This document describes the labels that should be created for this repository. Labels help organize and categorize issues for the FIS 25-26 experiment.

## How to Create Labels

Labels need to be created through GitHub's web interface or API. To create them manually:

1. Go to the repository on GitHub: https://github.com/Alex-GF/fis-25-26
2. Click on "Issues" tab
3. Click on "Labels" button
4. Click "New label" for each label below

Alternatively, use the GitHub CLI:
```bash
gh label create "SPACE" --description "Issues related to SPACE framework" --color "0075ca"
gh label create "SPHERE" --description "Issues related to SPHERE architecture" --color "0075ca"
gh label create "bug" --description "Something isn't working" --color "d73a4a"
gh label create "enhancement" --description "New feature or request" --color "a2eeef"
gh label create "documentation" --description "Improvements or additions to documentation" --color "0075ca"
gh label create "doubt" --description "Questions about concepts or usage" --color "d876e3"
gh label create "duplicate" --description "This issue or pull request already exists" --color "cfd3d7"
gh label create "good first issue" --description "Good for newcomers" --color "7057ff"
gh label create "help wanted" --description "Extra attention is needed" --color "008672"
gh label create "invalid" --description "This doesn't seem right" --color "e4e669"
gh label create "question" --description "Further information is requested" --color "d876e3"
gh label create "wontfix" --description "This will not be worked on" --color "ffffff"
```

## Required Labels

### Technology-Specific Labels

| Label Name | Color | Description |
|------------|-------|-------------|
| SPACE | `#0075ca` (blue) | Issues related to the SPACE (Self-adaPtive Application based on Cost Estimation) framework |
| SPHERE | `#0075ca` (blue) | Issues related to the SPHERE (Self-adaPtive arcHitecture based on Economic-driven Reconfiguration Engine) architecture |

### Issue Type Labels

| Label Name | Color | Description |
|------------|-------|-------------|
| bug | `#d73a4a` (red) | Something isn't working correctly |
| enhancement | `#a2eeef` (light blue) | New feature or improvement request |
| documentation | `#0075ca` (blue) | Improvements or additions to documentation |
| doubt | `#d876e3` (purple) | Questions about concepts, usage, or experiments |
| duplicate | `#cfd3d7` (gray) | This issue or pull request already exists |

### Additional Helpful Labels

| Label Name | Color | Description |
|------------|-------|-------------|
| good first issue | `#7057ff` (purple) | Good for newcomers to the project |
| help wanted | `#008672` (green) | Extra attention is needed from instructors or TAs |
| invalid | `#e4e669` (yellow) | This doesn't seem right or is incorrectly filed |
| question | `#d876e3` (purple) | Further information is requested |
| wontfix | `#ffffff` (white) | This will not be worked on |

## Label Usage Guidelines

### For Students

- **SPACE**: Use when your issue specifically involves the SPACE framework code, configuration, or behavior
- **SPHERE**: Use when your issue relates to SPHERE architecture or infrastructure
- **bug**: Use when something is broken or not working as documented
- **enhancement**: Use to suggest new features or improvements to existing functionality
- **documentation**: Use when you find unclear documentation or want to suggest documentation improvements
- **doubt**: Use for conceptual questions about self-adaptation, pricing models, or how to use the technology
- **duplicate**: Usually applied by instructors when an issue has already been reported

### For Instructors/TAs

- Apply appropriate component labels (SPACE/SPHERE) to help categorize issues
- Use **good first issue** for simple problems that new students can help solve
- Use **help wanted** for issues that need immediate attention
- Mark **duplicate** issues and link to the original
- Use **invalid** for incorrectly filed issues, with explanation
- Apply **wontfix** with justification when an issue won't be addressed

## Creating Labels via GitHub CLI

If you have the GitHub CLI installed, you can create all required labels with these commands:

```bash
# Technology-specific labels
gh label create "SPACE" -d "Issues related to SPACE framework" -c "0075ca"
gh label create "SPHERE" -d "Issues related to SPHERE architecture" -c "0075ca"

# Issue type labels
gh label create "bug" -d "Something isn't working" -c "d73a4a"
gh label create "enhancement" -d "New feature or request" -c "a2eeef"
gh label create "documentation" -d "Improvements or additions to documentation" -c "0075ca"
gh label create "doubt" -d "Questions about concepts or usage" -c "d876e3"
gh label create "duplicate" -d "This issue or pull request already exists" -c "cfd3d7"

# Additional helpful labels
gh label create "good first issue" -d "Good for newcomers" -c "7057ff"
gh label create "help wanted" -d "Extra attention is needed" -c "008672"
gh label create "invalid" -d "This doesn't seem right" -c "e4e669"
gh label create "question" -d "Further information is requested" -c "d876e3"
gh label create "wontfix" -d "This will not be worked on" -c "ffffff"
```

## Creating Labels via GitHub API

You can also use the GitHub API to create labels programmatically:

```bash
# Set your repository details
OWNER="Alex-GF"
REPO="fis-25-26"
TOKEN="your_github_token"

# Function to create a label
create_label() {
    curl -X POST \
      -H "Authorization: token $TOKEN" \
      -H "Accept: application/vnd.github.v3+json" \
      https://api.github.com/repos/$OWNER/$REPO/labels \
      -d "{\"name\":\"$1\",\"description\":\"$2\",\"color\":\"$3\"}"
}

# Create all required labels
create_label "SPACE" "Issues related to SPACE framework" "0075ca"
create_label "SPHERE" "Issues related to SPHERE architecture" "0075ca"
create_label "bug" "Something isn't working" "d73a4a"
create_label "enhancement" "New feature or request" "a2eeef"
create_label "documentation" "Improvements or additions to documentation" "0075ca"
create_label "doubt" "Questions about concepts or usage" "d876e3"
create_label "duplicate" "This issue or pull request already exists" "cfd3d7"
create_label "good first issue" "Good for newcomers" "7057ff"
create_label "help wanted" "Extra attention is needed" "008672"
create_label "invalid" "This doesn't seem right" "e4e669"
create_label "question" "Further information is requested" "d876e3"
create_label "wontfix" "This will not be worked on" "ffffff"
```

## Verification

After creating labels, verify them by visiting:
https://github.com/Alex-GF/fis-25-26/labels

You should see all the labels listed with their descriptions and colors.
