# CP-PC-SAFT-EoS
The repository contains an implementation of the CP-PC-SAFT method, used to predict both the speed of sound and density in ionic liquids
----
-The code is provided in the Wolfram language, which can be run using Wolfram Mathematica software
---
<h1>CP-PC-SAFT Instructions</h1>
-First, create a directory for example [C4Mim][Ac].
Copy the Mathematica file into this directory, add a subdirectory name dir = CreateDirectory["Outputs_NEWEST/413.15_K"], where directory 413.15K says that's where all outputs will be put.

-Define molar mass, three rho points I.E.

Mw = 19833/100; \[Rho]exp1 = 10624/10; \[Rho]exp2 = 
 10845/10; \[Rho]exp3 = 10128/10;

Ptrial1 = (P /. {V -> Mw/\[Rho]exp1}) /. {T -> 
    29315/100}; Ptrial2 = (P /. {V -> Mw/\[Rho]exp2}) /. {T -> 
    29315/100}; Ptrial3 = (P /. {V -> Mw/\[Rho]exp3}) /. {T -> 
    39315/100};
res = FindRoot[{Ptrial1 == 1, Ptrial2 == 600, 
   Ptrial3 == 200}, {\[Epsilon]k, 250}, {\[Sigma], 3.5*10^-9}, {m, 7},
   MaxIterations -> 1500, WorkingPrecision -> 58]
m = m /. res; \[Sigma] = \[Sigma] /. 
  res; \[Epsilon]k = \[Epsilon]k /. res; 

-Define the temperature (413.15 K) and the maximum iteration pressure in bars
  T = 413.15; stop = 1400;

<h2>Tips</h2>
-Remember to define the temperature in the code first, e.g. T=273.15, only then add the name of the new folder /273.15 K
If you do not do this, the script will overwrite the values from the previous temperature. 
-In Mathematica, it is much worse and less intuitive to create double loops, especially with the operation of multiple iterations in the very body of finding numerical solutions. That's why you <b>MUST<//b> close Mathematica, or clear the data, after getting results for a given temperature. 
  
