# Bioinformatics-HW1
## Основные команды:
```bash

seqtk sample -s517 oil_R1.fastq 5000000 > R1_pairend.fastq

seqtk sample -s517 oil_R2.fastq 5000000 > R2_pairend.fastq

seqtk sample -s517 oilMP_S4_L001_R1_001.fastq 1500000 > R1_matepairs.fastq

seqtk sample -s517 oilMP_S4_L001_R2_001.fastq 1500000 > R2_matepairs.fastq

mkdir fastqc

ls *.fastq* | xargs -P 4 -tI{} fastqc -o fastqc {}

mkdir multiqc

multiqc -o multiqc fastqc

platanus_trim R1_pairend.fastq R2_pairend.fastq 

platanus_internal_trim R1_matepairs.fastq R2_matepairs.fastq

time platanus assemble -o Poil -t 2 -m 16 -f R1_pairend.fastq.trimmed R2_pairend.fastq.trimmed 2> assemble.log

time platanus scaffold -o Poil -t 2 -c Poil_contig.fa -IP1 R1_pairend.fastq.trimmed R2_pairend.fastq.trimmed -OP2 R1_matepairs.fastq.int_trimmed R2_matepairs.fastq.int_trimmed 2> scaffold.log

time platanus gap_close -o Poil -t 2 -c Poil_scaffold.fa -IP1 R1_pairend.fastq.trimmed R2_pairend.fastq.trimmed -OP2 R1_matepairs.fastq.int_trimmed R2_matepairs.fastq.int_trimmed 2> gapclose.log

```
Создавал, перемещал и удалял папки и файлы в WinSCP.

## Информация для данных до обрезки

![image](https://user-images.githubusercontent.com/93095449/139110865-222e38e6-a4b8-4985-96fb-047a0840d12a.png)

![image](https://user-images.githubusercontent.com/93095449/139111575-a16d3101-393e-428d-b889-f4b6df59e94e.png)

## Информация для данных после обрезки

![image](https://user-images.githubusercontent.com/93095449/139114406-734bd8ce-8d4e-4525-85a1-2a0d08f0cb43.png)

![image](https://user-images.githubusercontent.com/93095449/139114467-35a578f6-c76e-4c21-9652-42fb9fc60356.png)

## Изучение данных в Jupyter Notebook

![image](https://user-images.githubusercontent.com/93095449/139111760-1c037e91-1808-4189-9a45-6da32562e713.png)

![image](https://user-images.githubusercontent.com/93095449/139111886-8e42fbd7-9053-4ff4-bcba-62e57c4e5457.png)

![image](https://user-images.githubusercontent.com/93095449/139113115-34688e55-ffe7-4159-acd7-0cfd659afa8a.png)

![image](https://user-images.githubusercontent.com/93095449/139112850-d995428b-79f2-4ebd-99ec-5d6907554ee0.png)

