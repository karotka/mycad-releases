# MyCAD — ke stažení

2D kreslení a 3D modelování nad přesným geometrickým jádrem, s příkazovou
řádkou. Tenhle repozitář drží jenom hotové buildy — zdrojový kód je jinde a
je soukromý.

**Vyzkoušet bez instalace:** [mycad.online](https://mycad.online/) — celá
aplikace běží v prohlížeči. Práce se soubory je jen v desktopové verzi.

## Stáhnout

Poslední verze je vždy na stránce
[**Releases**](https://github.com/karotka/mycad-releases/releases/latest).

| | |
|---|---|
| **Windows** | `MyCAD-<verze>-setup.exe` (instalátor) nebo `MyCAD-<verze>-portable.exe` (bez instalace) |
| **macOS, Apple Silicon** | `MyCAD-<verze>-arm64.dmg` |
| **macOS, Intel** | `MyCAD-<verze>.dmg` |
| **Linux** | `MyCAD-<verze>.AppImage` |

## ⚠️ Windows: stažený soubor se jmenuje divně — přejmenuj ho

Žádný build není podepsaný, a Edge i Chrome na to reagují tak, že **souboru
nedají jméno ani příponu**. Ve `Stažených souborech` pak najdeš něco jako:

```
Nepotvrzeno 889533.crdownload
```

To **není poškozené ani nedostažené stahování** — je to celý, funkční
instalátor, kterému prohlížeč jen odmítl vrátit jeho jméno. Nic nestahuj
znovu, jen ho přejmenuj:

1. V `chrome://downloads` (nebo `edge://downloads`) dej u souboru
   **Ponechat** / **Zachovat**.
2. Pokud už soubor leží ve `Stažených souborech` jako
   `Nepotvrzeno ….crdownload`, přejmenuj ho na `MyCAD-<verze>-setup.exe`.
   - Přípony nejsou vidět? V Průzkumníku *Zobrazení* → *Zobrazit* → zapnout
     **Přípony názvů souborů**, jinak se `.crdownload` neodstraní.
3. Spusť ho. Windows hlásí „Windows protected your PC" → *Více informací* →
   *Přesto spustit*.

Instaluje se pro uživatele, bez práv správce, do
`C:\Users\<ty>\AppData\Local\Programs\MyCAD`.

## Ostatní systémy

- **macOS** hlásí „MyCAD is damaged and can't be opened". Poškozená není, jen
  nepodepsaná: `xattr -cr /Applications/MyCAD.app`.
- **Linux**: `chmod +x MyCAD-<verze>.AppImage` a spustit.

## Co umí

**Kreslení a modelování.** 2D entity s uchopovacími body a osnapy, 3D tělesa
nad OpenCascade — zaoblení, skořepiny, booleovské operace, tažení po cestě,
šroubovice, plochy (LOFT, THICKEN, SURFOFFSET, SURFSCULPT) a skutečné závity,
které řežou materiál podle normy. Přesná geometrie, ne síť trojúhelníků,
takže z modelu vypadne výrobní soubor i výkres.

**Výkres.** Listy s rámečkem a okrajem, vlastní záložky, viewporty ukazující
model ve zvoleném měřítku — včetně pohledu ze směru s odstraněnými
neviditelnými hranami, který se sám překreslí, když se model změní. Tisk
listu v jeho velikosti, PDF.

**Kóty, které něco vědí.** Kóta posazená přichycením na geometrii si pamatuje,
na čem leží, a jde s ní, když se objekt posune nebo zvětší. A obráceně:
`DIMCONSTRAINT` z ní udělá řídicí, takže napsané číslo pohne geometrií.

**Výměna dat.** DXF tam i zpět (včetně bloků, vrstev, typů čar a kót), STEP,
STL, PDF jako podklad, DWG převodem (skripty jsou v instalaci), G-code pro
plotr i gravírku.

**České znaky.** Tahové písmo kreslí celou českou a slovenskou abecedu plus
`° ± × ⌀` a pomlčky — na plotru i v exportu.

**Pro agenty.** Každý příkaz je dosažitelný přes MCP toutéž cestou, kterou ho
dělá člověk. Není druhé API, které by zaostávalo.
