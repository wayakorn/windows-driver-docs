---
title: Audio Endpoints, Properties and Events
description: Audio Endpoints, Properties and Events
ms.assetid: ffc5834f-30c8-40b5-b57b-fe784331690c
keywords:
- audio events WDK
- audio properties WDK
- port drivers WDK audio , properties
- port drivers WDK audio , events
- adapter drivers WDK audio , events
- adapter drivers WDK audio , properties
- audio properties WDK , about audio properties
- audio events WDK , about audio events
- WDM audio properties WDK
- WDM audio events WDK
- WDM audio properties WDK , about audio properties
- KS properties WDK audio
- KS events WDK audio
- properties WDK audio
- pins WDK audio
ms.author: windowsdriverdev
ms.date: 04/20/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
---

# Audio Endpoints, Properties and Events


## <span id="audio_properties_and_events"></span><span id="AUDIO_PROPERTIES_AND_EVENTS"></span>


The PortCls system driver supports a subset of the intrinsic operations that are described in [KS Properties, Events, and Methods](https://msdn.microsoft.com/library/windows/hardware/ff567673).

The port drivers in Portcls.sys support properties and events by providing handlers for some property and event requests and by forwarding other requests to the miniport drivers' handlers.

The current implementations of the WaveCyclic, WavePci, MIDI, and DMus port drivers provide the following:

-   Support for properties on a filter and its pins and nodes

-   Support for events on pins and nodes but not for events on the filter

A client can specify the handle to a filter or pin instance as the target for a property or event request. A request for a node property or event specifies a node ID in addition to a filter or pin handle. For more information, see [Filter, Pin, and Node Properties](filter--pin--and-node-properties.md).

The Topology port driver provides the following:

-   Support for properties on a filter and its nodes

-   Support for events on nodes

The pins on a topology filter represent hardwired connections that exist permanently and thus cannot be instantiated or deleted.

None of the port drivers provide support for methods on either the filter or its pins and nodes. The port drivers never handle method requests, and they never forward these requests to miniport drivers for handling.

Audio adapter drivers support some or all of the following standard property sets:

[KSPROPSETID\_AC3](https://msdn.microsoft.com/library/windows/hardware/ff537436)

[KSPROPSETID\_Acoustic\_Echo\_Cancel](https://msdn.microsoft.com/library/windows/hardware/ff537438)

[KSPROPSETID\_Audio](https://msdn.microsoft.com/library/windows/hardware/ff537440)

[KSPROPSETID\_DirectSound3DBuffer](https://msdn.microsoft.com/library/windows/hardware/ff537447)

[KSPROPSETID\_DirectSound3DListener](https://msdn.microsoft.com/library/windows/hardware/ff537449)

[KSPROPSETID\_DrmAudioStream](https://msdn.microsoft.com/library/windows/hardware/ff537481)

[KSPROPSETID\_General](https://msdn.microsoft.com/library/windows/hardware/ff566576)

[KSPROPSETID\_Hrtf3d](https://msdn.microsoft.com/library/windows/hardware/ff537482)

[KSPROPSETID\_Jack](https://msdn.microsoft.com/library/windows/hardware/ff537484)

[KSPROPSETID\_Pin](https://msdn.microsoft.com/library/windows/hardware/ff566584)

[KSPROPSETID\_Synth](https://msdn.microsoft.com/library/windows/hardware/ff537486)

[KSPROPSETID\_Synth\_Dls](https://msdn.microsoft.com/library/windows/hardware/ff537488)

[KSPROPSETID\_TopologyNode](https://msdn.microsoft.com/library/windows/hardware/ff537491)

All audio drivers support the **KSPROPSETID\_Audio** property set.

Some audio adapter drivers support the following event set:

[KSEVENTSETID\_AudioControlChange](https://msdn.microsoft.com/library/windows/hardware/ff537122)

In addition, audio adapter drivers are free to provide property handlers for other property sets that are defined in header file Ksmedia.h. Drivers can also define and support their own custom property and event sets, but only an application that knows about a custom property or event will be able to use it.

This section discusses audio-specific properties and events. It contains the following topics:

[Audio Property Requests](audio-property-requests.md)

[Filter, Pin, and Node Properties](filter--pin--and-node-properties.md)

[Audio Property Handlers](audio-property-handlers.md)

[Basic Support Queries for Audio Properties](basic-support-queries-for-audio-properties.md)

[Audio Endpoint Builder Algorithm](audio-endpoint-builder-algorithm.md)

[Dynamic Subdevice Registration and Unregistration](dynamic-subdeviceregistration-and-unregistration.md)

[Exposing Multichannel Nodes](exposing-multichannel-nodes.md)

[Pin Category Property](pin-category-property.md)

[Friendly Names for Audio Endpoint Devices](friendly-names-for-audio-endpoint-devices.md)

[Audio Position Property](audio-position-property.md)

[Pin Data-Range and Intersection Properties](pin-data-range-and-intersection-properties.md)

[Jack Description Property](jack-description-property.md)

[Microphone Array Geometry Property](microphone-array-geometry-property.md)

[Hardware Events](hardware-events.md)

 

 


--------------------
[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20[audio\audio]:%20Audio%20Endpoints,%20Properties%20and%20Events%20%20RELEASE:%20%287/18/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")


