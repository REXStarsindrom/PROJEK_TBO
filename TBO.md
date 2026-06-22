# PROJEK_TBO
# Implementasi Mesin Turing Deterministik Untuk Operasi Bitwise NOT Pada Konversi Subnet Mask ke Wildcard Mask
def calculate_wildcard_mask(subnet_mask: str) -> str:
    wildcard_octets = []
    
    # Pecah string Subnet Mask berdasarkan titik menjadi list, misal: ['255', '255', '255', '0']
    octets = subnet_mask.split('.')
    
    print("=" * 75)
    print(f"{'Blok':<8} | {'Desimal':<8} | {'Biner Subnet':<14} | {'Biner Wildcard':<14} | {'Hasil':<6}")
    print("=" * 75)
    
    for i, octet_str in enumerate(octets):
        # 1. Ubah string angka menjadi integer desimal
        # (contoh: string '255' jadi angka 255)
        octet_val = int(octet_str)
        
        # 2. Lakukan bitwise NOT dan mask ke 8-bit (0xFF)
        # Di sinilah proses inversi bit terjadi, persis seperti kode Anda
        inverted_val = ~octet_val & 0xFF
        
        # 3. Ubah kembali hasil inversi ke string untuk digabungkan nanti
        wildcard_octets.append(str(inverted_val))
        
        # Cetak visualisasi transformasi bitnya
        bin_asli   = f"{octet_val:08b}"
        bin_invert = f"{inverted_val:08b}"
        print(f"Oktet {i+1:<2} | {octet_val:<8} | {bin_asli:<14} | {bin_invert:<14} | {inverted_val}")
        
    print("=" * 75)
    
    # Gabungkan kembali dengan titik
    return ".".join(wildcard_octets)

if __name__ == "__main__":
    print("=== Simulator Inversi Bit: Subnet ke Wildcard Mask ===\n")
    
    # Program menunggu input dari user di terminal
    # Diharapkan user memasukkan format IP (misal: 255.255.255.0 atau 255.255.255.224)
    input_user = input("Masukkan Subnet Mask (contoh: 255.255.255.0): ")
    
    print(f"\nInput Subnet Mask : {input_user}\n")
    
    hasil_output = calculate_wildcard_mask(input_user)
    
    print(f"\nOutput Wildcard Mask: {hasil_output}\n")
