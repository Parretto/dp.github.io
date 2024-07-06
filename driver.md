---
layout: page
title: Driver
permalink: /driver/
nav_order: 5
---

# Driver
<br>
The DisplayPort IP requires a processor to setup the core. This can be any processor. 
A DisplayPort driver (prt_dp_drv) is provided for this task. 

## API

This section provides information about the driver API.

<br>

**prt_dp_set_base**
```
    description: Sets the DisplayPort peripheral base address.
    syntax: void prt_dp_set_base (prt_dp_ds_struct *dp, uint32_t base);
    parameters: 
        dp - pointer to DP peripheral
        base - base address
    returns:
        none
```

<br>

**prt_dp_set_cb**
```
    description: Sets the DisplayPort call back handlers. 
    syntax: void prt_dp_set_cb (prt_dp_ds_struct *dp, prt_dp_cb_type cb_type, void *cb_handler);
    parameters: 
        dp - pointer to DP peripheral
        cb_type - call back type 
            PRT_DP_CB_HPD       - Hot Plug Detect
            PRT_DP_CB_STA       - Status
            PRT_DP_CB_TRN       - Link training
            PRT_DP_CB_PHY_RATE  - Link rate change 
            PRT_DP_CB_PHY_VAP   - Link voltage and pre-emphasis change 
            PRT_DP_CB_LNK       - Link
            PRT_DP_CB_VID       - Video    
            PRT_DP_CB_MSA       - Main stream attributes 
        cb_handler - pointer to call back handler
    returns:
        none
```

<br>

**prt_dp_rom_init**
```
    description: Loads the DisplayPort IP ROM code.
    syntax: void prt_dp_rom_init (prt_dp_ds_struct *dp, uint32_t len, uint8_t *rom);
    parameters:
        dp - pointer to DP peripheral
        len - length of ROM code
        rom - pointer to ROM code
    returns:
        none
```

<br>

**prt_dp_ram_init**
```
    description: Loads the DisplayPort IP RAM code.
    syntax: void prt_dp_ram_init (prt_dp_ds_struct *dp, uint32_t len, uint8_t *ram);
    parameters:
        dp - pointer to DP peripheral
        len - length of RAM code
        ram - pointer to RAM code
    returns:
        none
```

<br>

**prt_dp_init**

```
    description: Initialize the DisplayPort IP.
    syntax: void prt_dp_init (prt_dp_ds_struct *dp, uint8_t id);
    parameters:
        dp - pointer to DP peripheral
        id - DP peripheral identifier 
    returns:
        none
```
<br>

**prt_dp_ping**
```
    description: Checks if the DisplayPort IP is alive.
    syntax: uint8_t prt_dp_ping (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        Returns true when the peripheral is running. 
```

<br>

**prt_dp_set_lnk_max_rate**
```
    description: Sets the maximum supported rate.
    syntax: void prt_dp_set_lnk_max_rate (prt_dp_ds_struct *dp, uint8_t rate);
    parameters:
        dp - pointer to DP peripheral
        rate - maximum link rate
            PRT_DP_PHY_LINERATE_1620 - RBR (1.62 Gbps)
            PRT_DP_PHY_LINERATE_2700 - HBR (2.7 Gbps)
            PRT_DP_PHY_LINERATE_5400 - HBR2 (5.4 Gbps)
            PRT_DP_PHY_LINERATE_8100 - HBR3 (8.1 Gbps)
    returns: 
        none
```

<br>

**prt_dp_set_lnk_max_lanes**
```
    description: Sets the maximum supported lanes.
    syntax: void prt_dp_set_lnk_max_lanes (prt_dp_ds_struct *dp, uint8_t lanes);
    parameters:
        dp - pointer to DP peripheral
        lanes - maximum number of lanes (1, 2, or 4)
    returns: 
        none
```
<br>

**prt_dp_cfg**
```
    description: Configures the DisplayPort IP.
    syntax: uint8_t prt_dp_cfg (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        none
```
<br>

**prt_dp_sta**
```
    description: Reads the DisplayPort IP status.
    syntax: void prt_dp_sta (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        none
```

<br>

**prt_dptx_msa_set**
```
    description: Sets the Main Stream Attributes (MSA)
    syntax: uint8_t prt_dptx_msa_set (prt_dp_ds_struct *dp, prt_dp_tp_struct *tp, uint8_t stream);
    parameters:
        dp - pointer to DP peripheral
        tp - pointer to timing parameters
        stream - stream number (0 or 1)
    returns: 
        Returns true when the video is started, else false.
```

<br>

**prt_dp_vid_str**
```
    description: Starts the video stream.
    syntax: uint8_t prt_dp_vid_str (prt_dp_ds_struct *dp, uint8_t stream);
    parameters:
        dp - pointer to DP peripheral
        stream - stream number (0 or 1)
    returns: 
        Returns true when the video is started, else false.
```

<br>

**prt_dp_vid_stp**
```
    description: Stops the video stream.
    syntax: uint8_t prt_dp_vid_stp (prt_dp_ds_struct *dp, uint8_t stream);
    parameters:
        dp - pointer to DP peripheral
        stream - stream number (0 or 1)
    returns: 
        Returns true when the video is started, else false.
```

<br>

**prt_dp_hpd_get**
```
    description: Gets HPD status.
    syntax: uint8_t prt_dp_hpd_get (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        PRT_DP_HPD_UNPLUG - HPD deasserted
        PRT_DP_HPD_PLUG - HPD asserted
        PRT_DP_HPD_IRQ - HPD interrupt
```

<br>

**prt_dp_get_phy_rate**
```
    description: Gets requested PHY linerate.
    syntax: uint8_t prt_dp_get_phy_rate (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        PRT_DP_PHY_LINERATE_1620 - 1.62 Gbps
        PRT_DP_PHY_LINERATE_2700 - 2.7 Gbps
        PRT_DP_PHY_LINERATE_5400 - 5.4 Gbps
        PRT_DP_PHY_LINERATE_8100 - 8.1 Gbps
```

<br>

**prt_dp_get_phy_volt**
```
    description: Gets requested PHY voltage level.
    syntax: uint8_t prt_dp_get_phy_volt (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        0 - 400 mV
        1 - 600 mV
        2 - 800 mV
        3 - 1200 mV
```

<br>

**prt_dp_get_phy_pre**
```
    description: Gets requested PHY preamble level.
    syntax: uint8_t prt_dp_get_phy_volt (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        0 - 0 dB
        1 - 3.5 dB
        2 - 6.0 dB
        3 - 9.5 dB
```

<br>

**prt_dp_lnk_req_ok**
```
    description: Informs the driver that the requested line rate and/or voltage and preamble levels has been set.
    syntax: void prt_dp_lnk_req_ok (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        none
```

<br>

**prt_dp_is_trn_pass**
```
    description: Check if the link training passed.
    syntax: uint8_t prt_dp_is_trn_pass (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        Returns true when the trainig passed, else false.
```

<br>

**prt_dp_is_lnk_up**
```
    description: Check if the link is up.
    syntax: uint8_t prt_dp_is_lnk_up (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        Returns true when the link is up, else false.
```

<br>

**prt_dp_get_lnk_act_lanes**
```
    description: Gets number of active lanes.
    syntax: uint8_t prt_dp_get_lnk_act_lanes (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
         1, 2 or 4
```

<br>

**prt_dp_get_lnk_act_rate**
```
    description: Gets active line rate
    syntax: uint8_t prt_dp_get_lnk_act_rate (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        PRT_DP_PHY_LINERATE_1620 - 1.62 Gbps
        PRT_DP_PHY_LINERATE_2700 - 2.7 Gbps
        PRT_DP_PHY_LINERATE_5400 - 5.4 Gbps
        PRT_DP_PHY_LINERATE_8100 - 8.1 Gbps
```

<br>

**prt_dp_get_lnk_reason**
```
    description: Gets reason why the link went down.
    syntax: uint8_t prt_dp_get_lnk_reason (prt_dp_ds_struct *dp, uint8_t stream);
    parameters:
        dp - pointer to DP peripheral
        stream - stream number (0 or 1)
    returns: 
        PRT_DP_LNK_DOWN_PHY - No video clock
        PRT_DP_LNK_DOWN_CLK - Link went down
        PRT_DP_LNK_DOWN_CDR - CDR loss of lock
        PRT_DP_LNK_DOWN_SCRM - Scrambler loss of lock
        PRT_DP_LNK_DOWN_TRN - Training error
        PRT_DP_LNK_DOWN_VID - Video error
        PRT_DP_LNK_DOWN_HPD - HPD
        PRT_DP_LNK_DOWN_IDLE - Link idle
        PRT_DP_LNK_DOWN_TO - Time out (evaluation)
```

<br>

**prt_dp_is_vid_up**
```
    description: Check if the video stream is up.
    syntax: uint8_t prt_dp_is_vid_up (prt_dp_ds_struct *dp, uint8_t stream);
    parameters:
        dp - pointer to DP peripheral
        stream - stream number (0 or 1)
    returns: 
        Returns true when the video is up, else false.
```

<br>

**prt_dp_get_vid_reason**
```
    description: Gets reason why the video stream went down.
    syntax: uint8_t prt_dp_get_vid_reason (prt_dp_ds_struct *dp, uint8_t stream);
    parameters:
        dp - pointer to DP peripheral
        stream - stream number (0 or 1)
    returns: 
        PRT_DP_VID_DOWN_CLK - No video clock
        PRT_DP_VID_DOWN_LNK - Link went down
        PRT_DP_VID_DOWN_ERR - Error
        PRT_DP_VID_DOWN_IDLE - Video idle
```

<br>

**prt_dprx_hpd**
```
    description: Sets DPRX HPD.
    syntax: uint8_t prt_dprx_tp_get (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
        hpd - hot plug state 
            PRT_DP_HPD_UNPLUG - HPD deassert
            PRT_DP_HPD_PLUG - HPD assert
            PRT_DP_HPD_IRQ - HPD interrupt
    returns: 
        Returns true when successful, else false.
```

<br>

**prt_dprx_tp_get**
```
    description: Gets DPRX timing parameters.
    syntax: prt_dp_tp_struct prt_dprx_tp_get (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        pointer to timing parameters
```

<br>

**prt_dprx_edid_wr**
```
    description: Write EDID data.
    syntax: uint8_t prt_dprx_edid_wr (prt_dp_ds_struct *dp);
    parameters:
        dp - pointer to DP peripheral
    returns: 
        Returns true when successful, else false.
```

<br>


---

## Callbacks

The callback functions are used by the driver to signal the application about an event. 
These functions are registered using the prt_dp_set_cb function. 

The diagram show the DP states and the callbacks. 

{% include figure.html image="/images/dp_callbacks.svg" caption="Figure 1: DP callbacks"%}

<br>

**dptx_hpd_cb**
```
    description: The function is called when a DPTX HPD event occured.
```

<br>

**dp_phy_rate_cb**
```
    description: The function is called when the policy maker is requesting a new line rate.
```

<br>

**dptx_phy_vap_cb**
```
    description: The function is called when the policy maker is requesting to update the voltage swing and preamble levels.
```

<br>

**dptx_phy_vap_cb**
```
    description: The function is called when the policy maker is requesting to update the voltage swing and preamble levels.
```

<br>

**dp_trn_cb**
```
    description: The function is called when the policy maker is requesting to update the voltage swing and preamble levels.
```

<br>

**dp_lnk_cb**
```
    description: The function is called when the link status is updated.
```

<br>

**dp_vid_cb**
```
    description: The function is called when the video stream status is updated.
```

<br>

**dprx_msa_cb**
```
    description: The function is called when the DPRX received updated main stream attributes.
```

