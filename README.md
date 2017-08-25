# image-gender-inference
This repository consists of codes related to the paper " Inferring Gender from Names on the Web: A Comparative Evaluation of Gender Detection Methods" by Karimi et al., WWW Conf. 2016 http://dl.acm.org/citation.cfm?doid=2872518.2889385

Codes are written by
Fariba Karimi, Florian Lemmerich and Stefan Vujovic

In order to perform gender inference according to the aproach described in the paper mentioned above the following files can be used:
1. [genderize_query.py](https://github.com/frbkrm/image-gender-inference/blob/master/genderize_query.py)
2. [getGoogleImagesv0.31.jar](https://github.com/frbkrm/image-gender-inference/blob/master/getGoogleImagesv0.31.jar)
3. [faceplus_query.py](https://github.com/frbkrm/image-gender-inference/blob/master/faceplus_query.py)

## genderize_query

This is the first step in our "pipeline", where the [genderize API](http://genderize.io/) is used to infer gender, based on the first name of a person. 

### Dependencies

* [Pandas](https://pypi.python.org/pypi/pandas/)
* [Genderize Client](https://pypi.python.org/pypi/Genderize/0.1.5)
* Python 3.x
* Genderize API key

Before running the script a file (csv or json) with first names is needed. An output file with gender, confidence for assigning gender, and frequency of the names in the database will be generated.

In order to run the scipt two command line arguments need to be specified, path to the input file with names, and path where the output file should be saved. 
 
```{r, engine='bash', count_lines}
python genderize_query [inputfile.csv] [outputfile.csv]
```

For the next step we need to retrieve images for specified names from Google Image results by using getGoogleImages and then use [Face++ API](https://www.faceplusplus.com/) to infere gender out of these images.

## getGoogleImages

Before runing this file, a file containing first and last names should be prepared. The format of one name is:
FIRST_NAME+LAST_NAME, for example: fariba+karimi. As a result of runing the script, a file will be generated and it will contain 5 URLs of images retrieved for specified name, for example: fariba+karimi,[url1,url2,url3,url4,url5] 

### Dependencies

* Java

The script can be ran this way: 
```{r, engine='bash', count_lines}
java -jar getGoogleImagesv0.31.jar [inputfile.txt]  [output.csv]
```
## faceplus_query
