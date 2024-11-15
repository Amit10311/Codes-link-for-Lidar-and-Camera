# Impact of ROS 2 Node Composition in Robotic Systems


In the context of the **ROS 2 Node Composition**, creating a library for the `publisher_node` in the `CMakeLists.txt` file allows for **reusability**, **dynamic composition**, and **performance optimization**.

### Key Reasons for Creating a Library:

1. **Node Composition**:
    - In ROS 2, nodes can be composed into a single process using the **component architecture**. This requires nodes to be built as libraries, which can then be dynamically loaded into a container process.
    - This approach reduces the overhead of inter-process communication (IPC) and improves performance by enabling **intra-process communication**.
2. **Dynamic Loading**:
    - By building the publisher node as a library, you can dynamically load and unload it at runtime without needing to restart the entire system. This is useful for flexible deployment and testing.
3. **Code Reusability**:
    - Libraries make it easier to reuse the node across multiple applications. Instead of duplicating the code for the `publisher_node`, the library can be linked in various executables or dynamically loaded environments.
4. **Separation of Concerns**:
    - Building a node as a library separates the **node logic** from the **execution context** (e.g., single-threaded, multi-threaded, or container-based). This modular approach is a best practice in ROS 2 development.
5. **Performance Optimization**:
    - When multiple nodes (e.g., a publisher and a subscriber) are combined into a single process, using libraries minimizes memory usage and latency by leveraging shared memory for communication instead of standard DDS mechanisms.
6. **Compliance with ROS 2 Best Practices**:
    - The ROS 2 framework encourages developers to implement nodes as components (libraries) to take advantage of the composition API for resource-constrained systems or when deploying complex robotic systems.

### Reference to Your Uploaded Document:

According to your uploaded file on **ROS 2 Node Composition**, using libraries supports the **dynamic composition approach**, which is crucial for resource-efficient robotic systems. It also enables developers to leverage **component containers** for runtime flexibility and performance tuning(ROS 2 Node Composition).
