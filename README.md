# University Bus Transportation System Simulation

A multi-threaded simulation of a bus system transporting students between stops and university, with department-based capacity constraints.

## Features

- **Multi-threaded Architecture**:
  - Dedicated thread for bus operations
  - Separate thread for each student
- **Queue Management**:
  - FIFO queues for Stop A, Stop B, and Bus
  - Array-based storage for University
- **Department-based Capacity Control**:
  - Limits on students per department on the bus
  - Overall bus capacity constraints
- **Synchronization**:
  - Mutex locks for shared resource protection
  - Semaphores for thread coordination
- **Real-time Status Display**:
  - Continuous printing of student locations
  - Detailed student information (AM, department)

## Building and Running

1. Compile the program:
   ```bash
      make
   ```
2. Run
   ```bash
     ./bus_simulation
   ```
## Key Functions

### Thread Functions
- `bus_thread`: Manages bus routing and student transportation  
- `student_thread`: Handles individual student journeys  

### Queue Operations
- `addLocation`: Adds student to specified location (`STOP_A`, `BUS`, etc.)  
- `removeLocation`: Removes student from specified location  
- `removeStudentFromUni`: Special removal from university array  

### Utility Functions
- `initialize_students`: Creates student threads with random attributes  
- `printStops`: Displays current system state  
- `get_student_department`: Converts department enum to string  

---

## Simulation Flow

### Initialization
- Create specified number of student threads  
- Initialize bus thread  
- All students start at Stop A  

### Going to University
- Bus picks up students from Stop A (with capacity constraints)  
- Travels to University (simulated with `sleep`)  
- Students disembark and begin studying  

### Returning Home
- After studying, students go to Stop B  
- Bus picks up students from Stop B  
- Returns to Stop A where students go home  

### Termination
- Simulation ends when all students have returned home  
- All resources are cleaned up  

---

## Configuration Constants

| Constant         | Description                            |
|------------------|----------------------------------------|
| `MAX_STUDENTS`   | Maximum number of students (200)       |
| `N`              | Bus total capacity                     |
| `DEPT_CAPACITY`  | Per-department capacity limit          |
| `T`              | Travel time between stops (in seconds) |
| `WAIT`           | Bus waiting time at stops (in seconds) |

---

## Known Issues

### Thread Blocking
- Some student threads may get stuck during sleep operations  
- Particularly occurs with high numbers of threads  

### Synchronization Challenges
- Occasional race conditions during bus boarding  
- University array management can be inconsistent  

### Memory Management
- Potential memory leaks if simulation terminates unexpectedly  
   
