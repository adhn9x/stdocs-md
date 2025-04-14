# Send a Message with Formats

When sending a text message to a 1-on-1 chat or a group chat, thecontent field of text objects can be formatted into rich text. Formatting is also supported for interactive message description element. Here are the supported formatting methods:

# Basic Formatting using Markdown

## Text Style

|Element|Markdown Syntax|Effect|
|---|---|---|
|Bold|\*\*bold\*\* or \_\_bold\_\_|bold|
|Italic|\*italic\* or \_italic\_ Remarks: For the single underscore syntax, it is only activated by placing spaces before and after.|italic|
|Inline Code|\`inline code\`|![](data:image/png;base64,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)|

## Line Break

To make a new line, use the newline character (i.e., \\n) or the <br /> line break tag (note the space in between).

## List

|Element|Markdown Syntax|Effect|
|---|---|---|
|Bulleted List|- Item 1 - Item 2 Signs supported: asterisks \* , hyphens - , and plus signs + Code Sample: "content" : "- Item 1\\n- Item2"  Copy||
|Numbered List|1. Item 1 2. Item 2 Code Sample: "content" : "1. Item 1\\n2. Item2" ![](/static/media/copy-icon.42c9a7a8.svg) Copy|1. Item 1 2. Item 2|

## Code Block

|Element|Markdown Syntax|Effect|
|---|---|---|
|Code Block|\`\`\` code block \`\`\` or ~~~ code block ~~~||

## Escape a Markdown Format

To escape a certain markdown format, use**two** "\\" characters. E.g., "\\\\\_"

# Advanced Formatting

## Mention

In messages sent to a group chat, you can mention a particular user or all group chat members by including a mention tag by following the format below:

1. To mention a particular user using his/her email:**<mention-tag target="seatalk://user?email=xxxx@xxx.com"/>**
2. To mention a particular user using his/her SeaTalk ID:**<mention-tag target="seatalk://user?id=xxxxxxx"/>**
3. To mention all group chat members:**<mention-tag target="seatalk://user?id=0"/>**

Note:

* Notifying all group chat members will succeed only if the "**Notify all members with @All**" setting is turned on in the group chat

Was this document helpful?

No

Yes