# Quick + Dirty Networking Setup Guide

To play multiplayer, one person acts as the host server, the other player connects to the host as clients.

## 1. Hosting a Game (the server)

1. If you want to play custom maps, make sure all players have the levels downloaded (with the same names).
2. Start the game → Select 'Online Multiplayer'.
3. Pick a **port** (default rn: 8012, rest of the doc assumes this).  (IP address field is irrelevant if you're a host).
4. Hit **host**.  
5. The game starts listening on `0.0.0.0:PORT` (i.e., all interfaces).  
6. Tell your friends your **public ip** and **selected port** (Google “what is my ip” and you can find a site to tell you - if you're playing within a LAN you want to find out your **local ip**'**).

Then wait for people to connect.

## 2. connecting as a client

1. Start the game → Select 'Online Multiplayer'.
1. The host will tell you what **ip-address** and **port** to enter, so do that.
4. Hit **connect**.  
5. Fingers crossed/etc.

## 3. port forwarding (aka the reason most players will give up)

Unless you’re on the same local network, the host probably needs to forward a port.

### 3.1 What to do

1. Open your router’s admin page (usually `192.168.0.1` or `192.168.1.1` — yes, it’s stupid).  
2. Login.  
3. Find **port forwarding**, **virtual server**, or **NAT** settings.  
4. Add a rule:  
   - **protocol:** TCP+UDP
   - **external port:** 8012  
   - **internal port:** 8012  
   - **internal ip:** the host machine’s local address (will look something like `192.168.1.23`)  
5. Hit save!

Now outside clients can actually reach the game instead of screaming into the digital void.

### 3.2 Testing that it actually works

- on the host: go to `https://canyouseeme.org/` and check port `8012`.  
  if it says **success**, you’re golden.  
  if it says **connection refused** or **timeout**, something in your network stack hates you.

### 3.3 common faceplants

- Wrong port (lol).  
- Host forwarding TCP only.  
- Router silently blocks everything bc “security”.  
- Windows firewall throwing a tantrum → allow the game for both private + public networks.  
- cgNAT from your isp (you lose; only vpn or hosting elsewhere fixes this).

## 4 That's it!

Fingers crossed it works.  Problems for this kind of server/hosting stuff tend to be generic, so what works for one game will work for others. Google is your friend! 