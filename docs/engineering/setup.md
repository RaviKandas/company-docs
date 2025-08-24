# Development Environment Setup

Get your development environment ready in 30 minutes or less!

## Prerequisites

Before starting, ensure you have:
- [ ] GitHub account with 2FA enabled
- [ ] Slack access
- [ ] Admin rights on your machine

## Step 1: Install Core Tools

### macOS
```bash
# Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install essential tools
brew install git node python docker
brew install --cask visual-studio-code
```

### Linux (Ubuntu/Debian)
```bash
# Update package manager
sudo apt update && sudo apt upgrade -y

# Install essential tools
sudo apt install git nodejs npm python3 docker.io
```

### Windows
1. Install [WSL2](https://docs.microsoft.com/en-us/windows/wsl/install)
2. Install [Docker Desktop](https://www.docker.com/products/docker-desktop)
3. Install [Node.js](https://nodejs.org/)
4. Install [Git](https://git-scm.com/download/win)

## Step 2: Configure Git

```bash
# Set your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@company.com"

# Set up SSH key
ssh-keygen -t ed25519 -C "your.email@company.com"
cat ~/.ssh/id_ed25519.pub
# Add this key to GitHub: Settings → SSH Keys
```

## Step 3: Clone Repositories

```bash
# Create workspace
mkdir ~/workspace && cd ~/workspace

# Clone main repos
git clone git@github.com:yourcompany/frontend.git
git clone git@github.com:yourcompany/api.git
git clone git@github.com:yourcompany/infrastructure.git
```

## Step 4: Frontend Setup

```bash
cd ~/workspace/frontend

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env.local

# Start development server
npm run dev
# Visit http://localhost:3000
```

## Step 5: Backend Setup

```bash
cd ~/workspace/api

# Set up Python virtual environment
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up database
docker-compose up -d postgres
python manage.py migrate

# Run the server
python manage.py runserver
# API available at http://localhost:8000
```

## Step 6: IDE Configuration

### VS Code Extensions
Install these recommended extensions:
- ESLint
- Prettier
- GitLens
- Docker
- Python
- Code Spell Checker

### Settings
```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

## Step 7: Verify Everything Works

Run our verification script:
```bash
curl -s https://setup.company.com/verify.sh | bash
```

Or manually check:
- [ ] Frontend loads at localhost:3000
- [ ] API responds at localhost:8000/health
- [ ] Can commit and push to a test branch
- [ ] Docker is running
- [ ] All tests pass

## Common Issues

### Port Already in Use
```bash
# Find what's using the port
lsof -i :3000  # macOS/Linux
netstat -ano | findstr :3000  # Windows

# Kill the process
kill -9 <PID>
```

### Permission Denied (npm)
```bash
# Fix npm permissions
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.zshrc
source ~/.zshrc
```

### Docker Not Starting
1. Ensure virtualization is enabled in BIOS
2. Restart Docker Desktop
3. Check Docker daemon: `docker ps`

## Additional Setup

### Database GUI
- [TablePlus](https://tableplus.com/) (recommended)
- [DBeaver](https://dbeaver.io/) (free alternative)

### API Testing
- [Postman](https://www.postman.com/)
- [Insomnia](https://insomnia.rest/)

### Monitoring
- Install [Datadog Agent](https://docs.datadoghq.com/agent/) (optional)
- Set up local logging aggregation

## Next Steps

✅ Setup complete! Now you can:
1. Read our [Code Standards](standards.md)
2. Check the [current sprint](https://jira.company.com/sprint)
3. Join #engineering-newbies on Slack
4. Schedule 1:1 with your tech lead
5. Start with a "good first issue"

## Need Help?

- **Setup issues**: #engineering-help on Slack
- **Missing access**: #it-help on Slack
- **Documentation**: Update this page via PR!

Happy coding! 🚀