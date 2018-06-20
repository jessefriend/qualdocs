# qualdocs
A python library for supporting open qualitative coding of text data in Google Docs comments. 
Forked version which searches through folders instead of files.

## Motivation

Open qualitative coding (also called inductive qualitative coding) is a methodology common among social scientists who deal with heterogeneous, unstructured text data, such as news articles and interviews. Text is annotated with tags, called codes, which can be further categorized into a hierarchical structure. In contrast to closed qualitative coding, there is no pre-set list or typology of tags, as the researchers are supposed to inductively generate a typology. 

Existing offerings for open qualitative coding are closed source and expensive (MaxQDA, nVivo, Dedoose). Google Docs provides a relatively easy-to-use, free, collaborative, and secure platform for document annotation. But there is not an easy way to aggregate, synthesize, or search through codes -- particularly across documents. This is where qualdocs comes in.

## How to code text in Google Docs
This approach to qualitative coding is based on comments made in Google Docs files. Leave one set of codes per comment, in any of the following formats:
```
topcode1
topcode1, topcode2
topcode2: subcode1
topcode1: subcode1: subsubcode1
topcode2: subcode1, subcode2, subcode3
topcode1: subcode2: subsubcode1, subsubcode2, subsubcode3
```
You can see a sample of docs coded in [this public folder](https://drive.google.com/drive/folders/0B8Obkw_p7o4xTkU1Y2o0WVJmalU?usp=sharing) on Google Drive.

## Setup
You're going to have to download and setup the original qualdocs, and then replace the core.py code from within this repository.

## Usage

Alternatively, see [this Jupyter notebook](https://github.com/qualdocs/qualdocs/blob/master/qualdocs-example.ipynb) for a demo.

```
import qualdocs
import pandas as pd

credentials = qualdocs.get_credentials()
service = qualdocs.get_service()

parent_ids = get_folder_ids(service, search= "user_input")
ids = get_file_ids(service, parent_ids)

json_dict = qualdocs.get_json_dict(service, ids)

df = qualdocs.json_to_df(json_dict)
```

## Dependencies

Requires pandas, httplib2, apiclient, oauth2client, numpy, PyDrive
