# Eval Command & Repeat Eval Button.

## command: 
Trigger: `EVAL:`
Code:
```
$nomention
$if[$authorID==YOUR_USER_ID]
$eval[$message]

$title[Code Ran:]
$description[$message]
$footer[$authorID]
$addButton[no;runRepeat;Run Again;danger]
$endif
```

## interaction:
Trigger: `$onInteraction[runRepeat]`
Code:
```
$nomention
$if[$getEmbedData[$channelID;$messageID;1;footer]==$authorID]
$eval[$getEmbedData[$channelID;$messageID;1;description]]
$removeButtons
$description[$getEmbedData[$channelID;$messageID;1;description]]
$title[Code Ran Again $getTimestamp:]
$footer[$authorID]
$addButton[no;runRepeat;Run Again;danger]
$endif
```

