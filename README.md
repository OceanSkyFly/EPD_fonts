https://github.com/olikraus/u8g2/tree/master

http://wenq.org/

cat str.txt | iconv -f utf-8 -t c99 | sed 's/\\u\([0-9a-f]\{4\}\)/\$\1,\n/g' | sort | uniq | sed '/^$/d' | tr '/a-f/' '/A-F/' >> myfont.map


./bdfconv -b 0 -f 1 -M myfont.map -n u8g2_font_wqy12_t_myfont -o _u8g2_font_wqy12_t_myfont.c ./wenquanyi_12ptb.bdf


echo '#include "myfont.h"' > u8g2_font_wqy12_t_myfont.c

cat _u8g2_font_wqy12_t_myfont.c >> u8g2_font_wqy12_t_myfont.c

rm _u8g2_font_wqy12_t_myfont.c
