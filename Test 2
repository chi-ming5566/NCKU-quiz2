#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

uint64_t hexchar2val(char* in) {
    int str_point = 0, i = 0;
    uint64_t payload = 0, value = 0;
    if (*in == '0' && *(in + 1) == 'x')
        str_point = 2;
    memcpy(&payload, in + str_point, strlen(in) - str_point);
    uint64_t letter = payload & 0x4040404040404040;
    uint64_t shift = (letter >> 3) | (letter >> 6);
    for (letter = (payload + shift) & 0x0F0F0F0F0F0F0F0F; letter > 0; i++, letter = letter << 8)
        value |= value << 4 | ((letter & 0x0F00000000000000) >> 56);
    return value;
}

void main()
{
  printf("%ld\n", hexchar2val("f"));
  printf("%ld\n", hexchar2val("F"));
  printf("%ld\n", hexchar2val("0xFF"));
  printf("%ld\n", hexchar2val("0xCAFEBABE"));
  printf("%ld\n", hexchar2val("0x8BADFOOD"));
}
