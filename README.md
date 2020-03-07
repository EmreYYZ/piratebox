# piratebox
 Edit the PirateBox interface, or die tryin'. 

**IMPORTANT PSA:**You can upload this repository to **/opt/piratebox/** inside your piratebox to see the changes.

If your pc is connected to the internet via an ethernet cable, and if your pc has wifi capability; you can connect to the internet and to the piratebox at the same time, which makes the development way easier. 

I suggest using FileZilla for downloading and uploading files from piratebox. (download the zip version, not the sponsored shit. https://filezilla-project.org/download.php?show_all=1) You can also use Cyberduck, which is waaaay better but don't @ me if you do so.

The main themeing information is here: 
https://piratebox.cc/generic:mods:theming

Write this to SSH (after logging in as "alarm") change permissions: (source https://forum.piratebox.cc/read.php?7,19858)
>sudo chmod a+rw /opt/piratebox/www -R

Of course you should change the directory according to your needs. For example I did **sudo chmod a+rw /opt/piratebox/share/content -R**. Use your brain, change whatever you need.

**/opt/piratebox/share/Shared** has the html for header and the footer. If you ask me, it is kind of a d*ck move on the developer's part, but what can you do amiright?

After doing the permission trick, I was able to change the title of the page. From "Welcome" to "Your mum". Aaaand ofcourse it didn't work. It requires a f*cccckinggg miracle for it to do so. 

Trying to edit the piratebox interface is the most backward shit I've ever witnessed. And I'm from Turkey.

Ok. Let's try this folder **/opt/piratebox/www_content**:
>sudo chmod a+rw /opt/piratebox/www_content -R

Ok. So apparently that directory is just a f*cking distraction. So write this command to destroy that directory, we don't need it.
>sudo rmdir "/opt/piratebox/www_content"

This will remove the directory. Piratebox also uses that folder as a backup so we definitely don't need it. It is just confusing.

Giving permission to this **/opt/piratebox/bin/** might delete later >.<
...
Nevermind

The **lighttpd.conf** file in **/opt/piratebox/conf/lighttpd** has this info:
>+comment+ Grabs main css
>dir-listing.external-css     	= "/content/css/page_style.css"

So this might mean that **page_style.css** in that specific directory is the main css. The same doc also says this:
>server.document-root        = "/opt/piratebox/www"
I dunno what it means but might come in handy later.

This is getting frustrating. Apparently **/opt/piratebox/src/** also has the header file. At this point just give permission to all directories by writing:
>sudo chmod a+rw /opt/piratebox/ -R

When I enter to piratebox.lan (we need to change this too) and check the source, firefox shows me this:
><link rel="stylesheet" href="/content/css/page_style.css">
So this means that the correct CSS is in the /content/ directory. Let's try to change it. 

WHEN I FCKING DOWNLOAD THE F*CKING INDEX.HTML, IT DOWNLOADS THE FILE WITH THE CHANGES I'VE MADE.
HOWEVER, WHEN I ENTER THE WEBSITE, IT DOESN'T SHOW ME ANY OF THE CHANGES I'VE MADE.

Maybe the problem is being caused by **/opt/piratebox/share/content/locales/data.en.properties** cuz why not?
At this point, everything is a suspect. Let's change the info and check if it works.
IT WORKS!!!!!!!!! OMFG!!!!!

I don't have a clue how to change anything else.

Ok. Found the CSS. Don't panic.
>/opt/piratebox/share/content/css/page_style.css

