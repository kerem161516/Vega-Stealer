A Bitcoin wallet collider that brute forces random wallet addresses

Like This Project? Give It A Star


Dependencies
[Python 3.9](https://www.python.org/downloads/) or higher

If you have a Linux or MacOS operating system, libgmp3-dev is required. If you have Windows then this is not required. Install by running the command:

This program is essentially a brute forcing algorithm. It continuously generates random Bitcoin private keys, converts the private keys into their respective wallet addresses, then checks the balance of the addresses. If a wallet with a balance is found, then the private key, public key and wallet address are saved to the text file on the user's hard drive. The ultimate goal is to randomly find a wallet with a balance out of the 2160 possible wallets in existence.

How It Works
32 byte hexidecimal strings are generated randomly using os.urandom() and are used as our private keys.

The private keys are converted into their respective public keys using the fastecdsa python library. This is the fastest library to perform secp256k1 signing. If you run this on Windows then fastecdsa is not supported, so instead we use starkbank-ecdsa to generate public keys. The public keys are converted into their Bitcoin wallet addresses using the binascii and hashlib standard libraries.

A pre-calculated database of every funded P2PKH Bitcoin address is included in this project. The generated address is searched within the database, and if it is found that the address has a balance, then the private key, public key and wallet address are saved to the text file  on the user's hard drive.

This program also utilizes multiprocessing through the multiprocessing.Process() function in order to make concurrent calculations.

Efficiency
It takes 0.002 seconds for this progam to brute force a single Bitcoin address.

However, through multiprocessing.Process() a concurrent process is created for every CPU your computer has. So this program can brute force a single address at a speed of 0.002 รท cpu_count() seconds.

Parameters
This program has optional parameters to customize how it runs:

help: python3 builder.py help
Prints a short explanation of the parameters and how they work

time: python3 builder.py time
Brute forces a single address and takes a timestamp of how long it took - used for speed testing purposes

verbose: 0 or 1
python3 builder.py verbose=1: When set to 1, then every bitcoin address that gets bruteforced will be printed to the terminal. This has the potential to slow the program down

python3 builder.py verbose=0: When set to 0, the program will not print anything to the terminal and the bruteforcing will work silently. By default verbose is set to 0

substring: python3 builder.py substring=8: To make the program memory efficient, the entire bitcoin address is not loaded from the database. Only the last <substring> characters are loaded. This significantly reduces the amount of RAM required to run the program. if you still get memory errors then try making this number smaller, by default it is set to 8. This opens us up to getting false positives (empty addresses mistaken as funded) with a probability of 1/(16^<substring>), however it does NOT leave us vulnerable to false negatives (funded addresses being mistaken as empty) so this is an acceptable compromise.

cpu_count: python3 builder.py cpu_count=1: number of cores to run concurrently. More cores = more resource usage but faster bruteforcing. Omit this parameter to run with the maximum number of cores

By default the program runs using python3 builder.py verbose=0 substring=8 if nothing is passed.

Expected Output

#discord stealer #discord-stealer #rat #stealer #github-stealer #githubstealer #obfuscation #discord #discordapp #rat #startup #fud#stealer #cookie-logger #discord-logger #discord-token-grabber #discordinjector #password-stealer #discordtokengrabber #discord-token-stealer #undetectable-token-grabber #stealer-undetected #stealercookie
