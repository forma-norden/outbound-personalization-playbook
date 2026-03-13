# Ecosystem: outbound-personalization-playbook

How this repo connects to the rest of the Forma Norden GTM library.

## Works With

| Repo | Relationship | When to use together |
|------|-------------|---------------------|
| ``cold-email-copy-playbook`` | Parallel | Personalization hooks from here slot into the email templates provided over there. |
| ``signal-based-list-building-workflow`` | Upstream | Signals detected in the list-building stage provide the raw data required for personalization here. |
| ``clay-claude-code-skill-pack`` | Downstream | The prompts and logic defined in this playbook are physically executed inside Clay. |
| ``linkedin-profile-dm-conversion-playbook`` | Parallel | Personalization strategies apply identically to cold LinkedIn DMs as they do to email. |

## Suggested Skill Chains

1. Email Campaign Build: ``list-icp-definition`` (target list) > ``personalization-campaign-playbook`` (strategy) > ``personalization-at-scale-operator`` (build hooks) > ``copy-btl-practitioner-messaging`` (finish email)
2. Manual Enterprise ABM: ``personalization-research-framework`` (research) > ``personalization-hook-builder`` (write intro) > ``copy-atl-executive-messaging`` (finish pitch)
