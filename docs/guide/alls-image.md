# Imaging your ALLS drive

ALLS uses various tamper protections such as bitlocker, tpm, etc. that are provisioned from the factory. As such, you can't just stick in any drive and expect it to work, even with keychip.
Your drive contains your unique PCBID, so it's a very good idea to image your drive, so you can restore it and have it work, or to just have a 2nd drive handy.

Boot Linux through a USB drive (i recommend using Linux Mint and Rufus to create the bootable USB. plenty of guides on this). Do NOT use Windows, this can trigger bitlocker and your drive will get wiped.

Plug in an external drive if your boot USB drive isn't large enough to contain a 120gb image.

Plug in your wacca drive via usb sata enclosure device. Any sata enclosure will work, these are 2.5" drives so they don't need more than USB to power them but the ac powered 3.5" / 2.5" enclosures will be fine too.

Use DD to image the drive <https://linuxhint.com/make-disk-images-dd-command-linux/>

>? NOTE: **Confused? Click here for a line by line tutorial of this procedure**
> 
> Begin by installing lsscsi.
> 
> - `sudo apt install lsscsi`
> 
> `lsscsi` lists all the drives plugged in, look for your wacca drive (if you have some kind of complex setup, do the command prior to plugging in the drive and then after to discover which one)
> 
> - `sudo fdisk /dev/sd<wacca-drive>`
> 
> we want to access the wacca drive. replace `/dev/sd<wacca-drive>` with whatever you saw in the previous step
> 
>  - `p`
> 
>   This will list all the partitions on the drive and the exact sector count. Important to note them.
> 
>   - `q`
> 
>   quits out of fdisk
> 
>   - `sudo dd if=/dev/sd<wacca-drive> of=/pathtostorage/wacca.img bs=100M conv=noerror`
> 
>   Creates a clone image of the specified input `if` to the specified destination `of`
> 
>  - `ls -lh wacca.img`
> 
>   Checks permission of the drive, should match the original
> 
>   - `fdisk -l wacca.img`
> 
>   To compare the sector count, should match the original, then restore using
> 
>   - `sudo dd if=<wacca.img> of=<newdrive> bs=100M conv=noerror`
> 
> You'll want to restore on a 120gb or at most 240gb drive to be compatible with how a main storage format works at the moment. (but if you aren't doing that, any larger sized ssd can work)
> 
> UNKNOWN: expand the existing partition possible? would be good for the future of wacca+ / omnimix etc.
