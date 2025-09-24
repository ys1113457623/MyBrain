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
- [x] Unblock Suryam on Framer Webengage
- [x] Unblock Suryam on RCB Through Companion
- [x] Unblock Janardan on topics
- [x] Populate AI Interview Issue Activity For Sales Team
- [x] Analytics On Online MBA Page

##### 👎 Question that i have doubt about...
- 

---
# 📝 Notes
- Janardan
  - Test Btn Changes On Production [X]
  - Why Ai Button Not Working [X]
- Suryam
	- Webengage [X] Pending On Abhishek
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