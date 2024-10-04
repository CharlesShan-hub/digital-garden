---
{"dg-publish":true,"dg-permalink":"programming/c/library/stdio.h.md","permalink":"/programming/c/library/stdio.h.md/"}
---


# stdio.h

## Overview

<svg version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 719.6549682617188 388.1062469482422" width="1439.3099365234375" height="776.2124938964844">  <!-- svg-source:excalidraw -->  <!-- payload-type:application/vnd.excalidraw+json --><!-- payload-version:2 --><!-- payload-start -->eyJ2ZXJzaW9uIjoiMSIsImVuY29kaW5nIjoiYnN0cmluZyIsImNvbXByZXNzZWQiOnRydWUsImVuY29kZWQiOiJ4nO2d61PiTNbAv89fMeV+fcx2n77vNy8w4lxyRXHUt7asXHUwMDAwXHUwMDAxo0CQRFG3nv/9PVx1MDAxZC9ANDNxloTMOlrlXGZJoJvO+fW5duc/X75+XYlcdTAwMWVG3sq/vq54922373fG7mTlL3v8zlx1MDAxYod+MMRTXHUwMDEwv1x1MDAwZYPbcTu+8jKKRuG//vlPdzRyen7UXG6Ca6dcdTAwMWRcZp7e5vW9gTeMQrzw//D116//if/ONFx1MDAxNHn3UXxtfHSmXHUwMDE5opJH94Nh3CRTXHUwMDAw1Fx1MDAxOEpfL/DDTWwp8jp4tuv2Q296xlx1MDAxZVpRj15cdTAwMWSCtlT+/t3+Klx1MDAxZKpwtXI+bbXr9/tH0UM/7lBcdTAwMTjg956eXHUwMDBio3Fw7X33O9Hly5efOZ72rnFw27tcdTAwMWN6of3i025cdTAwMDYjt+1HXHUwMDBm9lx1MDAxOCGvR91hL/6M6ZF7fMWBOEwzoVx1MDAwNGeGXHUwMDBiNv1cdTAwMTT7flx1MDAxMOBcdTAwMDAjXFxqJVx1MDAxMl3aXGL6wdh26Vx1MDAxZtSzv9NOtdz2dVx1MDAwZns27LxeXHUwMDEzjd1hOHLHeI+m102ev6xWjlx1MDAxZGfgXHUwMDA2pFx1MDAxMkpPu3Dp+b3LKO7HtHUvXHUwMDFlfqZcdPZLXHUwMDEz83rCNjmqdWJcdTAwMTn493TMx+7Aq9l3XGZv+/3ZgVx1MDAxYnaeXHUwMDA3bu5Ey56ozIjT9KNuR1x1MDAxZPfp3lNcdTAwMDVcXIMhilxuOu1Z31x1MDAxZl4nP65cdTAwMWa0r99cdTAwMTGXbjCMjvxHL1x1MDAxNsC5o1V34PdcdTAwMWbmbmcsujiIJ+7Yd1t9L1xcmTu11vd7VpJX+l53XsQjXHUwMDFm4Xo9XHUwMDFkXHUwMDA1o+nZNjbl+kNv/HZogrHf84du/zi9Wfym3tbLvaHOzN1puaFnz9rjOj74919cdTAwMWZcdTAwMDNSk+TBXHUwMDE3XHUwMDFlqVCGXHUwMDAyV5RlXHUwMDA2st97PGSj6vaxd3d/wcngaHMrqpVcdTAwMWJIyYhDqZBcdTAwMDYo01LRqYDHQHLmcK6Z5GBJgfyoVOBIhlQyYoRcIoxOR+BcdTAwMDdUKq1cdTAwMTQn5DNR+Y+O17VcdTAwMDJfKJNvXHUwMDFhzZNIXG6pSKL2XHUwMDA0xVx1MDAwMFh2JMPW/n3Izvqr91x1MDAwMz7qflx1MDAxYlXF1XC/3EhcdTAwMDJcdTAwMTVcdTAwMGWgclx1MDAwNEG55JoznWDSOKg5tVbmSYUme7ZAVWlcdTAwMWOq0CSRTFNU2oZngZIjXHUwMDEyRDE2PVE8lJQwLouDsno7bEcop1x1MDAwNavKd5pdXHUwMDA0mGOvXHUwMDFkPUnme1x1MDAwNuyMfZqgUypGNFdqauH+XGZO7rl+Nzg5NmsnvTbet72DRqdebjiZkWjAXHUwMDEyzoCCNkTOjHBcZieTjlBMXHUwMDAzXHUwMDEwoPPsLlx1MDAxYU5qNTdcYqOkmO3FK5lcZpgjjWaMoY5cdTAwMDTGp/A+g0qZ4JRovVx1MDAwMO35XCJDUyliz0f+/kWlyjXls1L9XHUwMDEzfn9N01CZavxRnF45MTOz2M+E+YJVtvd6XHUwMDFi9SDc6bP7XHUwMDFiry731EG5hZmDdjiVhlx1MDAxMMm4laM5WcYp1CF4M7hEplx1MDAxOWc5+mRSONxaf5JyxSXJpmhQsvFcdTAwMGJQskxFU7D1XHUwMDE34lx1MDAxYi6iYrVMss1cXG0/lWr7XHUwMDE5rVx1MDAwNUFfZDpb/VxmyEvw7sXe4Jz5a53T7bWd4+bpt2rZgTRcdTAwMGVR0igwiFx1MDAwMoh5y49p5eB0LfTThJ4nkFx1MDAxY1tCIJEudIJcdJ2ZXHUwMDE5flx1MDAwMKRRXHUwMDE0XHUwMDE1XHUwMDFlXHUwMDExn1xiyGptt1Kw0TfXYp4wQrojhppcdTAwMTOlgkmS3da79c+3T7/deGehezgx/oNuNk7aZadROZRcdTAwMDJV3GilXGaY6bd9iE9Lx9p4Ulx1MDAxMzpcdTAwMWZIXFy4ejRcdTAwMGWz6pGQZNT0R35cdTAwMThan6BmTcP/eVx1MDAxYbujICxaPSbbzN9cdTAwMDObseRcdTAwMTNYcvS8JZU8e1xuYbN51YAz/4ZcdTAwMWPIVVVbPdo9OPWPyk2lYNphXHUwMDEy3S8qNMxFXG6fXHUwMDFjMO7kbKyCQMdcbptgmqmEXHUwMDBi+Fx1MDAwMeeLXHUwMDE4KZWcXHUwMDBlQYl8r1x1MDAwZjL766LMgaWJstSSXHSiRHZzr8rqtU69v3t3XHUwMDFkPfaCo6Bhblx1MDAxZZvlXHUwMDE2ZcrAYZxygz6YXHUwMDAxOpv1epJlg1xuXHUwMDA2QKOca0JUfrGEhYg0J1xmXGLSuVx1MDAwMIWzaJlcdTAwMDYh6Mys+F/KdH8uXHUwMDE2Plx1MDAxYk8waeJMXHUwMDE1XHUwMDBlrJ7NVPxMnFu9cVOs93tcdTAwMDd7l9/XL6reerSzdbtQce644aW32KmZc1x1MDAwN1xi1Vx1MDAxNFx1MDAxNEexJvPxXHUwMDA0MHhcdTAwMTaFXHUwMDFjPYSc7SVUkVx1MDAwZcPJVdg51sxlk1/FmeBcdTAwMTWEMWJcdTAwMDNcYomE87M3g56WsZKehzhDsVP0zEi742jdXHUwMDFmdvxhL/lcdTAwMTZv2Ek503fDaCNcdTAwMThcZvxcYrtxXHUwMDEw+MMoeUX8uWvjcTC59Nw3Y4GfnHpuZD9uWklhf6b/+zpcdTAwMTWw+MXr///917tXp9/4+O3JWz79uC+z/36UeyCpcUSNroNgTGS3yGpez1x1MDAxZDS6QbP5KEhrvHdy1253Ss89c4RcdTAwMTZcXFP8Q4WY95NcdTAwMTgqXHUwMDE3Slx1MDAxNbHxcpxcdTAwMDE1yETPSlx1MDAwNr5cdTAwMTBMUWbysc3+gP9cdTAwMWKCn1x1MDAxYa5kkDz6XHUwMDFhruRacSM/oPBxnI93Nnqi4tdIdZ9872yR0WKLR3JcdTAwMDBf2FxiXHRDw4ZwtFL1fDlcdTAwMTejtrZE4pBLXHUwMDFj+9n08cJcdTAwMDMk3NFcbk1oLbSer2L5UbhSXHUwMDEya4uIXHUwMDA1KPjfJUCyftvteuNiXHUwMDAzJMk281xmWc7k/N+Ujlx1MDAxMCY0cJZcdTAwMWRIXHSrstbYPj3fXHUwMDBljq52705ujFx1MDAwN+VcdTAwMDdSO+g2g8FcdFx1MDAwZnVuopxcdTAwMGJcdTAwMGY6VHKDYlx1MDAwZjlcdTAwMDdJ0LMlwlx1MDAxOKlcYo/zXHUwMDA373mUb5FE+4Ggd0D5J2Ky6vdcdTAwMGIu55pvcUn5PLRcdTAwMTRcdTAwMTn/UKySblfag5v1wWZ7KPotOI72Jnq15DxKXHUwMDA1SFx1MDAxY4CkRsb1XCLzPFx1MDAxMuNcdTAwMTD8g/JOpJz1l1x1MDAxN42joKiJjVHojWhmNM+UYFx1MDAwN41dXHUwMDEy1CxcdTAwMWRGOSusucK439zdLVx1MDAxNsb5XHUwMDE2c4XRpCZcdTAwMGWoQP0ogc7E7n5GY8W9XHUwMDFl6XZzu8ru9HC3ofzhTUeUnUZcdI5A2iSlmspkfIrbukt02DlIkGY2y7bw0i2iXHUwMDFknFx1MDAxMVxmN4yTOImRXHUwMDA1R9Tq+Fx1MDAxNvaJaDyqVHYuNpqNYol822quVMp0KjVXxqqH7Dbrduf04nCtUTmPTlx1MDAxZo5cdTAwMWHXnebJ5qj7XHUwMDFiUEmUZGhcdTAwMTFcdTAwMThNuJy3WTmnjpaGXHSOXHUwMDEyOHd28VSamMpcdTAwMTcms5msQInkmjHy2bg8qlx1MDAxYy+By7lWXHUwMDE3wWVaUJfTdC45XHUwMDE3lHCisi9D2IPo6m5393hUv7sle/Kw0ur6o5JzaaO6Slx1MDAwMeVcdTAwMDI0ZVwiWf2Clq2OXHUwMDBi7Ymw2pIlOlayoC4qfULtyoBcXKqdXHUwMDE3XHUwMDEw1f0lev9EdXOI6uI9SdfIQtpi6Vx1MDAwZqxcdPx21drx/HG/NYmY2d5xa3xLXHUwMDFklpx8KanDNOpa/CWcm/lcdTAwMTJcdTAwMWImiSNQXHUwMDFmI0tojeZcdTAwMTnWZcZBXHUwMDBiKDZcbt6l/lx1MDAxZG1sS/GY4nRcdTAwMDFFXGK/izau1KvFKuK5XHUwMDA287SNeWp5XHUwMDEwR/1cdTAwMGLsI4vlt0bh4dGje+zX9FxybO7fbVUnarv0XHUwMDFjoo4lYJehXHUwMDEwMZdAeSlcdTAwMDeXQjAjXHUwMDA0yXdxLlx1MDAwNXC4satzXHUwMDE1kXayzZZfUahwQXwmw7haP6jsX+ytnVx1MDAxNlx1MDAxY9B92+xysixoXHUwMDBlXG4rjjo7l1x1MDAxN/eDyff94KF+eLk2gtONSS1an5ScS5v21MC0Zmj7vo0jaemARJuFoNuaq36U2kEqXHLTJl4nnE1FSsW0tKu+Plx1MDAwZpZH0dhzXHUwMDA3XHUwMDA1e6uJNvNcdTAwMDRSpac9NeNaSchur571qoOzb2H/8Pyuvfl91Fx1MDAxY4mu2Sk5j1x1MDAxMi1SLpRcdTAwMTZcdTAwMDJgfvngXHUwMDEzj8yxVVgvVbT5xXW5wvtqbOlHclx1MDAxM5tcdTAwMWblPONcdTAwMDSpIZ/JZFxyI/RLi+Ux0WSue8qkLytGbUDt0r3s+vHwW+NgPI521d3R1fqw406aXHUwMDE3j4tdoZGP/4hzXHUwMDBloPP4TkRXXHUwMDAwc1x1MDAxNNeGUa3nV1x1MDAxZC9cXD9cIo+2LFxiRVx1MDAxY1x1MDAxZNaMq1x1MDAxOFx1MDAwMTRcdTAwMTdcdTAwMTSm0a7PQGNwW/Sq4kSbuarHVDeSXHUwMDAyyqdcdTAwMDQps+c9m9iZ7sgje+rse+W65z3Wm75bclx1MDAxZVx1MDAxNVC7kERK87SUP6FcdTAwMWaNcIik3NjoqFx1MDAwMZpfhsVOXHUwMDBiyCOLc69cdTAwMTkrglx1MDAwMKdcdTAwMGJj5FwiyvB/I1x1MDAxZb1xwVV6yTZzTXmSdFx1MDAwN1x1MDAxMijReMdldlx1MDAwNdlcIjdcdTAwMGbbJFCtYXiwWz2rbJ7vXHUwMDBmXHUwMDA2JVx1MDAwN5JcbnBcdTAwMTSzXHUwMDAxLCZcdTAwMTRcdTAwMDdUhHNEMluJIHnSqStJjVx1MDAxZeFcdTAwMDQ9Xy6XSWTRXHUwMDFiPP1cdTAwMGbU6KWuXmGpNXqcojqQs7j+XGbGxs54tdG+XHUwMDBlSbjvXHUwMDFksyti1rdaZfdcdTAwMWUp445GZ40jbsBZwlpcdTAwMDVjXHUwMDFjrbjdXHUwMDAzgCsmWX7acSF5TnRvpcL5pISLV36d2T9pzlx1MDAxY9KcPNVLXHUwMDA1YqhcIkR/oDa3tbd3oI89esuuqt6qt0lcdTAwMDfRVqXk3NuNXHUwMDE0qd1cdTAwMDL47V5tL0pcdTAwMTgnP05cdTAwMTB+okiO5YCCOFx1MDAwNm3ceMVsNlx1MDAxZKyktFth0qWqYPRcdTAwMTRmVEfue3tcdTAwMDQjr+CQUaLJXFwznanbglODXHUwMDEzXHUwMDAzWsXkXHUwMDAzMN43m53BNefi5PIybN2tnzTbi91cdTAwMTd88TBa2oStvNP0va3oqHRcdTAwMThcdTAwMGWBXCLa5GtcdTAwMTPbzI5NqYCWXHUwMDE0/2QsXHUwMDAylNhB7NxStzxcdTAwMDXCZYE4tvtBWLBNnGwz11x1MDAxY2d69Z/SqFx1MDAxOTlajJmBPNvkXHUwMDE3q2jRX17vhZ1g7Wy14j3sllx1MDAxY0gqLJBGoHKULDYp54jkVDtcdTAwMDBGcq5cdTAwMTReluPSXHUwMDE1XHUwMDEwXHUwMDBl+iEmNiAzO6laUYrdXmrUiDFQpjhcImv1YmmcbS/f/cBTw7doK3OQXFxlV43B6KAq1OZp1fjuhS9b472zsOzRW1x1MDAwMOkghmjycUIsavPlePaRXHUwMDFhIFx1MDAxNOFGJGpzXHUwMDE2rlx1MDAxYplDrW5cdTAwMTSGJtZz/zC9aVx1MDAxN5yBgmXWXHUwMDFisLiAqjBcdTAwMTRHY/RcdTAwMGW7xeKYbDPfXHUwMDAwbvpGR1xcXHUwMDFi61RB9jUrj8duo6VP2mdcdTAwMWS9dlxcq0eTcfew7GtWwG6GxY3dPtvuN5DcuYtLPG0r543dXHUwMDAyXCLXnZPBecraZKw20Ephf9VcIjbp+mVcdTAwMWGBS8k/srv3f2mqLlx1MDAwM8c3jea7zDrVWlx1MDAxNUJqXHUwMDA1SmVcdTAwMGbhnm7Vgl5EuMvZyeOoWVx1MDAwMc4nZd94jFx1MDAxMeloolx0ZTj5zG1X/KQhmYO+oyT6+Tk2eWpIu0hT4IjHRnHGjIq9nijs4lJVJFx1MDAxYVJcdTAwMDXuZN52h1x1MDAwNSOZaDJXIGnqxkCK26WMXHUwMDFmKJCdfDttXVQ2zMbJpiSNifdwXHUwMDA0O2HpeeSoloRcdTAwMTFcXCRcdTAwMDM2T+qRO4C2uy1tN3P1ejmEc+iHl3Ril1xiZ5ovXHUwMDEzx6J15GTsR0WHc1x1MDAxMm3mmeRkJtWJXHUwMDA0olx1MDAxNFxigr56ZiQ3mmfe5cnB+oa8P29tXYGoNS43So6kzXKi7WetXHUwMDAxQaTQOrGoy6BzR5iQQFx1MDAwMJ0lmef+yVx1MDAwYlnPXHUwMDE5T6LaiFx1MDAxMiY6sd/i17zNP4nOXHUwMDFjtudk6fW4RlP7eJuP7DJdWz+v1zau2sAm34O6hnbntlF69Fx1MDAwNTqrXFxcdTAwMWHQmiql9PxKbkGYw9D8M4qiP6tEjlx1MDAwNbmL2ZhcdTAwMTfpwi9TRvKBk9mw2Fx1MDAxZvJffpZT4sBSw1RcdTAwMWPVXHUwMDFj+oIye1x1MDAwZecuONurV1x1MDAxZetbO+dcdTAwMTecVDY2tOfrsoPPXHK6xcxoIZJPVX0qxFdcdTAwMGXgiKs35fFcdTAwMGKPUkmH2PWjRj8/3jWLXHUwMDE5blx1MDAwYlxmsHN0qVVcdTAwMGVxXHUwMDFmplx1MDAxZMjbXHUwMDBlr0eXKKjF2uHJNnN9plB6WlUq6zCyXHUwMDBmIFx1MDAxOTCfd2+bk7Nu3Vx1MDAxYtROhtBX4JVcdTAwMWNJkMKx9Vx1MDAxY4zQxCZjT0Rcbsfu0SdcdTAwMTiP58lcdTAwMWNzOTjnXG6Dsq1cdTAwMTkzmdeOgkA/QS93STegXHQzU1x1MDAxZZ777lxuqFx1MDAxZlx1MDAwYq7FTzSZJ4/pXHUwMDFiWFO7XHUwMDEzK/5Adlx1MDAxZdVJ7bJxc+9+617db/TD5mPEZavsPHLlcEElXHUwMDE4XHUwMDE5P/88WYmPXHUwMDFhVGnkVYFcdTAwMTbz1Vx1MDAwN1x1MDAwYidcdTAwMTJ+IbuqJSpTTvRSQ1WSXHUwMDFiU5yK7OJXvy44UjXfZK5Aplx1MDAxNuMzpm1x91x1MDAwN4pyXHUwMDBm94JDtbnx7VDdhtvhfaXfXHUwMDFh7N6VnEdGtWOfe05VcjHa06MkcLip3cHzmcf8aJSoiO1cdTAwMTNp4yfVZM3jXHUwMDEwaZ/IvNRccnOZ9WpcbnzkXrd/XHUwMDFiXlx1MDAxNoxjos1cdTAwMGbx+OXZR11xR6OjXGLHbuUlXGaAN8vvPFx1MDAwZsC0/ZU735us/1h6vjxzbpHy4rjC31/+/n/WPVx1MDAxMFx1MDAwNyJ9<!-- payload-end -->  <defs>    <style class="style-fonts">      @font-face {        font-family: "Virgil";        src: url("https://unpkg.com/@excalidraw/excalidraw@undefined/dist/excalidraw-assets/Virgil.woff2");      }      @font-face {        font-family: "Cascadia";        src: url("https://unpkg.com/@excalidraw/excalidraw@undefined/dist/excalidraw-assets/Cascadia.woff2");      }      @font-face {        font-family: "Assistant";        src: url("https://unpkg.com/@excalidraw/excalidraw@undefined/dist/excalidraw-assets/Assistant-Regular.woff2");      }    </style>      </defs>  <rect x="0" y="0" width="719.6549682617188" height="388.1062469482422" fill="transparent"/><g transform="translate(318.0420837402344 47.49609375) rotate(0 43.609962463378906 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">Variables</text></g><g transform="translate(527.7742004394531 38.7139892578125) rotate(0 36.31996154785156 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">#define</text></g><g transform="translate(112.95303344726562 44.719512939453125) rotate(0 44.58995819091797 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">Functions</text></g><g stroke-linecap="round" transform="translate(294.0389404296875 31.839447021484375) rotate(0 65.06298828125 161.8491668701172)"><path d="M32 0 C56.8 1.68, 76.94 -1.42, 98.13 0 M32 0 C46.53 0.21, 62.43 1.17, 98.13 0 M98.13 0 C118.31 1.73, 129.15 11.83, 130.13 32 M98.13 0 C119.07 -1.3, 129.92 12.2, 130.13 32 M130.13 32 C129.38 98.7, 128.33 165.2, 130.13 291.7 M130.13 32 C130.11 112.62, 129.97 192.42, 130.13 291.7 M130.13 291.7 C128.74 312.02, 118.15 322.51, 98.13 323.7 M130.13 291.7 C128.22 314.1, 118.22 322.77, 98.13 323.7 M98.13 323.7 C71.39 322.49, 47.67 324.76, 32 323.7 M98.13 323.7 C83.62 323.37, 70.13 324.2, 32 323.7 M32 323.7 C10.85 325.09, 1.56 313.82, 0 291.7 M32 323.7 C10.64 322.98, 0.14 311.1, 0 291.7 M0 291.7 C-1.23 218.38, 0.72 145.85, 0 32 M0 291.7 C-0.39 239.8, -0.52 188, 0 32 M0 32 C-0.87 12.51, 12.08 0.2, 32 0 M0 32 C-2.03 11.62, 11.43 -2.12, 32 0" stroke="#1e1e1e" stroke-width="2" fill="none"/></g><g transform="translate(326.0754089355469 141.34857177734375) rotate(0 32.71996307373047 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">size_t</text></g><g transform="translate(326.73548126220703 183.15521240234375) rotate(0 23.91999053955078 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">FILE</text></g><g transform="translate(324.7706832885742 221.41409301757812) rotate(0 34.669960021972656 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">fpos_t</text></g><g stroke-linecap="round" transform="translate(436.0206298828125 30) rotate(0 126.81716918945312 161.8491668701172)"><path d="M32 0 C88.62 0.32, 146.79 -0.04, 221.63 0 M32 0 C103.66 -1.07, 173.37 -1.48, 221.63 0 M221.63 0 C242.57 -0.59, 251.65 9.56, 253.63 32 M221.63 0 C242.98 0.09, 253.43 10.12, 253.63 32 M253.63 32 C252.99 87.95, 254.09 140.34, 253.63 291.7 M253.63 32 C253.91 88.76, 253.68 144.96, 253.63 291.7 M253.63 291.7 C254.23 313.94, 243.17 324.41, 221.63 323.7 M253.63 291.7 C251.5 314.96, 240.96 325.35, 221.63 323.7 M221.63 323.7 C163.63 324.95, 107.79 325.55, 32 323.7 M221.63 323.7 C148.19 323.81, 76.73 324.17, 32 323.7 M32 323.7 C11.34 322.49, -0.83 311.86, 0 291.7 M32 323.7 C10.15 324.77, -1.96 315.02, 0 291.7 M0 291.7 C-1.92 229.74, -1.33 167.76, 0 32 M0 291.7 C2.04 203.92, 2.2 116.59, 0 32 M0 32 C-1.22 9.62, 11.55 -0.46, 32 0 M0 32 C1.02 10.48, 11.79 -0.66, 32 0" stroke="#1e1e1e" stroke-width="2" fill="none"/></g><g stroke-linecap="round" transform="translate(30 34.40791320800781) rotate(0 126.81716918945312 161.8491668701172)"><path d="M32 0 C76.94 0.02, 125.28 -1.76, 221.63 0 M32 0 C87.54 -0.2, 143.92 -0.69, 221.63 0 M221.63 0 C242.67 -0.02, 253.15 10.72, 253.63 32 M221.63 0 C241.94 0.55, 254.47 10.79, 253.63 32 M253.63 32 C250.56 124.1, 252.7 216.45, 253.63 291.7 M253.63 32 C254.87 107.51, 253.88 184.43, 253.63 291.7 M253.63 291.7 C252.74 313.92, 243.14 324.9, 221.63 323.7 M253.63 291.7 C251.77 314.01, 241.65 323.03, 221.63 323.7 M221.63 323.7 C159.86 324.12, 100.7 323.4, 32 323.7 M221.63 323.7 C176.75 325.94, 130.82 326.34, 32 323.7 M32 323.7 C11.73 322.53, -0.29 311.76, 0 291.7 M32 323.7 C8.42 324.76, 1.38 315.01, 0 291.7 M0 291.7 C-0.79 199.92, 1.59 109.01, 0 32 M0 291.7 C-1.23 188.56, -1.96 85.3, 0 32 M0 32 C-0.7 10.94, 12.33 1.66, 32 0 M0 32 C1.36 12.56, 8.39 -0.99, 32 0" stroke="#1e1e1e" stroke-width="2" fill="none"/></g><g stroke-linecap="round"><g transform="translate(441.8603210449219 89.48440551757812) rotate(0 122.18807983398438 0.1851654052734375)"><path d="M-0.14 0 C40.86 -0.2, 204.26 -0.41, 244.84 -0.15" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/><g stroke-linecap="round"><g transform="translate(441.2439901549369 148.38265390009826) rotate(0 122.18807983398438 0.1851654052734375)"><path d="M-0.34 -0.45 C40.54 -0.6, 203.97 0.2, 244.91 0.18" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/><g transform="translate(454.7723083496094 105.38217163085938) rotate(0 32.439964294433594 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">Buffer</text></g><g transform="translate(456.1658020019531 165.43060302734375) rotate(0 16.029983520507812 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">File</text></g><g transform="translate(569.8207702636719 104.29653930664062) rotate(0 25.55998992919922 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">NULL</text></g><g transform="translate(560.2499694824219 210.55056762695312) rotate(0 54.309974670410156 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">SEEK_CUR</text></g><g transform="translate(559.7348937988281 237.13497924804688) rotate(0 54.809967041015625 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">SEEK_SET</text></g><g stroke-linecap="round"><g transform="translate(441.43065358214096 268.1566590569533) rotate(0 122.18807983398438 0.1851654052734375)"><path d="M0.61 -0.34 C41.19 -0.08, 203.67 0.2, 244.42 0.49" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/><g transform="translate(559.0432052612305 155.80111694335938) rotate(0 19.739990234375 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">EOF</text></g><g transform="translate(560.4606018066406 182.9210205078125) rotate(0 61.249961853027344 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">FOPEN_MAX</text></g><g transform="translate(455.4823913574219 281.5315856933594) rotate(0 34.499969482421875 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">Stream</text></g><g transform="translate(558.1163635253906 279.2510070800781) rotate(0 23.629974365234375 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">stdin</text></g><g transform="translate(559.2817687988281 319.0145568847656) rotate(0 33.63996124267578 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">stdout</text></g><g transform="translate(618.8011779785156 290.3271179199219) rotate(0 30.8399658203125 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">stderr</text></g><g transform="translate(50.390899658203125 110.5302734375) rotate(0 16.029983520507812 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">File</text></g><g stroke-linecap="round"><g transform="translate(32.54605314321816 95.14037484736389) rotate(0 122.18807983398438 0.1851654052734375)"><path d="M0.53 -0.19 C41.43 -0.04, 204.58 -0.4, 245.07 -0.17" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/><g transform="translate(146.82608032226562 110.42703247070312) rotate(0 25.469970703125 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">fopen</text></g><g transform="translate(213.19259643554688 111.5657958984375) rotate(0 28.949966430664062 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">fclose</text></g><g transform="translate(53.198028564453125 213.49526977539062) rotate(0 12.709991455078125 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">IO</text></g><g transform="translate(124.17916870117188 215.52267456054688) rotate(0 26.59996795654297 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">printf</text></g><g transform="translate(121.3076171875 258.8870849609375) rotate(0 31.4599609375 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">fprintf</text></g><g transform="translate(204.46652221679688 218.28323364257812) rotate(0 26.649978637695312 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">scanf</text></g><g transform="translate(202.574462890625 259.5340270996094) rotate(0 28.559967041015625 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">fwrite</text></g><g stroke-linecap="round"><g transform="translate(32.435195551440074 188.36918702350675) rotate(0 122.18807983398438 0.1851654052734375)"><path d="M-0.1 0.68 C40.5 0.96, 202.7 1.08, 243.31 0.96" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/><g stroke-linecap="round"><g transform="translate(33.30320118255912 298.59932211087556) rotate(0 122.18807983398438 0.1851654052734375)"><path d="M0.18 0.77 C40.65 0.77, 202.93 0.18, 243.6 0.24" stroke="#1e1e1e" stroke-width="2.5" fill="none" stroke-dasharray="8 10"/></g></g><mask/><g transform="translate(47.462493896484375 322.4710998535156) rotate(0 33.049964904785156 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">Others</text></g><g transform="translate(162.81063842773438 321.0641784667969) rotate(0 25.179977416992188 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">Error</text></g><g transform="translate(145.11013793945312 145.05084228515625) rotate(0 26.09996795654297 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">fseek</text></g><g transform="translate(216.17312622070312 146.48477172851562) rotate(0 28.39996337890625 12.5)"><text x="0" y="0" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="text-before-edge">fflush</text></g></svg>stdio.h大致内容[1]

## Functions

### printf

<details>

<summary>Demo</summary>

<pre class="language-c"><code class="lang-c">/* printout.c -- uses conversion specifiers */
#include &#x3C;stdio.h>
#define PI 3.141593
int main(void)
{
    int number = 7;
    float pies = 12.75;
    int cost = 7800;

<strong>    printf("The %d contestants ate %f berry pies.\n", number,
</strong><strong>           pies);
</strong><strong>    printf("The value of pi is %f.\n", PI);
</strong><strong>    printf("Farewell! thou art too dear for my possessing,\n");
</strong><strong>    printf("%c%d\n", '$', 2 * cost);
</strong>
    return 0;
}

// The 7 contestants ate 12.750000 berry pies.
// The value of pi is 3.141593.
// Farewell! thou art too dear for my possessing,
// $15600
</code></pre>

</details>

<details>

<summary>一图胜千言</summary>

![../../../gitbook/assets/image (31).png](/img/user/gitbook/assets/image%20(31).png)printf format specifications quick reference[2]

</details>

<details>

<summary>转换说明[3]</summary>

* %a 浮点数、十六进制数和p记数法（C99/C11）
* %A 浮点数、十六进制数和p记数法（C99/C11）
* %c 单个字符
* %d 有符号十进制整数
* %e 浮点数，e记数法
* %E 浮点数，e记数法
* %f 浮点数，十进制记数法
* %\_g 根据值的不同，自动选择\_f或\*e。\*e格式用于指数小于-4或者大于或等于精度时
* %\_G 根据值的不同，自动选择\_f或\*E。\*E格式用于指数小于-4或者大于或等于精度时
* %\_i 有符号十进制整数（与d\_相同）
* %o 无符号八进制整数
* %p 指针
* %s 字符串
* %u 无符号十进制整数
* %x 无符号十六进制整数，使用十六进制数0f
* %X 无符号十六进制整数，使用十六进制数0F
* %% 打印一个百分号

</details>

<details>

<summary>转换说明修饰符</summary>

* 标记：五种标记（-, +, 空格, #, and 0）
  * **-**：等待打印项左对齐。即，从字段的左侧开始打印该项。示例：“%-20s”
  * \+：有符号值若为正，则在值前面显示加号；若为负，则在值前面显示减号。示例：“%+6.2f”
  * 空格：有符号值若为正，则在值前面显示前导空格（不显示任何符号）；若为负，则在值前面显示减号+标记覆盖一个空格。示例：“%6.2f”
  * \#：把结果转换为另一种形式。如果是%o格式，则以0开始；如果是xx或XX格式，则以0x或0X开始；对于所有的浮点格式，#保证了即使后面没有任何数字，也打印一个小数点字符。对于gg和GG格式，#防止结果后面的0被删除。示例：“%#0”、“%#8.0f”、“%+#10.3e”
  * 0：对于数值格式，用前导0代替空格填充字段宽度。对于整数格式，如果出现-标记或指定精度，则忽略该标记
* 数字：最小字段宽度。如果不能容纳字符串，会自动增长。Example: "%4d".
* .数字：精度。Example："%5.2f"，字段宽度为5字符，其中小数点后有两位数字
  * 对于%e、%E和%f转换，表示小数点右边数字的位数
  * 对于%g和%G转换，表示有效数字最大位数
  * 对于%s转换，表示待打印字符的最大数量
  * 对于整型转换，表示待打印数字的最小位数
  * 如有必要，使用前导0来达到这个位数
  * 只使用.表示其后跟随一个0，所以%.f和%.0f相同
* h
  * 和整型转换说明一起使用，表示short int或unsigned short int类型的值
  * 示例: "%hu"、"%hx"、"%6.4hd"
* hh
  * 和整型转换说明一起使用，表示signed char或unsigned char类型的值
  * 示例: "%hhu"、"%hhx"、"%6.4hhd"
* j
  * 和整型转换说明一起使用，表示intmax\_t或uintmax\_t类型的值。这些类型定义在stdint.h中
  * 示例: "%ja"、"%8jx"
* l
  * 和整型转换说明一起使用，表示long int或unsigned long int类型的值
  * 示例: "%ld"、"%8lu"
* ll
  * 和整型转换说明一起使用，表示long long int或unsigned long long int类型的值(C99)
  * 示例: "%lld"、"%8llu"
* L
  * 和浮点转换说明一起使用，表示long double类型的值
  * 示例: "%Ld"、"%10.4Le"
* t
  * 和整型转换说明一起使用，表示ptrdiff\_t类型的值。ptrdiff\_t是两个指针差值的类型(C99)
  * 示例: "%td"、"%12ti"
* z
  * 和整型转换说明一起使用，表示size\_t类型的值。size\_t是sizeof返回的类型(C99)
  * 示例: "%zd"、"%12zd"

</details>

<details>

<summary>*：让程序指定 printf 宽度</summary>

<pre class="language-c"><code class="lang-c">/* varwid.c -- uses variable-width output field */
#include &#x3C;stdio.h>
int main(void)
{
    unsigned width, precision;
    int number = 256;
    double weight = 242.5;

    printf("Enter a field width:\n");
    scanf("%d", &#x26;width);
<strong>    printf("The number is :%*d:\n", width, number);
</strong>    printf("Now enter a width and a precision:\n");
    scanf("%d %d", &#x26;width, &#x26;precision);
<strong>    printf("Weight = %*.*f\n", width, precision, weight);
</strong>    printf("Done!\n");

    return 0;
}

// Enter a field width:
// 10
// The number is :       256:
// Now enter a width and a precision:
// 10 3
// Weight =    242.500
// Done!
</code></pre>

</details>

### scanf

{% hint style="warning" %}
scanf() 最不常用，因为他容易卡住。最好用 getchar()或者fgets()吧。
{% endhint %}

<details>

<summary>scanf 与 printf 两点不一样</summary>

* 变量前要加&
* double 的转换说明是 lf 而不是 f

</details>

<details>

<summary>Demo</summary>

<pre class="language-c"><code class="lang-c">// input.c -- when to use &#x26;
#include &#x3C;stdio.h>
int main(void)
{
    int age;      // variable
    float assets; // variable
    char pet[30]; // string

    printf("Enter your age, assets, and favorite pet.\n");
<strong>    scanf("%d %f", &#x26;age, &#x26;assets); // use the &#x26; here
</strong><strong>    scanf("%s", pet);              // no &#x26; for char array
</strong>    printf("%d $%.2f %s\n", age, assets, pet);

    return 0;
}

// 10 9.9
// a
// 10 $9.90 a
</code></pre>

</details>

<details>

<summary>*：让程序跳过某个输入（读取文件有常用）</summary>

```c
/* skiptwo.c -- skips over first two integers of input */
#include <stdio.h>
int main(void)
{
    int n;
    
    printf("Please enter three integers:\n");
    scanf("%*d %*d %d", &n);
    printf("The last integer was %d\n", n);
    
    return 0;
}

// Please enter three integers:
// 1 2 3
// The last integer was 3
```

</details>

<details>

<summary>如果输入里边有空格，scanf 会认为这是两个输入！另外可以指定输入字符串长度</summary>

```c
/* scan_str.c -- using scanf() */
#include <stdio.h>
int main(void)
{
    char name1[11], name2[11];
    int count;

    printf("Please enter 2 names.\n");
    count = scanf("%5s %10s", name1, name2);
    printf("I read the %d names %s and %s.\n",
           count, name1, name2);

    return 0;
}

// (base) kimshan@MacBook-Pro output % ./"scan_str"
// Please enter 2 names.
// 123 45
// I read the 2 names 123 and 45.
// (base) kimshan@MacBook-Pro output % ./"scan_str"
// Please enter 2 names.
// 1234567890
// I read the 2 names 12345 and 67890.
// (base) kimshan@MacBook-Pro output % ./"scan_str"
// Please enter 2 names.
// 1234567890 1234567890
// I read the 2 names 12345 and 67890.

```

</details>

### getchar, putchar

<details>

<summary>Demo</summary>

<pre class="language-c"><code class="lang-c">/* echo_eof.c -- repeats input to end of file */
#include &#x3C;stdio.h>
int main(void)
{
    int ch;
    
<strong>    while ((ch = getchar()) != EOF)
</strong><strong>        putchar(ch);
</strong>    
    return 0;
}

</code></pre>

</details>

### gets, puts

{% hint style="danger" %}
不要用gets这个函数
{% endhint %}

<details>

<summary>gets 会访问未规定的内存！！不要用这个函数！C99已经废除，不过大多数编译器保留了。</summary>

```c
#include <stdio.h>
#include <stdlib.h>
int main()
{
    char array1[8];
    fflush(stdin);
    gets(array1); // 1234567
    puts(array1); // 1234567
    char array2[8];
    fflush(stdin);
    gets(array2); // 12345678
    puts(array2); // 12345678
    char array3[8];
    fflush(stdin);
    gets(array3); // 123456789
    puts(array3); // 123456789
    return 0;
}

// (base) kimshan@MacBook-Pro output % ./"a"
// warning: this program uses gets(), which is unsafe.
// 1234567
// 1234567
// 12345678
// 12345678
// 123456789
// 123456789
// (base) kimshan@MacBook-Pro output
```

</details>

<details>

<summary>puts看到空字符才会结束。下面的例子打印不是字符串的东西，会出 bug</summary>

```c
/* nono.c -- no! */
#include <stdio.h>
int main(void)
{
    char side_a[] = "Side A";
    char dont[] = {'W', 'O', 'W', '!'};
    char side_b[] = "Side B";

    puts(dont); /* dont is not a string */
    // WOW!Side A

    return 0;
}
```

</details>

### fgets, fputs

<details>

<summary>fgets 会留出\0的位置，超出范围的长度会被截断；fputs 不会自动换行</summary>

```c
#include <stdio.h>
#include <stdlib.h>
int main()
{
    char array1[8];
    fflush(stdin);
    fgets(array1, sizeof(array1), stdin); // 1234567
    fputs(array1, stdout); // 1234567
    char array2[8];
    fflush(stdin);
    fgets(array2, sizeof(array2), stdin); // 12345678
    fputs(array2, stdout); // 1234567
    char array3[8];
    fflush(stdin);
    fgets(array3, sizeof(array3), stdin); // 123456789
    fputs(array3, stdout); // 1234567
    return 0;
}

// (base) kimshan@MacBook-Pro output % ./"a"
// 1234567
// 123456712345678
// 1234567123456789
// 1234567%
// (base) kimshan@MacBook-Pro output %
```

</details>

### gets\_s

{% hint style="danger" %}
很多编译器不支持这个 C11 的新函数！
{% endhint %}

<details>

<summary>你是否觉得 fgets 还要用 sizeof 有点麻烦，那就用gets_s吧。但是它没有fgets灵活</summary>

```c
#include <stdio.h>
#include <stdlib.h>
int main()
{
    char array1[8];
    fflush(stdin);
    gets_s(array1, 8);
    puts(array1);
    char array2[8];
    fflush(stdin);
    gets_s(array2, 8);
    puts(array2);
    char array3[8];
    fflush(stdin);
    gets_s(array3, 8);
    puts(array3);
    return 0;
}
```

</details>

<details>

<summary>我们写一个自己的 s_gets</summary>

```c
char * s_gets(char * st, int n)
{
    char * ret_val;
    int i = 0;
    
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        while (st[i] != '\n' && st[i] != '\0')
            i++;
        if (st[i] == '\n')
            st[i] = '\0';
        else // must have words[i] == '\0'
            while (getchar() != '\n')
                continue;
    }
    return ret_val;
}
```

</details>

### sprintf

<details>

<summary>进行字符串格式化，形成一个字符串保存到某个变量中</summary>

```c
/* format.c -- format a string */
#include <stdio.h>
#define MAX 20
char *s_gets(char *st, int n);

int main(void)
{
    char first[MAX];
    char last[MAX];
    char formal[2 * MAX + 10];
    double prize;

    puts("Enter your first name:");
    s_gets(first, MAX);
    puts("Enter your last name:");
    s_gets(last, MAX);
    puts("Enter your prize money:");
    scanf("%lf", &prize);
    sprintf(formal, "%s, %-19s: $%6.2f\n", last, first, prize);
    puts(formal);

    return 0;
}

char *s_gets(char *st, int n)
{
    char *ret_val;
    int i = 0;

    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        while (st[i] != '\n' && st[i] != '\0')
            i++;
        if (st[i] == '\n')
            st[i] = '\0';
        else // must have words[i] == '\0'
            while (getchar() != '\n')
                continue;
    }
    return ret_val;
}

// (base) kimshan@MacBook-Pro output % ./"format"
// Enter your first name:
// Charles
// Enter your last name:
// Shan
// Enter your prize money:
// 1000000
// Shan, Charles            : $1000000.00
```

</details>

## Reference

\[1] [https://www.runoob.com/cprogramming/c-function-fflush.html](https://www.runoob.com/cprogramming/c-function-fflush.html)

\[2] [https://www.pixelbeat.org/programming/gcc/format\_specs.html](https://www.pixelbeat.org/programming/gcc/format\_specs.html)

\[3] [https://www.gnu.org/software/libc/manual/html\_node/Table-of-Output-Conversions.html](https://www.gnu.org/software/libc/manual/html\_node/Table-of-Output-Conversions.html)