# Replicate Model

This is a Cog model for Replicate. It's set up with GitHub Actions to automatically build and push to Replicate.

## Setup Instructions

### Prerequisites

- A Replicate account
- A GitHub repository (create one and push this code)
- Docker (for local testing)

### Step 1: Get your Replicate CLI Auth Token

1. Go to [replicate.com/auth/token](https://replicate.com/auth/token)
2. Copy the token to your clipboard

### Step 2: Add your Replicate token as a GitHub Secret

1. Go to your GitHub repository
2. Click **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret**
4. Name it `REPLICATE_CLI_AUTH_TOKEN`
5. Paste in your token from Step 1

### Step 3: Push your code to GitHub

```bash
git init
git add .
git commit -m "Initial commit: Add Cog model with GitHub Actions"
git branch -M main
git remote add origin <your-github-repo-url>
git push -u origin main
```

### Step 4: Test the workflow manually

1. Go to your repository on GitHub
2. Click **Actions** tab
3. Click **Push to Replicate** workflow
4. Click **Run workflow**
5. Enter your model name (e.g., `yourusername/model-name`)
6. Click **Run workflow**

## Local Development

### Install Cog

```bash
sudo curl -o /usr/local/bin/cog -L https://github.com/replicate/cog/releases/latest/download/cog_$(uname -s)_$(uname -m)
sudo chmod +x /usr/local/bin/cog
```

### Test locally

```bash
# Build the model
cog build

# Run predictions
cog predict -i text="Hello world"
```

### Push to Replicate manually

```bash
# Authenticate
export REPLICATE_API_TOKEN="your-token-here"

# Push your model
cog push r8.im/yourusername/model-name
```

## Next Steps

1. Implement your model logic in `predict.py`
2. Update `cog.yaml` with your specific dependencies
3. Add your Python dependencies to `requirements.txt`
4. Test locally before pushing to Replicate

## Resources

- [Cog Documentation](https://github.com/replicate/cog)
- [Replicate Documentation](https://replicate.com/docs)
- [GitHub Actions Guide](https://docs.github.com/en/actions)

