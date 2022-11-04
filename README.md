### The Ripple-Spreading Algorithm for the *k* Shortest Paths Problem in Co-Evolutionary Path Optimization

##### Reference: HU X B,ZHANG M K,ZHANG Q,et al.Co-evolutionary path optimization by ripple-spreading algorithm[J].Transportation Research:Part B,2017,106:411-432.

The k shortest paths problem aims to find the k shortest paths between two nodes in a dynamic network. 

| Variables     | Meaning                                                      |
| ------------- | ------------------------------------------------------------ |
| network       | Dictionary, {node 1: {node 2: [weight 1, weight 2, ...], ...}, ...} |
| s_network     | The network described by a crisp weight on which we conduct the ripple relay race |
| source        | The source node                                              |
| destination   | The destination node                                         |
| k             | The *k* shortest paths                                       |
| orad          | The radius of the obstacle                                   |
| ospeed        | The moving speed of the obstacle                             |
| nn            | The number of nodes                                          |
| neighbor      | Dictionary, {node1: [the neighbor nodes of node1], ...}      |
| v             | The ripple-spreading speed (i.e., the minimum length of arcs) |
| t             | The simulated time index                                     |
| nr            | The number of ripples - 1                                    |
| epicenter_set | List, the epicenter node of the i-th ripple is epicenter_set[i] |
| path_set      | List, the path of the i-th ripple from the source node to node i is path_set[i] |
| radius_set    | List, the radius of the i-th ripple is radius_set[i]         |
| state_set     | List, state_set[i] = 1, 2, or 3 means the ripple i is waiting, active, or dead |
| objective_set | List, the objective value of the traveling path of the i-th ripple is objective_set[i] |
| omega         | Dictionary, omega[n] contains all ripples generated at node n |

#### Example

![](https://github.com/Xavier-MaYiMing/The-ripple-spreading-algorithm-for-the-k-shortest-paths-in-co-evolutionary-path-optimization/blob/main/CEPO1.gif)

The first shortest path, length is 162.17650824456905.

![](https://github.com/Xavier-MaYiMing/The-ripple-spreading-algorithm-for-the-k-shortest-paths-in-co-evolutionary-path-optimization/blob/main/CEPO2.gif)

The second shortest path, length is 162.32929237033122.

![](https://github.com/Xavier-MaYiMing/The-ripple-spreading-algorithm-for-the-k-shortest-paths-in-co-evolutionary-path-optimization/blob/main/CEPO3.gif)

The third shortest path, length is 162.36920013460093.

![](https://github.com/Xavier-MaYiMing/The-ripple-spreading-algorithm-for-the-k-shortest-paths-in-co-evolutionary-path-optimization/blob/main/CEPO4.gif)

The fourth shortest path, length is 162.5219842603631.

![](https://github.com/Xavier-MaYiMing/The-ripple-spreading-algorithm-for-the-k-shortest-paths-in-co-evolutionary-path-optimization/blob/main/CEPO5.gif)

The fifth shortest path, length is 162.73900697813062.

The obstacle moves from the lower right corner to the upper right corner with radius = orad and speed = ospeed.

```python
if __name__ == '__main__':
    network, x, y = init_network()  # the grid network has 100 nodes
    s = 0  # lower left corner
    d = 99  # upper right corner
    orad = 15  # obstacle radius
    ospeed = 6  # obstacle speed
    k = 5
    print(main(network, s, d, k, x, y, orad, ospeed))
```

##### Output:

```python
{
    1: {
        'path': [0, 10, 21, 22, 32, 42, 52, 53, 63, 73, 74, 75, 86, 87, 88, 89, 99], 
        'length': 162.17650824456905
    }, 
    2: {
        'path': [0, 1, 11, 12, 23, 33, 43, 53, 63, 73, 74, 75, 86, 87, 88, 89, 99], 
        'length': 162.32929237033122
    }, 
    3: {
        'path': [0, 10, 21, 22, 32, 42, 52, 53, 63, 64, 74, 75, 86, 87, 88, 89, 99], 
        'length': 162.36920013460093
    }, 
    4: {
        'path': [0, 1, 11, 12, 23, 33, 43, 53, 63, 64, 74, 75, 86, 87, 88, 89, 99], 
        'length': 162.5219842603631
    }, 
    5: {
        'path': [0, 10, 21, 22, 23, 33, 43, 53, 63, 73, 74, 75, 86, 87, 88, 89, 99], 
        'length': 162.73900697813062
    }
}
```

