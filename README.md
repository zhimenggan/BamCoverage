# BamCoverage
<b>BamCoverage: A efficient software tools to Calculate site depth of genome based  bam/sam List</b>

1) Install
------------

  This software rely htslib，so should Pre-install htslib first [samtools-1.5/htslib-1.5](https://sourceforge.net/projects/samtools/files/samtools)
  </br>Then Just  [make]  or [sh  make.sh ]  to compile this software.
  </br>the final software can be found in the Dir [bin/BamCoverage]

 For <b>linux /Unix </b>
<pre>
        tar -zxvf  BamCoverage-XXX.tar.gz
        cd BamCoverage-XXX;                             # if Link do not work ,Try <b>re-install</b>  third  library
        cd src;                                         #【zlib and gzstream htslib】 and copy them to the  library Dir
        make ; make clean                               # BamCoverage-XX/src/include/zlib 
        ../bin/BamCoverage                              # BamCoverage-XX/src/include/gzstream
</pre>
</br>

For <b>macOS </b>
<pre>
#step1 :Should must <b>re-install</b>  third  library 【zlib and gzstream htslib】
              see  [zlib and gzstream] website 
#step2  :  # Copy these two library into Dirs 
              cp libz.a libz.so*  BamCoverage-XX/src/include/zlib
              cp libgzstream.a  BamCoverage-XX/src/include/gzstream
#step3  : 
              sh make.sh # or [make && make clean]
</pre>

2) Example
------------
* 1) Calculate bam files
```
#To Calculate bam

    ./bin/BamCoverage  -List  bam.list  -OutPut  out.depth.fa.gz -MinQ -1
   # To out Put the each chr meanDepth Coverage add [-Stat]
    ./bin/BamCoverage  -List  bam.list  -OutPut  out.depth.fa.gz  -Stat

```

* 2) Calculate sam files
```
# To cCalculate sam
	./bin/BamCoverage  -List  sam.list  -OutPut  out.depth.fa.gz  -Stat
# Also you the  add the  -MinQ to filter some reads
	./bin/BamCoverage  -List  sam.list  -OutPut  out.depth.fa.gz  -MinQ 10
```

* 3) Calculate GC-Depth Dis Figure
```
# First Out Put the Depth-GC wig info with [-Ref  Ref.fa]
	./bin/BamCoverage  -List bam.list   -OutPut outFix   -Ref Ref.fa  -Stat
# Second To Plot the Figure 
# Must PreInstall R with library ggplot2,gridExtra,ggExtra
	perl  bin/GC_Depth_Plot.pl  outFix.DepthGC.wig.gz  MaxDepth  OutFig
```

3) Introduction
------------

* <b> Parameter description</b>

```php

  ./bin/BamCoverage

        Usage: BamCoverage  -List  <bam.list>  -OutPut  <out.depth.gz>

                -List      <str>     Input Bam/Sam File List
                -OutPut    <str>     OutPut Depth info Fa file

                -Ref       <str>     In Ref.fa If Want Out Depth-GC wig info
                -Windows   <int>     Windows size for Depth-GC wig[10000]
                -Stat                Stat Coverage,MeanDepth & Depth Dis info

                -MinQ      <int>     Filter the read low mapQ[10]

                -help                Show this help [hewm2008 v1.10]

```

4) Results
------------
Format Introduction

* [sam bam format](https://samtools.github.io/hts-specs/SAMv1.pdf)

5）Discussing
------------
- email: hewm2008@gmail.com / hewm2008@qq.com
- join the<b><i> QQ Group : 125293663</b></i>



######################swimming in the sky and flying in the sea ########################### ##


