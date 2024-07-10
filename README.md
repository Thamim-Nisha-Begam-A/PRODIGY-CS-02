# PRODIGY-CS-02

from PIL import Image

def swap_pixels(image, x1, y1, x2, y2):
    """
    Swaps the pixel values at coordinates (x1, y1) and (x2, y2) in the image.
    """
    pixel1 = image.getpixel((x1, y1))
    pixel2 = image.getpixel((x2, y2))
    image.putpixel((x1, y1), pixel2)
    image.putpixel((x2, y2), pixel1)

def apply_math_operation(image, operation):
    """
    Applies a basic mathematical operation to each pixel in the image.
    Example: operation = lambda r, g, b: (r + 10, g - 20, b * 2)
    """
    width, height = image.size
    for x in range(width):
        for y in range(height):
            r, g, b = image.getpixel((x, y))
            new_r, new_g, new_b = operation(r, g, b)
            image.putpixel((x, y), (new_r, new_g, new_b))

def encrypt_image(image_path, output_path):
    image = Image.open(image_path)
    
    # Example: Swap pixels at (10, 20) and (30, 40)
    swap_pixels(image, 10, 20, 30, 40)
    
    # Example: Apply a brightness adjustment
    brightness_adjustment = lambda r, g, b: (r + 20, g + 20, b + 20)
    apply_math_operation(image, brightness_adjustment)
    
    image.save(output_path)
    print(f"Encrypted image saved as {output_path}")

def decrypt_image(encrypted_path, output_path):
    # To decrypt, simply reverse the operations applied during encryption
    # Swap back the pixels and apply the inverse of the mathematical operation
    pass  # Implement decryption logic here

# Example usage:
input_image_path = "input_image.jpg"
encrypted_image_path = "encrypted_image.jpg"
decrypted_image_path = "decrypted_image.jpg"

encrypt_image(input_image_path, encrypted_image_path)
# Decrypt the image using the reverse operations
# decrypt_image(encrypted_image_path, decrypted_image_path)
