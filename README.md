# Pyjamask on Cortex-M4

This repository provides the source code of a high-order masked implementation of [Pyjamask](https://pyjamask-cipher.github.io/) on ARM Cortex-M4. The source code has been tested on STM32F407 Discovery Kit.

## Authors

* Dahmun Goudarzi ([PQShield](https://pqshield.com/)) 
* Matthieu Rivain ([CryptoExperts](https://www.cryptoexperts.com)) 

## Contents

### Source files

* `masked_pyjamask.c`: main Pyjamask functions (key schedule, encryption, decryption) for both 96 and 128 modes;
* `masked_pyjamask_asm.S`: optimized assembly functions for the masked implementation of Pyjamask (matrix vector multiplication, ISW MACC, randomness generation);
* `random.c`: call the hardware RNG of the STM32F407 board (only use to generate the initial masks of the state and the keys);

Two versions (__v1__ and __v2__) of the code source are provided. __v2__ is optimized for timings with a larger code size than __v1__. See the [specification document](https://csrc.nist.gov/CSRC/media/Projects/Lightweight-Cryptography/documents/round-1/spec-doc/Pyjamask-spec.pdf) for details.

### Header files

* `api.h`: prototypes of main entry points;
* `param.h`: definition of implementation parameters:
	* the masking order,
	* hardware RNG configuration constants;
* `random.h`: prototypes for random generation function.

## Documentation

The detailed description of this implementation as well as a performance benchmark can be found in the Pyjamask [specification document](https://csrc.nist.gov/CSRC/media/Projects/Lightweight-Cryptography/documents/round-1/spec-doc/Pyjamask-spec.pdf).

## Setup

Some guidelines for installing the tools can be found <a href="https://github.com/mupq/pqm4">here</a>.
