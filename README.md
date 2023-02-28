## Fluxo de Deploy Github Actions + AWS

### Exemplo com GO

```
    name: "Deploy"

    on:
      push:
        branches:
          - develop
    
    permissions:
      id-token: write
      contents: read
    
    jobs:
      deploy-go:
        uses: maelsilva96/fluxo_reutilizavel/github/workflows/reusable-deploy-lambda.yml
        with:
          s3: "meu-s3-bucket-nome"
          repository: ${{ github.event.repository.full_name }}
          repository_name: ${{ github.event.repository.name }}
          version: ${{ github.run_id }}
        secrets:
          account_id: ${{ secrets.AWS_ACCOUNT_ID }}
          region: ${{ secrets.AWS_REGION }}
          role: ${{ secrets.AWS_ROLE }}
```