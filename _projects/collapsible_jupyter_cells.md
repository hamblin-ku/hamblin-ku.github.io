---
layout: project
title: 'Collapsible Jupyter Cells'
date: 03 June 2020
image: /assets/img/projects/hy-drawer.svg
screenshot: /assets/img/projects/code2.png
caption: Make your Jupyter Notebook cells collapsible!
description: >
  Make your Jupyter Notebook cells collapsible!
accent_color: '#4fb1ba'
accent_image:
  background: 'linear-gradient(to bottom,#193747 0%,#233e4c 30%,#3c929e 50%,#d5d5d4 70%,#cdccc8 100%)'
  overlay:    true
---

I was working on some Jupyter Notebook's for a class I was helping with, and I was searching for a way to make the code cells in Jupyter notebooks collapsible because I wanted the code to be, for the most part, hidden as the students were not meant to fiddle with the code. I found a lot of unsatisfactory methods using various extensions, and then I stumbled across an answer on a [stackoverflow thread](https://stackoverflow.com/questions/31517194/how-to-hide-one-specific-cell-input-or-output-in-ipython-notebook). All credit for this approach goes to the user [Ferrard](https://stackoverflow.com/users/1913724/ferrard) on StackOverflow, I merely hope to make more aware of this capability. 

I advise saving this code into a separate python script, let's call it 'collapse.py', and then importing this script into whatever notebook you wish to use it in (we'll assume you have placed collapse.py in the same directory as the notebook you wish to use it in). Then, collapse.py would look like:

{% raw %} 
```python
from IPython.display import HTML
import random

def hide_toggle(for_next=False):
    this_cell = """$('div.cell.code_cell.rendered.selected')"""
    next_cell = this_cell + '.next()'

    toggle_text = 'Toggle show/hide'  # text shown on toggle link
    target_cell = this_cell  # target cell to control with toggle
    js_hide_current = ''  # bit of JS to permanently hide code in current cell (only when toggling next cell)

    if for_next:
        target_cell = next_cell
        toggle_text += ' next cell'
        js_hide_current = this_cell + '.find("div.input").hide();'

    js_f_name = 'code_toggle_{}'.format(str(random.randint(1,2**64)))

    html = """
        <script>
            function {f_name}() {{
                {cell_selector}.find('div.input').toggle();
            }}

            {js_hide_current}
        </script>

        <a href="javascript:{f_name}()">{toggle_text}</a>
    """.format(
        f_name=js_f_name,
        cell_selector=target_cell,
        js_hide_current=js_hide_current, 
        toggle_text=toggle_text
    )

    return HTML(html)}
```
{% endraw %}

Now, to use this in the Jupyter notebook of our choice, we must simply import collpase.py (preferably at the start of the notebook) and use the 'hide_toggle' function in the cell(s) we wish to be collapsible:

~~~python
import collapse
	
#### Start Code Cell

##
##Code we wish to be collapsible
##

collapse.hide_toggle()
#### End Code Cell
~~~

Then, the code cell will have a toggle link you can click to collapse/uncollapse the code. It'll look something like this when we run the code block(note that this must be ran in python 3.6 and up):

![Uncollapsed](/website/assets/img/projects/uncollapsed.png){:.lead}

When we click 'Toggle show/hide' it will collapse the code cell and only show the output:

![Collapsed](/website/assets/img/projects/collapsed.png){:.lead}

I've found this to be pretty useful, and it can help keep long notebooks looking tidy while you're using them. As user [Ferrard](https://stackoverflow.com/users/1913724/ferrard) pointed out on his post, this is also useful for presentations, and really just anytime you're showing other people your notebooks where the focus is on the output (like group meetings!). If you go to the StackOverflow page, Ferrard also demonstrates how you can use this to easily toggle the *next* code block, rather than the code block you call the hige_toggle() function in.

{:.lead}


