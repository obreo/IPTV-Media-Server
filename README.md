# IPTV-Media-Server
## Running IPTV Media Server using Apache
### This is an instruction to run your favourite IPTV media on your TV by connecting it to Apache server.

### Requirements
1. Linux server - I'm using Ubuntu
2. Apache web server 
3. Iptv player - Tivimate or Kodi 

### Installation:
1. Install apache:
``` 
Apt get install Apache2 
``` 
2. Enable apache:
``` 
Systemctl start Apache2 && systemctl enable apache2 
``` 
3. Edit `000-default.conf` file and change the `document root` to the directory you want to add your M3U8 file
```
sudo nano /etc/apache2/sites-available/000-default.conf
```
4. Edit `apache2.conf` :
```
sudo nano /etc/apache2/apache2.conf
```
5. Navigate to <Directory /> and make it similar to this:
```
<Directory />
 Options FollowSymLinks
 AllowOverride None
 Require all denied
</Directory>
<Directory /usr/share>
 AllowOverride None
 Require all granted
</Directory>
<Directory /YourFolderDirectory>
 Options Indexes FollowSymLinks
 AllowOverride All
 Require all granted
</Directory>
```
Now reload apache service again and browse your server's localhost, it should show you the directory you edited in the config files.

### Setting IPTV Playlist
1. Add your IPTV playlist in the directory which apache uses, you will notice this file is shown when you browse your apache server.
2. Using your favourite IPTV player, connect to the server and make your IPTV file as path:
```
https://IP_ADDRESS/PLAYLIST.m3u8
```
