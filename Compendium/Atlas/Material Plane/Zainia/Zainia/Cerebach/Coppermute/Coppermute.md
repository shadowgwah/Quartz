---
type: locale
locations:
- "[[Cerebach]]"
tags:
 - location/city
headerLink: "[[Coppermute#Coppermute]]"
---

![[banner.jpg|banner]]
###### Coppermute
<span class="sub2">:FasCity: City</span>
___

> [!quote|no-t] SUMMARY
>Description of the city Coppermute.

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
const page = dv.current().file.path;
const pages = new Set();
const stack = [page];
while (stack.length > 0) {
const elem = stack.pop();
const meta = dv.page(elem);
if (!meta) continue;
for (const inlink of meta.file.inlinks.concat(meta.file.outlinks).array()) {
const locations = dv.page(inlink.path);
if (!locations || pages.has(inlink.path) || inlink.path === meta.locations?.[0]) continue;
 if (dv.array(locations.locations).join(", ").includes(meta.file.path)) {
 pages.add(inlink.path);
 stack.push(inlink.path);
}}}
const data = Array.from(pages)
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
FROM "Compendium/Atlas/Material Plane/Zainia/Zainia/Cerebach/Coppermute"
WHERE type= "landmark"
SORT file.name ASC
>
>> [!note]- HISTORY
>>```dataview
LIST WITHOUT ID headerLink
FROM "Session Notes" AND [[Coppermute]]
SORT file.ctime DESC