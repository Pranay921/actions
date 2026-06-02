name: ghcr-push

on:
  push:

jobs:
  docker:
    runs-on: ubuntu-latest

    permissions:
      contents: read
      packages: write

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Login to GHCR
        uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Build Image
        run: |
          docker build -t ghcr.io/${{ github.repository }}/myapp:latest .

      - name: Push Image
        run: |
          docker push ghcr.io/${{ github.repository }}/myapp:latest