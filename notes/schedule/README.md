# schedule
My weekly schedule, exam dates, calendars, etc.

### weekly.csv
My weekly course schedule

Format:

    -,Monday,Tuesday,Wednesday,Thursday,Friday,Saturday,Sunday
    15:40,JA202 ie104,CENG280 bmb1,HIST2202 m04,CENG232 bmb2,-,-,-
    16:40,JA202 ie104,CENG280 bmb1,HIST2202 m04,-,-,-,-

Commands:
    
    $ courses() {
    $   if [ -z ${1+x} ]; then cat weekly-pretty.txt; return; fi
    $   awk -F, "{ print \$1 \"\t\" \$(1+$(date -d $1 +%u)) }" weekly.csv
    $ }

    $ courses "2 days ago"
    -       Wednesday
    08:40   -
    09:40   CENG222 bmb3
    10:40   -
    11:40   -
    12:40   JA202 ie104
    13:40   JA202 ie104
    14:40   -
    15:40   HIST2202 m04
    16:40   HIST2202 m04
    17:40   -

    $ courses
    -      Monday        Tuesday       Wednesday     Thursday      Friday  Saturday  Sunday
    08:40  -             -             -             -             -       -         -
    09:40  -             -             CENG222 bmb3  -             -       -         -
    10:40  CENG222 bmb2  CENG232 bmb2  -             -             -       -         -
    11:40  CENG222 bmb2  CENG232 bmb2  -             CENG280 bmb1  -       -         -
    12:40  -             -             JA202 ie104   -             -       -         -
    13:40  -             -             JA202 ie104   -             -       -         -
    14:40  -             -             -             -             -       -         -
    15:40  JA202 ie104   CENG280 bmb1  HIST2202 m04  CENG232 bmb2  -       -         -
    16:40  JA202 ie104   CENG280 bmb1  HIST2202 m04  -             -       -         -
    17:40  -             -             -             -             -       -         -

### weekly-transposed.csv
Weekly course schedule where days are records and hours are fields

    $ findcourse() {
    $     awk -F, "/$1/{for(i=1;i<NF;i++){if(\$i~/$1/){print\$1,6+i\":40\",\$i}}}" weekly-transposed.csv
    $ }

    $ findcourse CENG232
    Tuesday 10:40 CENG232 bmb2
    Tuesday 11:40 CENG232 bmb2
    Thursday 15:40 CENG232 bmb2
