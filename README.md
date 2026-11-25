# Examples

Here's a quick walkthrough on how to use the examples.

## Prerequisites

To use the examples you should have a code editor (I suggest [Visual Studio Code](https://code.visualstudio.com/)) and install [uv](https://docs.astral.sh/uv/getting-started/installation/).

To install `uv`, open a terminal and then for Mac paste in:

```
curl -LsSf https://astral.sh/uv/install.sh | sh
```

or for Windows:

```
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

I suggest [downloading this entire git repository](https://github.com/antiboredom/how-to-find-workshop/archive/refs/heads/main.zip) as a folder, then unzipping it, and opening `scraping-examples` in Visual Studio Code.

Then, open Visual Studio Code's built-in terminal, by going to the `Terminal` menu and selecting `New Terminal`.

Finally, type `uv run SCRIPTNAME.py`, replacing "SCRIPTNAME.py" with the file you'd like to run.

## General Notes

I've tried to make these examples as accessible to new coders as possible by putting the important variables at the top of the file, in all caps. This means that for _many_ (but not all) cases, you should be able to just modify the variable values to make the examples work with different websites.

## scrape_text.py

```
uv run scrape_text.py
```

Download post titles from reddit.

This looks for elements matching a particular css selector and saves the text content of each one to a file. Each line of the file represents the text of a single element. The script will attempt to click a "next" button if available to get multiple pages of results.

Variables:

`START_URL`: the url to visit

`HEADLESS`: determines if the browser runs in "headless" mode, or will be visible to you. It helps with avoiding bot detection if you leave this to `False`, but it makes the script run a little bit slower.

`CONTENT_SELECTOR`: the css selector of the elements we want

`NEXT_SELECTOR`: the css selector of the "next" button

`OUTPUT_FILE`: the filename to save the content to

`MAX_PAGES`: the maximum number of pages to scrape.

## scrape_images.py

```
uv run scrape_images.py
```

Download images of crying cops from Shutterstock.com.

This looks for images matching a particular css selector and saves them to the same folder as the script. The script will attempt to click a "next" button if available to get multiple pages of results. HOWEVER, in this example the next button is located with `page.get_by_text()` which looks for an element with a particular text value.
