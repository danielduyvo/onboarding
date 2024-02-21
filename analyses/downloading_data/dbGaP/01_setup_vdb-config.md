# Setting up vdb-config

Before downloading data from dbGaP, you will need to setup your SRA Toolkit.
This will inform SRA Toolkit how it should fetch, cache and store data. Steps
01, 02 and 03 here will cover data downloads from dbGaP as well. Alternatively,
a tutorial from NCBI on how to download from dbGaP is available
[here](https://www.ncbi.nlm.nih.gov/sra/docs/sra-dbgap-download/).

```{bash}
# Assuming SRA Toolkit is in your PATH
vdb-config -i
```

![vdb-config user interface](images/01_00_vdb-config_ui.png)

The underlined letters on each of the UI elements indicates what letter to press
to use that element. For example, press `s` to save.`  

You can hit `x` to exit and begin using SRA Toolkit now that a configuration has
been made. If you would like to change default behavior, such as where downloads
will go by default, you can change it within this configuration tool. More
details about the tool can be found on the [GitHub Wiki](https://github.com/ncbi/sra-tools/wiki/05.-Toolkit-Configuration).