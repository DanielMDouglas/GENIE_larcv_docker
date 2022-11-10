# GENIE + LArCV2 container recipes

This repository consists of two docker recipes for building the dependencies of the GENIE neutrino event generator (and some other useful software.  It is based on the work of [Callum Wilkinson](https://github.com/wilkinson-nu/2x2_truth_studies), extended to Docker and based on the existing LArCV2 image.

To build the GENIE container, first build ROOT with Pythia6:

```
docker build . -f root-pythia6-recipe -t ub20.04-cuda11.3-cudnn8-pytorch1.10.0-root-pythia
```

Next, build the GENIE image on top of it

```
docker build . -f genie-recipe -t ub20.04-cuda11.3-cudnn8-pytorch1.10.0-genie
```

If you wish, you can then convert the image to a singularity image file:

```
docker save ub20.04-cuda11.3-cudnn8-pytorch1.10.0-GENIE:latest -o ub20.04-cuda11.3-cudnn8-pytorch1.10.0-genie.tar
singularity build ub20.04-cuda11.3-cudnn8-pytorch1.10.0-genie.sif docker-archive://ub20.04-cuda11.3-cudnn8-pytorch1.10.0-genie.tar
```

This singularity image is also available on SLAC's SDF.  If you have access, you can find it at `/sdf/group/neutrino/dougl215/images/larcv2_ub20.04-cuda11.3-cudnn8-pytorch1.10.0-larndsim-2022-10-28.sif`.  Enjoy!
