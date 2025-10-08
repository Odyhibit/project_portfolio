# How I Built My ASCII‐to‐Bitmapped‐Font Converter

**Date**: 2025‐05‐07

**Problem**  
I frequently need a quick way to see a hexadecimal representation of a 1‐bit image, especially when experimenting with bit‐level steganography. Manually converting ASCII to a 5×7 or 8×8 dot matrix in hex was tedious.

**Solution**  
I wrote a Python script that:

1. Takes any ASCII string
2. Uses a custom 5×7 bitmapped font
3. Renders each character into a binary matrix
4. Concatenates rows into bytes
5. Outputs a hex string (or Base64) that can be embedded in web demos

```python title="hex_string_to_bit_matrix()" linenums="1"
# Example snippet from `hex_string_to_bit_matrix`
def hex_string_to_bit_matrix(hex_string: str) -> list[list[str]]:
    bytes_data = bytes.fromhex(hex_string)
    bit_matrix = []
    for byte in bytes_data:
        bits = list(f"{byte:08b}")
        bit_matrix.append(bits)
    return bit_matrix
```
# Result

* This is a custom bitmap font representation of the input text.
* Use this to create/decode messages for CTF like chanllenges.
* You can set the output to base64 if that is more convienient.
* Full source is on GitHub.

Thanks
   — Josh
