# Awesome Ageless FLOSS

*Traduccions: [English](README.md)*

Recull de projectes de programari lliure (*free libre open source software* or *FLOSS* en anglès), no tots en la capa de sistema operatiu, que defensen que els ordinadors han d'obeir els seus operadors humans i que s'oposen a les lleis de verificació i restricció per edat.

Aquesta llista la manté la [Protecció de la Frontera Electrònica](https://fronteraelectronica.cat), una organització [catalana](https://ca.wikipedia.org/wiki/República_Catalana) que treballa pels drets digitals i que creu que les màquines han fer allò que els seus operadors humans indiquin.

## Índex

- [Context](#context)
- [Sistemes operatius](#sistemes-operatius)
- [Programari de sistema](#programari-de-sistema)
- [Microprogramari](#microprogramari)
- [Maquinari](#maquinari)
- [Recursos](#recursos)
- [Com contribuir-hi](#com-contribuir-hi)
- [Llicència](#llicència)

## Context

Existeix normativa emergent en diverses jurisdiccions que desplaça la càrrega de la verificació demogràfica d'edat de les aplicacions web a la capa del sistema operatiu. Lleis com l'AB 1043 de Califòrnia i l'ECA Digital del Brasil forcen els sistemes operatius a recollir, emmagatzemar i exposar les dates de naixement dels usuaris mitjançant APIs estandarditzades. A través d'aquesta exigència, el que era un entorn d'execució neutre es transforma en un agent actiu de classificació d'identitat, i els ordinadors es converteixen en màquines que es neguen a fer allò que un humà els ordena pel sol fet que aquest humà no pertany a un determinat grup demogràfic.

Dins l'ecosistema Linux, això es va materialitzar quan systemd va fusionar la [PR #40954](https://github.com/systemd/systemd/pull/40954) i va afegir un camp `birthDate` als registres JSON del seu userdb.

Els projectes que apareixen en aquesta llista rebutgen aquest paradigma. Defensen que la infraestructura informàtica ha de romandre demogràficament neutra i tractar els usuaris com a entitats autenticades exclusivament per permisos, no per edat biològica.

## Sistemes operatius

Sistemes operatius amb desenvolupadors o editors que han pres partit públicament contra la verificació d'edat o han actuat activament per obstaculitzar-ne el compliment.

- [Ageless Linux](https://agelesslinux.org): script de conversió per a sistemes basats en Debian, dissenyat per aplicar-se sobre una instal·lació estàndard de Debian 13 (o equivalent), que substitueix les metadades d'identitat del sistema operatiu i desplega una API de verificació d'edat que retorna deliberadament un error i tanca el procés. Dissenyat explícitament per a «humans d'edat indeterminada». ([Declaració](https://x.com/lundukejournal/status/2032951803134837237))
- [Omarchy Linux](https://omarchy.org/): entorn de desenvolupament basat en Arch Linux i Hyprland, creat per David Heinemeier Hansson (DHH). El desenvolupador va qualificar públicament l'AB 1043 d'inaplicable i va declarar que no preveu respondre a aquestes lleis, tot qualificant-les al mateix temps amb un improperi. ([Declaració](https://x.com/lundukejournal/status/2029580164498108846))
- [Artix Linux](https://artixlinux.org/): distribució d'actualització continuada (*continous delivery*) basada en Arch, construïda completament sense systemd, que utilitza OpenRC, runit o s6 com a sistemes d'inici. Va declarar: «Mai no exigirem cap verificació ni identificació de l'usuari.» Arquitecturalment immune al camp `birthDate` del userdb, ja que els sistemes d'inici que incorpora no tenen cap base de dades centralitzada de metadades d'usuari. ([Declaració](https://x.com/lundukejournal/status/2034776326901555488))
- [Devuan Linux](https://www.devuan.org/): bifurcació (*fork*) de Debian sense systemd, amb declaracions oficials dels desenvolupadors que confirmen el rebuig a implementar el rastreig d'edat. ([Declaració](https://x.com/lundukejournal/status/2034697759291310115))
- [GrapheneOS](https://grapheneos.org/): sistema operatiu mòbil optimitzat per a la privacitat, basat en AOSP (Android). Els desenvolupadors van equiparar els mandats regionals de verificació d'edat a la censura autoritària i van afirmar que no tenen més obligació de filtrar Internet per a Califòrnia que per a la Xina. ([Declaració](https://x.com/lundukejournal/status/2035073741613338964))
- [Adenix GNU/Linux](https://www.adenixgnulinux.org/): distribució de l'ecosistema Debian mantinguda per J. Mazzullo. Emmarca els mandats de verificació d'edat com a violacions de la Primera Esmena (la protecció legal que la llibertat d'expressió té als Estats Units d'Amèrica) i ha demanat a Debian eines amb privilegis d'arrel (root) per purgar i vetar permanentment els paquets de vigilància imposats per l'estat. ([Declaració](https://lists.debian.org/debian-legal/2026/03/msg00022.html))
- [Vendefoul Wolf Linux](https://vendefoul-wolf-linux.sourceforge.io/index_en.html): les declaracions dels desenvolupadors confirmen el rebuig a implementar la verificació d'edat. ([Declaració](https://x.com/lundukejournal/status/2035390136356077822), [#2](https://x.com/vendefoulwolf/status/2035441292520386852))
- [FreeDOS](https://freedos.org/): sistema operatiu de codi obert compatible amb DOS. Els coordinadors del projecte rebutgen la imposició de vigilància demogràfica en arquitectures heretades de línia d'ordres. ([Declaració](https://x.com/lundukejournal/status/2034770975309361583))
- [Golden Dog Linux](https://goldendoglinux.org/): la desenvolupadora principal, Alexia Michelle, va declarar que el projecte no implementarà la verificació d'edat i va al·legar que ho feia per adequació als estàndards del codi obert. (La declaració es va publicar com a història d'Instagram i ja no es troba disponible; [Protecció de la Frontera Electrònica](https://fronteraelectronica.cat) en va verificar l'existència.)
- [MX Linux](https://mxlinux.org/): distribució d'escriptori basada en Debian. L'equip de desenvolupament va declarar que ningú de l'equip vol implementar la verificació d'edat, per preocupacions sobre la privacitat dels usuaris, la viabilitat i la coherència amb els principis del codi obert. ([Declaració](https://linuxiac.com/mx-linux-takes-clear-stance-against-age-verification-requirements/))
- [EndeavourOS](https://endeavouros.com/): distribució basada en Arch. L'equip va declarar que no disposa de la infraestructura, el personal ni els recursos per implementar la verificació d'edat i que va en contra dels fonaments del programari lliure. Van assenyalar que cap entitat del món FLOSS va ser consultada quan es va crear la llei i van demanar a l'OSI, la FSF i la Linux Foundation que actuïn en nom de les distribucions sense representació legal als Estats Units. ([Declaració](https://endeavouros.com/news/whats-new-in-endeavouros-titan-release/))
- [Void Linux](https://voidlinux.org/): distribució independent que utilitza runit com a sistema d'inici (sense systemd). Un moderador va publicar un comentari fixat al subreddit oficial on afirmava que «de moment no tenen cap pla» per implementar la verificació d'edat. ([Declaració](https://www.reddit.com/r/voidlinux/comments/1ryhgpl/comment/obeigup/), [#2](https://x.com/LundukeJournal/status/2036521455752495439))
- [Garuda Linux](https://garudalinux.org/): distribució basada en Arch. L'equip va declarar que Garuda Linux no implementarà cap mesura de verificació d'edat, ja que les seves jurisdiccions legals no tenen lleis que ho exigeixin. Van demanar a la comunitat que dirigeixi la seva indignació cap als polítics i les els grups d'interès (lobbies) i no cap als desenvolupadors voluntaris de distribucions. ([Declaració](https://forum.garudalinux.org/t/a-statement-on-age-verification-the-state-of-the-community-discourse/47652))

Aquests projectes s'hi oposen de manera obstaculitzadora i preventiva: bloquegen l'accés des de jurisdiccions amb lleis de verificació d'edat o en revoquen la llicència de programari per als seus residents.

- [Arch Linux 32](https://archlinux32.org/): bifurcació de 32 bits d'Arch Linux mantinguda per la comunitat. Va implementar el bloqueig per IP de tot el trànsit brasiler i en prohibeix l'ús al Brasil i a Califòrnia per evitar multes. ([Declaració](https://x.com/lundukejournal/status/2033896030178029675))

## Programari de sistema

Bifurcacions i pedaços que eliminen la infraestructura de verificació d'edat de les bases de codi originals.

- [Liberated systemd](https://github.com/jeffrey-sardina/systemd): bifurcació (*fork*) de systemd mantinguda per Jeffrey Sardina que elimina el camp `birthDate` i tot el codi associat d'anàlisi, emmagatzematge i visualització del userdb. Sardina la va crear després que el systemd original fusionés la [PR #40954](https://github.com/systemd/systemd/pull/40954) que afegia el camp i el mantenidor principal [tanqués un intent de reversió de la comunitat](https://github.com/systemd/systemd/pull/41179) sense fusionar-lo, de forma que, efectivament, el `systemd` original ara fa verificació d'edat. Manté paritat de codi completa amb l'original en tots els altres aspectes.
- [systemd-no-age-verification](https://github.com/r4shsec/systemd-no-age-verification): bifurcació de systemd del investigador en ciberseguretat R4shSec que elimina la verificació d'edat introduïda mitjançant la [PR #40978](https://github.com/systemd/systemd/pull/40978). ([Declaració](https://r4shsec.github.io/posts/how_to_remove_systemd_age_verification/))
- [systemd-fuck-california](https://github.com/Queer-Coded-LGBTQ/systemd-fuck-california): bifurcació de systemd de [Queer Coded](https://queercoded.lgbt/) que elimina la verificació d'edat. Es descriu com «systemd, però sense les ximpleries d'edat que hi han afegit».
- [paramazo/systemd](https://github.com/paramazo/systemd): bifurcació de systemd de paramazo, l'autor de la [PR de reversió #41179](https://github.com/systemd/systemd/pull/41179) que Poettering va tancar sense fusionar. La reversió argumentava que l'emmagatzematge de dates de naixement crea una nova categoria de dades sensibles, que les distribucions comunitàries no tenen cap voluntat d'actuar com a autoritats d'identitat i que ja existeix precedent de no-compliment per sobre de mesures a mitges.
- [ganitam/systemd](https://github.com/ganitam/systemd): bifurcació de systemd presa just abans de l'addició de la verificació d'edat, d'un desenvolupador de [Ganitam](https://ganitam.in/). La descripció a GitHub expressa l'esperança que desenvolupadors i mantenidors més hàbils facin el mateix (és a dir, anima altra gent a bifurcar també ells systemd per evitar-ne les restriccions d'edat).
- [GSYT-Productions/systemd-fork](https://github.com/GSYT-Productions/systemd-fork): bifurcació de systemd de [GSYT Productions](https://github.com/GSYT-Productions), l'empresa que fa BunnyPad. Es descriu com «el gestor de sistema i serveis systemd, sense l'estúpida verificació d'edat».
- [fightthesystemd](https://github.com/Pingasmaster/fightthesystemd): bifurcació de systemd d'Adrian Noyes, especialista en ciberseguretat defensiva. Es descriu com «systemd sense les ximpleries: sense verificació d'edat ni lighthouse integrat».
- [systemd-saneagecheck](https://github.com/HaplessIdiot/systemd-saneagecheck): bifurcació de systemd de Collin (HaplessIdiot), desenvolupador aficionat a Steam Deck i OpenMandriva Linux. Es descriu com «el gestor de sistema i serveis systemd amb opcions per eludir la verificació d'edat i configurar-ne la freqüència de consulta».
- [unshitted-systemd](https://github.com/Codiak540/unshitted-systemd): bifurcació de systemd de Codiak540. Es descriu com «una bifurcació de systemd que aspira a millorar-lo. Demandeu-me, Califòrnia».

## Microprogramari

- [DB48X](https://48calc.org/): microprogramari de calculadora de codi obert. Els desenvolupadors van rebutjar directament el rastreig d'edat, cosa que posa en relleu l'excés d'una legislació prou àmplia per abraçar dispositius que no són de propòsit general. ([Declaració](https://github.com/c3d/db48x/blob/dev/LEGAL-NOTICE.md), [#2](https://x.com/lundukejournal/status/2027358439991615715))

## Maquinari

- [Ageless Device](https://agelesslinux.org/hardware.html): sèrie de dispositius informàtics basats en RISC-V (Milk-V Duo S, SoC SG2000 amb NPU de 0,5 TOPS) en tres nivells de 6 a 18 dòlars dels Estats Units d'Amèrica, amb Ageless Linux preinstal·lat i etiquetats com a no conformes amb l'AB 1043. Dissenyats per distribuir-se a infants en fires de ciència, tecnologia, matemàtiques i enginyeria, biblioteques i trobades *maker* com a acte de desobediència civil. Les instruccions de muntatge i els dissenys de maquinari es publiquen sota la llicència Unlicense.

## Recursos

- [DoesItAgeVerify](https://github.com/BryanLunduke/DoesItAgeVerify): llista mantinguda per Bryan Lunduke que fa seguiment de l'estat de compliment de la verificació d'edat en sistemes operatius de codi obert. Inclou projectes que preveuen implementar-la, projectes que s'hi neguen i l'estat actual de la legislació aprovada i proposada.

## Com contribuir-hi

Els afegits i modificacions a aquesta llista són molt benvinguts. Si coneixeu un projecte FLOSS que s'hagin posicionat púbicament contra la verificació d'edat, no necessàriament a nivell de sistema operatiu, si us plau obriu un pull request i afegiu-lo a la secció corresponent. Si us plau, incloeu-hi un enllaç a la declaració del desenvolupador o a la font pertinent.

## Llicència

[CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)
