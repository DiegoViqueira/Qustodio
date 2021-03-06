# Qustodio
	Test for Qustodio
	
	client-server OOP application in C++. The client is in charge of analyzing router logs and sending questionable 
	activities to the server. 
	The server application will receive those reports from many clients simultaneouslyand store them in memory to 
	process them later. 

### Prerequisites
  - GCC > 5 
  - Makefile 

### Filesystem Structure

```
  + -- /boost ( Boost Framework Utils. )
  |
  + -- /common ( Common Headears. )
  |
  + -- /src ( Sources Files. )
  :
  + -- /obj ( Temporary repository for builded Objects. )
  :
  + -- /build ( Build Directory for Executables.  )
```  

## Internal Protocol

+ Message Sequence

```
	CLIENT                    		SERVER
          |                          		   |
	  +---   Request (MSG TYPE = 0) ---------> +
	  |					   |
	  + <---- Responce (MSG TYPE = 1) ---------+

```

+ Field size Notation

```
  Common Header:
	
	Field		Size Octects         Type                  Description
	Msg Type            1 var	     uint8              Message type 0 = Request / 1 = Responce
	Msg Size            4 bytes          uint32             Message variable data Size
	
  Request:
  
  	Field		Size Octects         Type                  Description
        data               variable       C-Octet String         Data of Message
  
  Responce:
    
  	Field		Size Octects         Type                  Description
        data               variable       C-Octet String         Data of Message
	
```

+ Message Content

```
  Request  :  Common Header +  Request
  Responce :  Common Header +  Responce
```


## Deployment 

+ Clone repository localy
+ Download Boost C++ Framework (https://www.boost.org/users/download/) in Git project repository.

## Build Boost

* uncompress bost_[Version].zip into /boost 

```
cd boost
bootstrap.bat gcc
b2 --build-dir=MYBOOST
```


## Build

Makefile Fixes:
Edit Makefile in Project root dir and replace this 3 libraries for the right builded in boost/stage/lib
  - boost_filesystem-mgw73-mt-x64-1_67 
  - boost_system-mgw73-mt-x64-1_67 
  - boost_thread-mgw73-mt-x64-1_67

Compile Proyect:
```
make dirs
make all
```

Clean Proyect:
```
make clean
```



## Running the tests



Run Server
```
build\QustodioServer.exe
```
Run Client 1
```
build\QustodioCient.exe -f sample.log
```
Run Client 2
```
build\QustodioCient.exe -f sample1.log
```

## Console Output Example

```
every 5 second the server will print the qtty of offensive words and each Message

Inappropiate Message print:
   [1d9c]OFFENCIVE WORDS IN[device: c0-a0-39-6e-c8-8e][url: http://tubeboobsxxx.com/content][timestamp: 1397656906]

inappropriate qtty Report:
   Inapropiate Activities in last 5 seconds: 80

```
## Authors

* **Diego Viqueira** - *Initial work* 

## Built With

* [boost] Version: 1.67.0 - (https://www.boost.org/) - Boost Framework.


## License

This project is licensed under the GNU General Public License V.3 - see the [LICENSE.md](LICENSE.md) file for details
