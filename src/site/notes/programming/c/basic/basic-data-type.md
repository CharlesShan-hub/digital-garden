---
{"dg-publish":true,"permalink":"/programming/c/basic/basic-data-type/","contentClasses":".content svg {width: 100%; height: auto;}"}
---


# Basic Data Type

## Overview

<svg version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780.3905280090868 364.7090566117316" width="1560.7810560181736" height="729.4181132234633">  <!-- svg-source:excalidraw -->  <!-- payload-type:application/vnd.excalidraw+json --><!-- payload-version:2 --><!-- payload-start -->eyJ2ZXJzaW9uIjoiMSIsImVuY29kaW5nIjoiYnN0cmluZyIsImNvbXByZXNzZWQiOnRydWUsImVuY29kZWQiOiJ4nO2cW3PayFx1MDAxMsff8ylSPlXnaT079+nZN1+DL8R3O/apLZdcdTAwMDBcdTAwMTnLgIRBNthb+e7bI18kXHUwMDA0OCSFXHUwMDA0lTqkKlx0M5JaaPqn/vdMS/98+vx5JX7q+it/fV7xh3WvXHUwMDFkNHreYOVcdTAwMGbX/uj3+kFcdTAwMTRiXHUwMDE3T773o4dePdnyNo67/b/+/NPrdkkziGtR1Fwi9ajzspvf9jt+XHUwMDE493HD/+H3z5//Sf7OXHUwMDE4iv1hnGybtKZmZL7ta1x1MDAxNCZcdTAwMDaZXHUwMDAxLYw1IN63XGL6m2go9lx1MDAxYth947X7ftrjmlZcdTAwMWWPhoNe3DxuVG+Oo8rx5T6s3Vx1MDAxZKRGb4J2+yR+aifn04/wZ6d9/bhcdTAwMTe1/IugXHUwMDEx37799kz7tL160UPzNvT77nez99ao69WD+Mm1Ufre6oXN5Fx1MDAxOGnLXHUwMDEwvyluiVx1MDAwNFxuQlpNrTDqvdftz6UlVlx1MDAxYqmBa2ZcdTAwMThkul9ObCNqRz13Yv9hvvuTnlrNq7eaeH5h432buOeF/a7Xw4FKt1x1MDAxYrz+ZElcdLPWXHUwMDAy02ClXHUwMDEyjKembv2geVx1MDAxYrvTyZj3k1FcdTAwMDCpjFx1MDAxNIanP97Z7O40XHUwMDEyT/g7vfQ9r+PvuD3Ch3Y7e/3Cxuv1XHUwMDFi6ai5jq2MU6WHeug2vFx1MDAxN1x1MDAxN2CGS1x1MDAxMEJbKyE9s3ZcdTAwMTC28odrR/XWXHUwMDA0r7mJwvgkeHajwulI67bXXHTaTyOjmjgwXsW9/1x1MDAxZa+MNK61g6bz5JW2fzPq4nGAcL13x1E37a2jXHUwMDExL1xi/d74RYl6QTNcYr326SSD+Ov8ytt4MJJcdTAwMTmRmtf3Xa9rh6Tx+1x1MDAxZj+HojJTWWRSS6Vccksvx49Y3L/eXHUwMDE5mrXH3Xbn4uhu9bJ6LFx1MDAxZTfry82iUZZwqqxcdTAwMTiDLWFRcVwiXHUwMDE5RTCM4JIzgMJYXHUwMDE0QFx1MDAwMGE0XHUwMDFhqNaS6tlYZMgtt3j+doEwoovYXGZLRcO4YWm5MI5cdTAwMTgsXHUwMDEyxkzYy8FotFx1MDAxMkoxOXtcXFxc629tVjVf5/vdjTV5Rjf6/t3X5WZcdTAwMTGdn1AwknIhx6KiXHUwMDEyXHUwMDA0hEZPV4aORKq5g2hcYlx1MDAxN1xiorRGKVA2XHUwMDE1K1x1MDAxZnFcYlohhEjjQjlUUuhcdTAwMTI5tGVzaMvhkPF841x1MDAxYoeKcq5HtM+POIxUXGJcdTAwMDfXlerw9Oy8Lje6h9eb4na5OVx1MDAxNDq15fZcdTAwMTBS5mzPjzZgXHUwMDA0XHUwMDA1v+WgXHUwMDAwXHUwMDAwxUZcdTAwMWHHPqCNS433XHUwMDAxKlPtslx1MDAwMNi4XHUwMDA1w7LuWChsO2Hsh02/Vy5x41ZcdTAwMGLVolPzQmkwLFx1MDAwMGZFM2N3eH5E2/d794fnPO5cdTAwMWVcdTAwMWbs281rXHUwMDFjoCXHTlx1MDAxM25RhFJmlIFsjHNcdTAwMDeQmDVyg2xSjIKYXHUwMDFkXHUwMDE2mFx1MDAxN1x1MDAxYU44alFJXHUwMDE5KGcqVb1cdTAwMWZKUSU05rR0kXmhMYozk/XWQqnc9OtBx2uXXHUwMDBi5ZjRXCKZ1FMlKapRoJhcdTAwMTXNXHUwMDFlXG7F0/HaOTOV6perraHqr8VcdTAwMGY+31puJlx1MDAxNVx1MDAxN1x1MDAwNGm0VFxiPio7k8DIKaFcdTAwMTaAKcuMLVx1MDAxNEmuXGJ16SHqYlx0wCEjUT5iXHUwMDEyY6tknKeDWD6SmNXiaZSGZJC9emXgOGKwUFU6PT4ysEpKbuzs+eFOeL6tTsLhRf2bPDy/6HVgtbXsMDJDJFKI2osmSeAojFxuXGLlTHIhhIWRXHUwMDA0cu4polwiXHUwMDFhkz2tpXiZrJmFRY23XHUwMDEwUIItcqZcdTAwMDaYXHUwMDExXHUwMDE5LyqaxXZcdTAwMTQ2y4Vx1GKhYlXnXHUwMDFi32HUTFHKXHUwMDE1nVx1MDAxZEZ5tb7drPvBmmZ6sKFcdTAwMDPu+0c3S1x1MDAwZaNB3FxmXHUwMDE3YLRVXHUwMDEzI6Om1M2fXHUwMDE0XHSiYsRkhaqZadLUUkuBS7rI9Fx1MDAxMbTWtDxcdTAwMTL7t1Gv5LiYM1lsZJyqUkFKbSkquJlZvLi2u/X+6kG8Zc53Wzd6s3K2cbfkLFpJmODchT9cdTAwMTibOpVcdTAwMTiuLGp1jD5aumW+wnDUXHUwMDE0xbK1gs2+gMFcdTAwMTmjYFx1MDAwNerrRcKoaHbmtmhcdTAwMThcdTAwMWLRQ63tl0tj3maROPLpoVx1MDAxMX1Za8V+XHUwMDAyx7jVuzbD6HFY/Vwih53ml/PBXHUwMDBlk0uOI+pUg5JcdTAwMWNTr1FcdTAwMGVeaDSEYdBUXFyBXHUwMDAxm9GOc1x1MDAwZo40UamK5Vx1MDAxNjY/ylx1MDAxN3FoqFv5WCSM0nJT3mriTTvySo6MOZOFqtSpK1x1MDAxOYxiLLBcZjXTzChWLlx1MDAwNNydt9h++HS2uX17WT1cdTAwMGKH/nKjaDUnSJlCr1x1MDAxZZtQXHUwMDE1Ulx1MDAxMfQ3hjqMUlEoiUAkxkX5kzBSaplLI1x1MDAxNjmhXG6o4kuk8Xo9ikqeTs2ZXFxMYOSAMlXCT8C4fr33RbaeIK5cdTAwMWOE++1+vbrxdNpfblx1MDAxOI2SxM1BXGKJ4S9cdTAwMWZcdTAwMTeFpERcdTAwMTlMJo1RXHUwMDBlxlx1MDAwMlf4lSZcdTAwMTazRmGYXHUwMDEwoyH4I6FKMWPEs14sjYDnILK+WmzWiGj5jXJxzNssdHGD5lx1MDAxYjNzOIJqdNPZgWxWKmd6e6t++Y1ebjHauuat5+pyXHUwMDAzqUBcdTAwMTChOJ1cdTAwMThcdTAwMWRdYVx1MDAxY1xu2LHQOffFRkM00shcdTAwMDB4UmM3W1x1MDAwNVx1MDAwMFdSm8WW24DhpsTQ+Fx1MDAxMC5cdTAwMDLHcatFXHUwMDAyKadWo1ptXHUwMDE1hkczO4/+6UXjuMn2XHUwMDFmd+P96ta3qyB4Prpfblx1MDAxZTEpJNpQlOZcdTAwMTboyLp7QiRcdTAwMDPMXHUwMDFjOd6WwDBa6LyqZFx1MDAwNJS1XHUwMDA2XHUwMDE1KPp4tv7nI70qKXCDenGhK1x1MDAxY8aCtllnLVx1MDAxNMr6rVdySc6oxVwiYVx1MDAxNJBvTKOjdcXQKt3gRzB2n3dP4ufDk/r+sDf49lx1MDAxMJxcbiOWfLVRaEswY5tcdTAwMTBcdTAwMDHd/opaXHUwMDAyXHUwMDE4XHUwMDFmUbLm51xc5y5XVVKQKjFfXHUwMDA36k5lJlx1MDAxOI3irlx1MDAxZUYsKkJipsukRK3Ps85aKIxcdTAwMDfxbdlcdTAwMDVyOZOFLnKwqWpVXGKmmLvxzcxjqzPo+kfWNE73g1x1MDAwMO43zjtcdTAwMGaVZc9cdTAwMWU1I0q58Kg1ZSpXo6qYJFx1MDAwNT8t5Vxuw918Ksq+fIb6XHUwMDAxiIa7stbFPS31wiFYXZ5SfYyCklXqqMVCXHUwMDE16tRcdTAwMWFcdTAwMWNOjUS3oDD72sbxt1xuu7yo9u78gy11MqhdXHUwMDA1ezdLvtRoJVx1MDAxMFx1MDAwNVx1MDAxM1x1MDAxZlxcxGBIuFx1MDAxNkiHe3JcZlxuLFx1MDAxYbeU4KW2jL7UjM9YnypRIaKeXWgxnGWKllhcZne9XHUwMDExdbptf1jyjOqY1UJcdTAwMWaamipT0TOkdjVPM1x1MDAwM2nC+y/PV19r/mVcYpdf6563Ry+Ollx1MDAxZEhBYFJReIKktERrRV3yPCpcdTAwMWTnjSSymKxxMDxcdTAwMWYxWvTzXHUwMDAxk0JaRamGRc6pWtRcdTAwMTOmPJF6vdPxXHUwMDFjLb2nkqGcYHdcdTAwMWVYJltNlKtcdTAwMWZUXHUwMDAxMEE5xok0QvxcYkzvXHUwMDBi7a/by3P/rOufdbyNlle53J0rmFxyr3/rzzeBVIJcdTAwMTjkXHUwMDEy3mZYR9DE+OV6JTCbXHUwMDA3Zu4zrIxcdTAwMTOG90ElqHFPOU+YYWWEWYP8XCJcdTAwMTE092zJa/WqYZpcblxyc5jbeXOh1In4a8v3X1O3gjP9S4tcIv3Y68XrQdhcYsJmflx1MDAxNz9sTOlpe/1cdTAwMTgjXFwniPE0XHUwMDBlI1f/ndtcIjnuWq9cdTAwMTdccm59b+xa4JGn9nXd4dI3arhP+r/PqYMlX97///dcdTAwMWZcdTAwMTO3njru7jM24unRPmX//VnuzdRwLFx1MDAwNFxii4EqRfBH1O/eXpr1y2b/6XDwXFypbVx1MDAxZDz3/frVklMvwVx1MDAxMGu1VHbiyz2UXCJGgaBcdTAwMDUvqnBcIiTq3dFl1jRcdTAwMTBbjVx1MDAwMlqMv38kfZpZXGImlV5G2qVkvzan9JvTvjppzN0nP9pzXHUwMDAyPVx1MDAxM8/G3uJDueKAXj4z6V83u/Geujro9Ct630NVM9hcXH9actIxvcArri1IxGXkiaxcdTAwMTfSjXtyTKjX4qJcdTAwMDJhp8RYZfA2n39GLVx1MDAwMzzelFx1MDAwNFx1MDAxNa9cdTAwMGZZT4jvXG5cdTAwMTjuqcxcdTAwMWOmi+dcdTAwMWbfLZO/VCr/m1x1MDAxMz9t3N1nfMTnhD3jU1x1MDAwM7zmVijK6ezT0Kfdo5Pt2uGmWb3pVGqqs3OzVW0uOfZgXHUwMDE5QdXE8I76XHUwMDEyxXPYXHUwMDAzsYpzasfC7/xjvGYq96qUlHjA9MJcdTAwMTVcdTAwMGZqzfOLxS/Eo2xG9+FLXHUwMDE54lxyzcjI/1x1MDAwM//2mTDiSfPYWM+JdU6nv1x1MDAxZFxm0Lvx1ixmX1x1MDAwM4anu1x1MDAwNjs5fdi+2Vx1MDAwZjfaNbxr1e6Pl1x1MDAxY3YhgVBqXHUwMDE1pvDUveBgNIeX4F7kZ6zR1LhcdTAwMDXxQnN4Rdy7XHUwMDE1jJXJXHUwMDA024SKXGa8LYHUzOZcdTAwMWU6eH9nXG7HO1x1MDAxMobSJeSdW6Z/6VUqvznvU1x1MDAwN919Rod7TsRn3qk4VvNBQbmHd2ZcdTAwMDe+tdc806tHjcGdt7tWfajVr+nB3rJcdTAwMDOP8Vx1MDAxYtOX99espOExmbSjjFxijn1cYlx1MDAxMldFzqdcdTAwMWJcboRcdTAwMWLMoaybLeVcdTAwMTOLPlxiXHUwMDE1cuy9XHUwMDEzb1x1MDAxOTxcdTAwMDVMPFxmm8Ni1/z1vFK/tlx1MDAxYf274z5tzN1nNTvc02j/9HrsXHUwMDE1r9s9ifGyv1x1MDAwZlx1MDAxZlx1MDAwZX/QeF2sSH/BymPgXHUwMDBm1j92zU+v4+x49Vx1MDAxM3/4/un7v0/f/+oifQ==<!-- payload-end -->  <defs>    <style class="style-fonts">      @font-face {        font-family: "Virgil";        src: url("https://unpkg.com/@excalidraw/excalidraw@undefined/dist/excalidraw-assets/Virgil.woff2");      }      @font-face {        font-family: "Cascadia";        src: url("https://unpkg.com/@excalidraw/excalidraw@undefined/dist/excalidraw-assets/Cascadia.woff2");      }      @font-face {        font-family: "Assistant";        src: url("https://unpkg.com/@excalidraw/excalidraw@undefined/dist/excalidraw-assets/Assistant-Regular.woff2");      }    </style>      </defs>  <rect x="0" y="0" width="780.3905280090868" height="364.7090566117316" fill="transparent"/><g transform="translate(211.9130154509097 30) rotate(0 20.099990844726562 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">K&amp;R</text></g><g transform="translate(441.6381131071597 32.442657470703125) rotate(0 19.409988403320312 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">C90</text></g><g transform="translate(658.5195828337222 33.86859130859375) rotate(0 18.61998748779297 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">C99</text></g><g transform="translate(44.43218048997221 124.03253173828125) rotate(0 40.689964294433594 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">Intenger</text></g><g transform="translate(48.72936066575346 209.30615234375) rotate(0 36.10997009277344 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">Decimal</text></g><g transform="translate(205.6080838102847 100.13134765625) rotate(0 12.509986877441406 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">int</text></g><g transform="translate(199.83531769700346 138.053955078125) rotate(0 17.84998321533203 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">long</text></g><g transform="translate(260.5045681852847 100.63311767578125) rotate(0 25.859970092773438 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">short</text></g><g transform="translate(276.5643826384097 215.98056030273438) rotate(0 30.0899658203125 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">double</text></g><g transform="translate(200.1511746305972 217.22018432617188) rotate(0 25.3499755859375 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">float</text></g><g transform="translate(645.2217312712222 125.86569213867188) rotate(0 29.239974975585938 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">_Bool</text></g><g transform="translate(436.7703152555972 120.6102294921875) rotate(0 28.45996856689453 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">signed</text></g><g transform="translate(265.7842312712222 139.27398681640625) rotate(0 38.809959411621094 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">unsigned</text></g><g transform="translate(335.10228547044096 98.214599609375) rotate(0 20.92998504638672 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">char</text></g><g transform="translate(51.93132599778471 289.856689453125) rotate(0 27.619972229003906 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">Other</text></g><g transform="translate(443.98888215012846 294.20440673828125) rotate(0 18.649978637695312 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">void</text></g><g transform="translate(631.0171414274722 195.29580688476562) rotate(0 45.21995544433594 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">_Complex</text></g><g transform="translate(626.2942410368472 229.69760131835938) rotate(0 54.239959716796875 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">_Imaginary</text></g><g stroke-linecap="round"><g transform="translate(36.138265695050336 179.739013671875) rotate(0 356.06907653808594 0.5987396240234375)"><path d="M-0.76 1.16 C117.89 1.52, 592.4 1.6, 711.31 1.42" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/><g stroke-linecap="round"><g transform="translate(170.4286404509097 35.79083251953125) rotate(0 -1.17236328125 148.2166748046875)"><path d="M0.42 -0.24 C0.18 49.37, -0.89 248.13, -1.51 297.4" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/><g stroke-linecap="round"><g transform="translate(400.77916535325346 37.2078857421875) rotate(0 0.397857666015625 148.96517944335938)"><path d="M-0.47 1.19 C-0.21 50.73, 1.46 248.01, 1.58 297.5" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/><g stroke-linecap="round"><g transform="translate(574.3563137907535 38.9847412109375) rotate(0 1.3076171875 144.86251831054688)"><path d="M1.11 -1.05 C1.57 47.42, 3.25 242.03, 3.53 290.39" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/><g stroke-linecap="round"><g transform="translate(30.441732491925336 269.5205078125) rotate(0 357.6700897216797 0.9923095703125)"><path d="M-0.44 1.13 C119.01 1.79, 596.81 2.93, 716.16 3.07" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/><g stroke-linecap="round"><g transform="translate(41.134542550519086 81.35873413085938) rotate(0 354.13941955566406 -1.01708984375)"><path d="M0.27 -1.15 C118.63 -1.48, 591.32 -1.4, 709.26 -1.4" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/></svg>()

***

## Intenger

### int, long, short, unsigned

int 可以与 short 等关键字搭配，构造更具体的 int：

* `int`代表整数
* `short`代表短
* `long`或者`long long`代表长
* `unsigned`代表无符号

不同的 int 在不同电脑中占用字节数不同，这也就代表了不同电脑的某种 int 可以表示的范围不同。

<details>

<summary>查看自己电脑不同类型整数所占字节数</summary>

```c
#include <stdio.h>
int main()
{
    // 定义各种数据类型变量
    int a;
    unsigned int h;
    short int b;
    short c;
    unsigned short int i;
    long int d;
    long e;
    unsigned long int j;
    long long int f;
    long long g;
    unsigned long long int k;

    // 输出每个变量的位数
    printf("int a: %d bytes\n", sizeof(a));
    printf("unsigned int h: %d bytes\n", sizeof(h));
    printf("short int b: %d bytes\n", sizeof(b));
    printf("short c: %d bytes\n", sizeof(c));
    printf("unsigned short int i: %d bytes\n", sizeof(i));
    printf("long int d: %d bytes\n", sizeof(d));
    printf("long e: %d bytes\n", sizeof(e));
    printf("unsigned long int j: %d bytes\n", sizeof(j));
    printf("long long int f: %d bytes\n", sizeof(f));
    printf("long long g: %d bytes\n", sizeof(g));
    printf("unsigned long long int k: %d bytes\n", sizeof(k));
    return 0;
}

// int a: 4 bytes
// unsigned int h: 4 bytes
// short int b: 2 bytes
// short c: 2 bytes
// unsigned short int i: 2 bytes
// long int d: 8 bytes
// long e: 8 bytes
// unsigned long int j: 8 bytes
// long long int f: 8 bytes
// long long g: 8 bytes
// unsigned long long int k: 8 bytes

```

</details>

一个具体写在程序中的数字叫做字面量，它可以加入**前缀**来表示不同的进制：

* 十进制（Decimal）：不加前缀，默认就是十进制。
* 二进制（Binary）：0b，0B。
* 八进制（Octal）：0。（数字 0️⃣，不是字母 O）
* 十六进制（Hexadecimal）：0x，0X。

<details>

<summary>Demo</summary>

```c
#include <stdio.h>
int main()
{
    // 定义各种数据类型变量
    int binary_number = 0b1010011010;
    int octal_number = 01232;
    int decimal_number = 666;
    int hexadecimal_number = 0x29a;

    // 查看他们是否想等
    printf("%d", (int)(binary_number == octal_number));        // 1
    printf("%d", (int)(octal_number == decimal_number));       // 1
    printf("%d", (int)(decimal_number == hexadecimal_number)); // 1
    return 0;
}

```

</details>

也可以为字面量加入**后缀**，来代表它是不同的整数类型：

* `u`：无符号数。
* `L`：Long。
* `LL`，`UL`，`ULL`，自由组合

最后，在 printf 函数中，要用不同的占位符来表示这些类型，下面是总结表：

<table><thead><tr><th>type</th><th width="86">printf</th><th>hexadecimal</th><th>octal</th><th>decimal</th></tr></thead><tbody><tr><td>char</td><td>%c</td><td>\0x41</td><td>\0101</td><td>N.A.</td></tr><tr><td>int</td><td>%d</td><td>0x41</td><td>0101</td><td>65</td></tr><tr><td>unsigned int</td><td>%u</td><td>0x41u</td><td>0101u</td><td>65u</td></tr><tr><td>long</td><td>%ld</td><td>0x41L</td><td>0101L</td><td>65L</td></tr><tr><td>unsigned long</td><td>%lu</td><td>0x41UL</td><td>0101UL</td><td>65UL</td></tr><tr><td>long long</td><td>%lld</td><td>0x41LL</td><td>0101LL</td><td>65LL</td></tr><tr><td>unsigned long long</td><td>%llu</td><td>0x41ULL</td><td>0101ULL</td><td>65ULL</td></tr></tbody></table>

### char

char 代表字符，采用 ASCII 码，占用内存 8 bits。

* ✅：`char a = 'T';`
* ❌：`char b = "T";`

除了普通的数字与字母，特殊含义的字符是转义字符

| 转义序列 | 含义                                    |
| ---- | ------------------------------------- |
| \a   | 警报（ANSI C）                            |
| \b   | 退格                                    |
| \f   | 换页                                    |
|      | 换行                                    |
|      | 回车                                    |
|      | 水平制表符                                 |
| \v   | 垂直制表符                                 |
| \\\\ | 反斜杠（\）                                |
| '    | 单引号                                   |
| "    | 双引号                                   |
| ?    | 问号                                    |
| \0oo | 八进制值（oo必须是有效的八进制数，即每个o可表示0\~7中的一个数）   |
| \xhh | 十六进制值（hh必须是有效的十六进制数，即每个h可表示0\~f中的一个数） |

### \_Bool

* C99添加了布尔类型，占用 1bit。 我们可以直接就使用`_Bool`
* 也可以通过引入`stdbool.h`来使用`bool`

{% content-ref url="../library/stdbool.h.md" %}
[stdbool.h.md](../library/stdbool.h.md)
{% endcontent-ref %}

<details>

<summary>Demo</summary>

使用 \_Bool

```c
// boolean.c -- using a _Bool variable
#include <stdio.h>
int main(void)
{
    long num;
    long sum = 0L;
    _Bool input_is_good;
    
    printf("Please enter an integer to be summed ");
    printf("(q to quit): ");
    input_is_good = (scanf("%ld", &num) == 1);
    while (input_is_good)
    {
        sum = sum + num;
        printf("Please enter next integer (q to quit): ");
        input_is_good = (scanf("%ld", &num) == 1);
    }
    printf("Those integers sum to %ld.\n", sum);
    
    return 0;
}

```

通过引入stdbool.h来使用 bool

```c
// divisors.c -- nested ifs display divisors of a number
#include <stdio.h>
#include <stdbool.h>
int main(void)
{
    unsigned long num;          // number to be checked
    unsigned long div;          // potential divisors
    bool isPrime;               // prime flag
    
    printf("Please enter an integer for analysis; ");
    printf("Enter q to quit.\n");
    while (scanf("%lu", &num) == 1)
    {
        for (div = 2, isPrime = true; (div * div) <= num; div++)
        {
            if (num % div == 0)
            {
                if ((div * div) != num)
                    printf("%lu is divisible by %lu and %lu.\n",
                           num, div, num / div);
                else
                    printf("%lu is divisible by %lu.\n",
                           num, div);
                isPrime= false; // number is not prime
            }
        }
        if (isPrime)
            printf("%lu is prime.\n", num);
        printf("Please enter another integer for analysis; ");
        printf("Enter q to quit.\n");
    }
    printf("Bye.\n");
    
    return 0;
}

```

</details>

### stdint.h & inttypes.h

> stdint.h：用于各种 int 的声明
>
> inttypes.h：用于各种 int 的 printf

{% content-ref url="../library/stdint.h.md" %}
[stdint.h.md](../library/stdint.h.md)
{% endcontent-ref %}

{% content-ref url="../library/inttypes.h.md" %}
[inttypes.h.md](../library/inttypes.h.md)
{% endcontent-ref %}

***

## Decimal

### float, double, long double

占用字节数与表示范围

| 类型          | 范围                      | 大小       |
| ----------- | ----------------------- | -------- |
| float       | 大约 -3.4e38 到 3.4e38     | 通常 4 字节  |
| double      | 大约 -1.8e308 到 1.8e308   | 通常 8 字节  |
| long double | 大约 -1.2e4932 到 1.2e4932 | 通常 16 字节 |

浮点型常量

```c
 double a = .2; // 可以省略整数
 float b = 2. // 可以省略小数，但不能都省略
  
 float c = 6.6e3-34; // 科学计数法： 基数+e+指数,不能有空格
 double d = .8E-5; // 也可以用 E
```

不同格式的 printf

| 类型       | 占位符 |
| -------- | --- |
| 普通       | %f  |
| 科学计数法（e） | %e  |
| 科学计数法（E） | %E  |
| 自动选择     | %g  |

<details>

<summary>Demo1</summary>

```c
#include <stdio.h>

int main()
{
    double num = 12345.6789;

    // 使用 %f 打印浮点数
    printf("Decimal notation: %f\n", num);
    // Decimal notation: 12345.678900

    // 使用 %e 打印科学记数法
    printf("Scientific notation (lowercase e): %e\n", num);
    // Scientific notation (lowercase e): 1.234568e+04

    // 使用 %E 打印科学记数法
    printf("Scientific notation (uppercase E): %E\n", num);
    // Scientific notation (uppercase E): 1.234568E+04

    // 使用 %g 自动选择格式
    printf("General format: %g\n", num);
    // General format: 12345.7

    return 0;
}

```

</details>

<details>

<summary>Demo2</summary>

```c
/* showf_pt.c -- displays float value in two ways */
#include <stdio.h>
int main(void)
{
    float aboat = 32000.0;
    double abet = 2.14e9;
    long double dip = 5.32e-5;

    printf("%f can be written %e\n", aboat, aboat);
    // 32000.000000 can be written 3.200000e+04

    // next line requires C99 or later compliance
    printf("And it's %a in hexadecimal, powers of 2 notation\n", aboat);
    // And it's 0x1.f4p+14 in hexadecimal, powers of 2 notation
    printf("%f can be written %e\n", abet, abet);
    // 2140000000.000000 can be written 2.140000e+09
    printf("%Lf can be written %Le\n", dip, dip);
    // 0.000053 can be written 5.320000e-05

    return 0;
}

```

</details>

浮点数会产生舍入误差（因为 10 进制转换 成 2 进制有的数会转换成无限的小数）

<details>

<summary>Demo</summary>

```c
/* floaterr.c--demonstrates round-off error */
#include <stdio.h>
int main(void)
{
    float a, b;

    b = 2.0e20 + 1.0;
    a = b - 2.0e20;
    printf("%f \n", a); // 4008175468544.000000

    return 0;
}
```

</details>

### Complex, Imaginary

* C99
  * 复数：float \_Complex, double \_Complex, long double \_Complex
  * 虚数：float \_Imaginary, double \_Imaginary, long double \_Imaginary
* `complex.h`
  * 复数：float complex, double complex, long double complex
  * 虚数：I, float imaginary, double imaginary, long double imaginary

{% content-ref url="../library/complex.h.md" %}
[complex.h.md](../library/complex.h.md)
{% endcontent-ref %}

<details>

<summary>Demo</summary>

```c
#include <stdio.h>
#include <complex.h> // 包含对 _Complex 类型支持的函数和宏

int main()
{
    // 声明两个 _Complex 类型的变量
    double complex z1 = 3.0 + 2.0 * I; // 使用 I 宏表示虚数单位
    double complex z2 = 1.0 - 2.0 * I;

    // 打印原始复数
    printf("z1 = %f + %fi\n", creal(z1), cimag(z1));
    printf("z2 = %f + %fi\n", creal(z2), cimag(z2));

    // 复数加法
    _Complex double sum = z1 + z2;
    printf("Sum: %f + %fi\n", creal(sum), cimag(sum));

    // 复数减法
    _Complex double diff = z1 - z2;
    printf("Difference: %f + %fi\n", creal(diff), cimag(diff));

    // 复数乘法
    _Complex double product = z1 * z2;
    printf("Product: %f + %fi\n", creal(product), cimag(product));

    // 复数除法
    _Complex double quotient = z1 / z2;
    printf("Quotient: %f + %fi\n", creal(quotient), cimag(quotient));

    // 复数的模（绝对值）
    double magnitude = cabs(z1);
    printf("Magnitude of z1: %f\n", magnitude);

    return 0;
}
```

</details>