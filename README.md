# AchieveCxO membership inquiries

The right-edge tab opens the membership form. Submissions are saved to SQLite and appear in the password-protected team inbox at `/admin/inquiries`.

## Preview in GitHub Codespaces

Copy these files into the repository root. Include `.gitignore`. From that folder, run these commands in the default Bash terminal.

```bash
read -rsp "Set a strong inbox password: " INQUIRY_ADMIN_PASSWORD
echo
export INQUIRY_ADMIN_PASSWORD
python3 server.py
```

Open forwarded port **8000** and keep its visibility **Private** while testing. Submit a sample inquiry. Open the same preview URL with `/admin/inquiries` appended. Sign in as **membership** with the password you entered. If the browser retains the login, close that browser session or use a private window to test signed-out access.

## Go live

Use a Python host with HTTPS and persistent disk storage. Run the WSGI application `server:application` with a production server such as Gunicorn. Set `INQUIRY_ADMIN_PASSWORD` as a hosting secret and `INQUIRY_DB_PATH` to a file on the persistent volume. Restrict read access to the database and its backups, and configure request rate limits at the public proxy for submissions and staff sign-in. The local preview server is for development.

GitHub can store the project source. GitHub Pages only serves static files, so it cannot receive inquiries or run the inbox. Submissions appear in the web inbox without sending an email notification.
