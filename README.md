# Hopper Boost

Fabric-Mod fuer Minecraft 1.21.11 (nur Server noetig). Trichter **und Trichter-Loren** bewegen pro Tick
bis zu **192 Items (3 Stacks)** statt 1 Item alle 8 Ticks (Lore: alle 4 Ticks).

## Bauen

    ./gradlew build          (Windows: .\gradlew.bat build)

Die fertige Mod liegt danach in `build/libs/hopperboost-1.0.0.jar` (nicht die `-sources.jar`).

## Konfiguration

`config/hopperboost.properties` (wird beim ersten Start erzeugt):

    itemsPerTick=192

Erlaubt sind Werte von 1 bis 4096. Gilt fuer jeden Trichter und jede Trichter-Lore einzeln.

## So funktioniert es

- Trichter: Cooldown wird vor dem Vanilla-Tick auf 0 gesetzt (Trichterketten werden nicht ausgebremst),
  danach wird "Item ausgeben + Item einsaugen" wiederholt, solange etwas bewegt wurde, maximal `itemsPerTick` mal pro Tick.
- Trichter-Lore: gleiche Logik ueber `canOperate()` (einsaugen aus Behaeltern und Item-Entities), Cooldown 0.
