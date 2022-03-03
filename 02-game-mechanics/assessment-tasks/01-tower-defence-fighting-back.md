# 01: Game Mechanics assessment tasks - Fighting back

In this section we will set up our defence monsters to fire at the bugs as they march towards the cookie.

## Enemy health bar

First, we need to add some sort of health indicator to the enemy bugs. Drag **Enemy** from the prefabs folder onto the scene; then drag from **Images\Objects\HealthBarBackground** onto the **Enemy** in the **hierarchy** to add it as a child. Set the position for the **HealthBarBackground** to **(X:0, Y:1, Z:-4)**.

Next, select **Images\Objects\HealthBar** and ensure its **Pivot** is set to **Left**. Then add it as a child to **Enemy** in the **hierarchy** and set its position to **(X:-0.63, Y:1, Z:-5)**. Set its **X Scale** to 125.

Create a new C# script called **HealthBar** and add it as a component to the **HealthBar** Game Object. Select **Enemy** in the **hierarchy** and change its position to **(X:20, Y:0, Z:0)**. Click on the **Overrides** near the top of the Inspector and click **Apply All** to update all the prefabs.

Run the scene - you should see all the enemy bugs now with health bars above them.

Open the **HealthBar** script and add the following variables:

```csharp
public float maxHealth = 100;
public float currentHealth = 100;
private float originalScale;
```

`maxHealth` stores the enemy's maximal health points, and `currentHealth` tracks how much health remains. Lastly, `originalScale` remembers the health bar's original size. In `Start` add this line to remember the health bar's initial size:

```csharp
originalScale = gameObject.transform.localScale.x;
```