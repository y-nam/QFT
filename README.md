# QFT

Approximate Quantum Fourier Transform (AQFT) with O(n log(n)) T gates

This repository contains:

* Quantum circuits of the AQFT with O(n log(n)) T gates
  in a custom notation in the netlist representation.

Explicit descriptions of the algorithms, implementation details, and
original references can be found in the following paper.

* Yunseong Nam, Yuan Su, and Dmitri Maslov
  Approximate Quantum Fourier Transform with O(n log(n)) T gates
  March 2018. Available from
  https://arxiv.org/abs/1803.04933.

## License

* The code is released under the Apache License. See the LICENSE and
  NOTICE files for more information.

## Notations

All gates are of the following form

        :G [target(s)] [control(s)] {classical control(s)} Angle

* ":" := Prefix for a gate
* "G" := Gate type
* "[]" := Qubit register
* "{}" := Classical register
* "Angle" := Optional angle (default pi)

Available gate types are

* i := Initialization to 0
* m := Measurement
* h := Hadamard gate
* rz := RZ gate
* s := S gate
* si := Inverse S gate
* t := T gate
* ti := Inverse T gate

The exceptional case in the notation is a CNOT gate.
In this special case, the notation is

        :cnot [control] [target] {classical control(s)}

Note that the control qubit comes first.

The two preceding lines in each circuit file

        // max qubit #
        // ops count #
        
denote the total number of qubits and the number of
gates in a given circuit file.

## Circuits

The circuits are given in the ASCII format. The circuits correspond
to the AQFT of sizes 8, 16, 32, 64, 128, 256, 512, 1024, 2048, and
4096. All cases considered here use b = 13, i.e., those controlled
z^a rotation gates with rotation angle less than pi/2^b are removed.
The circuit optimizations were carried out using the techniques detailed 
in the following paper.

* Yunseong Nam, Neil J. Ross, Yuan Su, Andrew M. Childs, and Dmitri
  Maslov. Automated optimization of large quantum circuits with
  continuous parameters. October 2017. Available from
  https://arxiv.org/abs/1710.07345.
  
Filenames for the AQFT circuits are

        Postoptim_QFT#_bandwdith#
        
The first # is the size of the AQFT.
The second # is the aforementioned b parameter.

Filenames for the Repeat-Until-Success (RUS) circuits are

        RUS#.txt
        
The # is the angle parameter. The angle that each RUS
approximates is pi/2^#.

Note that each of the RZ gates in the AQFT circuits, 
used to prepare the special state |\Upsilon>, is exercised 
by using appropriate RUS circuits.

## Contributors

* Yunseong Nam
* Yuan Su
* Dmitri Maslov

## Contact

Questions and comments can be addressed to: nam@ionq.co
