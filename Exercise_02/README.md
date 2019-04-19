# Exercise no.02 - Analyse datasets stored in the Onedata volume space

In this exercise we learn how to:

* Analyse the datasets stored in the volume space (filename = stocks.csv).
* Generate plot of the stock prices over time.

## Requirements
* Access the EGI Training infrastructure (see previous exercise).
* Generate the token to access the Onedata volume space (see previous exercise).
* Install missing libraries (see previous exercise).
* Mount the volume space with the datasets (see previous exercise).

<b>IMPORTANT NOTICE: We are using Python (v2.7.12) and the following libraries: `requests`, `csv` and `matplotlib (v1.5.3)` to analyse the datasets. If you are confident with other programming language and/or libraries, feel free to install additional libraries in the running container.</b>

## Dataset
The datasets to be analysed are available in the volume space (EGI Foundation/CSV/stock.csv) and have the following structure:

Add figure here..

In column B are reported the final values of the Apple stock at the end of the day.

## Hands-on

* Plot the Apple stock prices over time.
* Save the resulted plot image.

## Hints
Hint1: 
`→ ]$ pip install pandas`

Hint2:
 → In python run matplotlib.use('agg') before matplotlib.pyplot is imported anywhere, otherwise plt.plot() won't work

Hint3:
→ use `plt.savefig('fname.png')` to save figure in container.
→ then do `sudo docker cp <containerId>:/file/path/within/container /host/path/target` to copy file from the Docker container to your  VM account. 
→ use the `display` command to check the file image.

