# AlSciPy (Alpine Science Python)

[![Docker Stars](https://img.shields.io/docker/stars/jfloff/alscipy.svg)][hub]
[![Docker Pulls](https://img.shields.io/docker/pulls/jfloff/alscipy.svg)][hub]

[hub]: https://hub.docker.com/r/jfloff/alscipy/


Image with common packages for doing science in [alpine-python](https://github.com/jfloff/alpine-python)!


## Supported tags
* **`2.7` ([2.7/Dockerfile](https://github.com/jfloff/docker-alscipy/blob/master/2.7/Dockerfile))**
* **`3`,`latest` ([2.7/Dockerfile](https://github.com/jfloff/docker-alscipy/blob/master/3/Dockerfile))**


## Packages
- [numpy](http://www.numpy.org/)
- [scipy](https://scipy.org/scipylib/)
- [pandas](http://pandas.pydata.org/)
- [matplotlib](https://matplotlib.org/)
- [seaborn](https://seaborn.pydata.org/)
- [jupyter](http://jupyter.org/)
- [scikit-learn](http://scikit-learn.org/stable/)
- [lxml](http://lxml.de/)

***Submit a PR or open an issue for new packages to be added!***


#### Jupyter
This images comes with Jupyter server included! Amazing for quick plots! To run some notebook just mount the folder with your notebooks to docker and run:
```
docker run --rm -p 8888:8888 -v "$(pwd)/jupyter":/home/jupyter -ti jfloff/alscipy jupyter /home/jupyter/<notebook filename>
```


## Building it yourself
This image is available on Docker Hub, but you can always fork it, change it and built it yourself! Remember, if you are just adding a new package think about opening a PR or issue. I will add it here directly!

- Build image with:
  `docker build --rm -t jfloff/alscipy .`

- Run image:
  `docker run --rm -ti jfloff/alscipy`


## License
The code in this repository, unless otherwise noted, is MIT licensed. See the LICENSE file in this repository. Please refer to each package LICENSE when using this image.
