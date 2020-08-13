# Modding game code  
This is done in a similar way to enabling the console, and as such I will not get into the basics here; if you need more detailed guide, check notes on the console.  

**Short note on distributing modified assemblies:**  
Whether it is ethical or legal is a matter for another discussion. However, one reason against this is the fact that modding code is generally incompatible with game updates. If you swap `Assembly-csharp.dll` for a modded version you've grabbed off somewhere, there is a huge chance it will break the game. Delta-patching is an alternative, but many users may (and *should*) be wary against such patches from unknown sources.
  
Here I will describe how I made specific mods.

**Requirements:** dnSpy (or another C# decompiler)
  
---
### Armature stays dead after hitting it  
**Path:**
  
```
Assembly-CSharp (0.0.0.0) -> Assembly-CSharp.dll ->
Gameplay.GameControllers.Enemies.GoldenCorpse.AI ->
GoldenCorpseBehaviour
```
  
**Method:**
  
```
OnUpdate()
```
**Original code:**  
  
```
public override void OnUpdate()
{
	base.OnUpdate();
	this.GoldenCorpse.Status.CastShadow = (!this.isNapping && this.isAwake);
	if (this.isAwake && this.isNapping)
	{
		this.sleepTime -= Time.deltaTime;
		if (this.sleepTime < 0f)
		{
			this.isNapping = false;
			this.ReAwaken();
		}
	}
}
```  
**Modified code:**  
  
```
public override void OnUpdate()
{
	base.OnUpdate();
	this.GoldenCorpse.Status.CastShadow = (!this.isNapping && this.isAwake);
	if (this.isAwake && this.isNapping)
	{
		return;
	}
}
```  
