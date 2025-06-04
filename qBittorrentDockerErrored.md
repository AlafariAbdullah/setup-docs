# qBittorrent Docker — Torrents Stuck in "Errored" State

While self-hosting qBittorrent in Docker on my NAS, I ran into an issue where every torrent I added ended up stuck in an `Errored` state with 0% progress and no tracker activity.


---

## The Problem

Even though:
- The Web UI loaded fine via Tailscale
- I could see a healthy number of peers (e.g., 45)
- DHT, PeX, and LSD all showed as "Working"
- DNS and internet were reachable from the container

No torrent ever started downloading. The status just stayed like this:

```
Status: Errored
Progress: 0.0%
Trackers: Not contacted yet
```

---

## What I Tried First

I wanted to make sure this wasn’t a DNS or network issue. Since I recently added Pi-hole to my network, I checked whether DNS worked correctly using:

```bash
nslookup google.com 192.168.1.1
```

Worked perfectly.

Then I tested network access from inside the container:

```bash
sudo docker exec -it qbittorrent ping google.com
```

Also successful — packets were getting through. So the network and DNS were clearly not the issue.

---

## Finding the Real Cause

After ruling out network issues, I started suspecting a file system permission problem.

I checked what the container sees for its `/downloads` folder:

```bash
sudo docker exec -it qbittorrent ls -ld /downloads
```

Here’s what I got:

```
d--------- 1 abc abc ... /downloads
```

This told me that although the directory existed, it had no permissions — not even read or execute. The qBittorrent container had no access to the path it was supposed to write downloaded files to.

The kicker? On the host, the folder looked completely fine:

```bash
ls -ld "/volume2/Media Server/qbittorrentDownloads"
drwxrwxrwx+ 1 Admin1 users ...
```

But Docker’s user mapping didn’t translate that correctly inside the container.

---

## How I Fixed It

On the NAS host, I updated the ownership and permissions of the downloads directory so that the user inside the container (mapped by PUID 1026 and PGID 100) could actually use it:
```bash
sudo chown -R 1026:100 "/volume2/Media Server/qbittorrentDownloads"
sudo chmod -R 775 "/volume2/Media Server/qbittorrentDownloads"
```
Check [LinuxServer.io](https://docs.linuxserver.io/general/understanding-puid-and-pgid/) and [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-permissions-linux) for further details regarding `PUID`, `PGID`, `chown`, and `chmod`.

Then restarted the container:

```bash
sudo docker restart qbittorrent
```

---

## What Happened After

As soon as the container restarted, the torrents that were stuck in "Errored" started working immediately.

```
Status: Downloading
```

Trackers connected. DHT found peers. Files started downloading as expected.

---

## Final Thoughts

If you’re running into similar symptoms—torrents stuck at 0% with no real activity, and everything else looks fine—don’t just trust the host’s folder permissions. Check what the container actually sees.

Look *inside* the container for permission issues, especially when using bind mounts with Docker and mapped users like `PUID`/`PGID`.

Sometimes the issue isn’t with the internet, tracker, or torrent file at all — it’s simply that qBittorrent lacks write access to the disk.

## 🖤 Credits

Written by [Abdullah Alafari](https://github.com/AlafariAbdullah)

Connect with me on [Linkedin](www.linkedin.com/in/alafari-abdullah)
