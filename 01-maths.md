# Stage 1: Maths

**Start here:** [Immersive Linear Algebra](https://immersivemath.com/ila/index.html)

Robots describe where things are, how they are rotated and how they move using vectors and matrices, so linear algebra is the language of everything else in this course. The repositories below let you practise that language in code, which is the fastest way to make it stick. Read a chapter of the interactive book, then reproduce its main idea in a short Python script.

## Repositories to learn from

### [3b1b/manim](https://github.com/3b1b/manim)
This is the animation engine behind the 3Blue1Brown videos. Learning to draw a matrix transformation as a moving grid is a great way to test whether you really understand what a matrix does.

### [fastai/numerical-linear-algebra](https://github.com/fastai/numerical-linear-algebra)
A set of notebooks from a practical numerical linear algebra course. It focuses on how the maths behaves on a real computer, including precision, speed and decompositions, which matters as soon as you solve for joint angles or estimate a state.

### [mitmath/matrixcalc](https://github.com/mitmath/matrixcalc)
Course material on matrix calculus from MIT. Jacobians and gradients appear in inverse kinematics, state estimation and learning, so this is worth returning to in later stages.

### [numpy/numpy](https://github.com/numpy/numpy)
The array library that every Python robotics tool is built on. Read its source for the basic operations once you are comfortable using them.

### [scipy/scipy](https://github.com/scipy/scipy)
Optimisation, rotations, interpolation and linear algebra routines. You will use `scipy.spatial.transform` for rotations and `scipy.optimize` for numerical inverse kinematics.

### [sympy/sympy](https://github.com/sympy/sympy)
A symbolic maths library. Use it to derive the equations of a two-link arm by hand-style algebra and then check your answer.

### [AllenDowney/ThinkBayes2](https://github.com/AllenDowney/ThinkBayes2)
A gentle, code-first introduction to probability and Bayesian thinking. It prepares you for the Kalman filter in Stage 5, which is Bayesian reasoning with Gaussians.

## What to be able to do before moving on

You should be able to multiply matrices and explain what the result means geometrically, build a 2D and 3D rotation matrix, explain what an eigenvector is, and compute a derivative of a vector function. If you can rotate a point by 30 degrees with a matrix in NumPy and verify it by hand, you are ready.

## Trending and most-starred additions (checked 25 Nov 2026)

Star counts below are approximate figures reported by public aggregator pages on 25 Nov 2026, so treat them as a rough guide to popularity, not exact numbers. Entries without a count had no figure in the pages I could reach. Links not marked as checked are from memory, so confirm they open.

Robot-specific maths repositories are not where the big star counts are, so this stage is mostly served by general learning lists. The two I would add are [kenjihiranabe/The-Art-of-Linear-Algebra](https://github.com/kenjihiranabe/The-Art-of-Linear-Algebra), a set of graphic notes based on Gilbert Strang's *Linear Algebra for Everyone*, and [rossant/awesome-math](https://github.com/rossant/awesome-math), a list of maths resources for machine learning that includes books, tutorials and videos. For a ranked view of what is popular across robotics generally, the [OSSInsight robotics collection](https://ossinsight.io/collections/robotics) ranks the top GitHub robotics repositories by stars and activity.
