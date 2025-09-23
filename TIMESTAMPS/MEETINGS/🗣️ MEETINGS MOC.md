[[+Home]] %% tags:: #MOC %% 

# Meetings MOC
Meetings are timestamped events with other people, where information is exchanged and collected. Meeting notes are intrinsically ephemeral. They're stored in a separate Space than other Umami notes (`Timestamps/Meetings`) and rarely reviewed. If there's information in a meeting that needs to be accessed later, it should be moved into a more evergreen note in the Umami folder. 

**Template:** [[Template, Meeting]]
```meta-bind-button
label: New Meeting
icon: ""
hidden: false
class: ""
tooltip: ""
id: ""
style: default
actions:
  - type: templaterCreateNote
    templateFile: EXTRAS/TEMPLATES/Template, Meeting Notes.md
    folderPath: TIMESTAMPS/MEETINGS
    fileName: TKTK
    openNote: true
    openIfAlreadyExists: false

```
## Meeting Notes

```dataview
TABLE file.cday as Created, summary
FROM "Timestamps/Meetings" and -#MOC
SORT file.cday DESC
```