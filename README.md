# Docker Image API Caller GitHub Action

This GitHub Action receives a Docker image and makes an API call to an external service with the image information.

## Inputs

- `docker-image`: The Docker image to process (required)
- `api-endpoint`: The external API endpoint to call (required)
- `api-key`: API key for authentication (required)

## Usage

```yaml
name: Process Docker Image

on:
 push:
  branches: [main]

jobs:
 process-image:
  runs-on: ubuntu-latest
  steps:
   - uses: actions/checkout@v4

   - name: Call API with Docker Image
     uses: ./
     with:
      docker-image: "my-registry/my-image:latest"
      api-endpoint: "https://api.example.com/process-image"
      api-key: ${{ secrets.API_KEY }}
```

## Example

This action will:

1. Receive the Docker image name
2. Make a POST request to the specified API endpoint
3. Include the Docker image information in the request body
4. Use the provided API key for authentication

## Security Notes

- Always store your API key as a GitHub Secret
- Use HTTPS endpoints for API calls
- Consider adding input validation for the Docker image format
