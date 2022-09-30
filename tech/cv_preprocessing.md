# Batch conversion between JPG and PNG on Mac Terminal
### Batch Convert PNG to JPG
```mkdir jpegs; sips -s format jpeg *.* --out jpegs```

### Batch Convert JPG to PNG
```mkdir pngs; sips -s format png *.* --out pngs```

Reference: http://tutorialshares.com/batch-convert-png-jpg-mac-terminal/

# Count the number of files in the current directory
`` ls |wc -l``
### count file with a specific extension (e.g. png)
`` ls *.png |wc -l``

# Move files with the same name but different extension into current directory on Mac Terminal
- Goal:Current directory has all the files of interest \*.json, to move the \*.png from the parent directory to the current one
- create a script ``vi mv.sh``
- type the follow commands
``
for NAME in *.json; do
	FILE="${NAME%.json}"
	IMAG="${FILE}.png"
	cp ../"$IMAG" .
done
``
- convert file to be executable ``chmod +x mv.sh``
- execute the script ``./mv.sh``
