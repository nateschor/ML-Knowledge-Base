Philosophy behind using an editor (taken from [missing semester](https://missing.csail.mit.edu/2020/editors/))

> Writing English words and writing code are very different activities. When programming, you spend more time switching files, reading, navigating, and editing code compared to writing a long stream. It makes sense that there are different types of programs for writing English words versus code (e.g. Microsoft Word versus Visual Studio Code).
> 
> As programmers, we spend most of our time editing code, so it’s worth investing time mastering an editor that fits your needs

 ### Resources

- type `vimtutor` in the shell
- [hub](https://learnbyexample.github.io/curated_resources/vim.html) for vim resources
- MIT's [missing semester](https://missing.csail.mit.edu/2020/editors/) lecture and notes on VIM

To make vim your default RStudio keybinding, go to Tools --> Global Options and the select Vim in the Code pane

![[vim_in_rstudio.png]]

#### Some vim Shortcuts not Covered in the Tutorials

- SHIFT + s to right indent, > or >> and < or << to right/left indent
- pressing * while on a text finds all occoruences of that text and then can use n/N to navigage
- CTRL + A /CTRL + X to increment/decrement text number
- { or } to jump b/w paragraphs
- gv to reselect what you just selected
- Use % in v mode to select the last parenthesis without selecting the %>% (or use t + %)

#### Saving a Repeated Keystroke Action
 Using register with "number or thing"p, saves your copying history
![[vim_registers.png]]
![[vim_recording.png]]

Adjusting your screen relative to the cursor

![[vim_adjust_screen.png]]

