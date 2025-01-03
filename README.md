# Digital Camera ASIC
## 1. Introduction
We aim to design an ASIC for surveillance digital cameras, which will support edge computing for local image processing to reduce network bandwidth usage and server resources required for image processing.

The ASIC provides some features 
- Capturing images from a camera interface
- Streaming frames to a display interface.
- System programmable via a processor
- Object classification via an image processor
  
Therefore, when the Image Processor identifies frames containing relevant objects, the user can decide whether to stream those frames to the display interface via the processor.

## 2. System architecture
![image](https://github.com/user-attachments/assets/7ae09727-2edd-43bb-911c-d61b993bbd10)

### 2.1. Interface description
The system has 3 main interfaces:
| Interface | Description |
|------------|------------|
| Program port | This interface is used to load the program into the system to configure parameters of the camera controller, display controller, mode of the system, etc.|
| Camera interface | This interface is used to capture images into the system via the camera interface |
| Display interface | This interface is used to display frames via the display interface |

### 2.2. Block description
The ASIC is divided into 2 subsystems:
- Configuration subsystem
- Image Processing subsystem

#### 2.2.1. Configuration subsystem
| Block Name | Description |
|------------|------------|
| Processor | The processor block (RV32) is the system's processor, which provides users with the function to configure internal components and the mode of the ASIC.|
| MEM | The Configuration subsystem's memory |
| UART | The UART peripheral is used to load the program into the system or communicate with other devices |

#### 2.2.2. Image Processing subsystem
| Block Name | Description |
|------------|------------|
| Image Processor | The Image Processor is used to process the frames when they enter the system |
| Camera Interface | The Camera interface is used to capture the image into the system |
| Display Interface | The Display interface is used to display the image |
| DMA | The DMA is used to arbitrate between and fetch frames into the Display Interface and Image Processor |
| VMEM | The memory to store the frames from the Camera Interface |


