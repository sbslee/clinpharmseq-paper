# clinpharmseq-paper

Data and code repository for the ClinPharmSeq paper

# Star allele calling with PyPGx

```
# Gene list (N=27)
$ cat 27-gene-list.txt
CYP1A2
CYP2A6
CYP2B6
CYP2C8
CYP2C9
CYP2C19
CYP2D6
CYP2E1
CYP3A4
CYP3A5
CYP4F2
DPYD
GSTM1
GSTP1
GSTT1
NAT1
NAT2
SLC15A2
SLC22A2
SLCO1B1
SLCO2B1
TPMT
UGT1A1
UGT2B7
UGT2B15
UGT2B17
VKORC1

# Run PyPGx for WGS data
for gene in `cat 27-gene-list.txt`
do
  pypgx run-ngs-pipeline \
  $gene \
  wgs-$gene \
  --variants pypgx-input-files/wgs.merged.joint.filtered.vcf.gz \
  --depth-of-coverage pypgx-input-files/wgs-depth-of-coverage.zip \
  --control-statistics pypgx-input-files/wgs-control-statistics-VDR.zip \
  --platform WGS
done

# Run PyPGx for ClinPharmSeq Set 1 data
for gene in `cat 27-gene-list.txt`
do
  pypgx run-ngs-pipeline \
  $gene \
  ts1-$gene \
  --variants pypgx-input-files/ts1.merged.joint.filtered.vcf.gz \
  --depth-of-coverage pypgx-input-files/ts1-depth-of-coverage.zip \
  --control-statistics pypgx-input-files/ts1-control-statistics-VDR.zip \
  --platform Targeted
done

# Run PyPGx for ClinPharmSeq Set 2 data
for gene in `cat 27-gene-list.txt`
do
  pypgx run-ngs-pipeline \
  $gene \
  ts2-$gene \
  --variants pypgx-input-files/ts2.merged.joint.filtered.vcf.gz \
  --depth-of-coverage pypgx-input-files/ts2-depth-of-coverage.zip \
  --control-statistics pypgx-input-files/ts2-control-statistics-VDR.zip \
  --platform Targeted
done
```

# Figure4_SVExamples

```
$ pypgx plot-cn-af \
wgs-CYP2D6/copy-number.zip \
wgs-CYP2D6/imported-variants.zip \
--samples 7d077b89f2514fb0b8e002f8d9a10189

$ pypgx plot-cn-af \
ts2-CYP2D6/copy-number.zip \
ts2-CYP2D6/imported-variants.zip \
--samples TS2_NA18526

$ pypgx plot-cn-af \
wgs-CYP2A6/copy-number.zip \
wgs-CYP2A6/imported-variants.zip \
--samples 543558ae08cd44b3850fc7b835484037

$ pypgx plot-cn-af \
ts1-CYP2A6/copy-number.zip \
ts1-CYP2A6/imported-variants.zip \
--samples TS1_NA18861

$ pypgx plot-cn-af \
wgs-CYP2B6/copy-number.zip \
wgs-CYP2B6/imported-variants.zip \
--samples 3fcca708192c4ffe8e57318c7d64e480

$ pypgx plot-cn-af \
ts1-CYP2B6/copy-number.zip \
ts1-CYP2B6/imported-variants.zip \
--samples TS1_NA19178
```

# Figure5_SVUpdates

```
$ pypgx plot-cn-af \
wgs-CYP2A6/copy-number.zip \
wgs-CYP2A6/imported-variants.zip \
--samples 54db734bc1ec46b29fc6c5c6df35ca65

$ pypgx plot-cn-af \
ts1-CYP2A6/copy-number.zip \
ts1-CYP2A6/imported-variants.zip \
--samples TS1_HG00436

$ pypgx plot-cn-af \
wgs-CYP2D6/copy-number.zip \
wgs-CYP2D6/imported-variants.zip \
--samples f00e1071f840476c9872de73f0ea8a02

$ pypgx plot-cn-af \
ts2-CYP2D6/copy-number.zip \
ts2-CYP2D6/imported-variants.zip \
--samples TS2_NA18540

$ pypgx plot-cn-af \
wgs-CYP2E1/copy-number.zip \
wgs-CYP2E1/imported-variants.zip \
--samples 0d73bafef55a4a718489f3fdca91fd55

$ pypgx plot-cn-af \
ts1-CYP2E1/copy-number.zip \
ts1-CYP2E1/imported-variants.zip \
--samples TS1_NA19908
```
