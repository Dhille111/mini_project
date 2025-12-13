# Pneumonia Detection from Chest X-Rays (Mini Project)

This is a small Flask app and training script for detecting pneumonia from chest X-ray images using a ResNet-18 model (PyTorch).

**Contents**
- `app.py` — Flask web app for uploading an X-ray and getting a prediction.
- `main.py` — Training script that fine-tunes a ResNet-18 and saves `pneumonia_model.pth`.
- `pneumonia_model.pth` — (Committed) model weights used by `app.py`.
- `Dataset/` — expected dataset layout (train/val/test with `NORMAL` and `PNEUMONIA` subfolders).

**Prerequisites**
- Python 3.8+
- Git (optional)

**Install dependencies**
1. Upgrade pip:

```powershell
python -m pip install --upgrade pip
```

2. Install non-PyTorch dependencies from `requirements.txt`:

```powershell
python -m pip install -r requirements.txt
```

3. Install PyTorch (choose the correct wheel for your machine):

- CPU-only (Windows):

```powershell
python -m pip install torch torchvision --index-url https://download.pytorch.org/whl/cpu
```

- GPU (example CUDA 11.8) — change `cu118` to match your CUDA version:

```powershell
python -m pip install torch torchvision --index-url https://download.pytorch.org/whl/cu118
```

**Run the web app**

```powershell
python app.py
```

Open `http://127.0.0.1:5000/` in your browser and upload an X-ray image.

**Training**
- Edit `main.py` to point `data_dir` at your dataset (default expects `dataset/train`, `dataset/val`).
- Run `python main.py` to train and produce `pneumonia_model.pth`.

**Notes and tips**
- `pneumonia_model.pth` is loaded directly by `app.py`. If you replace or retrain the model, ensure the architecture matches (ResNet-18 with `model.fc` adjusted for 2 classes).
- The `static/uploads/` folder currently contains example images; if you want to avoid committing uploaded images to Git, add them to `.gitignore` and remove them from the repo.

**License**
- This repository has no explicit license file. Add one if you plan to share publicly.

If you want, I can also:
- Add a `.gitignore` that excludes `static/uploads/`.
- Pin exact dependency versions in `requirements.txt` for reproducibility.
