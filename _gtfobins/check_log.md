---
description: |
  This is the `check_log` Nagios plugin, available e.g. in `/usr/lib/nagios/plugins/`.
functions:
  file-read:
    - code: |
        LFILE=file_to_read
        OUTPUT=output_file
        umask 022
        check_log -F "$LFILE" -O "$OUTPUT"
        cat "$OUTPUT"
  file-write:
    - code: |
        LFILE=file_to_write
        INPUT=output_file
        umask 022
        check_log -F "$INPUT" -O "$LFILE"
  suid:
    - code: |
        LFILE=file_to_write
        INPUT=output_file
        umask 022
        ./check_log -F "$INPUT" -O "$LFILE"
  sudo:
    - code: |
        LFILE=file_to_write
        INPUT=output_file
        umask 022
        sudo check_log -F "$INPUT" -O "$LFILE"
---