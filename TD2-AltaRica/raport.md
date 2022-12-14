### 
```
/* Radar subsystem 
*  represented by a block diagram modeling pattern with repairable components 
*
*/
class GroundStationSubSystem
	// Parameters
	// ...


    // Components
	// ...
	RepairableInOutComponent Antenna;
	NonRepairableInOutComponent Transmitter1;
	NonRepairableInOutComponent Transmitter2;
	NonRepairableInOutComponent Receiver1;
	NonRepairableInOutComponent Receiver2;

	Boolean vfOutput ( reset = false );

	// Connections
	assertion
		Antenna.vfInput := true;
		// ...
		Transmitter1.vfInput := Antenna.vfOutput;
		Transmitter2.vfInput := Antenna.vfOutput;

		Receiver1.vfInput := Transmitter1.vfOutput or Transmitter2.vfOutput;
		Receiver2.vfInput := Transmitter1.vfOutput or Transmitter2.vfOutput;
		// vfOutput := ...;
		vfOutput := Receiver1.vfOutput or Receiver2.vfOutput;
end 
```
dfs