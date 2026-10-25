# Klaviatūra, pelė, jutiklinė plokštė

Hyprland leidžia itin detaliai konfigūruoti visus įvesties įrenginius. Galite pakeisti klaviatūros kartojimą taip, kad jis būtų viršgarsiniai greitas, arba priversti jutiklinę plokštę naudoti natūralų slinkimą. Visa tai keičiate faile `~/.config/hypr/input.lua`, kurį taip pat galite pasiekti per _Setup > Input_ Omarchy meniu (`Super + Space`). Viskas, ką ten nustatysite, pakeis Omarchy numatytuosius nustatymus.

Štai pavyzdys:

```lua
hl.config({
  input = {
    -- Use multiple keyboard layouts and switch between them with Left Alt + Right Alt
    kb_layout = "us,dk",
    kb_options = "omarchy:shift_caps_compose,grp:alts_toggle",

    -- Change speed of keyboard repeat
    repeat_rate = 40,
    repeat_delay = 600,

    -- Increase sensitivity for mouse/trackpad (default: 0)
    sensitivity = 0.35,

    touchpad = {
      -- Use natural (inverse) scrolling
      natural_scroll = true,

      -- Use two-finger clicks for right-click instead of lower-right corner
      clickfinger_behavior = true,

      -- Control the speed of your scrolling
      scroll_factor = 0.3,
    },
  },
})

-- Scroll faster in the terminal
o.window("(Alacritty|kitty|foot)", { scroll_touchpad = 1.5 })
```

Visas įvesties parinktis galite [peržiūrėti visas įvesties parinktis](https://wiki.hypr.land/Configuring/Basics/Variables/#input) Hyprland wiki puslapyje, skirtame įvestims.

CapsLock veikia kaip įprastas Caps Lock, o `Shift + CapsLock` yra compose klavišas [greitiems jaustukams](07-hotkeys.md#quick-emojis) ir [kitiems užbaigimams](07-hotkeys.md#quick-completions). Jei compose klavišą verčiau norėtumėte turėti kitur, `kb_options` pakeiskite `omarchy:shift_caps_compose`. Pavyzdžiui, tai perkelia compose klavišą į Right Alt:

```lua
hl.config({
  input = {
    kb_options = "compose:ralt",
  },
})
```

### Jutiklinės plokštės gestai

Taip pat galite įjungti [jutiklinės plokštės gestus](https://wiki.hypr.land/Configuring/Advanced-and-Cool/Gestures/), pavyzdžiui, braukimą trimis pirštais, norint keisti darbo sritis:

```lua
hl.gesture({ fingers = 3, direction = "horizontal", action = "workspace" })
```

Dell XPS nešiojamuosiuose kompiuteriuose su haptine jutikline plokšte taip pat galite nustatyti paspaudimo stiprumą į žemą, vidutinį arba aukštą skiltyje _Trigger > Hardware > Touchpad Haptics_.

### Rašymas kinų, japonų ir kitomis kalbomis

Pasirinkite japonų, korėjiečių, kinų (supaprastintą, Pinyin), Taivano (Zhuyin) arba Honkongo (Cangjie), kai diegimo programa paklaus apie jūsų klaviatūrą. Omarchy automatiškai sukonfigūruoja klaviatūrą ir atitinkamą įvesties variklį, taip pat ir neprisijungus atliekamos pirmojo paleidimo sąrankos metu. Japonų kalba naudoja Mozc, korėjiečių kalba naudoja standartinį dviejų rinkinių Hangul, supaprastinta kinų kalba naudoja Pinyin, Taivanas naudoja Chewing standartinį Zhuyin išdėstymą, o Honkongas naudoja Cangjie su Honkongo rašmenų formomis. Japonų (JAV klaviatūra) suteikia Mozc su JAV klaviatūros išdėstymu. Hangul, Zhuyin ir Cangjie klavišai lieka standartinėse vietose, net kai lotyniškas raides rašote naudodami Dvorak, Colemak arba AZERTY. Jei Hangul arba Chewing pridėjote anksčiau, panaikinkite jo pasirinkimą ir pasirinkite jį iš naujo skiltyje _Setup > Typing > Input Methods_, kad jo klavišai būtų perkelti ten; Omarchy variklio, kuriuo jau rašote, neliečia.

Rašymas prasideda lotynišku režimu. Paspauskite `Super + I`, kad pereitumėte per sukonfigūruotus įvesties metodus, ir `Super + Shift + I`, kad grįžtumėte atgal. Bakstelėkite `Shift` atskirai, kad iš įvesties metodo, pavyzdžiui, Pinyin, išeitumėte į lotyniškas raides, ir bakstelėkite jį dar kartą, kad grįžtumėte, kaip veikia Sogou, Microsoft Pinyin ir macOS; `Shift` kartu su raide vis tiek įveda didžiąją raidę. Japonų klaviatūrose 全角/半角 perjungia įvestį, 変換 ją įjungia, o 無変換 ją išjungia. Su korėjiečių kalba 한/영 perjungia Hangul, o 한자 konvertuoja į Hanja, nesvarbu, ar jūsų klaviatūra turi tam skirtus klavišus, ar jiems siunčia Right Alt ir Right Ctrl, kaip tai daro daugelis nešiojamųjų kompiuterių, todėl Right Alt ir Right Ctrl ten nėra paprasti modifikavimo klavišai; diktavimo push-to-talk lieka priskirtas F9. `Ctrl + Space` lieka prieinamas Tmux ir Herdr; `Shift + CapsLock` lieka compose klavišu.

Klaviatūros indikatorius pasirodo dešinėje juostos pusėje, kai turite kelis klaviatūros išdėstymus arba įvesties metodus. Spustelėkite jį, kad perjungtumėte įvesties kalbas; japonų kalba hiraganai rodo あ. Norėdami pasirinkti japonų rašmenis, perjunkite į japonų kalbą, įveskite žodį, pavyzdžiui, `nihongo`, tada dukart paspauskite Space. Paspauskite Enter, kad patvirtintumėte savo pasirinkimą. Jei taip pat turite kelis klaviatūros išdėstymus, dešiniuoju pelės mygtuku spustelėkite indikatorių, kad juos pereitumėte.

Naudokite _Setup > Typing > Keyboard Layouts_, kad pasirinktumėte išdėstymus, pavyzdžiui, anglų ir prancūzų, iš tų pačių variantų, kurie siūlomi diegimo metu. Naudokite _Setup > Typing > Input Methods_, kad pasirinktumėte, kurie kompozicijos varikliai yra aktyvūs. Abu parinkikliai atsidaro Omarchy meniu, o jūsų dabartiniai pasirinkimai yra pažymėti. Spustelėkite arba paspauskite Enter, kad perjungtumėte pasirinkimą; kiekvienas pakeitimas pritaikomas iškart. Panaikinus įvesties metodo pasirinkimą, jis pašalinamas iš ciklo jo neišdiegiant; klaviatūra lieka prieinama.

Paleiskite `omarchy setup keyboard` arba `omarchy setup input`, kad atidarytumėte tuos pačius parinkiklius. Norėdami iš komandinės eilutės pridėti vieną kalbą, naudokite `omarchy setup input mozc`, `hangul`, `pinyin`, `chewing` arba `cangjie5`. Quick, Boshiamy ir Array yra tame pačiame pakete kaip Cangjie ir pasirodo Input Methods parinkiklyje. Jūsų pasirinktiniai perjungimo klavišai išsaugomi. Norėdami naudoti alternatyvius variklių išdėstymus arba klavišus, įdiekite `fcitx5-configtool` naudodami `omarchy pkg add fcitx5-configtool` ir paleiskite jį iš terminalo. Įvesties kalbos pasirinkimas nepakeičia darbalaukio kalbos. Pasirinkus japonų, korėjiečių arba kinų kalbą skiltyje _Setup > Language_, pridedamas jos įvesties metodas, kai dar neturite nė vieno.

Naudokite `Super + I`, kad pereitumėte per įvesties metodus arba klaviatūros išdėstymus, ir `Super + Shift + I`, kad grįžtumėte priešinga kryptimi, todėl turėdami tris sukonfigūruotus galite judėti tarp dviejų kaimynų. Įvesties indikatorius dešinėje juostos pusėje pasirodo tik tada, kai sukonfigūruotas daugiau nei vienas įvesties metodas arba išdėstymas. Šis darbalaukio susiejimas veikia kartu su jūsų esamais Fcitx perjungimo klavišais; galite jį pakeisti faile `~/.config/hypr/bindings.lua`. Įvesties varikliai ir compose sekos naudoja [Fcitx5](https://fcitx-im.org/) paslaugą, jau veikiančią kiekvienoje sesijoje.

### ALT naudojimas kaip SUPER

Kai kuriose klaviatūrose nepatogu naudoti pagrindinį meta klavišą (Windows/cmd klavišą) kaip SUPER. Vietoj to galite jį pakeisti į ALT naudodami šį pakeitimą:

```lua
hl.config({
  input = {
    kb_options = "omarchy:shift_caps_compose,altwin:swap_alt_win",
  },
})
```
