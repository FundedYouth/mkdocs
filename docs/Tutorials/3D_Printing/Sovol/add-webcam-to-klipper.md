---
title: Add Webcam to Klipper
date: 2024-02-27
authors:
  - ryan_jones
---

# Add a Webcam to Klipper on The Sovol SV07 Plus

![](https://fundedyouth.org/wp-content/uploads/2024/02/add-webcam-to-klipper-on-sv07-plus.webp){width="500", loading-lazy}

There are two options to adding a webcam to a 3D Printer with Klipper installed. Plug it in and hope it automatically works or install ustreamer through the Linux terminal which is what this tutorial covers. <!-- more -->

## Instructions

1) Turn on your Sovol SV07-Plus with Klipper.

2) Maker sure the printer is connected to the network

3) Get your printer IP address

!!! info "The Linux Terminal Noob"

    If you are new to using a terminal/command prompt. The $: in the code examples should NOT be copied. It’s just referencing the current directory.

4) SSH into the Printer.

```bash
# User: mks
# Pass: makerbase

$: ssh mks@0.0.0.0
```

!!! note "Are you sure (Terminal) prompt"

    - Are you sure you want to continue connecting (yes/no/[fingerprint])?
    - Type: **yes**

5) When prompted type in your password. If you are on Windows using a GUI based tool, you’ll likely supply the password before attempting to connect.

!!! info "Typing passwords in Linux"

    For those you who are new to the Linux terminal. You might notice that you don't see your password when typing it. This is an intentional security measure built into the Linux operating system.

    You just have to know the password. Type it in, don't add any spaces, and click the **Enter/return** key to continue.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*4EHp9chXQgra7XUd7J1vTg.png)

6) Change into the `Klipper` directory

```bash
# cd = change directory

$ cd klipper
```

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*UEd0T_RG2byidJzWWCEnWQ.png)

7) Clone/download the ustreamer repo from [GitHub.com](https://github.com/pikvm/ustreamer) using the following command:

```bash
$ git clone --depth=1 https://github.com/pikvm/ustreamer
```

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*nyHI1vNAGQyQJJhddEN9EA.png)

8) Change into the `ustreamer` directory.

```bash
$ cd ustreamer
```

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*FV4j90CjwOLTjQ6Pw4ZjnQ.png)

9) Type `make` and press enter key to execute the process.

```bash
$ make
```

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*kJyKQNgfQBm-X31M_ThcSw.png)

10) Connect your USB camera. Must be type: `USB-A`. You can disconnect from your SSH connection. This is no longer needed.

11) Open your browser and go to your printer’s IP address. In this scenario, Mainsail is loaded.

12) In the top-right of the **Mainsail Web Application** locate the settings gear icons.

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*KC9uV5Kvphw0SfX29Y3rIw.png)

13) In the pop-up window. Scroll-down through the left-side navigation and select **WEBCAMS** and then click on **ADD WEBCAM**

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*1a7b-yEoKWs2_nxPmwXc9g.png)

14) After clicking `ADD WEBCAM`, the **Create Webcam** window will appear. Provide a **Name** for the webcam.

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*arPD9eg-i0rg6D2nT9WP8w.png)

15) Now under the **Service** drop-down select: **MJPEG-Streamer**.

!!! warning "Do not confuse this with the (experimental) option."

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*zEFqIRUwscqgt_rFz5VL4Q.png)

16) You will see a white screen appear. Nothing will show up until restart the printer.

17) Click the **SAVE WEBCAM** text.

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*-V96zM12nsPfRh9zNVMmug.png)

18) Close out of the **Interface Settings**.

19) Back in the top-right of the `Mainsail` web application. Click on the **Power Button** then under the drop-down under **Host Control** select: `Reboot`

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*LYILwaFbqWbwDtHUDXDtsw.png)

20) Once you click the `Reboot` your web app screen will display a **Connection failed** notice while it restarts.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*cgVyjpRhwToyBGfhtPMhmQ.png)

21) After the printer restarts, log back into `Mainsail` and you should see a live Webcam.

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*fshltZzAsdtd_oCaqTLP0Q.png)

> Yay! Your done. Have some fun!

!!! Quote "Original Archived Article by Sovol"

    https://web.archive.org/web/20230812220606/https://sovol3d.com/blogs/news/how-to-use-external-camera-on-sv07