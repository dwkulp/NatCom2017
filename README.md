# NatCom2017
Protocol Capture for design calculations in Kulp et al. Nature Communications 2017

## Design of Olio6 ##
first relax the structure 4TVP (note rosetta database needs to be specified)

  `relax -symmetry:symmetry_definition gp120_symm.def -in::file::s  4TVP_ABC_INPUT.pdb -fa_input  -ignore_unrecognized_res -relax::constrain_relax_to_start_coords -relax::sc_cst_maxdist 3.0 -nstruct 10000 -overwrite` 

selected the best energy model and used as the starting structure 

  `fixbb -database rosetta_database -fa_input -resfile resfile_cluster3_apolar -ignore_unrecognized_res -multi_cool_annealer 10 -packing:soft_rep_design -use_input_sc -no_his_his_pairE -nstruct 10 -overwrite -mute core.io.pdb.file_data`

## Design of Olio6 CD4KO ##

1) Thread the sequence of 4TVP to 3JWO as bound structure

2) Relax the bound(3JWO) and unbound structure 4TVP. Relax as above without symmetry.

3) saturated mutagenesis for each interface position with fixbb and calculate the energy difference(for each position, allow all 20 amino acid, the neighboring residues in 8A are allowed to repack)
An example resfile is: 4TVP_A_relaxed_mutate_A0473_T.resfile

## Rosetta Version ##
Rosetta version bdef871ea0f9cfd3bd76188d3ba0724dd72cee5b 2014-08-14 00:30:00 -0400 from git@github.com:RosettaCommons/main.git

