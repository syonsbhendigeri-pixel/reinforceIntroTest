import pybullet as p
import pybullet_data
import time

p.connect(p.GUI)
p.setAdditionalSearchPath(pybullet_data.getDataPath())
p.setGravity(0, 0, -10)

planeId = p.loadURDF("plane.urdf")
r2d2 = p.loadURDF("r2d2.urdf", [0, 0, 1])

arm = p.loadURDF("arm.urdf", basePosition=[0, 0, 0], useFixedBase=True)

# Let it fall to ground
for i in range(200):
    p.stepSimulation()
    time.sleep(1./240.)

while True:
    for joint in range(4):
        p.setJointMotorControl2(
            r2d2, 
            joint, 
            p.VELOCITY_CONTROL, 
            targetVelocity=10,  # increase for faster
            force=500
        )

    p.stepSimulation()
    time.sleep(1./240.)
