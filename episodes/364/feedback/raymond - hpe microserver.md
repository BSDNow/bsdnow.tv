Greetings,

You recently had an emailer ask about the HPE Microserver Gen10. I just wanted to let you and the person know that they shouldn't have must trouble with the server unless he tries to use the AMD version of PCI Passthrough. I needed this in my situation and when I turned it on via the virtualization option in the BIOS, the onboard controller for the hard drives required a driver (which only runs in windows) or you would have to have raid setup on the controller. I got around this by adding my own LSI controller in IT mode. Other than that, I would encourage  the Gen 10 with the x3421 processor as it's the only one with 4 cores. 

Thanks for the podcast!