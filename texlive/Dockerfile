FROM base/archlinux

MAINTAINER Linus Arver <linus@ucla.edu>

# Bring Arch Linux up to date. The base image is quite old so we have to jump
# through some hoops. We install the texlive-most and texlive-lang metapackages
# that comprise the entire suite of texlive packages offered in Arch Linux.
RUN \
	(: Update Arch Linux.) \
	&& perl -pi -e 's/https/http/' /etc/pacman.d/mirrorlist \
	&& pacman -Sy --noconfirm archlinux-keyring \
	&& pacman -Syu --noconfirm \
	&& pacman-db-upgrade \
	&& pacman -Syy \
	&& (: Finally, install texlive metapackages.) \
	&& pacman -S --noconfirm base-devel texlive-most texlive-lang \
	&& (: Clear pacman cache.) \
	&& yes | pacman -Scc

CMD ["tail", "-f", "/dev/null"]
