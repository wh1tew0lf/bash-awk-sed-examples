Add your script autoload
========================


1. First way

Before this take a look at /etc/init.d/skeleton

```
sudo chmod ugo+x /etc/init.d/<your_script>
sudo rc-update add <your_script> defaults

sudo update-rc.d -f <your_script> remove # To remove your script from autoload
```
2. Second way

```
sudo nano /etc/rc.local # Add here before exit line
```
3. Third way

```
sudo nano /etc/systemd/system/<your_service>.service
```

At file write this:
```
[Unit]
Description=Your service
After=network.target
[Service]
ExecStart=/etc/init.d/<your_service>
[Install]
WantedBy=multi-user.target
```
Concent of file you can check by a google

After save file:
```
sudo systemctl start <your_service>
sudo systemctl enable <your_service>

# To cancel
sudo systemctl disable <your_service>
```
