# snpeff-usage

##对vcf文件注释
nohup java -jar snpEff.jar CriGri ~/ym/GS.vcf > ~/ym/GS.ann.vcf &

##snpeff配置自己的数据库
1、NCBI下载基因组gff、fna文件,假设名字为crigri
cd snpeff
mkdir -p data/crigri
mkdir -p data/genomes
cp crigri.gff data/crigri/genes.gff
mv crigri.fna data/genomes/crigri.fa
echo "crigri.genome : crig" >> snpeff.config
java -Xmx1G -jar snpEff.jar build -gff3 -v crigri


optional:指定使用的密码表

假设使用的名字为vibrio.
vibrio.genome : Vibrio Cholerae
	vibrio.chromosomes : NC_002505.1, NC_002506.1
	vibrio.NC_002505.1.codonTable : Bacterial_and_Plant_Plastid
	vibrio.NC_002506.1.codonTable : Bacterial_and_Plant_Plastid
