## A Policy Language to Capture Compliance of Data Protection Requirements.


### Overview:

This repository contains Maude's formalization of the submitted work: **A Policy Language to Capture Compliance of Data Protection Requirements**.  

### Download and Run: 

To run and test the code, the rewriting tool [http://maude.cs.illinois.edu/][Maude version 3.1] is needed. To download, please refer to the documentation for installation instructions and further information., it's downloadable free of charge from the University of Illinois. 


### Usage
The formalization is an initial implementation of compliance checking and hierarchical structures. The proof of concept makes the checking of compliance executable.  The tree structures are specified in taxonomy.maude. The Compliance checking is specified in the file PolicyCompliance.maude. The actions are specified in action.maude.

* Download Maude 3.1 and the files listed on /maude in the same directory. After installing Maude, to run the examples and test the compliance, use the following commands in your terminal:

```
 sudo ./maude.darwin64 
 load  PolicyCompl.maude .
 ```
 

Once the files are loaded to Maude, you can check the properties mentioned like . 
 
* Example 1 : We check the compliance between two individual policies i.e, 
  - PE1 = (doctor , {Use, Store}, healthServ\marketing\admin, 21/02/2022, EU)
  - PE2 =(hospital\admin, {Use,Collect,Store}, treatm, 21/02/2024, EU)
  - PE3 = (doctor, {Use, Store, Transfer}, healthServ\marketing\billing, 21/02/2022, EU)

```
red PE1 \C PE2 .
red PE3 \C PE2 .

```
* Example 2 : We check the compliance between two policy sets  i.e,
  #### Policy set 1 
  * PE4 =(doctor,{Use,Collect,Store},healthServ,21/02/2023,EU)
  * PE5 =(hospital\marketing,{Use,Transfer},healthServ,30/08/2023,EU)
  * PE6 =(healthAsso,{Use,Collect,Store},treatm,30/03/2023,EU))
  #### Policy set 2 
  * PE′ = (hospital\admin,{Use},treatm,01/01/2023,EU) 
  * PE′′ = (doctor,{Use},spclTreatm,01/01/2023,EU)
  * PE′′′ = (doctor,{Use,Store},spclTreatm,01/01/2023,EU)

```
red totalcomply( PE` , (PE4,, PE5,, PE6)) .
red totalcomply( PE`` , (PE4,, PE5,, PE6)) .
red totalcomply( PE``` , (PE4,, PE5,, PE6)) .
```


### Remarks:

* This implementation is part of the work in progress framework.
* We will extend this implementation in the future with more added properties.
