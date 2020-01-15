
This project skeleton was made joining pieces from two Intel repos available on Github

----------Rationale----------
Handle application dependencies across different Data Science projects and environments could be tricky. Especially, if you want to scale in number of team members and expand collaboration with other organisations. 
----------Rationale----------

prerequisites

icc, if compiling native benchmarks. Intel Distribution for Python* 2019 Gold benchmarks used icc 17.0.1.
For this, you also need an INTEL_SERIAL_NUMBER=XXXX-XXXXXXX"
The following lines have to be uncommented inside the dockerfile if you need to run icc:

# It needs INTEL_SERIAL_NUMBER=XXXX-XXXXXXX
# COPY activate-icc-online.sh activate-icc-online.sh
# RUN ./activate-icc-online.sh

# RUN make nomkl TARGET_ARCH=host

# RUN /opt/intel/parallel_studio_xe_2019/uninstall.sh -s

./activate-conda.sh to installs miniconda on Linux and Mac
./create-conda-envs.sh installs packages for all environments, channels and all python versions

First, get into the docker folder:

            cd docker-dependencies

Then, build the image, named intel_local in the following example:

            docker build -t intel_local .

To run the container do:

            docker run intel_local [COMMANDS]
            
For instance, 

            docker run intel_local python --version
            Python 3.6.8 :: Intel Corporation

            docker run intel_local conda env list

Access into the container itself is not supported as the goal is to have immutable environment configuration. 

As an example, there are three environments defined inside the conda-configs directory






