# CDMA Signal Transmission & Reception Simulation

A MATLAB/Octave simulation of Code Division Multiple Access (CDMA): four users transmit simultaneously over the same channel, each spread with their own Walsh code, and the receiver recovers every user's original data exactly, with zero bit errors, by exploiting the orthogonality of those codes.

Built for an Analog & Digital Communication Lab practical at Institute of Engineering & Management, Kolkata.

## Team project

Two people worked on this: Sayantan Sarkar and me. Verified with the code, not just claimed: the report's own file metadata lists Sayantan Sarkar as the author.

## How it works

Each of the 4 users has an 8-bit data stream (`D`, using bipolar `+1`/`-1` instead of `1`/`0`) and a unique 4-bit spreading code from a Walsh set (`C`), chosen so the codes are mutually orthogonal. Each user's data is spread by multiplying every bit against their own code, and all four users' spread signals are summed onto one shared channel (`T`), simulating simultaneous transmission.

At the receiver, recovering one user's data means multiplying the combined channel signal back against that user's own code and averaging. Because the codes are orthogonal, every other user's contribution cancels out in that step, leaving only the intended user's original bits.

## Run it

```bash
# Octave (free): sudo apt-get install octave
octave cdma_simulation.m
```

Also runs unmodified in MATLAB.

## Verified

I ran this in this repo's own history, not just transcribed it: the reconstructed 4x8 matrix at the receiver is checked programmatically against the original transmitted data and matches exactly, every bit, for all four users, confirming the spreading codes are truly orthogonal and the CDMA round trip introduces zero error.

Full report: [CDMA_Report.pdf](https://github.com/user-attachments/files/32419142/CDMA_Report.pdf) in this repo.
