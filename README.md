# debian-package-tbo
Paquetería debian del proyecto TBO

## Generar paquetes DEB.

```bash
mkdir -p src
docker run --rm -ti -v $PWD/src:/src ieperez/docker-builder-deb
```
```bash
cd src
git clone -b master https://github.com/danigm/TBO.git
cd TBO
apt update && apt install \
    libglib2.0-dev \
    libgtk-3-dev \
    librsvg2-dev \
    gnome-common \
    intltool \
    libgtk2.0-devel \
    libgnome2-dev \
    gnome-pkg-tools
    
./autogen.sh && make
dpkg-buildpackage -us -uc && ls -lah ../*.deb
```
