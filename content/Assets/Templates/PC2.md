---
type: pc
tags:
- race/{race}
- class/{class}
headerLink: "[[name#name]]"
level: 
race: 
class: 
subClass: ""
cover: "/Assets/Images/Party/"
---

###### <% name %>
:FasPerson: Player Character &nbsp; | &nbsp; :FasQuoteLeft: (insert quote) :FasQuoteRight:

---
> [!infobox|no-t right]
> ![[]]  ^put pic here
> ###### Details:
>Type | Stat |
> | ---- | ---- |
> | :FasCrown: Level   | `=this.level` |
> | :RiSwordFill: Class | `=this.class` |
> | :FasHandFist: Archetype | `=this.subClass` |
> |  :FasUserGroup: Race | `=this.race` |

> [!quote|no-t]
>

#### marker
> [!column|flex 3]
>> [!info]- STORYLINES:
>>```dataview
>>LIST WITHOUT ID headerLink
>>FROM "Compendium/Party/Quests" AND [[<% name %>#<% name %>]]
>>SORT file.ctime DESC
>
>>[!note]- HISTORY
>>```dataview
>>LIST WITHOUT ID headerLink
>>FROM "Session Notes" AND [[<% name %>#<% name %>]]
>>SORT file.ctime DESC