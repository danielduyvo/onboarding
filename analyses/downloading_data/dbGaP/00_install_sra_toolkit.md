# Installing SRA Toolkit

To download data from dbGaP, you will need to use their command line tools
included in NCBI Sequence Read Archive (SRA) Toolkit. These are available as
compiled binaries that you can download and run immediately, as well as source
code if you need to build the binaries yourself (unlikely that you need to
though). Luckily, due to the popular use of SRA Toolkit, both Hoffman2 and
Respublica have the toolkit installed as modules.

## Respublica

Respublica, as of 2024-02-19, has two versions of SRA Toolkit installed: version
2.10.5 and version 3.0.3. By default, version 3.0.3 will be loaded, but you can
select the older version if necessary.

```{bash}
# Loading in the default version of SRA Toolkit
module load SRA-Toolkit

# Equivalent to
module load SRA-Toolkit/3.0.3-gompi-2022a

# Switching to the older version of SRA Toolkit
module load SRA-Toolkit/2.10.5-centos_linux64
```

## Hoffman2

Hoffman2, as of 2024-02-19, has only one version of SRA Toolkit installed:
version 2.10.9.

```{bash}
module load sra-tools

# Equivalent to
module load sra-tools/2.10.9
```

## Downloading the compiled binaries

If you need a different version of SRA Toolkit, or you are using a
server/computer that does not have SRA Toolkit installed, you can download the
compiled binaries from their [GitHub page](https://github.com/ncbi/sra-tools/wiki/01.-Downloading-SRA-Toolkit).  

If you are installing SRA Toolkit on a computer with a web browser, you can
navigate to their GitHub page and download SRA Toolkit from their links. If you
are installing SRA Toolkit on a server without a web browser, you will have to
open the GitHub page on a computer with a web browser, copy the download link
and then use the command line to download the binaries. In either case, make
sure to select the download that matches your server's/computer's operating
system and architecture. For a recent MacBook, it would be MacOS on Arm64 bit
architecture; for a server, it would probably be CentOS Linux or Ubuntu Linux on
64 bit architecture. Hoffman2 is CentOS and Respublica is Red Hat Enterprise
Linux and is able to run CentOS binaries.

```
# Download and extract the tarball file from GitHub
wget https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/3.0.10/sratoolkit.3.0.10-centos_linux64.tar.gz`
tar -xzvf sratoolkit.3.0.10-centos_linux64.tar.gz

# Path to the binaries will be at
# ./sratoolkit.3.0.10-centos_linux64/bin/
# For example, you can call vdb-config from SRA Toolkit like this:
./sratoolkit.3.0.10-centos_linux64/bin/vdb-config --version

# You can optionally add the binaries to your PATH environment variable for convenient use
export PATH=$PWD/sratoolkit.3.0.10-centos_linux64/bin/:$PATH
vdb-config --version
```