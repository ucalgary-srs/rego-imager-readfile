# Redline All-Sky Imager Raw PGM Data Readfile (REGO)

![idl-required](https://img.shields.io/badge/IDL-6.0%2B-lightgrey)
![license](https://img.shields.io/badge/license-MIT-brightgreen)

IDL procedures for reading Redline All-Sky Imager (REGO ASI) stream0 raw PGM-file data. The data can be found at https://data.phys.ucalgary.ca. 

NOTE: these programs are the exact same as those used to read THEMIS ASI data (https://github.com/ucalgary-aurora/themis-imager-readfile). This is why they are called "themis_imager_readfile".

## Requirements

- IDL 6.0+ is required
- Windows 7/10, Linux

## Supported Datasets

- REGO raw: [stream0](https://data.phys.ucalgary.ca/sort_by_project/GO-Canada/REGO/stream0) PGM files

## Installation

Download the programs and include in your IDL Path or compile manually as needed.

## Usage Examples

This readfile can be used in a couple of different ways. Below are a few ways:

1) read a single file
2) read a list of files
3) read files and populate all metadata fields
4) read the only the first frame
5) read files without processing the metadata (ie. skip metadata, or you know the file doesn't have any)

### Read a single one-minute file

```
IDL> themis_imager_readfile_new,filename,img,meta
IDL> help,img
IMG             UINT      = Array[256, 256, 20]
IDL> help,meta
META            STRUCT    = -> THEMIS_IMAGER_METADATA Array[20]
```

### Read multiple files (ie. one hour worth)

```
IDL> f=file_search("C:\path\to\files\for\an\hour\*")
IDL> themis_imager_readfile_new,f,img,meta
IDL> help,img
IMG             UINT      = Array[256, 256, 1200]
IDL> help,meta
META            STRUCT    = -> THEMIS_IMAGER_METADATA Array[1200]
```

### Read file and populate all metadata fields

```
IDL> themis_imager_readfile_new,filename,img,meta,/all_metadata
```

### Read only the first frame of a file (can be used to speed up performance if you only need the first frame)

```
IDL> themis_imager_readfile_first_frame,filename,img,meta,/first_frame
IDL> help,img
IMG             UINT      = Array[256, 256]
IDL> help,meta
String          STRUCT    = -> THEMIS_IMAGER_METADATA
```

### Read file without processing metadata (file has no metadata or you just don't want to read it)

```
IDL> themis_imager_readfile_no_meta,filename,img,meta,/no_metadata
```
