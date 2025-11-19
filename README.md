# GAME_PROGRAM-EX--7
# To create an AI character in Unreal Engine that roams randomly within a NavMesh area and chases
# Aim
the player when they come within a certain range, using Behavior Trees, Blackboard, and AI Perception.

# STEPS
1. Setup Navigation Add a NavMeshBoundsVolume to your level and scale it to cover the roamable area. Press P to confirm the green nav area is visible (indicating navigable space).

2. Create AI Character Create a Blueprint character (e.g., BP_AIEnemy ) with a skeletal mesh and AIController class. Create an AI Controller Blueprint (e.g., BP_AIController ) and assign it to the character.

3. Enable AI Perception In BP_AIController , add an AIPerception component. Configure a Sight sense (set detection range, lose sight range, peripheral vision angle). Bind OnPerceptionUpdated to update a blackboard value (e.g., CanSeePlayer and PlayerActor ).

4. Set Up Blackboard Create a Blackboard with the following keys: TargetLocation (Vector) PlayerActor (Object) CanSeePlayer (Bool)

5. Create Behavior Tree (BT_AI) Structure it like this: AI Random Roam with Chase - Unreal Engine 🎯 Aim

# Procedure
Root Selector
Sequence (Chase Player)
Blackboard Check: CanSeePlayer == truTask: Find Random Location → TargetLocation Move To: TargetLocation

6.Custom Task: Find Random Location Create a new BTTask_BlueprintBase to get a random reachable point using: Set the result to the TargetLocation blackboard key.

7.Test the AI Add a player character to the level. Place the AI enemy in the map and assign its controller and behavior tree. Press Play: the AI should roam when the player is far and chase the player when within sight. UNavigationSystemV1::GetRandomReachablePointInRadius()

# Output

<img width="561" height="285" alt="516193450-4aa59b7d-88a7-4456-b172-7013ec853b64" src="https://github.com/user-attachments/assets/1061e88a-ebaa-4f2d-b836-5df131b7bd1e" />

<img width="560" height="234" alt="516193630-1e9f28ae-57bd-41cd-a183-6ca905dcd63a" src="https://github.com/user-attachments/assets/2aa1db70-6a3e-46df-b3e8-d3b49a4492b1" />

<img width="557" height="214" alt="516193882-c9683673-5589-47fb-9540-dc747628401f" src="https://github.com/user-attachments/assets/514a42bd-0054-44ce-8873-50fea894f14e" />

The AI character roams randomly within a defined area. When the player enters its sight range, the AI stops roaming and begins to chase the player until the player is out of sight, after which it resumes roaming.

# Result
The AI character roams randomly within a defined area. When the player enters its sight range, the AI stops roaming and begins to chase the player until the player is out of sight, after which it resumes roaming.
