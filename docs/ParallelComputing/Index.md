

- Install OpenMPI from Distribution
  - Download tar file from [Official Downloads](https://www.open-mpi.org/software/ompi/v4.1/) 
    - Or [OpenMPI](https://download.open-mpi.org/release/open-mpi/v4.1/openmpi-4.1.4.tar.gz)
  - Extract to some folder and run Configure
    ```bash
    tar -xvf openmpi-4.1.4.tar.gz
    cd openmpi-4.1.4
    ./configure --prefix=/where/to/install
    ```
- Install MPI Compiler and Executables on Ubuntu-22
  ```bash
  sudo apt-get update
  sudo apt install openmpi-bin
  sudo apt install libopenmpi-dev
  ```

---
- [All Tutorials](https://mpitutorial.com/tutorials/)
- [Hello World](https://mpitutorial.com/tutorials/mpi-hello-world/)
- [Within Lan](https://mpitutorial.com/tutorials/running-an-mpi-cluster-within-a-lan/)
- [Official MPI Documentation](https://docs.open-mpi.org/en/v5.0.x/building-apps/index.html)
