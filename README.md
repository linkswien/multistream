# multistream

multistream is just a few nginx and stunnel configuration files with the aim to replace Restream.io. It takes an RTMPS stream input and pushes it to multiple RTMPS streaming providers (including Youtube and Facebook Live).

## Usage

Install `nginx` (including `libnginx-mod-rtmp`) and `stunnel4` via your package manager, e.g.:

```
sudo apt install nginx libnginx-mod-rtmp stunnel4
```

Clone the repository and edit configuration files, then copy them to the correct locations:

```
git clone https://github.com/linkswien/multistream.git
cd multistream

# vim multistream-module.conf     # Edit incoming stream key
# vim multistream-site.conf       # Edit SSL certificate locations and outgoing stream keys

cp multistream-module.conf /etc/nginx/modules-available/multistream.conf
cp multistream-site.conf /etc/nginx/sites-available/multistream.conf
cp stunnel.conf /etc/stunnel/stunnel.conf
```

Now reload nginx and start stunnel:

```
sudo systemctl reload nginx
sudo systemctl start stunnel
sudo systemctl enable stunnel
```
