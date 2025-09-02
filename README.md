# 🎵 n8n Spotify Mood Playlist

Create a Spotify playlist from a mood prompt using **n8n**, **OpenAI**, and the **Spotify Web API**.  
This tutorial project is designed for **beginners**, with step-by-step setup and an importable n8n workflow.

---

## ✨ What You’ll Build
- Input a mood (e.g., *“soft focus, late-night coding”*).
- AI generates track search terms.
- n8n fetches tracks from Spotify’s API.
- A playlist is created automatically in your Spotify account.

---

## 📂 Repo Contents

README.md
spotify_mood_playlist.workflow.json
.env.example
assets/
   ├── demo.gif
   └── screenshots/
        ├── n8n-flow.png
        ├── playlist-result.png
        └── tally-form.png   (optional)



---

## 🚀 Getting Started

### 1. Prerequisites
- n8n (Cloud or self-hosted)
- Spotify Developer account  
- OpenAI API key (if using AI step)

---

### 2. Spotify App Setup
1. Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard).  
2. **Create App** → copy **Client ID** and **Client Secret**.  
3. Add Redirect URI:  
   - n8n Cloud: `https://<your-subdomain>.n8n.cloud/rest/oauth2-credential/callback`  
   - Self-hosted: `https://<your-domain>/rest/oauth2-credential/callback`  
4. Enable scopes:  
   - `playlist-modify-public`  
   - `playlist-modify-private`  
   - `user-read-email` (optional)  

---

### 3. Environment Variables
Copy `.env.example` → `.env` and fill in:
```bash
SPOTIFY_CLIENT_ID=
SPOTIFY_CLIENT_SECRET=
SPOTIFY_REDIRECT_URI=
OPENAI_API_KEY=           # optional
SPOTIFY_USERNAME=

⚠️ Do not commit .env with real secrets. Add it to .gitignore.
4. Import the Workflow
In n8n: Workflows → Import from File → select spotify_mood_playlist.workflow.json.
Create Spotify OAuth2 credentials in n8n using your app’s ID, Secret, and Redirect URI.
Attach credentials to the Spotify nodes.
If using AI: attach OpenAI credentials to the OpenAI node.
5. Run the Flow
Trigger manually (or via Webhook).
Enter your mood text.
OpenAI (optional): converts mood into search phrases.
Spotify nodes:
Get access token
Search tracks
Create playlist (title = mood + date)
Add tracks
Check Spotify: your new playlist should be live!
🛠 Troubleshooting
401 Unauthorized: re-run OAuth and confirm redirect URI matches.
No tracks: loosen search terms, add market=US.
Add tracks error: ensure you’re passing spotify:track:... URIs, not raw IDs.
