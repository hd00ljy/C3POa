# C3POa
Computational pipeline for calling consensi on R2C2 nanopore data.

# C3POa_preprocessing.py # 

Takes raw 1D nanopore R2C2 reads in fastq format, removes low quality and short reads and then finds splint sequences in those reads using BLAT. It then adds the position of the splint to the read name and generates separate folders each containing a fastq file containing 4000 raw reads.  

# C3POa.py #

Takes fastq output by C3POa_preprocessing and generates consensus sequences in fasta format and a subread sequences in fastq format.

# C3POa_postprocessing.py #

Trimms and reorients consensus sequences.


### Dependencies ###
- [Python 3.6](https://www.python.org/downloads/)
- [NumPy 1.13.3](https://scipy.org/install.html)
- [poa v1.0.0 Revision: 1.2.2.9](https://github.com/tanghaibao/bio-pipeline)
- [EMBOSS water: watHerON v8](https://users.soe.ucsc.edu/~rvolden/C3POa/EMBOSS-6.6.0_v8.tar.gz)
- [minimap2 2.7-r654](https://github.com/lh3/minimap2)
- [racon](https://github.com/isovic/racon)
- [blat source](https://users.soe.ucsc.edu/~kent/src/blatSrc35.zip) or [blat executable](http://hgdownload.soe.ucsc.edu/admin/exe/)

To install dependencies, use setup.sh.  
setup.sh will download and make all of the packages that you need to run C3POa (except Python, NumPy and blat).  
You don't need to have these in your PATH, but if you don't, you'll need to use a [config file](example_config).
```bash
chmod +x setup.sh
./setup.sh
```

To install NumPy, you can go [here](https://scipy.org/install.html).  
Otherwise, you can use your computer's package manager (apt-get, dnf, brew, etc.) to install.  
Pip3 is another option for NumPy installation.  
Example:
```bash
sudo dnf install python3-numpy
```
or
```bash
pip3 install numpy
```

For blat, there are a couple options. You can build from [source](https://users.soe.ucsc.edu/~kent/src/blatSrc35.zip) or you can get an [executable](http://hgdownload.soe.ucsc.edu/admin/exe/). Please follow the documentation in the blat readme for make instructions.

### Usage ###
After resolving all of the dependencies, you can run C3POa with python.

```bash
python3 C3POa.py --reads reads.fastq [--path PATH] [--matrix MATRIX] [--config CONFIG] [--output OUTPUT] [--figure FIGURE]
```
