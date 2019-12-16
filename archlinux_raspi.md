# How to Install ArchLinuxArm on raspberry pi:
1) Doanload image: https://sourceforge.net/projects/archlinux-rpi2/
2) Write to sd-card with Win32DiskImager
3) Stick in Pi and boot.
4) login as alarm/alarm
5) su root with root as password
6) pacman -Syu --ignore ca-certificates-utils
7) pacman-key --init
8) pacman-key --populate archlinuxarm
9) pacman -Syu

pacman -S python
python -m venv shyft
source shyft/bin/activate

# 09.12.19 ArchLinux
Jeg vil prøve å kjøre shyft på min RaspberryPi. Her er prosessen.

- Jeg må installere Arch på Rpi.
- Viser seg at jeg trenger linux for å installere Arch, har bare windows.
- Installerer Ubuntu on Windows som gir meg Linux cmd på windows.
- Bruker Windows DiskPart til å slette partisjoner på minnekort.
- Bruker Windows Partition tool for å lage og formattere korrekte partisjoner på sd-kort.
- Må få Ubuntu on Windows til å snakke med minnekort - ikke lett på grunn av permission denied.
- Har funnet en fil jeg kan editere for å få vekk permission denied melding.
- Må lære vim for å editere denne fila.
- Prøvde vim-varianten. Funka ikke.
- Fant ut at jeg kunne pakke opp filene med 7zip. Putta OS-feilene på sd-kort via windows.
- Grønt, kontinuerlig lys på rpi, betyr at den ikke kan lese SD. Må prøve igjen.

# 11.12.19 ArchLinux del 2.
Vel, det forsøket gikk i dass. Nå prøver jeg noe annet.

- Virtualisere en linux maskin på min egen windows box med VmWare Workstation. Laster ned ArchLinux, og det funker! Hurra!
- Da finner jeg en mal for å installere ArchLinux på RPI: https://www.instructables.com/id/Arch-Linux-on-Raspberry-Pi/
- De første stegene er formattering og partisjonering av sd-kortet.
- Det ser ikke ut til å funke helt å gjøre det fra VM Ware, så nå er microsd-kortet ødelagt.
- [x] Kjøp to ekstra SD-kort, for sikkerhets skyld. Trenger bare 32 GB.

# 12.12.19 ArchLinux del 3.
Det er jævlig vanskelig å installere linux.

- Har omsider fått til å installere arch VM ordentlig. Den driver å laster ned nå.
- Når den er ferdig kan jeg endelig få satt opp RPI arch.
- TIl hælvete med det her. Det er faen meg for innfløkt og vanskelig.

# 12.12.19 ArchLinux del 4
Og, jeg har fått tenkt litt.

Jeg må bruke et annet, enklere Linux for VM. ArchLinux er for stress. Jeg trenger noe som funker ut av boksen.
- [x] Slette alt eksisterende for nåværende VM.
- [x] Opprette ny VM med en enklere distro (Ubuntu).
- [x] Formattering av SD-kort skal allerede være løst i DiskPart.
- [x] Plan: Følge [oppskriften](https://www.instructables.com/id/Arch-Linux-on-Raspberry-Pi/)

**Mother fucker**
Linux VM har ikke ren linux skriving til SD-kort, så symbolske lenker feiler.
Trenger altså å opprette sd-kort fra REN linux, nytter ikke å gjøre det via windows.

# 12.12.19 ArcLinux del 5
Ny plan:
- [x] Installere NOOBS på RPI.
- [x] Koble minnekortleser til RPI og putte inn ferdig formattert arch-sdkort.
- [x] Bruke Noobs (debian) til å laste ned og opprette så må bare laste ned og installere arch på sdkort.
Funker ikke. Installasjonen får feilmeldinger ang "cannot create symbolic link".
- [x] Prøver å se om jeg har feil filsystem.
Faen, SD-kortet er herpa. Må kjøpe nytt. Ok ny plan.\:

### Ny plan:
~~- [ ] Kjøpe nytt sd-kort.~~
Trengte ikke, klarte å redde det kortet jeg hadde.
- [x] Koble den opp til Raspbian på rpi.
- [x] Følge planen på https://archlinuxarm.org/platforms/armv6/raspberry-pi
Er i gang. Installerte bsdtar for å pakke ut, og jeg tror den holder på å pakke ut nå. Jeg går og legger meg, så sjekker jeg imorgen.
Jeg trenger et nytt sd-kort, antakeligvis.
- [x] Begynne å gråte (om det så funker eller ikke).
Funker ikke. Booter ikke. RPI klarer ikke finne noe bootbart på disken.

# Ny plan
Verifisere eksisterende sd-kort
- [x] Installere noobs på den, og se om raspberry pi can boote fra den.
Nope kortet er herpa.

# Ny plan:
- [x] Nytt kort, følge Arch-oppskrift fra Debian på RPI slavisk.
Nope funker ikke. Får feilmelding i bsdtar.

# Ny plan:
Prøve image-varianten på helt nytt sd-kort.
Lastet ned: https://sourceforge.net/projects/archlinux-rpi2/
Rullet ut på sd-kort med Win32DiskImager
- [x] Plugge inn og sjekke om funker.

YEEEESSS!



UTROLIG TRIKS:
Hvis et SD-kort er konka med skrivebeskyttelse ser det ut til at man kan redde det:
1. Laste ned guiformat.exe
2. Åpne guiformat.exe
3. Åpne Task Manager,
4. Steng Windows Explorer (Utforsker)
5. Formater diskene.
6. I Task Manager. Fil, Ny, explorer.exe
7. PROFIT.



