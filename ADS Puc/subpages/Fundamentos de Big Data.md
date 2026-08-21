---
base: "[[ADS - PUC-PR.base]]"
Reviewed: false
Created: 2023-05-15T12:55:00
Status: Not started
Description: ""
---
# Definição

- Grande quantidade de dados
- Podem estar em bancos separados
- Podem não estarem estruturados

# 5 V’s de Big Data

- Volume
	- Grande volume
	- Múltiplas fontes
- Velocidade
	- De processamento
	- Exige grande capacidade de HW
- Veracidade
	- Verificação de fontes
	- Dados tendenciosos
- Variedade
	- Estruturados
	- Não estruturados
	- Semiestruturados
- Valor
	- Significância dos dados coletados

# MapReduce

- Aplicação de funções nas entradas de valores, de forma a se obter apenas um valor na saída
- Map
	- Função aplicada a cada valor do conjunto
- Reduce
	- Visa encontrar um único valor de saída
	- Exemplo: média, mínimo, máximo, soma, moda

# HDFS - Hadoop Distributed File System

- Projeto Open Source
- Viabilizar resultados mais rápidos distribuindo o processamento entre vários nós
- É possível criar nós de maneira simples, em máquinas comuns
- Se ocorre falha em um dos nós, os dados são redirecionados e balanceados nos demais nós do cluster
- Permite armazenar dados em qualquer formato
- Nós que compõem o sistema
	- NameNode: 
		- armazena os metadados
		- Atua como mestre da arquitetura
		- Gerenciamento e monitoramento dos nós
	- DataNodes:
		- Armazenam o conteúdo dos arquivos em pequenos pedaços conhecidos como blocos
		- Os blocos são de tamanho fixo
		- Armazenamento dos blocos de forma distribuída
	- NameNode Secudário:
		- Verifica o log do NameNode
		- Armazena backup dos metadados
		- Testa as transações

![[Untitled 58.png]]

```shell
hadoop fs -copyFromLocal <arquivo> <pasta no HDFS>
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.pucpr</groupId>
    <artifactId>TesteMR</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.apache.hadoop</groupId>
            <artifactId>hadoop-common</artifactId>
            <version>2.7.3</version>
        </dependency>
        <dependency>
            <groupId>org.apache.hadoop</groupId>
            <artifactId>hadoop-mapreduce-client-core</artifactId>
            <version>2.7.3</version>
        </dependency>
        <dependency>
            <groupId>org.apache.hadoop</groupId>
            <artifactId>hadoop-mapreduce-client-jobclient</artifactId>
            <version>2.7.3</version>
        </dependency>
    </dependencies>
</project>
```

```java
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package com.pucpr.testemr;

import java.io.IOException;
import org.apache.hadoop.conf.Configuration;
import org.apache.hadoop.fs.Path;
import org.apache.hadoop.io.IntWritable;
import org.apache.hadoop.io.Text;
import org.apache.hadoop.mapreduce.Job;
import org.apache.hadoop.mapreduce.Mapper;
import org.apache.hadoop.mapreduce.Reducer;
import org.apache.hadoop.mapreduce.lib.input.FileInputFormat;
import org.apache.hadoop.mapreduce.lib.output.FileOutputFormat;
/**
 *
 * @author eduardo.quinalha
 */
public class Implementacao1 {
    
    public static class MapperImplementacao1 extends Mapper<Object, Text, Text, IntWritable> {
        
        @Override
        public void map(Object chave, Text valor, Context context) throws IOException, InterruptedException {
            String linha = valor.toString();
            String[] campos = linha.split(";");
            
            if (campos.length == 9){
                String ano = campos[2];
                int ocorrencia = 1;
                
                Text chaveMap = new Text(ano);
                IntWritable valorMap = new IntWritable(ocorrencia);
                
                context.write(chaveMap, valorMap);
            }
        }
        
    }
    
    public static class ReducerImplementacao1 extends Reducer<Text, IntWritable, Text, IntWritable>{
        
        @Override
        public void reduce(Text chave, Iterable<IntWritable> valores, Context context) throws IOException, InterruptedException{
            int soma = 0;
            for (IntWritable val : valores){
                soma += val.get();
            }
            IntWritable valorSaida = new IntWritable(soma);
            context.write(chave, valorSaida);
        }
        
    }
    
    public static void main(String[] args) throws IOException, InterruptedException, ClassNotFoundException{
        
        String arquivoEntrada = "/home/Disciplinas/FundamentosBigData/OcorrenciasCriminais/ocorrencias_criminais_sample.csv";
        String arquivoSaida = "/home2/ead2022/SEM1/eduardo.quinalha/Desktop/implementacaoLocalMR/implementacao1";
        
        if(args.length == 2){
            arquivoEntrada = args[0];
            arquivoSaida = args[1];
        }
        
        Configuration conf = new Configuration();
        Job job = Job.getInstance(conf, arquivoSaida);
        
        job.setJarByClass(Implementacao1.class);
        job.setMapperClass(MapperImplementacao1.class);
        job.setReducerClass(ReducerImplementacao1.class);
        job.setOutputKeyClass(Text.class);
        job.setOutputValueClass(IntWritable.class);
        
        FileInputFormat.addInputPath(job, new Path(arquivoEntrada));
        FileOutputFormat.setOutputPath(job, new Path(arquivoSaida));
        
        job.waitForCompletion(true);
        
    }
}
```

# Principais comandos hadoop

```bash
hadoop fs -copyFromLocal <arquivo de entrada> <diretório>
yarn jar <arquivo JAR> <entrada> <saida>
hadoop jar <arquivo JAR> <entrada> saida>

hadoop fs -ls <diretorio>

hadoop fs -copyToLocal <arquivo>

#Monitoramento do cluster
http://localhost:19888/

# Interface Gráfica
http://localhost:9870/

# Passo a passo
hadoop fs -copyFromLocal /home/thiago/wordcount/* input
yarn jar hadoop-cases.jar input output
hadoop fs -copyToLocal output/part-r-00000

```

![[Untitled 59.png]]
