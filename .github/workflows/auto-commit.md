name: 21f3002034@ds.study.iitm.ac.in
on:
  schedule:
    - cron: "0 3 * * *" # Runs daily at 3:00 AM UTC (Adjust as needed)

  workflow_dispatch: # Allows manual triggering

jobs:
  auto-commit:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Configure Git
        run: |
          git config --global user.name "github-actions[bot]"
          git config --global user.email "21f3002034@ds.study.iitm.ac.in"

      - name: Make a Change
        run: |
          echo "Last update: $(date)" > last_update.txt
          git add last_update.txt
          git commit -m "Automated commit: $(date)" || echo "No changes to commit"

      - name: Push Changes
        run: git push
