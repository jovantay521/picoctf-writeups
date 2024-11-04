# Scan Surprise

**Category:** Forensics  
**Difficulty:** Easy  
**Date:** 2024-11-03

## Challenge Description
I’ve grown tired of handing out flags as plain text. Wouldn’t it be more exciting if they were presented as an image instead?

## Files Provided  
- `flag.png` - An image containing a QR code.

## Approach & Solution

### Tools Used  
- CyberChef

### Steps Taken  
1. **Load the Image**: Open `flag.png` in CyberChef.
2. **Parse the QR Code**: Utilise CyberChef’s QR code decoder to extract the hidden data.

![alt text]({989D67BE-8537-4A89-9457-F9F951D6E9A8}.png)

### Explanation  
By applying CyberChef’s QR code parsing capabilities, I was able to decode the image and reveal the flag.

## Flag  
```
picoCTF{p33k_@_b00_7843f77c}
```

## Key Takeaways

### Techniques Learned  
- Leveraged CyberChef for QR code decoding, demonstrating its versatility in forensics challenges.