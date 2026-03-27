# Enhancing 3D Gaussian Splatting for Dynamic Scenes: Integrating Semantic and Geometric Consistency

Official implementation of the paper: **"Enhancing 3D Gaussian Splatting for Dynamic Scenes: Integrating Semantic and Geometric Consistency"**.

---

## 🛠️ Installation

### 1. Clone the Repository
```bash
git clone [https://github.com/deream-king/E3DGS-SGC.git](https://github.com/deream-king/E3DGS-SGC.git)
cd E3DGS-SGC
We recommend using Conda to manage your environment:
conda env create --file environment.yml
conda activate E3DGS-SGC
Install the necessary rasterization and KNN submodules:
# For Linux/macOS
pip install submodules/diff-gaussian-rasterization
pip install submodules/simple-knn

# For Windows
# pip install submodules\diff-gaussian-rasterization
# pip install submodules\simple-knn
We utilize depth maps as an additional feature to identify moving objects. For real-world datasets, you must generate depth maps for each input image:
Clone Depth Anything v2:

Bash
git clone [https://github.com/DepthAnything/Depth-Anything-V2.git](https://github.com/DepthAnything/Depth-Anything-V2.git)
Download Weights: Place the Depth-Anything-V2-Large weights under Depth-Anything-V2/checkpoints/.

Generate Depth Maps:

Bash
python Depth-Anything-V2/run.py --encoder vitl --pred-only --grayscale --img-path <path_to_input_images> --outdir <output_path>
Generate depth_params.json:
Use the provided utility script to scale the depth:

Bash
python utils/make_depth_scale.py --base_dir <path_to_colmap> --depths_dir <path_to_generated_depths>
Usage
Training
Start the training process by specifying the source data and output model path:

Bash
python train.py -s <dataset_path> -m <model_path> -r <factor>
Rendering
To render images from a trained model:

Bash
python render.py -m <model_path>
Evaluation
To evaluate the quality (PSNR, SSIM, LPIPS) of the reconstruction:

Bash
python metrics.py -m <model_path>


