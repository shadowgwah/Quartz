<%*  
// ###########################################################  
// Helper Functions  
// ###########################################################

// Convert string to camelCase  

// ###########################################################  
// Main Code Section  
// ###########################################################

// Call modal form  
const result = await MF.openForm('PC');

// Declare variables after form returns values  
const level = result.Level.value;  
const subclass = result.Subclass.value;  
const classs = result.Classs.value;  
const name = result.Name.value;  
const race = result.Race.value;

// Rename & open note  
await tp.file.rename(name);  
await app.workspace.getLeaf(true).openFile(tp.file.find_tfile(name));  
new Notice().noticeEl.innerHTML = `<span style="color: green; font-weight: bold;">Finished!</span><br>New PC <span style="text-decoration: underline;">${name}</span> added`;  
_%>

---
type: pc
tags:
- name/<% name.toLowerCase() %>
- race/<% race.toLowerCase() %>
- level/<% level %>
- class/<% classs.toLowerCase() %>
- subclass/<% subclass.toLowerCase() %>
headerLink: "[[<% name %>#<% name %>]]"
level: <% level %>
race: <% race %>
class: <% classs %>
subClass: "<% subclass %>"
cover: "/Assets/Images/Party/<% name %>.png"

---

###### <% name %>

:FasPerson: Player Character &nbsp; :FasQuoteLeft:  ""   :FasQuoteRight:

---
> [!infobox|no-t right]
> ![[<% name %>.png]]
> ###### Details:
>Type | Stat |
> | ---- | ---- |
> | :FasCrown: Level   |  <% level %> |
> | :RiSwordFill: Class | <% classs %> |
> | :FasHandFist: Archetype | <% subclass %> |
> |  :FasUserGroup: Race | <% race %> |

> [!quote|no-t]
> ""

#### marker
> [!column|flex 3]
>> [!info]- STORYLINES:
>>```dataview
>>LIST WITHOUT ID headerLink
>>FROM "Compendium/Party/Quests" AND [[<% name %>]]
>>SORT file.ctime DESC
>
>>[!note]- HISTORY
>>```dataview
>>LIST WITHOUT ID headerLink
>>FROM "Session Notes" AND [[<% name %>]]
>>SORT file.ctime DESC
