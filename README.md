The repository contains a KNIME workflow to generate novel fragments for FBDD using the "syntax corrected" dual encoder model reported in Bisland et al (2021).

See https://pubs.acs.org/doi/10.1021/acs.jcim.0c01226

Full description of the KNIME workflow, instructions, and requirements are detailed in Bilsland et al (2022).

See ......

Tested on:
- Ubuntu 16.04
- KNIME Analytics Platform 4.1.2
- KNIME Server 4.10.1

Other requirements:
- Anaconda3
- CUDA >= 10.0.130

KNIME requirements:
- Python, RDKit, and Keras integration - see paper for details but KNIME should automatically offer to search and install these when the workflow is opened.

Installation:
- Install KNIME (https://www.knime.com/)
- Install Anaconda (https://www.anaconda.com/)
- Create the anaconda environment in the file knime_environment_ubuntu.yml either in anaconda prompt or anaconda navigator
- Import workflow to KNIME local workspace: File > Import KNIME workflow and browse to the .knar
- You should now be prompted to find and install the required KNIME integration if it is not already present
- Setup python integration in File > Preferences > KNIME > Python:
- Choose python3 as default
- Set environment configuration as conda and set the path to the Anaconda installation
- Create a new preconfigured python2 environment with [new environment]
- Select the environment created from the yml from the drop down list for the python3 environment
- Press [apply]
- In File > Preferences > KNIME > Python Deep Learning, select "Use python configuration"
- You should be ready to go

Notes:
- The workflow and conda environment have been tested in Analytics Platform and KNIME Server under Ubuntu 16.04. We also make available a conda environment yml for Windows, tested on Analytics Platform only (we do not have a KNIME server instance under Windows so we cannot vouch for this...) 
- For server deployment, we suggest to leave the 3 Keras network reader nodes executed and loaded in the workflow prior to deployment
- All other nodes should be reset
- Details of parts of the workflow relating to exotic SMILES and PSO parameters that can be reconfigured are in the paper
- Note that the PSO optimisation requires a SMARTS file containg structural alerts

- A default file is provided from sureChembl with some additions to rein in the model's imagination.
See https://www.surechembl.org/knowledgebase/169485-non-medchem-friendly-smarts.
Original source: Sushko et al (2012), Journal of Chemical Information and Modeling 2012 52 (8), 2310-2316.

- The user is advised to supply their own more comprehensive file for optimal performance. We direct users to a larger set of filters curated by Greg Landrum for optimal performance in RDKit. 

- These curated filters are available at https://github.com/rdkit/rdkit/blob/master/Data/Pains/wehi_pains.csv

For further details on the origin of these, see:
- http://rdkit.blogspot.com/2015/08/curating-pains-filters.html
- Baell and Holloway (2010) J Med Chem, 2010. 53(7): p. 2719-40
- Saubern et al (2011) Mol Inform, 2011. 30(10): p. 847-50

- The data folder contains the file BaseFeatures.fdef by Greg Landrum containing base definitions of pharmacophore features
- The BSD 3-clause license covering rdkit code redistribution is included below (just in case - I'm not a lawyer):

Copyright (c) 2006-2015, Rational Discovery LLC, Greg Landrum, and Julie Penzotti and others All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

The data folder also contains a modified version of the GPUutil.py file by Anders Krogh Mortensen (anderskm).

See https://github.com/anderskm/gputil

The MIT license is included in the modified file.
