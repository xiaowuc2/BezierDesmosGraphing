<p align="center">
  <a href="https://www.youtube.com/channel/UCX7oe66V8zyFpAJyMfPL9VA">
    <img src="https://github.com/xiaowuc2/xiaowuc2/blob/master/source/SHM/shm%203.png" alt="Logo" width="250" height="250">
  </a>
  <h3 align="center">Bézier Desmos Graphing</h3>
  <p align="center">
    Plotting image/video in Desmos Graphing Calculators using Bézier Curve
      <br />
    <br>
  </p>
</p>

[![GitHub](https://img.shields.io/static/v1.svg?label=Collaborators&message=1&color=success&logo=github&style=social)](https://github.com/qxresearch/Simple-Harmonic-Motion/graphs/contributors)
[![YouTube](https://img.shields.io/static/v1.svg?label=YouTube&message=@qxresearch&color=grey&logo=youtube&style=flat&logoColor=white&colorA=critical)](https://www.youtube.com/channel/UCX7oe66V8zyFpAJyMfPL9VA)
  [![LinkedIn](https://img.shields.io/static/v1.svg?label=LinkedIn&message=xiaowuc2&color=success&logo=linkedin&style=flat&logoColor=white&colorA=blue)](https://www.linkedin.com/in/xiaowuc2)
  [![Quora](https://img.shields.io/static/v1.svg?label=Quora&message=85.5k+views&color=white&logo=quora&style=social)](https://www.quora.com/profile/Rohit-Prasan-Mandal)
    <a href="https://github.com/qxresearch/Simple-Harmonic-Motion/pulse" alt="Activity">
        <img src="https://img.shields.io/github/commit-activity/m/badges/shields" /></a>

### Sample
![](github/sample.png)

### Result
![](github/result.png)

## Setup
Install dependencies
```sh
apt update
apt install git python3-dev python3-pip build-essential libagg-dev libpotrace-dev pkg-config
```

Clone repository
```sh
git clone git@github.com:xiaowuc2/BezierDesmosGraphing.git
cd DesmosBezierRenderer
```

Install requirements
```sh
python3 -m venv env
. env/bin/activate
pip3 install -r requirements.txt
```

Create a directory called `frames` and add images named `frame%d.png` where `%d` represents the frame-number starting from 1. To render just a single image, add a single image named `frame1.png` in the directory. Works best with 360p to 480p resolution (may have to lower the resolution further with more complex frames). 

You can change the `DYNAMIC_BLOCK`, `BLOCK_SIZE`, and `MAX_EXPR_PER_BLOCK` constants in `backend.py` to change the number of expressions the backend will send to the frontend per call (too much will cause a memory error, too little could kill the backend with too many requests). This only really matters if you are rendering a video.
```sh
mkdir frames
...
```

Run backend (This may take a while depending on the size and complexity of the frames). Should eventually show that the server is running on `localhost:5000`.
```sh
python3 backend.py
```

Load `index.html` into a web browser and run `init()` in the developer console. The image should start rendering or the video should start playing at a slow rate.
