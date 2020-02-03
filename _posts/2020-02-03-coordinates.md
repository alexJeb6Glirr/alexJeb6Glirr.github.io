---
layout: post
title: Georeferencing TGN
subtitle:
tags: [homework]
comments: false
---

In the Dispatch XML files place names are annotated with TGN identifiers.

We can use these identifiers to map them to coordinates.
But we need to prepare the coordinates DB first.

- Download the TGN `explicit.zip` (1GB) from <http://vocab.getty.edu/> (under "Datasets")
- Extract the file `TGNOut_Coordinates.nt`
- Run this oneliner to just get `longitude` and `latitude`:

```shell
cat TGNOut_Coordinates.nt | sed 's|^<http://vocab.getty.edu/tgn/||' | rg 'latitude|longitude' | sed 's/\^\^.*//' | sed 's|-geometry> <http://schema.org/|,|' | sed 's|> |,|' | sed 's/"//g' > tgn-coordinates.csv
```

- Copy the resulting file into the python-scripts folder
- Run the Python script which combines and maps the frequency files from the `extract-from-xml.py` script with

```shell
python combine-and-map-frequencies.py ./tgn-coordinates.csv  frequencies/
```

The resulting files are

- [tgn-coordinates.csv.gz](../../assets/tgn-coordinates.csv.gz) (26MB)
- [the-whole-dispatch-coord-frequency.csv](../../assets/the-whole-dispatch-coord-frequency.csv) (670KB)

### The code

The code can be found at <https://github.com/alexJeb6Glirr/python-scripts>.

### Screenshots

![Mapped coordinates with labels](../../assets/mapped-with-labels.png)
![Mapped coordinates to different dot sizes](../../assets/mapped-to-dot-sizes.png)
