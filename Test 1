#include <stdbool.h>
#include <stddef.h>
#include <stdint.h>
#include <stdio.h>
#include <string.h>

#define PACKED_BYTE(b) (((uint64_t)(b) & (0xff)) * 0x0101010101010101u)

bool is_ascii(const char str[], size_t size)
{
    if (size == 0)
        return false;
    int i = 0;
    for(int k = 0; k < size / 8; k++, i += 8){
        uint64_t s;
        memcpy(&s, str + i, 8);
        if((s & PACKED_BYTE(0x80)) == 0){
            s = s & PACKED_BYTE(0x5F);
            uint64_t A = s + PACKED_BYTE(128 - 'A');
            uint64_t Z = s + PACKED_BYTE(128 - 'Z' - 1);
            if(((A^Z) & PACKED_BYTE(0x80)) ^ PACKED_BYTE(0x80))
                return false;
        }
        else
            return false;
    }
    while(i < size){
        if ((str[i] & 0x5F) < 65 || (str[i] & 0x5F) > 90)
            return false;
        i++;
    }
    return true;
}

void main() {
  char t[] = {"sdsdsSDASrhjk"};
  char s[] = {"Abds@djilajdl~!]"};
  if (is_ascii(t, strlen(t)))
    printf("TRUE\n");
  if (is_ascii(s, strlen(s)))
    printf("TRUE\n");
}
