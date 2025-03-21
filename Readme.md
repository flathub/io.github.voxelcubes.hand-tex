## Notes:

See the Makefile for local test builds.


# Collecting manual dependencies.

For torch version 2.1.0 I had no issues running the flatpak, but users reported a strange error that indicated a version 
incompatibility between torch and torchvision. The versions matched, but I did notice that upon startup, torch output
an error message about missing some libjpg library which apparently would've been caused by a bad compilation.

To figure out why my version worked, I created a fresh venv and installed torch using the pip command from
https://pytorch.org/get-started/locally/: pip3 install torch torchvision --index-url https://download.pytorch.org/whl/cpu
Rather than using the index site myself. Pip grabbed a different file than the one on the index site, torchvision remained the
same. The new file worked in the venv, so I incorporated that into the flatpak.

To grab other dependencies automatically, that also include binaries, modify the pip generator to not discriminate against them and allow all wheels. Then take care of them manually.
