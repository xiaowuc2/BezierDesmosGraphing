<p align="center">
  <a href="https://www.youtube.com/channel/UCX7oe66V8zyFpAJyMfPL9VA">
    <img src="https://github.com/xiaowuc2/xiaowuc2/blob/master/source/ranger-1/gff.png" alt="Logo" width="250" height="250">
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
        

### Bézier Curve

Bézier curves appear in such areas as mechanical computer aided design (CAD). They are named after P. Bézier, who used a closely related representation in Rénault's UNISURF CAD system in the early 1960s (similar, unpublished, work was done by P. de Casteljau at Citroën in the late 1950s and early 1960s). The 1970s and 1980s saw a flowering of interest in Bézier curves, with many CAD systems using them, and many important developments in their theory.

The usefulness of Bézier curves resides in their many geometric and analytical properties. There are elegant and efficient algorithms for evaluation, differentiation, subdivision of the curves, and conversion to other useful representations. Moreover, Bézier curves interpolate their end-points ( P0 and Pn), have derivatives at the end-points depending only on the first few or last few control points (e.g., B′(0)=n(P1−P0)), are invariant under affine transformations (the transformed curve is identical to the curve obtained by applying the transformation to the control points, and then calculating the resulting Bézier curve), lie in the convex hull of their control points, and oscillate no more than the piecewise linear interpolant to their control points. Bézier curves also extend to surfaces (which are even more important for design purposes, cf. Bézier surface), volumes, etc. in a natural manner. There is also a rational extension of Bézier curves that allows exact representation of conic sections. These properties and algorithms make the curves popular in areas where shape is important. In addition to CAD, examples of such areas include computer animation and font design.

<p align="center">
  <a href="https://www.youtube.com/channel/UCX7oe66V8zyFpAJyMfPL9VA">
    <img src="https://github.com/xiaowuc2/xiaowuc2/blob/master/source/ranger-1/b110460a.gif" alt="Logo">
  </a>

Bézier curves are not the only representation used in these areas. One drawback of Bézier curves is that they approximate their control points, while some designers prefer to use an interpolating representation. A larger drawback is that Bézier curves are a polynomial representation and do not have the flexibility and generality of piecewise-polynomial representations such as B- spline curves (cf. also Bézier spline; Box spline). For example, Bézier curves do not have the local control property possessed by many piecewise-polynomial representations: changing one control point of a Bézier curve affects the entire curve. Using the end-point derivative property, it is possible to join Bézier curves to obtain piecewise-polynomial curves, but doing so creates additional concerns not present in the B- spline representation.

Therefore, some CAD systems use Bézier curves and surfaces, some employ the B- spline representation or NURBS (rational B- splines), and a few use still other representations. There is actually an elegant link between B- spline and Bézier representations, since Bézier curves can be thought of as B- spline curves with all the B- spline knots clustered at the end-points of a single interval. Because of this, many algorithms for B- spline and Bézier curves and surfaces share the same general form, and many CAD systems based on B- splines or NURBS contain Bézier curves and surfaces as a special case.

A parametric polynomial defined by a degree, n, and a sequence of n+1" control points" , P0…Pn. The resulting curve is then

B(t)=∑k=0n(nk)tk(1−t)n−kPk,t∈[0,1].


### Results

<p align="center">
  <a href="https://www.youtube.com/channel/UCX7oe66V8zyFpAJyMfPL9VA">
    <img src="https://github.com/xiaowuc2/BezierDesmosGraphing/blob/main/github/sample.png" alt="Logo" width="400" height="400">
    <img src="https://github.com/xiaowuc2/BezierDesmosGraphing/blob/main/github/result.png" alt="Logo" width="400" height="400">
  </a>


### Setup

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
