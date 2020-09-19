# Build instructions

## Building fonts

### Install dependencies 

Please ensure that [otfcc](https://github.com/caryll/otfcc) is already available in your environment path.

Install node dependencies,
```
$ npm install
```

python3 is required. Install python dependencies specified in `requirements.txt`. We strongly recommend you installing in a conda environment.
```
$ pip install -r requirements.txt
```

### Download fonts

Download font files to directory `fonts`, 
```
$ npm run init-fonts
```

### Dump fonts

Dump the OpenType fonts to otfcc json files.
```
$ npm run dump-fonts
```

### Convert Han glyphs to glyph models

A glyph model is a special construction extracted from glyph contours using a few image processing techniques, which allows deformable manipulations of the glyph contours. Glyph models can be restored back to glyph contours easily without much computational efforts. Manipulation of the glyph models is the key trick in Glow Sans's glyph parametrization and deformation.
```
$ npm run extract-han-models
```

By default, the script allow 4 processes, modifying the number of processes by simply adding the number to the command,

```
$ npm run extract-han-models 8
```
will run the script in 8 processes.

Also, kana-like glyphs need glyph model conversion as well. Run,

```
$ npm run extract-kana-models
```

### Extract other information from Source Han Sans

The other glyph categories need glyph extraction only.

```
$ npm run extract-gid-categories
```

Extract features from the CJK fonts.

```
$ npm run extract-shs-features
```

### Modify parameters

With our [online demo](https://welai.github.io/glow-sans), you can load and save parameter files that are used as configurations for deforming the glyph contours. The parameters used for building Glow Sans are located at `parameters/glow`.

### Build fonts

Before building the font family, please ensure that all resources needed are ready. It is recommended to look into the [building script](../scripts/build-family.js) before you start. Building the whole family may take serveral hours, and needs at least 4GB ramaining RAM.

```
$ npm run build-family
```

## Building demo

Before building the demo, you have to make sure that the fonts have already been downloaded and dumped.

### Sample fonts

Sample a few glyphs from the fonts and convert them to glyph models. Note that results of the scripts are already stored in the `samples` directory, you may skip the following steps.
```
$ npm run sample-shs-sc
$ npm run sample2model
$ npm run sample-fira
$ npm run sample-raleway
```

### Bundle demo scripts

```
$ npm run build-demo
```

### Serve static

```
$ npm run serve
```
