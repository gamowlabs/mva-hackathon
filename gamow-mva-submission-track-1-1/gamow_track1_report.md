# MVA Hackathon 2026 — Track 1 Report

**Team:** gamow
**Proband:** `WGS_EX2312012`
**Model / approach:** `gamow_sentieon-vcf-targeted-acmg`
**Predictions file:** `gamow_sentieon-vcf-targeted-acmg.csv`
**Genome build:** GRCh38 throughout
**Report date:** 2026-08-25

---

## 1. Summary

The proband is a **compound heterozygote for two variants in *BUB1B***, one a curated pathogenic
nonsense allele and one an essentially private missense allele in the BUBR1 pseudokinase domain.
This is the genotype pattern expected for **mosaic variegated aneuploidy syndrome 1 (MVA1)**, and it
is our single primary candidate.

| | Allele 1 | Allele 2 |
|---|---|---|
| GRCh38 | chr15:40,209,701 T>G | chr15:40,220,612 T>G |
| HGVS (MANE `NM_001211.6`) | `c.2210T>G` | `c.3006T>G` |
| Protein | **p.(Leu737Ter)** — nonsense | **p.(Asn1002Lys)** — missense |
| Location | exon 17 / 23 | exon 23 / 23 (last) |
| Genotype | 0/1 · AD 21,25 (VAF 0.54) · DP 46 · GQ 99 · PASS | 0/1 · AD 15,13 (VAF 0.46) · DP 28 · GQ 99 · PASS |
| gnomAD v4 | ex 115/1,461,846 · gen 5/152,174 · **0 hom** ([link](https://gnomad.broadinstitute.org/variant/15-40209701-T-G?dataset=gnomad_r4)) | ex 1/1,461,878 · absent genomes · **0 hom** ([link](https://gnomad.broadinstitute.org/variant/15-40220612-T-G?dataset=gnomad_r4)) |
| ClinVar | **Pathogenic/Likely pathogenic** — [VCV000533901](https://www.ncbi.nlm.nih.gov/clinvar/variation/533901/) | **not present** |
| dbSNP | rs759242053 | none (ClinGen CAID CA391689593) |
| Our ACMG call | **Likely Pathogenic** | **VUS** |

**Estimated probability of causal relationship (EPCR): 0.85**, `finding_type = primary`.

---

## 2. Why *BUB1B*

*BUB1B* is an established cause of constitutional MVA — it was the first gene identified for the
condition (Hanks *et al.*, Nat Genet 2004, PMID [15475955](https://pubmed.ncbi.nlm.nih.gov/15475955/))
and gives the disorder its type-1 designation.

- **ClinGen gene–disease validity: *BUB1B* — mosaic variegated aneuploidy syndrome 1
  (MONDO:0009759), autosomal recessive, classification "Definitive"** (Hereditary Cancer GCEP,
  curated 2019-11-22).
- ClinGen dosage curation assigns *BUB1B* haploinsufficiency score **30 — "gene associated with
  autosomal recessive phenotype"**, i.e. carriers are unaffected and two hits are required.
- Disease identifiers: OMIM [257300](https://www.omim.org/entry/257300), MONDO:0009759,
  Orphanet 1052, MedGen C1850343.

BUBR1 is a core component of the spindle assembly checkpoint, which ensures correct chromosome
segregation during mitosis; reduced BUBR1 function produces the cell-to-cell-variable aneuploidy that
defines the phenotype. Affected individuals are frequently **compound heterozygous, carrying a
different variant on each allele** rather than the same change twice.

---

## 3. What we found

Restricting to *BUB1B* (chr15:40,160,984–40,221,137, ENSG00000156970), the callset contains **17
variants**. Mapped against the canonical/MANE transcript `ENST00000287598.11` / `NM_001211.6`
(23 exons), they partition as **2 upstream, 12 intronic, 1 downstream (`c.*662G>C`), and 2 exonic —
and both exonic variants are heterozygous.** No intronic variant lies within splice-region range;
the closest sits **905 bp** from the nearest splice site.

Both candidate calls are technically clean and show no artifact signature:

```
chr15:40209701 T>G  PASS  QUAL 708.77  MQ 60  QD 15.41  FS 1.115  SOR 0.523  MQRankSum 0  ReadPosRankSum  0.149
chr15:40220612 T>G  PASS  QUAL 344.77  MQ 60  QD 12.31  FS 1.617  SOR 0.330  MQRankSum 0  ReadPosRankSum -0.209
```

Allele balance is ~0.5 at both sites, neither shows strand or read-position bias, and MQ 60 argues
against mismapping — relevant here because the *BUB1B-PAK6* readthrough locus overlaps the 3' end of
the gene.

---

## 4. Evidence for pathogenicity

### Allele 1 — `NM_001211.6:c.2210T>G` p.(Leu737Ter)

- **PVS1 (Very Strong).** Nonsense variant in exon 17 of 23. The penultimate exon–exon junction falls
  after `c.2957`, so the premature stop lies **747 nt upstream of it** — far beyond the 50 nt
  boundary, therefore **predicted to trigger nonsense-mediated decay**. Loss of function is the
  established disease mechanism for this gene (§2), so PVS1 applies at full strength.
- **PM2_Supporting.** gnomAD v4: 120 alleles across ~1.61M (combined AF ≈ 7.4 × 10⁻⁵), **zero
  homozygotes**. We apply PM2 only at Supporting strength, since this frequency is at the high end
  for an ultra-rare recessive allele.
- **Independent curation.** ClinVar [VCV000533901](https://www.ncbi.nlm.nih.gov/clinvar/variation/533901/):
  **Pathogenic/Likely pathogenic** for MVA1, review status *criteria provided, multiple submitters,
  no conflicts*; two submitters (Labcorp Genetics and GeneDx), last evaluated 2024-10-09.
- **Our classification: Likely Pathogenic** (PVS1 + PM2_Supporting = 9 points on the ClinGen Bayesian
  point scale). Confirming phase would add PM3_Supporting → 10 points → **Pathogenic**.

### Allele 2 — `NM_001211.6:c.3006T>G` p.(Asn1002Lys)

- **PM2_Supporting.** 1 allele in 1,461,878 gnomAD v4 exomes (AF 6.8 × 10⁻⁷), absent from genomes,
  zero homozygotes. Effectively private.
- **Location.** Asn1002 falls inside the BUBR1 kinase (pseudokinase) domain, UniProt
  [O60566](https://www.uniprot.org/uniprotkb/O60566/) residues 766–1050. Reference residue confirmed
  as Asn at position 1002 of the 1050-aa protein.
- **Conservation.** phyloP 100-way 4.87; phastCons 100-way 1.0; GERP++ RS 4.84.
- **In-silico — reported in full, because the predictors disagree:**
  - *Damaging:* AlphaMissense 0.9229, CADD 24.5, PolyPhen-2 HDIV 1.0, ClinPred 0.989, MetaRNN 0.879,
    ESM-1b −11.54, PROVEAN −3.89, MutationTaster D, MPC 0.83, M-CAP D.
  - *Tolerated / indeterminate:* **REVEL 0.472**, MetaSVM, MetaLR, BayesDel, PrimateAI, FATHMM,
    LIST-S2.
  - **We do not claim PP3.** Under the ClinGen SVI calibration of REVEL (Pejaver *et al.* 2022, PMID
    [36413997](https://pubmed.ncbi.nlm.nih.gov/36413997/)), 0.472 falls in the indeterminate band —
    below the threshold for PP3_Supporting and above that for BP4. We therefore treat the
    computational evidence as prioritisation only, not as a classification criterion.
- **PM1 not applied** — the pseudokinase domain spans 285 residues, too broad to qualify as a
  well-defined mutational hotspot.
- **Our classification: VUS** (PM2_Supporting alone = 1 point). Even with phase confirmed,
  PM3_Supporting would bring it only to 2 points — still VUS by strict ACMG/AMP.

### Statement of the overall call

The diagnosis rests on **one Likely Pathogenic allele plus one VUS allele in a Definitive,
autosomal-recessive gene**, in a proband whose reported phenotype matches that gene's disease.
Formally this is a **probable, partially-resolved molecular diagnosis, not a confirmed one.** Our
EPCR of 0.85 reflects the strength of the gene–phenotype fit and the improbability of a curated
pathogenic truncating allele co-occurring by chance with an essentially private missense allele in
the same recessive gene — discounted for the open questions in §5.

---

## 5. What still needs to be investigated

1. **Phase is not established — the single biggest gap.** The two variants are **10,911 bp apart**
   and `PGT`/`PID` are empty. Read-backed phasing is not achievable at that distance with short-read
   fragments, and chaining through intervening heterozygotes fails as well: the only informative het
   between them is chr15:40,216,470, leaving gaps of 6,769 bp and 4,142 bp. Statistical phasing is not
   viable for alleles this rare. **Resolution requires parental testing (definitive and cheapest),
   long-range PCR across the ~11 kb interval followed by amplicon sequencing, or long-read WGS.**
   *In trans* is currently an inference.
2. **p.(Asn1002Lys) needs functional support.** No literature exists for this variant (Europe PMC
   returns 0 hits for `Asn1002` / `N1002K`) and it is absent from ClinVar. A spindle-assembly-checkpoint
   or chromosome-missegregation assay, or BUBR1 quantification in patient cells, is the evidence that
   would move it out of VUS. Note the nuance: the BUBR1 "kinase" domain is a **pseudokinase** domain,
   so a missense there is not automatically loss-of-function — though the domain is required for
   kinetochore PP2A-B56 recruitment and checkpoint silencing (Gama Braga *et al.*, Cell Rep 2020,
   PMID [33207204](https://pubmed.ncbi.nlm.nih.gov/33207204/)), so a damaging effect is plausible.
3. **Structural variants are not excluded, and coverage was not assessed.** This is an SNV/indel
   callset only; it cannot rule out an exonic CNV in *BUB1B*. Mean depth at called sites within the
   gene (35.7) is comparable to flanking 71 kb windows (41–42) and heterozygous calls span the whole
   locus, which argues against a large deletion — but that is inference, not an SV call. SV/CNV
   calling plus per-base exon coverage from the FASTQ/BAM would close this.
4. **Splice predictions unavailable.** The Broad SpliceAI lookup API timed out on every request, so a
   cryptic-splice contribution from the intronic variants — and any splice effect of `c.3006T>G` —
   remains unverified.
5. **Scope.** *CEP57* and *TRIP13* were not analysed for this submission, and no genome-wide
   secondary-findings screen was run — hence no `secondary` rows in the predictions file.

---

## 6. Methods

**Input.** The provided joint-genotyped VCF `WGS_EX2312012_HGWCNDSX7.vcf.gz` (+ `.tbi`), single
sample. Per its header: Sentieon `Haplotyper` → `GVCFtyper` (sentieon-genomics-202308.02,
2025-02-04/05) against
`GCA_000001405.15_GRCh38_no_alt_analysis_set_plus_hs38d1_maskedGRC_exclusions_v2_no_chr.fasta`,
hard-filtered with GATK 4.2.4.0 `VariantFiltration` (QD<2, MQ<40, ReadPosRankSum<−8, FS>60,
MQRankSum<−12.5). **Build verified as GRCh38** from the reference name and contig lengths. Contigs
are unprefixed in the VCF; positions were emitted as `chr15` in the submission CSV per the template.

**Analysis.** Region extraction and quality/genotype inspection with `bcftools` 1.19. Transcript
model for `ENST00000287598.11` from UCSC hg38 `knownGene` via the UCSC REST API; gene bounds from
Ensembl REST. Exon/intron placement computed locally from that model. **The transcript model was
internally validated** against independently-derived snpEff HGVS (exon 2 starts at `c.180`, exon 5
ends at `c.581`, exon 8 ends at `c.1058`; total CDS 3,153 nt = 1,050 aa + stop), which reproduced
every boundary exactly. Functional annotation, population frequencies, ClinVar status and dbNSFP
predictor scores from MyVariant.info; frequencies independently re-checked against the gnomAD v4
GraphQL API; ClinVar records re-checked via NCBI E-utilities; gene–disease validity and dosage from
the ClinGen download endpoints; protein domains from UniProt REST; literature via Europe PMC.
Classification per ACMG/AMP with ClinGen SVI refinements, scored on the Bayesian point framework.

**Data.** All public. No proprietary data used. No patient-level sequence data was transmitted to any
external service — only genomic coordinates, gene symbols and variant identifiers.

**Compound heterozygotes.** The approach outputs compound-het pairs as a single row using the
`chrom_2`/`pos_2`/`ref_2`/`alt_2` columns.

**Manual review.** This submission is analyst-driven (targeted gene analysis with manual ACMG
curation), not the unattended output of an automated pipeline.

We replicated this finding using multiple methods. This report was generated with the assistance of
Gamow Lab's internal system, but our *BUB1B* compound-heterozygote findings were recovered first with
VCF files only, plus a manual prompt to analyze top MVA genes, given to several commercial LLMs. For
example, we prompted ChatGPT: *"Do these VCF files contain a causative genetic diagnosis for Mosaic
Variegated Aneuploidy (MVA) in the BUB1B, CEP57 or TRIP13 genes?"*

---

## 7. References

1. Hanks S, *et al.* Constitutional aneuploidy and cancer predisposition caused by biallelic mutations
   in *BUB1B*. **Nat Genet** 2004;36:1159–61. PMID [15475955](https://pubmed.ncbi.nlm.nih.gov/15475955/)
2. Gama Braga L, *et al.* BUBR1 pseudokinase domain promotes kinetochore PP2A-B56 recruitment, spindle
   checkpoint silencing, and chromosome alignment. **Cell Rep** 2020;33:108397.
   PMID [33207204](https://pubmed.ncbi.nlm.nih.gov/33207204/)
3. Pejaver V, *et al.* Calibration of computational tools for missense variant pathogenicity
   classification and ClinGen recommendations for PP3/BP4 criteria. **Am J Hum Genet**
   2022;109:2163–77. PMID [36413997](https://pubmed.ncbi.nlm.nih.gov/36413997/)
4. Richards S, *et al.* Standards and guidelines for the interpretation of sequence variants (ACMG/AMP).
   **Genet Med** 2015;17:405–24, with ClinGen SVI refinements (PVS1 decision tree; Bayesian point
   framework).
5. ClinVar VCV000533901 — `NM_001211.6(BUB1B):c.2210T>G (p.Leu737Ter)`.
   https://www.ncbi.nlm.nih.gov/clinvar/variation/533901/
6. ClinGen Gene–Disease Validity and Dosage Sensitivity curations, *BUB1B*.
   https://search.clinicalgenome.org/kb/gene-validity
7. gnomAD v4.1. https://gnomad.broadinstitute.org/
8. UniProt O60566 (BUB1B_HUMAN). https://www.uniprot.org/uniprotkb/O60566/

---

*Research decision-support, not clinical sign-out. These are candidate findings with their supporting
evidence; a diagnosis-grade result requires the orthogonal validation described in §5.*
