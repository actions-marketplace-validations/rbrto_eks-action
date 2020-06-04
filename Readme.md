# eks-kubectl

Access your EKS cluster via `kubectl` in a Github Action. just ensure you have `eks:ListCluster` and `eks:DescribeCluster` rights on your user.

## Example configuration

You just need to supply your AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, the region your cluster is
in and it's name

```yaml
jobs:
  jobName:
    name: Update deploy
    runs-on: ubuntu-latest
    steps:
      # --- #
      - name: Deploy to EKS
        uses: rbrto/eks-action@master
        with:
          aws_access_key_id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws_secret_access_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws_region: ${{ secrets.AWS_REGION }}
          cluster_name: ${{ secrets.CLUSTER_NAME }}
          args: apply -f deployment.yaml
      # --- #
```
