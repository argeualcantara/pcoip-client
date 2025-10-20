## Make & Install
```bash
makepkg -si
```
## OAuth login

If you use OAuth to authenticate you must add the proper handler for the pcoip-client mime type.

### Mime type configuration

In order to be able to login with OAuth authentications there are other steps needed.


### 1. Create a desktop handler

create the handler file:

```bash
sudo nano /usr/share/applications/pcoip-handler.desktop
```

add this to the file (verify the pcoip-client path)

```ini
[Desktop Entry]
Name=Anyware Client
Exec=/usr/bin/pcoip-client %u
Type=Application
Terminal=false
MimeType=x-scheme-handler/pcoip;
NoDisplay=true
```

### 2. Register the handler

```bash
xdg-mime default pcoip-handler.desktop x-scheme-handler/pcoip
```

Check if the configuratio was correctly applied

```bash
xdg-mime query default x-scheme-handler/pcoip
```
### 3. Update desktop handlers

```bash
sudo update-desktop-database /usr/share/applications/
```
