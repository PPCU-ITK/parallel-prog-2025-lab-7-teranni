[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/2CuuzvUr)
# assignment-7

Original code:
module load nvhpc
nvc++ laplace2d.cpp -mp -Ofast -o lap_cpu
srun -p gpu --gres=gpu:1 --cpus-per-task=4 --mem-per-cpu=2000 --time=00:05:00 --reservation=p_es_itkpp_204 ./laplace_cpu

1678 - 2966.53ms

Parallelisation 1:
module load nvhpc
module load craype-accel-nvidia80
nvc++ -mp=gpu -gpu=cc80 -Ofast laplace2d.cpp -o laplace -Minfo=accel,mp
srun -p gpu --gres=gpu:1 --ntasks=1 --time=00:05:00 --mem=40G --reservation=p_es_itkpp_204 ./laplace

9083.01ms


Assignment:
module load nvhpc
nvc++ -mp=gpu -gpu=cc80 -Ofast cfd_euler.cpp -o eu
srun -p gpu --gres=gpu:1 --ntasks=1 --time=00:05:00 --mem=40G ./eu
