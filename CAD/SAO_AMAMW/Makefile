#!/usr/bin/make
DEBUG=-vvvv
MAK=kibot.mak
CONFIG=SAO_AMAMW.kibot.yaml
SCH=SAO_AMAMW.kicad_sch
PCB=SAO_AMAMW.kicad_pcb
DEST=Fabrication

all: erc_and_fab drc_and_fab

$(MAK): $(CONFIG)
	kibot -e $(SCH) -b $(PCB) -c $< -d $(DEST) -m $@

erc: $(MAK)
	$(MAKE) -f $(MAK) run_erc

drc: $(MAK)
	$(MAKE) -f $(MAK) run_drc

sch_fab: $(MAK)
	$(MAKE) -f $(MAK) out_sch

pcb_fab: $(MAK)
	$(MAKE) -f $(MAK) out_pcb

erc_and_fab: $(MAK)
	$(MAKE) -f $(MAK) all_sch

drc_and_fab: $(MAK)
	$(MAKE) -f $(MAK) all_pcb

.PHONY: erc drc sch_fab pcb_fab erc_and_fab drc_and_fab
