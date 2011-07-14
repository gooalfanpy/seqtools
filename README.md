script: pileupExonFilter.py
usage: pileupExonFilter.py bedfile in_pileup > out_pileup
function: Filtering lines in in_pileup which position is outside of exon ranges which is specified by bedfile.
dependency: python RangeSet.py
#
script: pileupExonFilter.sh
usage: pileupExonFilter.sh bedfile in_pileup out_pileup > report
function: A Wrapper shellscript of pileupExonFilter.py which output matching ratio, and uses filtered pileup which is removed insertion or deletion base from specified pileup file.
dependency: pileupExonFilter.py
#
script: RangeSet.py
usage: class file
function: Defines RangeSet class. Create normalized range list internally, and allows to determine that requested position is insided or not as O(logn) speed.
dependency: python
#
script: fastqUnpairedFilter.py
usage: fastqUnpairedFilter.py in_seq_1 in_seq_2 out_seq_1 out_seq_2
function: Remove Unpaired read from pair fastq sequence files.
dependency: python

##script:
  fq2bam.sh

###usage:
  fq2bam.sh [options] in_seq_1 in_seq_2 

###function: 
  A lazy script to create sai,bam,pileup from paired fastq sequence data.

###options:
 -o PATH 
      Specify output directory.　
      If not specified then create out/ directory at where contains in_seq_1.

 -r PATH 
      Specify the directory which contais reference files. If not specified,
      uses /usr/local/share/doc/hg19.

 -p     
      Create pileup file additionaly.

 -q     


###dependency:
  python fastqUnpairedFilter.py bwa samtools fastx_toolkit