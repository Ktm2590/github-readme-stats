# Use

## [Server](https://github.com/yihong0618/github-readme-stats-server)

- Update your README

Add a comment to your `README.md` like this:

```md
<!--START_SECTION:my_github-->
<!--END_SECTION:my_github-->
```

- Write your own `yml` file

[Sample](https://github.com/yihong0618/2021)

```yml
name: GitHub README STATS

on:
  workflow_dispatch:
  schedule:
    - cron: "0 0 * * *"
  push:
    branches:
      - main

env:
  GITHUB_NAME: Ktm2590
  GITHUB_EMAIL: zouzou0208@gmail.com
  STARED_NUMBER: 10

jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: My GitHub Status
        uses: Ktm2590/github-readme-stats@main
        with:
          # if you also want to send TELE
          TELEGRAM_TOKEN: ${{ secrets.TELE_TOKEN }}
          TELEGRAM_CHAT_ID: ${{ secrets.TELE_CHAT_ID }}
          STARED_NUMBER: ${{ env.STARED_NUMBER }}

      - name: Push README
        uses: github-actions-x/commit@v2.6
        with:
          github-token: ${{ secrets.G_T }}
          # In this example, you can also use the ${{ secrets.GITHUB_TOKEN }} variable 
          # Permissions for the GITHUB_TOKEN : https://docs.github.com/en/free-pro-team@latest/actions/reference/authentication-in-a-workflow#permissions-for-the-github_token
        
          # If you need more precise Token permission control , you can create a personal access token and set it as a secret in your repository .
          commit-message: "Refresh README (GITHUB STATUS)"
          files: README.md
          rebase: "true"
          name: ${{ env.GITHUB_NAME }}
          email: ${{ env.GITHUB_EMAIL }}
```



# [My example](https://github.com/yihong0618/2021).

## My GitHub Status
<img align="middle" src="https://github-readme-stats-1.yihong0618.vercel.app/api?username=Ktm2590&show_icons=true&&&hide_title=true" />

<!--START_SECTION:my_github-->

<!--END_SECTION:my_github-->
