# GitHub Assignment Notifications

GitHub can notify you in Slack when you have been assigned a PR to review.
It can also give you a scheduled summary of PRs that still need your attention.

## Setup Slack with Github
The GitHub app for Slack is preinstalled in the workspace.
1. Visit https://github.com/settings/reminders and click the pencil next to your
organization.
2. From the slack workspace dropdown select `+ Add Slack workspace` or the `Authorize Slack workspace` button.
3. You'll be redirected to Slack to authorize access. Click `Allow`
4. After getting redirected back to GitHub, visit the organization page again.
5. From here you can select the Slack organization to receive notifications in and configure notifications.

## Configuring Notifications and Summaries
The top section of the scheduled reminders form lets you set the days of the week, and time to receive summaries.

You should check "Review requests assigned to you" to receive only notifications for pull requests directly assigned to
you. It's not recommended to select "Review requests assigned to your team".

## Setting Yourself Busy
GitHub lets you set yourself busy to stop receiving notifications, and stop
automatic code review assignments for you.

To set yourself busy:
1. Click on your avatar in GitHub
2. In the sidebar click on "Set status"
3. In the modal that comes up check "Busy"
4. Optionally select when the status will be cleared
5. Click "Set status"