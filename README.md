#wnNrMacPhyInterface
##Execution Steps
 Execution should be done in order : CU->PDCP->macSWintf->PhyEmulator->DU
Altran Stack executables are present in gNB_CU/bin and gNB_DU/bin 
1. Run wireshark in a terminal Using following commands
* cd build-3.0.2/
* sudo run/wireshark
* Capture on "any" interface and in order to see FAPI messages udp.port==38555 || udp.port==38556 can be used as display filter
2. Open another terminal and go to Altran Stack gNB_CU/bin/ and give root permission and run cu binary
* sudo su
* execute_cu.sh
3. Open another terminal and go to Altran Stack gNB_CU/bin/ and give root permission and then run pdcp binary
* sudo su
* execute_pdcp.sh
4. Open another terminal and go macSWintf/eclipse/wnNrMacPhyInterface/src/ and execute following commands
* gcc -o run_interface wnNrMacPhyInterface.c libSharedMem.a -lpthread
* sudo ./run_interface
5. Open another terminal and go to macFapi/wnNrPhyEmulator/debug/ and execute following commands
* make clean; make
* ./PhyFapiAPIExe     (no need for root privileges)
6.Open another terminal and go to ALtran Stack gNB_DU/bin/ and give root permission and run du binary
* sudo su
* ./execute.sh 