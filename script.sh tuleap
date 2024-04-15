#!/bin/bash

mysql_server="${mysql_server:-localhost}"


# Configuration de Tuleap
/usr/share/tuleap/tools/setup.sh \
  --configure \
  --server-name="$TULEAP_SERVER_NAME" \
  --mysql-server="$mysql_server" \
  --mysql-password="$MYSQL_PASSWORD" \
  --assumeyes
