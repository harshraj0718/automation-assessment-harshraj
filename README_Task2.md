# Task 2: GitHub Morning Brief

This n8n workflow searches GitHub for popular `topic:n8n` repositories, selects the five with the most stars, enriches each result, and sends a digest through Gmail. It is saved inactive so it will not run on a schedule or accept production webhook traffic until enabled.

## Workflow

- **Search:** `GET https://api.github.com/search/repositories?q=topic:n8n&sort=stars&order=desc&per_page=20`
- **Enrichment:** `GET https://api.github.com/repos/{owner}/{repo}` for each selected repository.
- **Transformation:** the Code nodes validate results, sort by star count, keep five, and format each repository’s name, description, stars, language, and link.
- **Branch:** the IF node sends the digest with a high-signal subject when the leading repository has at least 1,000 stars; otherwise it uses the standard subject.
- **Failure handling:** API and processing errors go to an execution log and a Gmail alert. Failed digest sends go to a separate error logger.
- **Notification:** Gmail nodes use a placeholder recipient; configure your own Gmail credential and address after importing. The Gmail API is enabled in its Google Cloud project. OAuth secrets remain in n8n.

## Deliverables and verification

- `Task2_Workflow_HarshRaj.json` — sanitized n8n workflow export with placeholder recipient and no credential references or secrets.
- `Task2_Workflow_Canvas_HarshRaj.png` — final canvas, successful path, Gmail success output, and `SENT` label.
- `Task2_Successful_Execution_HarshRaj.png` — successful n8n execution record.

The test webhook completed the GitHub search, selected five repositories, enriched them, evaluated the high-signal branch, and sent the digest. Gmail returned a message ID and `SENT` label. The successful execution took 2.628 seconds. The workflow is inactive and ready to import or review.
