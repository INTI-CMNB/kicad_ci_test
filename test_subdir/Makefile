#!/usr/bin/make

.PHONY: erc drc sch_fab pcb_fab erc_and_fab drc_and_fab

all: erc_and_fab drc_and_fab

erc:
	kiplot -d Fabrication -s run_drc,update_xml -i

drc:
	kiplot -d Fabrication -s run_erc,update_xml -i

sch_fab:
	kiplot -d Fabrication -s run_erc,run_drc  print_sch interactive_bom bom_html bom_csv

pcb_fab:
	kiplot -d Fabrication -s all print_front print_bottom gerbers excellon_drill gerber_drills position

erc_and_fab:
	kiplot -d Fabrication -s run_drc  print_sch interactive_bom bom_html bom_csv

drc_and_fab:
	kiplot -d Fabrication -s run_erc,update_xml print_front print_bottom gerbers excellon_drill gerber_drills position


