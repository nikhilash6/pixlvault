# PixlVault

PixlVault is a local picture library server for organizing, filtering, and reviewing large image collections.

It provides:
- A browser-based interface
- Fast metadata and tag filtering
- Smart score sorting
- Character and set organization
- Local storage of your library data

PixlVault runs on your machine and serves the UI at a local web address.

## Install PixlVault

Choose one installation method.

### Option 1: Windows installer

Use this if you want the easiest setup on Windows.

1. Go to the GitHub Releases page for this repository.
2. Download the latest Windows installer `.exe`.
3. Run the installer.
4. Start PixlVault Server from the Start Menu shortcut.
5. Open your browser to `http://localhost:9537`.

## Option 2: Install from PyPI

Use this if you already have Python and want a pip install.

Requirements:
- Python 3.10 or newer

Install:

```bash
pip install pixlvault
```

Run:

```bash
pixlvault-server
```

Then open:

```text
http://localhost:9537
```

## Option 3: Clone and run manually

Use this if you want to run from source.

Requirements:
- Python 3.10 or newer
- Node.js 20 or newer
- npm

Steps:

```bash
git clone <your-repo-url>
cd pixlvault

python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
# source .venv/bin/activate

pip install --upgrade pip
pip install -e .

cd frontend
npm ci
npm run build
cd ..

pixlvault-server
```

Then open:

```text
http://localhost:9537
```

## Installing plugins

PixlVault supports built-in plugins and user plugins.

- Built-in plugins are in `image-plugins/built-in/`.
- User plugins are in `image-plugins/user/`.
- Start from `image-plugins/user/plugin_template.py`.

To add your own plugin:

1. Copy `image-plugins/user/plugin_template.py` to a new `.py` file in `image-plugins/user/`.
2. Rename the plugin class and plugin id.
3. Implement the plugin `run()` method.
4. Restart PixlVault Server.

`plugin_template.py` is ignored by plugin discovery and will not be loaded as a plugin.

## First run and data location

On first run, PixlVault creates a user config directory and stores:
- Server config
- Database
- Imported media files

If you need to use a custom config path:

```bash
python -m pixlvault.app --server-config "C:\path\to\server-config.json"
```

## Updating PixlVault

### PyPI install

```bash
pip install --upgrade pixlvault
```

### Source install

Pull latest changes, rebuild frontend, and reinstall:

```bash
git pull
cd frontend
npm ci
npm run build
cd ..
pip install -e .
```

## Troubleshooting

- If the page does not load, confirm the server process is running.
- If port `9537` is in use, set a different port in your server config file.
- If frontend assets are missing, rebuild frontend with `npm run build` and restart the server.
