# GPU Server Infrastructure & Setup Guide

This repository documents the architecture, hardware configuration, and standard operating procedures for our multi-user High-Performance Multi-GPU environment.

## 🖥️ Hardware Specifications
* **CPU:** 128-core
* **RAM:** 512 GB
* **GPUs:** Dual NVIDIA L40S (48GB VRAM) - *ECC Disabled for ML throughput* (Total 96GB)
* **Storage Routing:** Secondary `/DATA` drive via symlinks

## 👥 User Architecture
The system utilizes generic lab accounts (`aglab0` through `aglab6`) over SSH. 
Global Python dependencies are managed via Miniconda environment.

## 🚀 Custom Tooling
* **Tmux Queue Engine:** Native bash script utilizing Tmux to sequentially schedule, monitor, and execute PyTorch jobs without VRAM overlap.
* **ML Data Loaders:** Refactored PyTorch `Dataset` classes utilizing `h5py` lazy-loading to minimize RAM footprints during large-scale model training.