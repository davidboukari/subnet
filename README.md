### IPV4 ###

* https://www.ipaddressguide.com/cidr
* https://cidr.xyz/

## Subnet nb IP

2 ^ (32 - mask) = nb addr in subnet - 2 (gateway + Braodcast)

ex: /28 => 32 - 28 = 4 => 2 ^ 4 =  16 - 2 = 14


### ADDR ###
1 byte = 1 Octets = 8bits  <= 255
2^7 + 2^6 + 2^5 + 2^4 + 2^3 + 2^2 + 2^1 + 2^0

1     1     1     1     1     1     1     1
128 + 64  + 32  + 16  + 8   + 4   + 2   + 1

IPV4 4 Octets => 8bits + 8bits + 8bits + 8bits => 32bits
DDN: Dot Decimal Notation
10101100	00010000	00000100	00000110
128+32+8+8	16	 	4		4+2
172		16		4		6


192		168		5		23
11000000	10101000	00000101	00010111

### IPV4 Classes ###

## Public => Pay ##
|	Class	| 1st Octet Dec Range 	|Start Addr/network ID	| 	Finish Addr	|  Default Subnet Mask	| Informations  | Network  | Example	|
| --            |  --                   |           ---         |       ---             |      ---              |   ---         |  ---     |  ---       |            
|	A	|	1-126	    	|	0.0.0.0	   	|	126.255.255.255	| 	255.0.0.0	|  Wan / Lan	| N.H.H.H  | 10.0.0.1	|	
| 127.0.0.0	| 127.255.255.255	|	Loopback	|			|			|  LoopBack	| 	   |		|
|	B	|	128-191		|	128.0.0.0	|	191.255.255.255 |	255.255.0.0	|		| N.N.H.H  | 172.16.0.1 |	
|	C	|	192-223		|	192.0.0.0	|	223.255.255.255 |	255.255.255.0	|		| N.N.N.H  | 192.168.0.1|
|	D	|	224-239		|	224.0.0.0	|	239.255.255.255	|			| Multicast	|   	   |		|
|	E	|	240-255		|	224.0.0.0	|	254.255.255.255 |	-----------	|		|	   |		|

## Private  => Free ##
|	Class	|  1st Octet Dec Range 	| Start Addr/network ID	| 	Finish Addr	|  Default Subnet Mask	|  Network   |
| ---           |  ---                  |   ---                 |  ---                  |   ---                 |    ---     | 
|	A	|	10		|  10.0.0.0		|	10.255.255.255  |   255.0.0.0		|   N.H.H.H  |
|	B	|	172		|  172.16.0.0		|	172.31.255.255	|   255.255.0.0		|   N.N.H.H  | 
|	C	|	192		|  192.168.0.0		|	192.168.255.255 |   255.255.255.0	|   N.N.N.H  | 	


### Exercices Network calc  ###
1.1.1.1  (ipcalc 1.1.1.1/8)
Class A
1Network part / 3Hosts part
Initial Addr 1.0.0.0 + 1 		=> 1.0.0.1
Last Addr 1.255.255.255 - 1 		=> 1.255.255.254

128.1.6.5  (ipcalc 128.1.6.5/16)
Class B
2N part / 2Host part
Initial Addr 128.1.0.0 + 1		=> 128.1.0.1
Last Addr 128.1.255.255 - 1		=> 128.1.255.254				

200.1.2.3  (ipcalc 200.1.2.3/24)
Class C
3N part / 1H part
Initial Addr 200.1.2.0 + 1		=> 200.1.2.1
Last Addr 200.1.2.255 - 1		=> 200.1.2.254

192.192.1.1  (ipcalc 192.192.1.1/24)
Class C
3N part / 1H part
Initial Addr 192.192.1.0 + 1		=> 192.192.1.1
Last Addr 192.192.1.255 - 1		=> 192.192.1.254

126.5.4.3  (ipcalc 126.5.4.3/8)
Class A
1N part / 1Host part
Initial Addr 126.0.0.0 + 1		=> 126.0.0.1
Last Addr 126.255.255.255 - 1		=> 126.255.255.254

| Ex Host Addr | Class | Network parts / Hosts parts | 		Initial addr		|     Last Addr				        |
|  ---         |  --   |    ---                      |    ---                           |    ---                                        |
| 1.1.1.1      |  A    |           1N / 3H           |  1.0.0.0     + 1  => 1.0.0.1	|     1.255.255.255    - 1 => 1.255.255.254     |
| 128.1.6.5    |  B    |           2N / 2H           |  128.1.0.0   + 1  => 128.1.0.1	|     128.1.255.255    - 1 => 128.1.255.254     |
| 200.1.2.3    |  C    |           3N / 1H           |  200.1.2.0   + 1  => 200.1.2.1	|     200.1.2.255      - 1 => 200.1.2.254       |
| 192.192.1.1  |  C    |           3N / 1H           |  192.192.1.0 + 1  => 192.192.1.1	|     192.192.1.255    - 1 => 192.192.1.254     |
| 126.5.4.3    |  A    |           1N / 3H           |  126.0.0.0   + 1  => 126.0.0.1  	|     126.255.255.255  - 1 => 126.255.255.254   |



### Example works netwokrs ###
Class private need 10Hosts / Networks => 128 64 32 16 8 4 2 1   => (16 > 10)  => 128 64 32 16 0 0 0 0 => 128 + 64 + 32 + 16 = 240 

Then for each network 16 by 16:
192.168.0.0

192.168.0.16


192.168.0.32


192.168.0.48




### Subnet ###

|   Prefix	| Binary Mask  				| Decimal 		|
|  ---          |   ---                                 |  ---                  |
|   /18 	|   11111111 11111111 11000000 00000000 | 255.255.192.0		|
|   /30		|   8        8        8        6        | 255.255.255.252       |  
                         Networks   <- -> Hosts


### Calculate Subnet ###

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
| --  | -- | -- | -- | - | - | - | - |

Calculate Existing Subnet Addresses

| Netwok  | Subnet | Hosts  |
| -       |  -     |  -     |
P = Prefix	N = Network	S = Subnet	H = Host

1 - Convert the mask to prefix /
2 - Determine N based on class
3 - Calculate S = P - N 
4 - Calculate H = 32 - P
5 - Calculate Hosts / Subnet: 2^H - 2
6 - Calculate Number of subnet 2^Subnet 

8.1.4.5  255.255.0.0   => P= /16 , A=8 , Subnet = 16 - 8 = 8, Host = 32 - 16 = 16 ,  Host/Subnet = 2^16 - 2 = 65536 - 2 = 65534 , Number of Subnet = 2^8 = 256

|      IP     |	    Mask	   |P = Mask to Prefix  | N = Class nb bits |Subnet bits S = P - N  | Host bits H=32-P  |  Hosts / Subnet = 2^H - 2  | Number of Subnet = 2^Subnet  |
|      -      |	    -   	   |        -           | -                 | -                     | -                 |  -                         | -                            |
| 8.1.4.5     |   255.255.0.0	   |    /16             |  A = 8            | S = 16 - 8  = 8       | H = 32 - 16 = 16  | 2^16 - 2 = 65536-2= 65534  |  2^8 = 256                   |
| 200.1.1.1   |   255.255.255.252  |    /30             |  C = 24           | S = 30 - 24 = 6       | H = 32 - 30 = 2   | 2^2 - 2 = 2 - 2  =  2      |  2^6 = 32 	            |	
| 130.4.102.1 |   255.255.255.0    |    /24             |  B = 16           | S = 24 - 16 = 8       | H = 32 - 24 = 6   | 2^6 - 2 = 32 - 2 =  30     |  2^8 = 255                   |




### Subnet Exercices ###
                   ->        <-
          | Network | Subnet | Host |              
2^	    7   6   5   4  3  3  1  0                   
    	  128  64  32  16  8  4  2  1 
  512  256   

|Ex n°|  Network ID | Mask Class | Nb Networks  | Nb Hosts	 |  Find nb bits to reserve 				 | Mask          | Find Network Step 			|
| -   |  -          | -          | -            | -      	 |  -    				                 | -             | -          		         	|
|  1  | 216.21.5.0  |     C	 |  5 Networks  |      ?   	 |  2^n >= 5 => 2^3=8 >= 5 => 3 bits Network 		 | /24 + 3 = /27 | 3 bits Network => 128 64 32		|	
|  2  | 195.10.30.0 |     C      |  50 Networks |      ?   	 |  2^6 = 64 >= 50 => 6 bits Network                     | /24 + 6 = /30 | 6 bits Network => 128 64 32 16 8 4   |
|  3  | 165.15.0.0  |     B      | 100 Networks |      ?   	 |  2^7 = 128 >= 100 => 7 bits Network                   | /16 + 7 = /23 | 7 bits Network => 128 64 32 16 8 4 2 |
|  4  | 216.21.5.0  |     C	 |     ?        |     30 Hosts   |2^n-2 >= 30 => 5 bits Hosts => 8-5= 3 bits Network     | /24 + 3 = /27 | 3 bits Network => 128 64 32          |
|  5  | 195.10.30.0 |     C      |     ?        |     50 Hosts   |2^6-2 = 62 >= 50 => 6 bits Host => 8-6= 2 bits Network | /24 + 2 = /30 | 2 bits Network => 128 64             |
|  6  | 165.15.0.0  |     B      |     ?        |    300 Hosts   |2^9-2 = 510 >= 300 => 9bits Hosts => 7 bits Netwok     | /16 + 7 = /23 | 7 bits Network => 128 64 32 16 8 4 2 |

## Ex n°1 ##
|Ex n°|  Network ID | Mask Class | Nb Networks  | Nb Hosts	 |  Find nb bits to reserve 				 | Mask          | Find Network Step 			|
| -   |  -          |  -         |  -           | -              |  -                                                    | -             |  -                                   | 
|  1  | 216.21.5.0  |     C	 |  5 Networks  |      ?   	 |  2^n >= 5 => 2^3=8 >= 5 => 3 bits Network 		 | /24 + 3 = /27 | 3 bits Network => 128 64 32		|	

Step of 32
| Network ID  | Initial  | Last  | Broacast  |
| -           | -        | -     |  -        |  
| 216.21.5.0  |  .1      | .30   | .31       |
| 216.21.5.32 |  .33     | .32   | .63       |
| 216.21.5.64 |  .65     | .66   | .96       |
| 216.21.5.96 |  .97     | .126  | .127      |
... 


## Ex n°2 ##
|Ex n°|  Network ID | Mask Class | Nb Networks  | Nb Hosts	 |  Find nb bits to reserve 				 | Mask          | Find Network Step 			|
| -   | -           |  -         |    -         |  -             |  -                                                    | -             |  -                                   |
|  2  | 195.10.30.0 |     C      |  50 Networks |      ?   	 |  2^6 = 64 >= 50 => 6 bits Network                     | /24 + 6 = /30 | 6 bits Network => 128 64 32 16 8 4   |

Steps of 4
| Network ID   | Initial | Last | Broacast |
| -            | -       | -    |   -      |
| 192.10.30.0  |  .1     | .2   | .3       |
| 192.10.30.4  |  .5     | .6   | .7       |
| 192.10.30.8  |  .9     | .10  | .11      |
| 192.10.30.12 |  .11    | .12  | .13      |
... 



## Ex n°3 ##
|Ex n°|  Network ID | Mask Class | Nb Networks  | Nb Hosts	 |  Find nb bits to reserve 				 | Mask          | Find Network Step 			|
| -   |  -          |  -         |  -           |  -             |   -                                                   |  -            |   -                                  | 
|  3  | 165.15.0.0  |     B      | 100 Networks |      ?   	 |  2^7 = 128 >= 100 => 7 bits Network                   | /16 + 7 = /23 | 7 bits Network => 128 64 32 16 8 4 2 |


## Ex n°4 ##
|Ex n°|  Network ID | Mask Class | Nb Networks  | Nb Hosts	 |  Find nb bits to reserve 				 | Mask          | Find Network Step 			|
| -   |  -          |  -         |  -           |  -             |   -                                                   |  -            |   -                                  | 
|  4  | 216.21.5.0  |     C	 |     ?        |     30 Hosts   |2^n-2 >= 30 => 5 bits Hosts => 8-5= 3 bits Network     | /24 + 3 = /27 | 3 bits Network => 128 64 32          |


## Ex n°5 ##
|Ex n°|  Network ID | Mask Class | Nb Networks  | Nb Hosts	 |  Find nb bits to reserve 				 | Mask          | Find Network Step 			|
| -   |  -          |  -         |  -           |  -             |   -                                                   |  -            |   -                                  | 
|  5  | 195.10.30.0 |     C      |     ?        |     50 Hosts   |2^6-2 = 62 >= 50 => 6 bits Host => 8-6= 2 bits Network | /24 + 2 = /30 | 2 bits Network => 128 64             |


## Ex n°7 ##
|Ex n°|  Network ID | Mask Class | Nb Networks  | Nb Hosts	 |  Find nb bits to reserve 				 | Mask          | Find Network Step 			|
| -   |  -          |  -         |  -           |  -             |   -                                                   |  -            |   -                                  | 
|  6  | 165.15.0.0  |     B      |     ?        |    300 Hosts   |2^9-2 = 510 >= 300 => 9bits Hosts => 7 bits Netwok     | /16 + 7 = /23 | 7 bits Network => 128 64 32 16 8 4 2 |












