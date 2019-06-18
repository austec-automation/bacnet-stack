The BACnet Scriptable (using Perl) Tool.

* Running this tool assumes that the library has been already built. The 
  library should be built with a command similar to
  
  CC=/mingw/bin/gcc BACNET_DEFINES="-DPRINT_ENABLED -DBACAPP_ALL -DBACFILE
  -DINTRINSIC_REPORTING" BBMD_DEFINE=-DBBMD_ENABLED\=1 BACNET_PORT=win32 make
  clean library

  On linux / raspbian:
  make BUILD=debug BACNET_PORT=linux BACDL_DEFINE=-DBACDL_BIP=1 BACNET_DEFINES=" 
  -DPRINT_ENABLED=1 -DBACFILE -DBACAPP_ALL -DBACNET_PROPERTY_LISTS"

* Currently, the tool only tries linux and win32 port, but should be easily modifiable
  for any port  build.
* For linux, a device-client lib is needed (for a client implementation), put it in the
  lib folder so we don't have to go hunting
  cd ./demo/object;
  ar crf ../../lib/libdevice-client.a ./device-client.o  
* This tool has to be run from a path without any spaces. The presence of the
  .Inline directory is required.
* Run the tool without any arguments to see usage instructions
* To run the example ReapProperty script (which reads Analog Value 0 Present
  Value) for Device at instance 1234 run the following command

  perl bacnet.pl --script example_readprop.pl -- --device=1234 --objName=OBJECT_ANALOG_VALUE --objInst=1 --property=PROP_PRESENT_VALUE

