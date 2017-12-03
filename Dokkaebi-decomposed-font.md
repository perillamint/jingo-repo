# File format
* Array of glyphs.
* Each glyphs has same width and height (Fixed-width font)
* Glyphs width and heights are multiple of 8

## Glyph bitmap format
* Each bit represents one pixel.
* pixels are stored in file line-by-line as *big endian*.

### Example: glyph 8x16
Hex sequence
```
00 00 08 1C 36 63 63 63 63 7F 63 63 63 63 00 00
```

are represented as
```
◻◻◻◻◻◻◻◻
◻◻◻◻◻◻◻◻
◻◻◻◻◼◻◻◻
◻◻◻◼◼◼◻◻
◻◻◼◼◻◼◼◻
◻◼◼◻◻◻◼◼
◻◼◼◻◻◻◼◼
◻◼◼◻◻◻◼◼
◻◼◼◻◻◻◼◼
◻◼◼◼◼◼◼◼
◻◼◼◻◻◻◼◼
◻◼◼◻◻◻◼◼
◻◼◼◻◻◻◼◼
◻◼◼◻◻◻◼◼
◻◻◻◻◻◻◻◻
◻◻◻◻◻◻◻◻
```

### Example: glyph 16x16
Hex sequence
```
00 00 00 00 3F FC 00 0C 00 0C 3F FC 00 0C 00 0C
00 18 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```

are represented as
```
◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻
◻◻◼◼◼◼◼◼◼◼◼◼◼◼◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◼◼◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◼◼◻◻
◻◻◼◼◼◼◼◼◼◼◼◼◼◼◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◼◼◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◼◼◻◻
◻◻◻◻◻◻◻◻◻◻◻◼◼◻◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻
◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻◻
```

# Font editor: HFED.EXE
When opening \*.FNT file with HFED.EXE, it requires header size, glyph width, glyph height. Although user can enter non multiple of 8 value to width and height, it will be ignored and ceiled to nearest multiple of 8.

# Font mapping
For convenience, I will call nth glyph to refer address (glyph size) * n.

## Latin alphabet glyphs
Extended ASCII. See https://imgur.com/l2dzvsb

## Hangul jamo glyphs
Consisted with 8x4x4 decomposed hangul glyphs.

8x4x4 decomposed hangul glyphs are consisted with
> 초성
>     초성 1벌 : 받침없는 ‘ㅏㅐㅑㅒㅓㅔㅕㅖㅣ’ 와 결합
>     초성 2벌 : 받침없는 ‘ㅗㅛㅡ’
>     초성 3벌 : 받침없는 ‘ㅜㅠ’
>     초성 4벌 : 받침없는 ‘ㅘㅙㅚㅢ’
>     초성 5벌 : 받침없는 ‘ㅝㅞㅟ’
>     초성 6벌 : 받침있는 ‘ㅏㅐㅑㅒㅓㅔㅕㅖㅣ’ 와 결합
>     초성 7벌 : 받침있는 ‘ㅗㅛㅜㅠㅡ’
>     초성 8벌 : 받침있는 ‘ㅘㅙㅚㅢㅝㅞㅟ’
>
> 중성
>     중성 1벌 : 받침없는 ‘ㄱㅋ’ 와 결합
>     중성 2벌 : 받침없는 ‘ㄱㅋ’ 이외의 자음
>     중성 3벌 : 받침있는 ‘ㄱㅋ’ 와 결합
>     중성 4벌 : 받침있는 ‘ㄱㅋ’ 이외의 자음
>
> 종성
>     종성 1벌 : 중성 ‘ㅏㅑㅘ’ 와 결합
>     종성 2벌 : 중성 ‘ㅓㅕㅚㅝㅟㅢㅣ’
>     종성 3벌 : 중성 ‘ㅐㅒㅔㅖㅙㅞ’
>     종성 4벌 : 중성 ‘ㅗㅛㅜㅠㅡ’

Ref: <cite>http://blog.naver.com/pulccot/40003192672</cite>
WebCite: <cite>http://www.webcitation.org/6eeyg9z2a</cite>

# Some fonts
## 둥근모꼴
### Latin alphabet glyphs
* Width: 8
* Height: 16

### Hangul jamo glyphs
* Width: 16
* Height: 16