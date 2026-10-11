# Raspberry-PI-home-server

A self-hosted server on a Raspberry Pi (Raspberry Pi OS, ARM64) using Docker and CasaOS, with a 1.8 TB external drive for storage.

Services
Nextcloud: file storage
Jellyfin: media streaming
Immich: photo backup
Ollama + Open WebUI: local LLM running on CPU
Tailscale: secure remote access
Storage design

App-private data (configs, databases) lives under /mnt/storage/appdata/, separate from user-facing media under /mnt/storage/shared/. This keeps databases out of media folders and lets containers be rebuilt without losing data.

What I learned

CasaOS defaulted app data to the microSD card, so I edited the Nextcloud compose file to point its volumes at the external drive and verified the mounts with docker inspect. There was many instances where the server would stop working and I didn't know why so I learned how to diagnose the errors. I also learned alot obout how to navigate the linux terminal. The biggest thing I learned though was how to edit .yaml files to create new docker containers and assign the IP of different apps.
