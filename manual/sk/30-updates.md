# Aktualizácie

Omarchy a vaše balíčky sa udržiavajú aktuálne cez _Update > Omarchy_ v ponuke Omarchy (`Super + Space`).

Samotné Omarchy sa inštaluje ako bežné balíčky pacman z [úložiska balíčkov Omarchy](https://github.com/omacom-io/omarchy-pkgs), takže aktualizácia nainštaluje [najnovšie vydanie Omarchy](https://github.com/omacom/omarchy/releases), spustí všetky čakajúce migrácie, aby sa váš systém zosúladil s najnovšou verziou, a aktualizuje všetky systémové balíčky zo [zrkadla Omarchy Arch Mirror](https://github.com/omacom-io/omarchy-mirror) a [AUR](https://aur.archlinux.org/) (ak máte nainštalované nejaké balíčky z AUR).

Keď vyjdú nové vydania, napravo od vašich hodín sa zobrazí ikona kruhovej šípky. Kliknite na ňu a proces aktualizácie sa spustí.

![update-available](images/update-available.webp)

### Štyri kanály

Omarchy sa aktualizuje prostredníctvom štyroch kanálov: stable, RC, edge a dev. Nové inštalácie začínajú na kanáli stable, ktorý sleduje [oficiálne vydania](https://github.com/omacom/omarchy/releases/), ako aj [stabilné zrkadlo Omarchy Arch](https://github.com/omacom-io/omarchy-mirror), ktoré zaostáva za najnovšou verziou o jeden mesiac, aby sme mohli zachytiť všetky nové nekompatibility, ktoré vyžadujú zmeny konfigurácie, skôr než ľuďom spôsobia problémy.

Ak však chcete pomôcť odhaľovať tieto potenciálne problémy, môžete používať kanál edge. Vďaka tomu budú vaše balíčky Omarchy sledovať najnovšie vývojové zostavenia a budete môcť aktualizovať na najnovšie balíčky Arch hneď, ako budú k dispozícii. Mali by ste to robiť len vtedy, ak máte skúsenosti s Linuxom a viete, ako obnoviť systém, ktorý má problémy.

Pred každým novým hlavným vydaním budeme vykonávať finálne overovanie pomocou kanála RC. Ak máte záujem pomôcť s finálnym dolaďovaním, príďte sa porozprávať do #omarchy-release-candidates na Discorde.

Nakoniec je tu kanál dev, ktorý prepája Omarchy priamo s git checkoutom zdrojového kódu v `~/omarchy` v kombinácii s balíčkami edge. Tento kanál by ste mali používať len vtedy, ak ste skúsený používateľ Linuxu, priamo pracujete na Omarchy a ste ochotní tolerovať, že sa niečo pokazí.

Medzi kanálmi môžete prepínať pomocou _Update > Channel_ v ponuke Omarchy (alebo `omarchy-channel-set` v termináli).

### Prepínanie jadier

Omarchy spúšťa svoje vlastné jadro `linux-omarchy`, ale popri ňom môžete mať nainštalované aj iné jadrá, napríklad štandardné jadro `linux` z Archu alebo experimentálne zostavenie, ktoré testujete. Keď ich je viac ako jedno, _Update > Kernel_ v ponuke Omarchy ich zobrazí so začiarknutím vedľa toho, ktoré sa spúšťa predvolene. Vyberte iné, raz zadajte svoje heslo a po ďalšom reštarte sa systém spustí s ním. Ostatné jadrá zostanú v ponuke zavádzania, takže si stále môžete ručne vybrať jedno z nich, ak vám nové predvolené jadro spôsobí problémy. V termináli použite `omarchy-kernel` na zobrazenie aktuálneho predvoleného jadra, `omarchy-kernel list` na zobrazenie nainštalovaných jadier a `omarchy-kernel set <kernel>` na prepnutie.

### Aktualizácie firmvéru

Nielen vaše balíčky zastarávajú. Mnohé notebooky a periférne zariadenia poskytujú firmvér pre BIOS, SSD a dokovacie stanice prostredníctvom služby Linux Vendor Firmware Service a _Update > Firmware_ v ponuke Omarchy stiahne a nainštaluje všetko, čo je pre váš hardvér k dispozícii. Pri prvom spustení nainštaluje `fwupd`. Veľa firmvéru je možné zapísať len počas reštartu, takže sa nečudujte, ak budete oň požiadaní.

### Varovanie pred priamymi aktualizáciami cez pacman/yay

Ak už Arch poznáte, možno vás bude lákať jednoducho spustiť `pacman -Syu` alebo `yay -Syu` sami, ale ak to urobíte, prídete o snímku, migrácie a aktualizácie konfigurácie, ktoré Omarchy spúšťa spolu s novými balíčkami. Preto Omarchy priamu aktualizáciu systému zastaví a namiesto toho vás nasmeruje na `omarchy update`. (Ak naozaj viete, čo robíte, ochranný mechanizmus vám povie, ako ho pre jednu transakciu obísť.)

### Vrátenie problematických aktualizácií

Ak po vykonaní aktualizácie narazíte na problém, môžete systém vrátiť do stavu zo snímky vytvorenej pred aktualizáciou. Jednoducho reštartujte systém a v ponuke zavádzania vyberte snímku z doby pred spustením aktualizácie.

![bootloader](images/bootloader.webp)

Ak sa vaše konfiguračné súbory nejako poškodili, môžete tiež vykonať preinštalovanie Omarchy pomocou `omarchy reinstall` v termináli. Tým sa preinštalujú všetky predvolené balíčky Omarchy, prepnete sa na stable a zníži sa verzia všetkých balíčkov, ktoré sú príliš nové, a obnovia sa všetky konfiguračné súbory. Upozorňujeme, že tým sa prepíšu všetky vaše používateľské zmeny predvolených nastavení Omarchy!
