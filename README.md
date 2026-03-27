# Enhance-3D-Gaussian-Splatting-for-Dynamic-Scenes-Integrating-Semantic-and-Geometric-Consistency
Source code for "Enhancing 3D Gaussian Splatting for Dynamic Scenes: Integrating Semantic and Geometric Consistency"
Installation
git clone https://github.com/deream-king/E3DGS-SGC.git
cd E3DGS-SGC
conda env create --file environment.yml
conda activate E3DGS-SGC
Install submodules
pip install submodules\diff-gaussian-rasterization
pip install submodules\simple-knn
We use depth as an additional feature to identify moving objects.
For real world datasets depth maps should be generated for each input images, to generate them please do the following:
Clone Depth Anything v2:
git clone https://github.com/DepthAnything/Depth-Anything-V2.git
Download weights from Depth-Anything-V2-Large and place it under Depth-Anything-V2/checkpoints/
Generate depth maps
python Depth-Anything-V2/run.py --encoder vitl --pred-only --grayscale --img-path <path to input images> --outdir <output path>
Generate a depth_params.json file using:
python utils/make_depth_scale.py --base_dir <path to colmap> --depths_dir <path to generated depths>
Running
python train.py -s <dataset path> -m <model path> -r <factor>
Rendering
python render.py -m <model path>
Eval
python metrics.py -m <model path>




