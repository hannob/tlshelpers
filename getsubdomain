#!/bin/sh

query="SELECT lower(NAME_VALUE) NAME_VALUE FROM certificate_and_identities WHERE plainto_tsquery('certwatch', '%.$1') @@ identities (CERTIFICATE) AND NAME_TYPE LIKE 'san:%';"

(echo $1; echo $query | \
    psql --csv -t -h crt.sh -p 5432 -U guest certwatch | \
    grep '\.'$1'$' | grep -v '#\| ' | \
    sed -e 's:^*\.::g' -e 's:.*@::g' -e 's:^\.::g') | sort -u
