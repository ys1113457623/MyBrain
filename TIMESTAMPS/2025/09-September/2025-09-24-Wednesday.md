---
created:
  - <% tp.file.creation_date() %>
tags:
  - DailyNote
---
<< [[Purpose/Routine/Daily/<%fileDate = moment(tp.file.title, 'DD-dddd').subtract(1, 'd').format('YYYY/MM-MMMM') %>/<%fileDate = moment(tp.file.title, 'DD-dddd').subtract(1, 'd').format('DD-dddd') %>|Yesterday]] | [[Purpose/Routine/Daily/<% fileDate = moment(tp.file.title, 'DD-dddd').add(1, 'd').format('YYYY/MM-MMMM') %>/<% fileDate = moment(tp.file.title, 'DD-dddd').add(1, 'd').format('DD-dddd') %>|Tomorrow]] >>

---
### 📅 Daily Questions

##### 🚀 One+ thing I plan to accomplish today is...
- [ ] Unblock Suryam on Framer Webengage
- [ ] Unblock Suryam on RCB Through Companion
- [ ] Unblock Janardan on topics

##### 👎 Question that i have doubt about...
- 

---
# 📝 Notes
- Janardan
  - Test Btn Changes On Production
- Suryam
	- Webengage
	- RCB Approch 
---
### Notes created today
```dataview
List FROM "" WHERE file.cday = date("<%tp.date.now('YYYY-MM-DD')%>") SORT file.ctime asc
```

### Notes last touched today
```dataview
List FROM "" WHERE file.mday = date("<%tp.date.now('YYYY-MM-DD')%>") SORT file.mtime asc
```