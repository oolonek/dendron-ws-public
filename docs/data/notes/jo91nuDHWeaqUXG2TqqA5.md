
# Meeting Notes

This is a video of keeping meeting notes in Dendron. Meeting notes are kept as **journal notes** on a per-project basis. 

<a href="https://www.loom.com/share/c04dd4b3c82a412b82b1f9f75e2291bd">  <img style="" src="https://cdn.loom.com/sessions/thumbnails/c04dd4b3c82a412b82b1f9f75e2291bd-with-play.gif"> </a>

## Resources

Settings and files used for the above video. 

- project schema
```yml
- id: pro
  title: pro
  desc: ""
  parent: root
  namespace: true
  children:
    - people
    - meet
    - todo
    - retrospective
- id: people
- id: meet
- id: todo
- id: retrospective
```

- journal specific settings

```json
{
    "dendron.defaultJournalAddBehavior": "childOfDomainNamespace",
    "dendron.defaultJournalDateFormat": "Y.MM.DD",
}
```
