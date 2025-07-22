# Self-Sorting-Bin
Code to make a waste bin that can sort on its own
This is a self-sorting trash bin I’ve been building over the summer. The goal is to use computer vision and a weight sensor to automatically decide whether an item goes to landfill or recycling — no human sorting needed.

The pipeline is split into multiple stages, each handled by a separate TensorFlow image classification model:

Landfill vs Recyclable
First, the bin decides whether the object is generally trash or recyclable. If it’s landfill, that’s it — the lid tips and the process ends there.

Bottle vs Other Recyclables
If the item is recyclable, it gets scanned again to check if it’s a bottle. This step helps catch liquids that might still be inside.

Light vs Heavy Bottle
If the item is a bottle, we classify it again to determine if it’s a light bottle or a heavy one (like a filled water bottle). Right now, this step runs on image only — later I’ll integrate it with a weight sensor to make it more accurate.

Eventually, if a bottle is heavier than it should be, it’ll be treated as landfill (to avoid liquids contaminating recycling). If it’s light, it’ll go to the recycling bin.

Everything runs on a Jetson Nano using TensorFlow, OpenCV, and a real-time camera feed. Right now, the master script handles one image at a time — I’ll add continuous classification, servo controls, and sensor integration soon.

The project still has a lot of room to grow, but it’s already up and running with decent accuracy. It’s been a grind figuring out the models, building datasets, and chaining all the logic together, but this is one of the most complete AI projects I’ve done so far. The end goal is to demo this in a real-world test environment before the end of July.

