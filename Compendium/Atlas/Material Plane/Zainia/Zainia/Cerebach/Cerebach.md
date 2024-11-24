---
type: region
locations:
- "[[Zainia]]"
tags:
- location/kingdom
headerLink: "[[Cerebach#Cerebach]]"
---

![[banner.jpg|banner]]
###### Cerebach
<span class="sub2">:FasChessRook: Kingdom</span>
___

> [!quote|no-t] SUMMARY
>Cold Siberian like country in the north.  Known as the Empire of Dragons.  Its ruler Ceberas the Silver Dragon is dead.  

Axefall - The northern region of the Empire of Ceberach, the Axefall Tundra, has large minorities of Dwarves, Tieflings, and Snow Elves, in addition to the Dragonborn and Humans usually found across the Empire. The region was ruled by the Dwarves of Thavarr until the Diamondwing Dragons froze their fortress from within in 1752 AZ, nearly 900 Cycles (300 years) ago. Yrda is the only port in Ceberach, but this far north, it remains frozen Cycle-round. Magic or Red Dragonborn assistance is usually used to facilitate long-distance trade as far as Dazazcor.

The Roselands - The southern region of the Empire of Ceberach, from the Wyrmspike Mountains in the south to the Keqvas hills. Mostly forested and fens, home to many Silver, Red and Copper Dragons in the highlands and Green, Black, White and Bronze in the Fens between. Dak’rose, the capital, is the only major urban city worldwide with a majority Dragonborn population.

#### marker
> [!column|flex 3]
> > [!hint]-  NPC's
> > <input type="checkbox" id="npc"/><ul class="sortMenu"><li class="sortIcon">:RiListSettingsLine:<ul class="dropdown npcedit"><li><label for="npc" class="directLabel active">Direct Links Only</label></li><li><label for="npc" class="childLabel">Include Sub-Locations</label></li></ul></li></ul>
> >```dataviewjs
dv.container.className += ' npcDirect';
dv.list(dv.pages('"Compendium/NPC\'s"')
 .where(p => p.file.outlinks.includes(dv.current().file.link))
.sort(p => p.file.link)
.map(p => p.headerLink), 1);
>>```
>>```dataviewjs
dv.container.className += ' npcChild';
let page = dv.current().file.path;
let pages = new Set();
let stack = [page];
while (stack.length > 0) {
let elem = stack.pop();
let meta = dv.page(elem);
if (!meta) continue;
for (let inlink of meta.file.inlinks.concat(meta.file.outlinks).array()) {
let locations = dv.page(inlink.path);
if (!locations || pages.has(inlink.path) || inlink.path === meta.locations?.[0]) continue;
 if (dv.array(locations.locations).join(", ").includes(meta.file.path)) {
 pages.add(inlink.path);
 stack.push(inlink.path);
}}}
let data = Array.from(pages)
.filter(p => dv.page(p)?.type === "npc")
.map(p => dv.page(p).headerLink)
.sort((a, b) => {
if (a < b) return -1;
if (a > b) return 1;
return 0;
});
dv.list(data);
> 
>> [!example]- LOCATIONS
>>```dataview
LIST WITHOUT ID headerLink
FROM "Compendium/Atlas/Material Plane/Zainia/Zainia/Cerebach"
WHERE type= "locale"
SORT file.name ASC
>
>> [!note]- HISTORY
>>```dataview
LIST WITHOUT ID headerLink
FROM "Session Notes" AND [[Cerebach]]
SORT file.ctime DESC
#### marker