# Skip32-java

skip32-java is an implementation of SKIP32 cipher written in Java. SKIP32 is a 80-bit key, 32-bit block cipher based on Skipjack. The original implementation is written by Greg Rose and can be found at [https://opensource.qualcomm.com/assets/dotc/skip32.c](https://opensource.qualcomm.com/assets/dotc/skip32.c)

The algorithm is useful for obfuscating 32-bit integers, such as database IDs, to make them look less sequential.

## Usage

Either download and compile it yourself from source, or use this in your pom.xml:

    <dependency>
      <groupId>com.boivie</groupId>
      <artifactId>skip32</artifactId>
      <version>1.0</version>
    </dependency>

Your java code will look something like:

    import com.boivie.skip32.Skip32
    
    ...
    
    byte[] key = { 0x11, 0x22, 0x33, 0x44, 0x55, 0x66, 0x77, (byte) 0x88,
                   (byte) 0x99, (byte) 0xAA };

    int id = 12345;

    int c = Skip32.encrypt(id, key);
    int p = Skip32.decrypt(c, key);
    
    Assert.assertEquals(id, p);

## Author

This code is written (or well, mostly translated from the original source) by Victor Boivie, <victor@boivie.com>.

## License

This code is distributed under the New BSD License. Please see the LICENSE file for full details.


