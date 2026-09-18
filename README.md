# ZOSC TOUCH
ZoscTouch is a dual [Z-Oscillator](https://docs.daisy.audio/DaisySP/classdaisysp_1_1ZOscillator/#detailed-description) monophonic synthesizer built for the [Synthux SimpleTouch](https://www.synthux.academy/store/touch-2-kit) which runs on a Daisy Seed. 

The project one main C++ file with minimal abstractions. It's meant to show every working part of the hardware peripherals and synth logic using this [template](https://github.com/chrisades/SimpleTouchTemplate) as a base, with [DaisySP](https://docs.daisy.audio/DaisySP/namespacedaisysp/) modules doing the heavy lifting.

If you're looking for a more professional coding style please reference the official Synthux SimpleTouch projects like [TouchBass](https://github.com/Synthux-Academy/TouchBass) or [TouchString](https://github.com/Synthux-Academy/TouchString) from which the peripheral logic and the rest of this README was adapted from.

## QUICK INSTALL
Download the [Binary file](https://github.com/chrisades/ZoscTouch/releases/latest/download/ZoscTouch.bin) and flash using the [Daisy Seed web programmer](https://flash.daisy.audio/)

## CONTROLS
<img src="touch.jpeg" width="300"/>

**Switches**
- S07-S08 - LFO Modulation Destination: (Frequencies | Formant Frequencies | Amplitude)
- S09-S10 - Touch Envelope: (Slow | Fast | Hold)

**Knobs**
- S30 - LFO Frequency
- S31 - ZOsc-1 Frequency
- S32 - ZOsc-1 Formant Frequency
- S33 - ZOsc-2 Formant Frequency
- S34 - ZOsc-2 Frequency
- S35 - LFO Amount
- S36 - ZOsc-1 and ZOsc-2 Shape
- S37 - ZOsc-1 and ZOsc-2 Mode

**Pads**
- P00 - Cycle Scales
- P01/P02 - Octave -/+
- P03...P09 - Notes
- P10/P11 - Level -/+ 

## PREREQUISITES
- [Daisy Toolchain](https://docs.daisy.audio/tutorials/cpp-dev-env/) (ARM GCC + make)
- **Windows:** use [Git Bash](https://git-scm.com/downloads) to run the commands below

## PROJECT SETUP
```shell
$ git clone --recurse-submodules https://github.com/chrisades/ZoscTouch.git
$ cd ZoscTouch/lib/libDaisy
$ make
$ cd ../DaisySP
$ make
$ cd ../..
$ make clean; make
```

If you already have the repo cloned without submodules, run this first:
```shell
$ git submodule update --init --recursive
```

## UPLOAD
```shell
$ make program-dfu
```

> [!NOTE]
> When tweaking code, run `make clean && make` for a full rebuild, or just `make` for an incremental rebuild (only recompiles changed files). The compiled binary is placed in the `build/` folder as `ZoscTouch.bin`.
