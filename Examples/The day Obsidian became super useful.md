---
tags:
  - Imported/me
  - experimental
---
When I discovered Obsidian had Markdown integration, I saw the potential for taking notes on the go using any PC and emailing them to myself to add to my 2nd brain vault when I got home (Though I would still need to maintain the habit of periodically using `Ctrl-S` when I was away from Obsidian). Markdown files have about the same data density as normal text files and less than proprietary files that use a markup language for formatting. Obsidian's backlinks feature makes building an Obsidian [vault](C:\Users\rtczi\OneDrive\Documents\2nd brain vault)slightly more useful than [Hypertext](https://en.wikipedia.org/wiki/Hypertext).
## Hyperlinks
Something I learned from [Twine](https://twinery.org) was how to quickly and easily embed [hyperlinks](https://zigguratpublishinghouse.blogspot.com) into my notes. This is especially useful when referencing other documents like my [[Gratitude Journal]].
### Hard Links, etc.
You can also create duplicates of a file in two places (on the same volume) using the command prompt (or *PowerShell* if that doesn't work) by using the command:
```PowerShell
mklink /H C:\path\to\hard_link C:\path\to\source_file
```
You can also use the same command to make **Junction points**: `mklink /J C:\d D:\`
Actually, the real syntax is *a lot* more complicated:
```PowerShell
mklink /J C:\path\to\junction C:\path\to\target_dir
```
The syntax is ***even more*** complicated for mounting a volume to a directory:
```PowerShell
mountvol C:\mnt \\?\Volume{12345678-1234-1234-1234-1234567890ab}\
```
Dave Plummer has more details in the [YouTube video](https://youtu.be/7Rbw953DXg0) he made on this topic.
### Named links
This is something I learned about from @Tris from the YouTube channel [No Boilerplate](https://www.youtube.com/@NoBoilerplate), ~~but I don't feel quite ready to implement yet. In the event that I do feel ready,~~ where I can simply create a new property or two in the front matter of a note like this:
```yaml
up:
 - "[[parent]]"
prev:
 - "[[left page doc]]"
```
This allows me to create a de-facto hierarchical structure that *does* show up on the graph; a feature that should prove useful for ordering daily notes I make during my [[daily journal challenge]].
Relationships between notes can also include:
* Parent / child
* Source / citation
* East / West
* Previous / Next
* ...and so much more!
## Live Queries
Remember the saved searches feature introduced in Windows Vista? Obsidian has that functionality built in too:
```query
tag: 0🌲
```
## Math equation building
For this demonstration, I'll do something crazy like multiplying a change of basis matrix by an antiderivative of a parametric vector equation:

$$\begin{bmatrix}2 & 1 & -7\\
-2 & -3 & 5\\
1 & 2 & 4\end{bmatrix} * \int \ln(t)\hat{i} + (3t - 7t^2)\hat{j} + \cos(t)\hat{k} \, dt $$

That's pretty wild, and useful for carrying over what I learned in [[Multivariate Calculus]] and Linear Algebra into my [[General Linear Models]] classes.
## Coding
This is honestly something I wish I had at the beginning of the semester, since it's an easy way to embed documentation for programs written in python (or most other commonly used programming locations like C++):  
```python
x = 2
is_prime = True
for k in range(x):
	if x % k == 0:
		is_prime = False
print(f"{x} is prime" if is_prime else f"{x} is not prime")
```
## Formatted blockquotes
Obsidian has build-in CSS formatting for specialized blockquotes that can be delineated with the following headers:
```md
> [!SUMMARY] Header
> [!INFO]
> [!Warning] Header
> [!Note] Header
```
>[!example] For example:
>...And these blockquotes can also contain **All** the *usual* `markdown` and <u>html</u> ==formatting== conventions.
#### The 12 built-in callout types and their aliases:
- note `(default)`
- abstract, summary, tldr
- info, todo
- tip, hint, important
- success, check, done
- question, help, faq
- warning, caution, attention
- failure, fail, missing
- danger, error
- bug
- example
- quote, cite
> [!attention] Caveat:
> These special blockquotes might not always be supported by other markdown apps.
#### Customizations
Snippets and plugins can define custom callouts too, or overwrite the default options. Callout types and icons are defined in CSS, where the color is an `r, g, b` tuple and the icon is the icon ID from any internally supported icon (like `lucide-info`). Alternatively, you can specify an SVG icon as a string.
```CSS
.callout[data-callout="my-callout-type"] {
    --callout-color: 82, 132, 145;
    --callout-icon: lucide-clipboard-clock;
    --callout-icon: '<svg>...custom svg...</svg>';
}
```
This quickly became (for me, at least) the most overused feature of Obsidian.
## Kanban Boards
Using the Kanban plugin, I can create obsidian notes that are displayed as flexible Kanban boards.
>[!danger] Caveat:
>When `![[embedded]]`, these notes display as Markdown instead of Kanban.
## What about shell commands?
#Imported/LLM/Gemini
Yes, Obsidian commands, particularly those from the "Shell commands" community plugin, can be linked within markdown documents. 
The "Shell commands" plugin allows you to define and execute system commands directly within Obsidian. It also provides a way to create special URIs (Uniform Resource Identifiers) that can be embedded in your markdown notes. When clicked, these URIs will trigger the execution of the associated shell command.
### Here's how it works: 

* **Install the “Shell commands” plugin**: This community plugin needs to be installed and enabled within your Obsidian vault. 
* **Define your shell command**: Configure the shell command you want to link in the plugin’s settings. 
* **Generate the URI**: The plugin provides an option to copy the URI for a defined shell command to your clipboard. 
* **Embed the URI in markdown**: Paste the copied URI into your markdown note as a link. 

> [!example] Example URI structure: 
> `obsidian://shell-commands/?vault=YOUR_VAULT_NAME&execute=YOUR_SHELL_COMMAND_ID`

By using this method, you can create interactive elements within your Obsidian notes that execute specific commands from the command palette, including system-level shell commands. 

*AI responses may include mistakes.*

[The plugin can be found here](https://www.obsidianstats.com/plugins/obsidian-shellcommands)