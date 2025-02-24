#!/usr/bin/make

.PHONY: erc drc sch_fab pcb_fab erc_and_fab drc_and_fab

all: erc_and_fab drc_and_fab

erc:
	kibot -d Fabrication -s drc -i

drc:
	kibot -d Fabrication -s erc -i

sch_fab:
	kibot -d Fabrication -s erc,drc  print_sch interactive_bom bom_html bom_csv

pcb_fab:
	kibot -d Fabrication -s all print_pcb gerbers excellon_drill gerber_drills position _blender_3d_top

erc_and_fab:
	kibot -d Fabrication -s drc  print_sch interactive_bom bom_html bom_csv

drc_and_fab:
	kibot -d Fabrication -s erc print_pcb gerbers excellon_drill gerber_drills position _blender_3d_top


