# lattepandalpha_bigsur
LattePanda Alpha 864 (m3-7y30) Opencore configuration for macOS Big Sur

![systeminfo](https://raw.githubusercontent.com/knuxyl/lattepandalpha_bigsur/main/systeminfo.png)

macOS Big Sur
LattePanda Alpha 864 (m3-7y30)

Working

	HDMI Audio
	3.5mm Audio
	m.2 Intel WiFi AX200 and Bluetooth
	m.2 SATA Storage
	Graphics Hardware Acceleration
	
Not Working

	iMessage (due to invalid serial)
Not Tested

	Realtek RTL8111 Ethernet (Should Work)
	Onboard Intel WiFi and Bluetooth (Should work)
	DRM playback in Safari (ie Netflix)

For DRM playback in a browser, use Chromium archive found at chromium.woolyss.com by Marmaduke that is ungoogled and includes widevine and all-codecs

You will need to generate your own platform information and put it into config.plist. Visit opencore’s guide on this process.


Files For DEBUG and RELEASE

	RealtekRTL8111-V2.4.2
	IntelBluetoothFirmware-v2.0.1
	AirportItlwm_v2.0.0_stable_BigSur.kext
	IntelBluetoothFirmware-v2.0.1

Files For DEBUG

	OpenCore-0.7.4-DEBUG
	WhateverGreen-1.5.4-DEBUG
	AppleALC-1.6.5-DEBUG
	Lilu-1.5.6-DEBUG
	VirtualSMC-1.2.7-DEBUG

Files For RELEASE

	OpenCore-0.7.4-RELEASE
	WhateverGreen-1.5.4-RELEASE
	AppleALC-1.6.5-RELEASE
	Lilu-1.5.6-RELEASE
	VirtualSMC-1.2.7-RELEASE

AMLs Loaded

	SSDT-EC.aml
	SSDT-PLUG.aml
	SSDT-USBX.aml
	SSDT-HPET.aml
	
Kext Load Order

	Lilu
	VirtualSMC
	WhateverGreen
	AppleALC
	RealtekRTL8111
	Airportltlwm
	SMCProcessor
	SMCSuperIO
	IntelBluetoothInjector
	IntelBluetoothFirmware
	
Boot Flags

RELEASE

	alcid=17
DEBUG

	-v keepsyms=1 debug=0x100 alcid=17

Changes made are found here
https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/kaby-lake.html#starting-point


This is what was used to fix graphics

	<key>DeviceProperties</key>
	<dict>
		<key>Add</key>
		<dict>
			<key>PciRoot(0)/Pci(0x02,0)</key>
			<dict>
				<key>AAPL,ig-platform-id</key>
				<data>
				AAAbWQ==
				</data>
				<key>framebuffer-con1-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-con1-alldata</key>
				<data>
				AQUKAAAIAACHAQAAAgQKAAAIAACHAQAA/wAAAAEAAAAg
				AAAA
				</data>
				<key>framebuffer-fbmem</key>
				<data>
				AACQAA==
				</data>
				<key>framebuffer-patch-enable</key>
				<data>
				AQAAAA==
				</data>
				<key>framebuffer-stolenmem</key>
				<data>
				AAAwAQ==
				</data>
			</dict>
		</dict>
		<key>Delete</key>
		<dict/>
	</dict>
