<div align="center">

# Tracking with Graph Neural Networks
![](profile/assets/banner.jpg)

</div>

[Charged particle tracking][tracking-wiki] reconstructs the trajectories ("tracks") of elementary particles traveling through a detector.
This task is different from many other problems that involve trajectories:

* there are several thousand particles that need to be tracked at once,
* there is no time information (the particles travel too fast),
* we do not observe a continuous trajectory but instead only around five points ("hits") along the way in different detector layers.

The task can be described as a combinatorically very challenging "connect-the-dots" problem, essentially turning a cloud of points (hits) in 3D space into a set of O(1000) trajectories.
Expressed differently, we must identify which hits belong to the same particle.

Unlike traditional tracking algorithms that are built around [Kalman filters][kalman], this project uses [graph neural networks][gnn-wiki] for significant increases in speed.

<details>
  <summary>Turning tracking into a machine learning task (click me)</summary>

  A conceptually simple way to turn tracking into a machine learning task is to create a fully connected graph of all points and then train an edge classifier to reject any edge that doesn't connect points that belong to the same particle.
  In this way, only the individual trajectories remain as components of the initial fully connected graph.
  In this project, we instead explore the idea of *object condensation*, where a GNN maps all hits to a latent space, learning to place hits from the same track close to each other, such that trivial clustering can recover the hits belonging to the same tracks.

</details>

<details>
  <summary>Further reading (click me)</summary>

  * [recording of overview talk that introduces the object condensation idea](https://www.youtube.com/watch?v=HBgpOh_mW0o)
  * [tutorial notebooks][tutorials]
  * [main code][main]
  * [hyperparameter optimization package][hpo]
  * [onboarding reading list](https://github.com/gnn-tracking/gnn_tracking/wiki/Onboarding-reading-list)

</details>

[tracking-wiki]: https://en.wikipedia.org/wiki/Tracking_(particle_physics)
[tutorials]: https://github.com/gnn-tracking/tutorials
[main]: https://github.com/gnn-tracking/gnn_tracking
[hpo]: https://github.com/gnn-tracking/hyperparameter_optimization
[kalman]: https://en.wikipedia.org/wiki/Kalman_filter
[gnn-wiki]: https://en.wikipedia.org/wiki/Graph_neural_network
