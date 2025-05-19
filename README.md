# pihole-allowlist-teen-bedtime

# Pi-hole Allowlist for Controlled Access

This repository hosts a custom `allowlist.txt` file for use with [Pi-hole](https://pi-hole.net/). It's designed to be used in a "default deny" setup — where all domains are blocked by default for a specific client or group — and only specific allowed domains are permitted.

## 🛠️ Use Case

Ideal for scenarios like:
- Allowing a child or teen's device access to only music apps (e.g. Spotify) during bedtime.
- Locking down a guest device to approved domains only.
- Creating a minimal-Internet mode during specific hours.

## 📄 File Format

- One domain per line.
- Wildcards (e.g. `*.spotify.com`) are supported by Pi-hole when used in the web interface or Gravity update.
- Comments and empty lines are ignored.

Example:
spotify.com
*.spotify.com
scdn.co


## 📦 How to Use

1. **Add this list to Pi-hole**  
   - Pi-hole Admin > *Group Management* > *Lists*
   - Add the raw file URL:  
     `https://raw.githubusercontent.com/NullPD/pihole-allowlist-teen-bedtime/main/allowlist.txt`
   - Assign it only to the appropriate group (e.g. `SpotifyOnly`).

2. **Block everything else**  
   - Add a wildcard domain block (`.*`) for the group you want to restrict.
   - This ensures only domains in this allowlist will resolve.

3. **Update gravity** after making changes:  
   ```bash
   pihole -g
