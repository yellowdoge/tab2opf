## How to create a Kindle dictionary from a free translation list

1. Went to https://www.dict.cc and downloaded the one I wanted (NL->EN).
2. Removed some strange empty line between comments and translations (that should be in the format `word \tab word`) -- it rubbed the script in step 3 the wrong way.
3. Ran `tab2opf.py` on the `.txt` and that gave me a `.opf` and 3 `.html` files. Had to edit by hand the `.opf` to read like:
```
    <DictionaryInLanguage>nl</DictionaryInLanguage>
    <DictionaryOutLanguage>en</DictionaryOutLanguage>
```
(Perhaps some modern versions of `tab2opf.py` accept `--source` and `--target` but not mine).

4. Ran kindlegen on the `.opf` to generate a `.mobi`. `kindlegen` was mentioned but not available in the [Amazon KDP web site](https://github.com/apeyser/tab2opf), so I got the Kindle Previewer v3 instead and found `kindlegen` inside:
```
   /Applications/Kindle\ Previewer\ 3.app/Contents/MacOS/lib/fc/bin/kindlegen
    the_opf_file.opf -verbose -o nederlands_engels_woordenboek.mobi
```
I tried copying and running `kindlegen` from elsewhere and it did work :-)

5. Stuffed the produced `.mobi` in my kindle, and it worked! :-)
6. Some interesting links:
  * http://rhystate.com/generating-a-kindle-compliant-ebook-with-kindlegen/
  * http://www.klokan.cz/projects/stardict-lingea
