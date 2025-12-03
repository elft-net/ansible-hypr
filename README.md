# Chickened out

Start to divert from the Ansible strategy because of time restrictions.

GIMP needs Python 2.7. Decided to use Flatpak instead of poluting the main system.
NOTE: No longer true, new release has finally been promoted to in fedora repo.

Added $XDG_DATA_DIRS to .zshrc file.

'''
sudo dnf install flatpak
flatpak remote-add --if-not-exists flathub <https://flathub.org/repo/flathub.flatpakrepo>
flatpak install flathub org.gimp.GIMP
flatpak run org.gimp.GIMP
'''

Changed strategy for ripCord accordingly.

OnlyOffice

NOTE: onlyOffice provides .rpm repo: <https://github.com/ONLYOFFICE/DesktopEditors/releases/latest/download/onlyoffice-desktopeditors.x86_64.rpm>

'''
sudo wget -O ~/Downloads/onlyoffice-desktopeditors.x86_64.rpm <https://download.onlyoffice.com/install/desktop/editors/linux/onlyoffice-desktopeditors.x86_64.rpm>
sudo dnf install ~/Downloads/onlyoffice-desktopeditors.x86_64.rpm
'''

Doesn't work after straightforward install, mailed Walter to gain time.

After research it turned out to be a bug within OnlyOffice, introduced after version 7.2
Decided to use flatpak and pin the release:
'''
flatpak install flathub org.onlyoffice.desktopeditors
sudo flatpak update --commit=6ae98cba3421104f2284ff31ea702d254d1561e6d127d22cf6cb562d21079ce6 org.onlyoffice.desktopeditors
flatpak mask org.onlyoffice.desktopeditors
flatpak run org.onlyoffice.desktopeditors
'''

Install kubectl:
'''
curl -LO "<https://dl.k8s.io/release/$(curl> -L -s <https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl>"
chmod +x kubectl
mv ./kubectl /usr/local/bin/kubectl
kubectl version --version
'''

Install kind:
'''
curl -Lo ./kind <https://kind.sigs.k8s.io/dl/v0.11.1/kind-linux-amd64>
chmod +x ./kind
mv ./kind /usr/local/bin/kind
'''

Install calibre:
'''
sudo -v && wget -nv -O- <https://download.calibre-ebook.com/linux-installer.sh> | sudo sh /dev/stdin
'''
