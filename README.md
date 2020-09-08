# orgzly-index-files
Python script to create a hierarchical file index of a directory with `.org` files.
Each file is a link to the corresponding note.

## usage
* `ORG_DIRECTORY` is the root directory that will be recursively traversed
* `ORGZLY_FILE_INDEX` is the path to the orgzly index file
`$ export ORG_DIRECTORY="/path/to/org/directory" ORGZLY_FILE_INDEX="/path/to/index/file.org" python make_index.py`

## pitfalls
* **The** `.org` **filenames cannot be repeated**. If so, orgzly will only pick one of the files with that given name and the links may go to the wrong file
* In Linux, you can [find duplicate files](https://stackoverflow.com/questions/16276595/how-to-find-duplicate-filenames-recursively-in-a-given-directory-bash) and rename if necessary:

```bash
dirname="."
find $dirname -type f | sed 's_.*/__' | sort|  uniq -d|
while read fileName
do
find $dirname -type f | grep "$fileName"
done
```
