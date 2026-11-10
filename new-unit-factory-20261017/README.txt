New M-VAVE FM-1, factory state, full flash backup (2026-10-17)

Identity before the dump (tools/fm1_install.py --info): FM-1_015 [running], port "FM-1", no unit ID (stock firmware)
Read with the FM-1 Transporter (USB_KEY -> mask-ROM UBOOT), chip key 0x980F, flash ID 0x856014 (1 MiB)
Read twice, both reads identical. Nothing was written to the unit.

fm1-transporter-dump-20261017-001153.bin   1048576 bytes
  sha256 bf6371a494c3f7313672a4b393ded14b101ad8be8a93f06768076c2e27aa6ebd  crc32 9250E2B6
  head 0x0000..0x3FFF   == official V15 package head (sha256 d9f43191...)
  app  0x4000..0x92FFF  sha256 fe15e5c355e49dbde2a5e838c9fc35b14504ef51d37865e7a1c2c0547355cc91
                        0/143 sectors equal to the downloadable FM-1.fwsc (V15) region, 0/143 equal to the
                        older units' dumps: the factory image is NOT the public V15 package. This file is the
                        only copy of it.
  data written: 0x93000..0x93FFF, 0xE9000..0xF1FFF, 0xFA000..0xFBFFF; everything else 0x93000.. is erased
  no staged loader, no update record (the "loader DAMAGED" line in the .txt is the analyser reading an
  erased 0xE0000 area; there was never a loader there)

To put this unit back exactly as it came: write 0x4000..0x92FFF and the data sectors from this dump with the
Transporter (fm1_transporter_recover.py); the head is already identical.
