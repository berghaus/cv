## Building
To build the PDF you may use the included Dockerfile to build a `latex` container and use it as follows:

```
docker build --tag latex .
docker run -it --rm --volume ${PWD}:/opt/work latex pdflatex resume
```
