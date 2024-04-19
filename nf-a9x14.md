FlashForge Adventurer 3 bottom cover/lid
========================================
for Noctua NF-A9x14 fan (92x92x14mm low-profile)

This is my second (and probably the last) iteration on the bottom cover and fan of my FlashForge Adventurer 3 (Monoprice Voxel).

A few months ago I shared a similar design for 40mm and 80mm fans. Those improve the airflow around the electronics and can reduce the noise too compared to the stock fan if the new fan of your choice isn't terrible. This time we use a larger 92mm fan that has lower speed and noise levels than smaller fans that have to operate at higher speed to create the same airflow.

Large parts of this text have been copy-pasted from the documentation of the previous 40mm/80mm design. The clearance test models used here are identical to the ones in the previous design.


Summary
-------

- Material: ABS
- Profile: Adventurer 3 Series / Flashforge-ABS / Standard (layer height: 0.18mm)
- Designed specifically for the Noctua NF-A9x14 fan (92x92x14mm)
- Multi-part (4-piece) design to support the limited build volume of the Adventurer 3 (150x150x150mm)
- Single-part design if you have access to a printer with larger build volume

The NF-A9x14 is one of the largest and quietest fans that fit between the mainboard of the printer and a low-profile bottom cover. Using an even larger/slower/quieter fan would require tall printer legs and a bottom cover protruding from the printer to house the large fan. The Noctua NF-A9x14 has two versions at the time of writing - both are standard desktop computer fans (4-pin PWM 12V): the original/normal version comes in brown (the usual "Noctua" colour theme), the high speed variant comes in black (Nocta labels it HS-PWM and chromax.black.swap).

This is a low-profile design that doesn't make the bottom of the printer deeper so you don't have to upgrade the printer legs. There is a "flat" and a "raised" version of the design, the raised version makes the bottom of the printer 2mm deeper in order to create a bit more space between the fan and the mainboard. The stock legs are only 5mm tall so I decided to extend them on my printer to 16mm with rubber-based furniture legs to provide more space for airflow but you don't have to do this.

The NF-A9x14 barely fits behind the bottom cover. If your mainboard leaves a little bit less space than my mainboard (e.g.: larger components soldered onto it) then you might not be able to use this bottom cover design. I could use both the "flat" and "raised" versions of this design but decided to stick with the "raised" one because my printer has taller upgraded legs and this way there is more space for airflow between the mainboard and the fan. I still had to bend a component on my mainboard to have enough space for the 92mm fan (see the attached photo for explanation).


Multi-part design
-----------------

I created the multi-part design with the default "Adventurer 3 Series / FlashForge-ABS / Standard" profile of FlashPrint in mind. That implies a layer height of 0.18mm that shouldn't be changed (to keep the clearances accurate along the Z axis). If you are confident you can use expert mode to customise some settings but that isn't necessary. (I usually tweak only a few things like infill density, number of support top solid layers, print speed...)

The four parts are kept together by interlocking joints that work best when the fit is at least a bit tight. Since the joints are 20mm long and the lid is attached to the printer with 4 screws the fit doesn't necessarily have to be tight in our case (my first prototypes worked well with a relatively loose fit). The tightest clearance values that still work with a given print configuration depend on many factors like the brand/colour/quality of the filament, the temperature and humidity of the environment in which you print, the roughness of your top and bottom layers, the unique quirks of your printer. This is why I uploaded 10 versions of the design with different XY and Z clearance value combinations:

- 0.18z 0.15xy
- 0.18z 0.20xy
- 0.18z 0.25xy
- 0.18z 0.30xy
- 0.18z 0.35xy
- 0.36z 0.15xy
- 0.36z 0.20xy
- 0.36z 0.25xy
- 0.36z 0.30xy
- 0.36z 0.35xy

Each clearance combination comes with a small pair of clearance test models (using only two and a half interlocking joints) that can be printed and tried quickly before printing the larger models. The tightest possible fit was 0.18z 0.25xy with my configuration in my environment. In order to figure out what works for you I recommend starting with the loosest fit (0.36z 0.35xy). If it works then decrease one of the Z and XY values in your next test. Repeat this process to find the smallest/tightest values on the Z and XY axes and use those or a bit larger/looser values if you want to play it safe.

The model filenames that belong to the same clearance combination share the same prefix. As an example here is the full list of files that belong to the 0.36mm Z 0.30mm XY clearance combination:

- 0.36z\_0.30xy\_clearance\_test\_side\_a\_09.stl
- 0.36z\_0.30xy\_clearance\_test\_side\_b\_09.stl
- 0.36z\_0.30xy\_lid\_top\_left.stl
- 0.36z\_0.30xy\_lid\_top\_right.stl
- 0.36z\_0.30xy\_lid\_bottom\_left\_flat.stl
- 0.36z\_0.30xy\_lid\_bottom\_left\_raised.stl
- 0.36z\_0.30xy\_lid\_bottom\_right\_flat.stl
- 0.36z\_0.30xy\_lid\_bottom\_right\_raised.stl


Print the models in whatever orientation you prefer. Both the "front side up" and "front side down" orientations have their own pros and cons.


Electronics
-----------

You have to unplug the original bottom fan of the printer and use its socket to power your new fan. That socket has the "BOTTOM FAN" label on the mainboard. The printer has 24V industrial fans so you need a DC-DC converter between the mainboard and the 12V NF-A9x14 fan. There are many types of DC-DC converters, the types you need here are usually called "buck converters" or "step-down converters". There are plenty of good tutorials on that topic (including 3D printer mods adding Noctua fans with buck converters) so I have no intention to create another one here. You may need tools like a soldering iron and a multimeter to get the job done.

The type of the fan connector on the printer mainboard is 2-pin JST-XH. Use a multimeter to check the polarity (in most cases GND is black wire while +VDC is usually red but can be something else like yellow). Unlike 3D printers, desktop computers always use the same standardised fan connector type and pinout (use google to figure out which pins are GND and +VDC on your NF-A9x14, you can ignore the other pins/wires). People usually refer to these as "3-pin fan connector", "4-pin fan connector" or simply "fan connector" instead of something like "molex 47054-1000" or "molex 47053-1000".

Fans can be undervolted to reduce the speed and change the noise profile (but the voltage should never be below the minimum startup voltage). Even if you drop only 1-2 volts it usually results in a significant drop in max static pressure - the relation probably isn't linear. A lot of buck converters come with a trimmer that can be adjusted with a screwdriver to change the output voltage. This is how you reduce the mainboard's 24V to 12V or a bit lower if you want to undervolt to achieve lower noise and airflow.

On one of my uploaded photos you can see the NF-A9x14 fan attached to the printed bottom cover along with a buck converter and the required wiring. I soldered the wires of a female JST-XH connector to the input pins of the buck converter. The wires of a male computer fan connector (only two pins: GND and +VDC) have been soldered to the output pins of the buck converter. I could have cut the wires of my NF-A9x14 fan and soldered them directly to the buck converter outputs but I wanted to keep the fan and its wire/connector intact. Instead I butchered one of the extension cables (the low noise adapter) that came with the fan to get access to a male fan connector (I uploaded a photo of the full contents of the NF-A9x14 package). Some Noctua fans (like the 40mm models I used in my previous design) come with an extra male connector that has only two wires with nothing attached to them - Noctua calls it "omnijoin adaptor set" - but unfortunately it doesn't ship with the NF-A9x14.

My buck converter is protected by transparent heat shrink tubing. I cut two holes into the tubing and used zip ties to attach the buck converter to the bottom cover through the ventilation holes. You can see those white zip ties (didn't have black at the time) on another photo on which the printer is assembled and the fan is running.


Cooling
-------

Cooling solutions usually follow some kind of strategy to force cool air through the enclosure using negative or positive pressure created by fans that push air through holes on the walls of the enclosure. Both positive and negative pressure have their own pros and cons. Since hot air naturally floats upward it's a good idea to avoid fighting it - this is why pulling in air at the bottom and extracting it at the top makes a lot of sense.

If we take a look at the bottom part of the printer's enclosure that houses most of the electronics (mainboard, PSU) then there are only two obvious areas with holes for ventilation: a long hole above the Y-rod of the build plate and a few rather small openings cut into the bottom cover. None of those openings have a fan to help push the air through that bottom cavity. The OEM bottom fan seems to just stir the air around the electronics in that area (and perhaps heat it a little bit with its motor). I don't know what the idea was behind that fan placement.

The hot air may exit the bottom cavity naturally by floating upwards into the printing chamber. If that's the case then just removing the bottom lid can help a lot because the holes on it aren't particularly large. A mediocre computer case often has similar problems, opening it can improve thermal performance a lot but that way the internals are less protected from dust (which isn't necessarily a huge negative when protection from dust wasn't even part of the plan like in case of this printer and most inexpensive computer cases). If you run an air filter/purifier in the same room then dust isn't an issue. (Running an air purifier next to your printer is a good idea for many reasons and makes dust-free printing easy with open-frame printers.)

We could say that the top fan of the printer is there for the rescue (pulling up air through the whole enclosure) but that small fan is unlikely to be strong enough to suck the air from the bottom especially because the middle portion of the printer (the printing chamber) has a lot of other holes to lose pressure. And anyway, the top fan isn't used in my printer when I print ABS, I don't want the toasty 45-50C air to leave the printing chamber too quickly.

Adding a fan to the bottom lid can be a huge improvement in terms of air flow and cooling around the electronics. It can pull in cool air and throw it directly at the hottest components of the mainboard. It can create some positive pressure too inside that cavity to push the air out. Even if it's a weak fan with little static pressure it can still perform better than the default setup due to the better fan placement.

When I print ABS I don't want the bottom fan to push too much cold air into the build chamber - that could result in warping due to reduced and/or fluctuating temperature. For this reason I slightly undervolted my fan - in this situation the relatively low max static pressure isn't an issue. Fortunately most of the air escapes through the printed bottom lid that has more holes than the original design. This way some of the exhausted hot air is sucked back by the fans immediately which isn't ideal but isn't a fatal flaw either. The solution could be improved by drilling the ventilation holes into the bottom part of the printer enclosure (as far from the intake fans as possible) but I didn't feel it necessary to go that far.


Noise levels
------------

A common reason to upgrade is to get rid of the noise produced by the OEM bottom fan. Making the system significantly quieter is probably more difficult than you think for several different reasons. Let's see what makes a very good setup quiet or "virtually silent" if you get everything right:

- A rigid enclosure with thick heavy walls. A good example is a high quality computer enclosure with thick metal walls with noise dampening materials glued to them on the inside. A good enclosure is less likely to become a resonant "loudspeaker" because its natural frequencies can't be excited so easily by a typical fan. It's easy to see that the flimsy plastic enclosure of the Adventurer 3 isn't ideal in this regard so I wouldn't expect a "virtually silent" setup with a fan attached to it. It'll amplify the noise even with the quietest fans.
- Fans with quality motors and bearings to reduce vibrations. Strong low-frequency vibrations are usually the worst because those are difficult to isolate, they penetrate even the best enclosures, your headphones and even the walls of the building. That's why the OEM fan of the Adventurer 3 is so bad, it sounds like an airplane engine or a small compressor. A lot of cheap 24V industrial fans have this issue because they have low quality motors/bearings and prioritise high speed and max static pressure.
- A larger fan at lower RPMs can usually create the same airflow as a smaller faster fan. The lower RPM often translates to lower noise levels assuming that the quality of the larger and smaller fans is roughly the same (perhaps from the same brand).

Certain things are clearly against you (like the flimsy resonant plastic enclosure and sometimes static pressure requirements). Fortunately you can increase the quality and/or the size of the fan and lower its speed too in this scenario.

How low you can go with the fan speed (and the max static pressure) depends on the situation. In my situation reducing the speed of the bottom fan was almost a requirement because I didn't want it to push too much cold air into the printing chamber during ABS prints. In some other cases (e.g.: the hotend cooling fan) I'd be more careful with lowering the max static pressure (like some people do with Noctua hotend fan "upgrades") because that may not work well with all print configurations that I use.

My hotend fan is also loud but its noise profile is nowhere near as bad and annoying as that of the bottom fan. It sounds like a turbine with a high pitch whine which is normal in case of a small high speed fan. A significant portion of the noise probably comes from airflow that would be difficult to reduce without lowering the speed and the max static pressure. The enclosure isn't resonating from that fan and its noise has no strong low-frequency components so it doesn't punch through the walls of the building and/or my headphones like the OEM bottom fan does. I'm not in the same room as my printer so I can't even hear that fan.

In my opinion it's a good idea to ignore the dB(A) values mentioned on fan spec sheets. They are pretty useless and probably good only for marketing purposes. A-weighted measurements underestimate how annoying the low-frequency components of the noise are (when they are present) and they don't tell much about the overall noise profile either (like the strongest frequencies, annoying repeating patterns in the noise, etc). You can tell how annoying its noise is only by trying it.


Notes
-----

Don't be surprised if the bottom layer of your ABS print is a bit ugly with the default profiles. I often had to cut off extra material from the edges of the ventilation holes at the bottom layer. Some hexagons looked like circles when my print finished. The most important thing is to avoid warping. In contrast the quality of the finish is unimportant. This print doesn't have to be beautiful because it goes to the bottom of your printer.

The design uses the "swirl" fan grill pattern because it was one of the best performers in an article that measured the reduction of airflow and increase in noise levels caused by different fan grill patterns.

I used FlashPrint 5.3.4 (Win10 64bit). When an STL is loaded into FlashPrint it uses blue colour to mark the bottom faces of the model that touch the build plate. In case of some STL files it seemed to colour only portions of those bottom faces and this was reflected by the ugly slice outputs too. I corrected those problems by re-exporting the affected "binary STLs" with higher "refinement" options. When that couldn't solve the problem I re-exported the model in "ascii STL" format (which results in larger file sizes). The reason must be some sort of floating point inaccuracy introduced by the modelling software, the binary STL format or FlashPrint (or some kind of combination of these).
