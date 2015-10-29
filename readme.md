Exact Maximum Clique *BBMC*-derived Algorithms
===================

This block currently contains a command-line interface for the **BBMC** bit-parallel exact maximum clique algorithms and other (published) variants. BBMCI is described in [1-2] and several applications of BBMCS are reported in literature connected to the Maximum Common Subgraph problem, as in [3-4]. It is currently being actively developped and several improvements have been proposed such as [5].This implementation uses the [BITSCAN](https://www.biicode.com/pablodev/bitscan) library for the bitstring encoding and [GRAPH](https://www.biicode.com/pablodev/graph) library for simple graphs encoded with BITSCAN. Both libraries are also available in the Biicode repository.

The source code has been developed with Visual Studio but has also been compiled with gcc.

The currently implemented algorithms are:

- *BBMC*:  Equivalent to BBMCI described in [1-2]. It uses an independent set approximate coloring procedure.
- *BBMC-T*: BBMCI implemented with a standard approximate coloring algorithm.
- *BBMCR*: BBMC with a recoloring strategy, described in [2].
- *BBMCL*: BBMC with a selective colorong strategy, described in [5].
- *BBMCL-T*: BBMCL with a standard approximate coloring procedure.
- *BBMCL-R*: BBMCL with a recoloring strategy.
- *BBMC-W*: BBMC optimized for sparse graphs.
- *BBMC-WT*: BBMC-W with a standard approximate coloring implementation.

We are working to include our latest improvements, as soon as they are published: *BBMCX*, *BBMCXS*, *BBMCSP* and *BBMCPara* 

Other parameters
-------------------------------

Critical parameters used by the command-line interface are:

- -x: number of threads (at the moment not used)
- -t: timeout in seconds
- -f: filename
- -a: algorithm [0-BBMC, 7-BBMC-WT]
- -o: initial ordering strategy (see later)
- -u: upper bound
- -l: lower bound
- -r: indicates first level loop unrolling

Initial ordering is well known to be critical in exact maximum clique. Currently the options available for the -o parameter are:

- 0: No initial ordering
- 1: Typical degeneracy ordering which runs in O(|V|*|V|)
- 2: Degeneracy ordering with neighbor degree tie-break
- 3: Degeneracy for sparse graphs (runs in O(|E|).

Instructions
-------------------------------
Only the -f parameter is required, the rest are optional. The binary created by default is called  *pablodev-examples-clique-test-clique.exe* and may be found inside the *bin* folder.

For additional instructions use the help parameter
   `<BINARY_NAME> --help`

For example, to execute BBMC with typical degeneracy ordering with no time-out over the DIMACS "brock200_1" graph the command line should be:

    <BINARY_NAME> -f <PATH>/brock200_1.clq -a 0 -o 1		


Performance of this implementation is similar to those described in the published papers. The developer is also the author of BBMCI.


Terms and conditions
-------------------------------

Please feel free to use this code. *Just remember it is a research prototype and may not work for you*.The only condition is that you cite references [1-2] and [5] in your work.

Finally your feedback is gladly welcome. If you run into any problems just send your specific question to Biicode forum or, if its a general issue, to *StackOverflow* (tags Biicode, C++).


Acknowledgements
-------------------------------
This work has been partially funded by the Spanish Ministry MINECO with grant [DPI2010-21247-C02-01](http://intelligentcontrol.disam.etsii.upm.es/arabot/).

References
-------------------------------
[1] *[An exact bit-parallel algorithm for the maximum clique problem](http://dl.acm.org/citation.cfm?id=1860369%20)*.

[2] *[An improved bit parallel exact maximum clique algorithm](http://link.springer.com/article/10.1007%2Fs11590-011-0431-y)*.

[3] *[Robust Global Feature Based Data Association With a Sparse Bit Optimized Maximum Clique Algorithm](http://ieeexplore.ieee.org/xpl/articleDetails.jsp?arnumber=6527958).*

[4] *[Fast exact feature based data correspondence search with an efficient bit-parallel MCP solver](http://http://link.springer.com/article/10.1007%2Fs10489-008-0147-6)*.

[5] *[Relaxed approximate coloring in exact maximum clique search](http://dl.acm.org/citation.cfm?id=2566230)*.


   