# EXOrDIA

Check the online JS demo at [Github Pages](https://juancroldan.github.io/exordia/).

This will be a simple python library called exordia, which relies on using XOR operations to split a file into N encrypted shards. The name is a reference to the Yu-Gi-Oh! card [Exodia the Forbidden One](https://yugioh.fandom.com/wiki/Exodia_the_Forbidden_One), which is split into 5 pieces.

The method is simple:

**Split**
* Generate N-1 random files
* Generate a file by XORing all the random files plus the original one
* The N generated files are the shards

**Merge**
* XOR the N random files

## Usage

Ideally, the installation will be as simple as

```py
pip install exordia
```

And the usage will be like:

```py
from exordia import split, merge

# split
split(input='secret.png', n=5)

# merge
merge(shards=['secret.png.1', 'secret.png.2', 'secret.png.3', 'secret.png.4', 'secret.png.5'], output='secret.png)
```

## Future work

Some future work might be required to add optional features like:

* GZipping the files before splitting
* Adding a EOF signature and a random padding, to avoid guessing the compressed filesize
* Adding some verification CRC to ensure the merge was correct
