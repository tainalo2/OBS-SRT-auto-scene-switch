# OBS SRT auto scene switch
A simple system to switch to a "lost signal" scene when your SRT connection is cut. Based on OBS WebSocket logs.

# Summary
  - Prerequesites
  - Technical explanation
  - Installation : alone web page
    - OBS Docking
    - OBS configuration
  - Installation : over Node Red
    - Node Red import
    - Nodes configuration
    - OBS configuration
  - Credit

# Prerequesites
  - OBS with obs-websocket plugin : https://github.com/Palakis/obs-websocket
  - Optional : If you chose the Node Red installation : A nodered server (free low code GUI for NodeJS server) https://nodered.org/

# Technical explanation
  The objective is to switch to a scene that is displaying classic "Signal lost, we will be back" when your SRT source is cutting. Moreover, it's automatically switching to the main scene when SRT signal is back.
  To do this we will checking OBS Websocket logs. SRT source is consider as a media, so when signal is lost we have a message of "MediaEnded". But we can't use "MediaStarted" tag because it's instantly next to the lost signal to continuely listen it. But SRT source goes to 0\*0 when no signal, and to 1920\*1080 when signal back, and it's notified by OBS WS !
  
# Installation : alone web page
  - OBS Docking
   - Download the git-file : "main.html" OR use the URL : https://common.taitools.fr/srtSwitch
   - In OBS go to "Display" > "Docks" > "personal internet docks..." > create a new dock with path file to "main.html" OR URL : https://common.taitools.fr/srtSwitch
   - Complete the form and click "LINK TO OBS"
   - Let this dock open everytime
  - OBS configuration
   - To automatically switch, your SRT source need to be in all your OBS scenes !

# Installation : over Node Red
  - Nodered import
   - Copy the content of the git file : "nodered_flow.json"
   - In nodered dashboard go to options and "Import"
   - Paste the file content and click "Import"
  - Nodes configuration
   - In nodes "OBS WS IN" and OUT change the configuration to your OBS websocket adress
   - In nodes "CHECK SOURCE" replace "SRT Source" by your srt source name in OBS
   - In nodes "Set scene BACK" replace "BACK" by your back scene name in OBS
   - In nodes "Set scene MAIN" replace "MAIN" by your main scene name in OBS
  - OBS configuration
   - To automatically switch, your SRT source need to be in all your OBS scenes !

# Credit
Create by tainalo2 : french streamer on twitch every week day from 07H to 09H (Paris hours)
Inspired by : https://github.com/loopy750/SRT-Stats-Monitor
All my links here : https://linktr.ee/tainalo2
  
