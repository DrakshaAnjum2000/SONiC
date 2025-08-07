# SONiC
 TC1: Checking Longevity Test
Goal: Validate that interfaces remain stable and traffic flows correctly over a long idle period (20+ minutes).

What it checks:

RX/TX packets and BPS before and after idle time

Consistent link state

No RX/TX errors or flaps (via syslog parsing)

Why it matters: Ensures SONiC behaves reliably under real-world idle conditions.

✅ TC2: Link Flap Stress Test
Goal: Stress test switch by flapping all ports 100 times.

What it checks:

Proper shutdown/startup of each interface

Interfaces come back to UP state

Why it matters: Tests interface resiliency under repeated flaps (common in high-availability networks).

✅ TC3: Verify SKU Ports and Speeds
Goal: Confirm hardware SKU matches expected port counts/types.

What it checks:

Total number of 100G, 400G, 25G ports

Presence and status of all expected ports

Why it matters: Ensures platform-level integrity and correct deployment.

✅ TC4: Verify Retimer to Non-Retimer Interface Speeds
Goal: Flap a combination of retimer and non-retimer ports and confirm recovery.

What it checks:

Interface UP status

Traffic is forwarded (RX/TX increase)

Why it matters: Validates behavior across different hardware paths.

✅ TC5: Multiple Link Flap Verification
Goal: Validate EEPROM and LLDP consistency after repeated flaps.

What it checks:

LLDP neighbors before and after flaps

EEPROM transceiver info before and after flaps

Why it matters: Ensures physical layer data is stable under port instability.

✅ TC6: Verify Retimer EEPROM & LLDP Post-Flap
Goal: Specifically test retimer ports for EEPROM/LLDP stability.

What it checks:

LLDP and EEPROM match pre- and post-flap

Why it matters: Retimer ports may behave differently under link resets.

✅ TC7: Verify Non-Retimer EEPROM & LLDP Post-Flap
Goal: Same as TC6, but for non-retimer ports.

Why it matters: Confirms stability on all port types.

✅ TC8: Verify Firmware via SDK
Goal: Retrieve firmware versions using Inphi Vega SDK inside syncd docker container.

What it checks:

Firmware versions for ports 1–6 and 27–32

Compares with expected values

Why it matters: Verifies correct firmware deployment at hardware level.

✅ TC9: Verify LLDP Post Link Flap
Goal: Ensure LLDP neighbor discovery survives link flaps.

What it checks:

LLDP neighbor info before/after flap

Why it matters: LLDP is critical for topology awareness and device communication.

✅ TC10: Verify EEPROM Post Link Flap
Goal: Confirm that transceiver EEPROM data remains consistent after link flaps.

Why it matters: Ensures hardware info (like vendor, part number) doesn’t get lost or reset.

✅ TC11: Verify LLDP, EEPROM, and Link Status (All Ports)
Goal: Perform a global health check across all interfaces.

What it checks:

LLDP neighbor presence

EEPROM validity

Interface admin and oper status

Why it matters: Catches any system-wide anomalies.

✅ TC12: Clear and Check Interface Counters
Goal: Reset counters and validate no residual RX/TX errors.

What it checks:

RX_ERR, TX_ERR, FCS errors == 0

Why it matters: Verifies clean interface state after reset.

✅ TC13: Verify BPS on Ethernet Ports
Goal: Ensure each port is actually forwarding traffic.

What it checks:

RX_BPS and TX_BPS > 0 for active interfaces

Why it matters: Detects silent interface failures with no traffic.

🧠 Summary of What You Demonstrated
🔧 Full-scale interface automation (shutdown/startup)

🔍 Pre/post validation strategy with data comparison

📶 LLDP & EEPROM integrity checks

🧪 Traffic verification through counters and BPS

🛠 Platform-level tests (SKU, firmware, port speeds)

🧼 Error validation via counter clearing

