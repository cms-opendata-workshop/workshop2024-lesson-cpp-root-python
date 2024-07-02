---
title: "Using ROOT with C++ to fill a histogram"
teaching: 10
exercises: 20
---

::::::::::::::::: questions
- Is there more than reading and writing files that can be done with ROOT?
- How do I run a ROOT script?
:::::::::::::::::

::::::::::::::::: objectives
- Learn to fill a histogram and save it to a file.
- Learn to run a simple ROOT script
:::::::::::::::::

## Filling a histogram

ROOT can easily fill a histogram as you are looping over individual events. Let's
try creating and filling a histogram with the transverse momentum values. We'll start
with the `read_ROOT_file.cc` code we wrote in the previous episode and copy what
we have to a new file, `fill_histogram.cc`.

```bash
cp read_ROOT_file.cc fill_histogram.cc
```

Into this file, we'll add some lines at some key spots. Again, use your favourite editor on your local computer. For now, we'll go through those lines
of code individually, and then show you the completed file at the end to see where they went.

First we need to include the header file for the ROOT [TH1F](https://root.cern.ch/doc/master/classTH1F.html) class.

```cpp
#include "TH1F.h"
```

We create an output file to store the histogram in.

```cpp
   // Let's make an output file which we'll use to save our
   // histogram
   TFile fout("output.root","recreate");
```

Define the histogram.
```cpp
   // We define an histogram for the transverse momentum of the jets
   // The arguments are as follow
   // * Internal name of the histogram
   // * Title that will be used if the histogram is plotted
   // * Number of bins
   // * Low edge of the lowest bin
   // * High edge of the highest bin
   TH1F h1("h1","jet pT (GeV/c)",50,0,150);
```

And then *inside the event loop*, we fill the histogram each time we get a new value for
the transverse momentum.

```cpp
         // Fill the histogram with each value of pT
         h1.Fill(pt[j]);
```

Before we leave the function, we "change directory" to the output file, write the histogram
to the file, and then close the output file.

```cpp
   fout.cd();
   h1.Write();
   fout.Close();
```


The final version of `fill_histogram.cc` will look like this:


::::::::::::::::: keypoints
- You can quickly inspect your data using just ROOT
- A simple ROOT script is often all you need for diagnostic work
:::::::::::::::::

