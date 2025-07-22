# matrix: 
- Run jobs across different versions/environments

# schedule
```
on:
  schedule:
    - cron: '0 0 * * *'
```
# mannual trigger
```
Manually trigger: on:
  workflow_dispatch:
    inputs:
      environment:
        type: choice
        options: [dev, prod]
```
# tag based deployment
```
steps:
  - name: Checkout code at specified tag
    uses: actions/checkout@v3
    with:
      ref: ${{ github.event.inputs.tag }}
```

# How to debug workflows
- Use ACTIONS_RUNNER_DEBUG and ACTIONS_STEP_DEBUG

# Why cashes are important?
- Dependencies (like node_modules, pip, or .m2) don’t need to be reinstalled every time.
- Saves time for repeated CI runs.
- Useful when external services are slow or rate-limited.
- Especially on GitHub-hosted runners where minutes are limited.
- You use fewer resources for the same job.
