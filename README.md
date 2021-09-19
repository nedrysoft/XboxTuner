# Xbox One Tuner Enclosure

This repositiry contains the STL files for printing a set of enclosures that will house multiple Xbox One tuners and provide a convenient means of easily connecting these to a host system.

![The electronics enclosure & 2 tuner enclosures with tuners evenly spread across the system](https://user-images.githubusercontent.com/55795671/133000789-60b35d42-c18e-4df9-8c8a-8cf211a29434.jpg)

## Why so many tuners?!

Here in the UK the major channels are broadcast on 6 MUXES, because this number is reasonably low, we can use a tuner per mux and pre-tune each tuner to a specific mux, the upside of this is that when a TV channel is requested, the tuning is already completed and the stream can be provided very quickly.

Another benefit of operating a system in this manner is that there is no limitation on the number of or combination of channels that can be recorded at the same time, every station could technically be recorded at the same time.

## Print Information

It is recommended that the files are printed using a filament that is not likely to soften under heat.  Using PETG filament or better should ensure that structural integrity is maintained.

There are no specific requirements for printing (support free!), it should be obvious when loading the STL files into your slicer as to the correct orientation that the parts should be printed in.

## The Design

The system was designed to allow the system to be neatly packaged in an attractive way and to prevent a neverending cycle of cable spaghetti, the tuners obviously need to accept a feed from the antenna, but apart from that a single 5.5mm by 2.5mm power jack to provide power to the USB hubs and a single USB-C connector to connect the hubs to the main PC.

### The Tuner Enclosure

Each tuner enclosure can hold 5 Xbox One tuners, a tuner "blank" is provided if not all slots are required.  There is sufficent space inside each enclosure to coil the cables into small enough stubs to pass through just enough cable to connect the tuners to the hubs.

Each enclosure includes a hole either side to allow cables to enter and exit the enclosure, this allows enclosures to be butted up to each other and have the actual USB connectivity completely hidden.

![The empty bottom section of the tuner enclosure](https://user-images.githubusercontent.com/55795671/133004180-a5be49f2-b912-40e7-993b-60510635fab3.jpg)

Each tuner is held firmly in place by an appropriately sized compartment and lips are used to ensure that the tuners stay inside the enclosure, so there is no worry of pulling the system apart by tugging on a wire!

For any position that is not to be populated, a "tuner blank" model is provided that matches the dimensions of the real tiner (it is not exactly the same, it has been reduced in size in places to prevent filament waste).

![The enclosure with 3 tuners and 2 "blanks"](https://user-images.githubusercontent.com/55795671/133004182-ad52cce5-ea14-435c-bc45-2620bc8bfac1.jpg)

The previous image shows a tuner enclosure with 3 tuners and 2 blanks, in the UK I am only interested in 6 MUXES, therefore I opted in my configuration to equally space the tuners across 2 enclosures rather than 5 in one enclosure and a final enclosure with 1 tuner and 4 blanks, this is a personal preference and you can choose to use any spacing your desire.

An M3 threaded insert is located in each corner of the bottom enclosure part to allow a strong connection to the top case.

### The Electronics Enclosure 

The electronics enclosure ties the whole system together, it consists of a number of other sub assemblies to provide a robust and easy to connect system.

![The main enclosure, power jack, USB connector and internal cradle](https://user-images.githubusercontent.com/55795671/133004166-f3b20400-5495-4203-b0f7-0c75c6423c8d.jpg)

#### The Cradle

The cradle part helps keep the USB hubs in the correct location, as the wiring is completed they may move around and become difficult to work with, so the cradle stops these problems from occuring and provide a controlled way to route cables.

![The cradle](https://user-images.githubusercontent.com/55795671/133004171-e015eb2c-8bef-4f30-9433-58805924ac02.jpg)

#### The USB clamp

As I used USB 3 hubs in the design, I wanted to make sure that the path from the hubs back to the host is at USB 3 speeds, I was unable to find a reasonably priced panel mount connector so used a USB 3 to USB C "coupler", and using a printed clamp that securely holds the coupler.

![The USB3-A to USB-C coupler and clamp](https://user-images.githubusercontent.com/55795671/133004185-3209ec7d-b2e1-4bc2-98ed-7e05ad7ac1e4.jpg)

Threaded inserts are used on one half of the clamp, an M3x7 cap head screw is used to tighten the clamp to a force that prevents the coupler moving.  The coupler should be positioned in the clamp so that it is flush to the outside bottom of the main electronics enclosure.

A notch exists on the top that allows the cables from the power jack to connect to the power supply module.  The clamp is designed to be as close of possible to the top of the enclosure, so the notch is necessary to feed the cables. 

![The fully assembled USB clamp](https://user-images.githubusercontent.com/55795671/133004183-198cdf4f-1a98-4333-bda8-c2326712adba.jpg)

#### The power supply

The main enckosure requires a power supply to allow the hubs to power all the tuners at the same time, the step down coverter allows a wide DC input range to be regulated down to the 5V which is then avaialble via 2 USB-A female sockets.

#### The Hubs

If you have more that 3 tuners, then the hubs should be placed so that the tops of the hubs are touching and at 180 degrees to each other, this allows the power cables to be routed far easier to the 2 USB A sockets that the step down converter provides.  The hubs are then cascaded, so that one hub is connected to the coupler and that hub them occupies one of the USB sockets on the other hub.   By chaining the hubs in this manner, we only require a single USB connection back from the tuner system to the host PC.

![The fully connected system](https://user-images.githubusercontent.com/55795671/133004172-dbe2316b-81c7-416e-a940-e859f4fad723.jpg)

![How it looks in CAD](https://user-images.githubusercontent.com/55795671/133004176-bb535cc6-9b31-4ed3-9846-9302aa783d5f.jpg)

## Software 

My configuration uses a linux distribution that runs TVheadend.  TVheadend provides streams across the network to any client that wishes to watch a live channel.  My particular configuration is such that tv headend is not directly accessed, instead I use Emby media server's live tv functions which provides an m3u file containing all the channels that TVheadend has discovered, emby is then responsible for either directly passing the stream to the client if the media is support, otherwise it will transcode the live tv stream to a format that the client supports.

## Fixing TVheadend with Emby

There is a problem with TVheadend and Emby.  TVheadend can supply an .m3u playlist to emby, but the channel numbers are not embedded in a format that emby can use, so the channel guide and order of channels is borken.  I have provides a nodejs application that can be run on the headend server or another machine that simply queries TVheadend to retrieve the stream URL and channel information, it then creates an .m3u file what contains the correct stream URL's along with the crucial channel number.

## Parts

| Quantity  				 | Part 						  | Usage 					| Link 				      |
| -------------------------- | ------------------------------ | ----------------------- | ----------------------- |
| n 						 | Xbox One tuner 				  | Electronics Enclosure   | [Amazon](https://www.amazon.co.uk/Xbox-One-Digital-TV-Tuner/dp/B0174G58B8) | 
| 4							 | M3x7 Cap Head Screw   		  | USB Clamp   		    | N/A
| 4        					 | M3 x D4.6 x L5.7 Heat Insert   | USB Clamp   		    | [AliExpress](https://www.aliexpress.com/item/Brass-Hot-Melt-Inset-Nuts-Heating-Molding-Copper-Thread-Inserts-Nut-SL-type-Double-Twill-Knurled/4000716825550.html) |
| 1  						 | 5.5x2.5mm 24V PSU 	  | Electronics Enclosure   | [Amazon](https://www.amazon.co.uk/gp/product/B087RDQFHD/ref=ppx_yo_dt_b_asin_title_o05_s00?ie=UTF8&psc=1) |
| 4							 | M3x12 Cap Head Screw   		  | Electronics Enclosure   		    | N/A | 
| 4 * (Total Tuner Enclosures)       | M3 x D4.6 x L5.7 Heat Insert   | Tuner Enclosure   		    | [AliExpress](https://www.aliexpress.com/item/Brass-Hot-Melt-Inset-Nuts-Heating-Molding-Copper-Thread-Inserts-Nut-SL-type-Double-Twill-Knurled/4000716825550.html) |
| 4 * (Total Electronics Enclosures)       | M3 x D4.6 x L5.7 Heat Insert  | Electronics Enclosure | [AliExpress](https://www.aliexpress.com/item/Brass-Hot-Melt-Inset-Nuts-Heating-Molding-Copper-Thread-Inserts-Nut-SL-type-Double-Twill-Knurled/4000716825550.html) |
| 2                          | USB 3 hub                      | Electronics Enclosure   | [Amazon UK](https://www.amazon.co.uk/gp/product/B07DWZCSPM) | 
| 1                          | USB 3 A to C coupler 		  | Electronics Enclosure   | [Amazon UK](https://www.amazon.co.uk/gp/product/B08G4NJ11F) | 
| 1  						 | USB 3 A to C cable 			  | Electronics Enclosure   | [Amazon UK](https://www.amazon.co.uk/gp/product/B01GN0M6NE) |
| 2 						 | Right angle make micro USB to A cable | Electronics Enclosure | [Amazon UK](https://www.amazon.co.uk/gp/product/B07KTXJ28G) | 
| 1 						 | 6 to 40V DC to 5V step down converter | Electronics Enclosure | [Amazon UK](https://www.amazon.co.uk/gp/product/B08KW1KZ95) |
| 1 						 | 24V 5A DC power supply | Electronics Enclosure | [Amazon UK](https://www.amazon.co.uk/gp/product/B087RDQFHD) | 
| 1 						 | 5.5mm x 2.5mm Panel mount jack | Electronics Enclosure | [Amazon UK](https://www.amazon.co.uk/gp/product/B081MWYT6T) | 

## Heat Inserts

I use heat inserts when i need to use screws to bind parts of a project together.  It's a much nicer and cleaner solution generally to providing fixtures that by using a put plastic hole or a combination of a holes, nuts and overhangs to create posts.

For a heat insert, I use specific ones that have a smaller diameterneck on one end which can be used to locate the insert into the desired location, I generally use 0 tolerance and because the neck is a very short stub, a small tap with a nylon hammer sets the insert into the correct place ready for the heat insertion.

You can use a normal soldering iron tip, but be aware that any solder on the tip combined with the shape, may result is the insert getting stuck to the iron at exactly the wrong moment, you can easily ruin a print in a couple of seconds if this occurs.

Instead, I recommend that a specialist tool is used which is a copper tip that you can fix to your iron.  You wull require a good soldering iron that has removable tips, cheap irons do not allow this and are not suitible.  It's critical that when you are looking for these tips that you buy the correct tip for your particular iron, as the size and mounting type will vary between iron manufacturers.

I can recommend the following seller on eBay (UK) who has supplied me with tips that work perfectly for my (genuine) Hakko FX888D soldering iron, again please check and double check that the listing you are hovering on "Buy" is the correct one for your soldering iron.

[Hakko FX-888D heat insert tip](https://www.ebay.co.uk/itm/284159136063?hash=item422934513f:g:JKAAAOSwtrZgDZbL)

