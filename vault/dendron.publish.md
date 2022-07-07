---
id: m262avkzc65xlfq2elg85mz
title: Publish
desc: ''
updated: 1657129929910
created: 1657129912966
---


# Change published page width 


Created a full link snippet

	"full_link": {
		"prefix": "full",
		"scope": "markdown,yaml",
		"body": "[Full display link]($1)",
		"description": "Full display link"
	}


It's possible to make a custom css them for dendron publishing

Add this to the custom css

.ant-layout.side-layout-main{
    max-width: 12000px !important;
}

.ant-layout.ant-layout-has-sider{
    width: calc(max((100% - 992px) / 5, 0px) + 200px) !important;
    padding-left: calc((100% - 992px) /5) !important;
}

And follow https://wiki.dendron.so/notes/jknrdi492m8nhq7mw4faydu/

