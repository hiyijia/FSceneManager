FSceneManager
=============

SceneManager for Futile, a Unity framework.

todo
-------------

- [ ] Transitions have been added. Could always make more!
- [ ] Tilemap stuff removed. May return as its own lib.


methods
-------------
FSceneManager.Instance.SetScene(); Sets the new scene passed as the only scene in the stack.
FSceneManager.Instance.PushScene(); Pushes a new scene onto the stack.
FSceneManager.Instance.PopScene(); Removes the last scene added from the stack.
FSceneManager.Instance.RemoveScene(); Removes a specific scene from the stack.



how-to example
-------------

[Game].cs (This is your main .cs file that loads Futile)
```csharp
FSceneManager.Instance.SetScene( new SceneGame() );
```

SceneGame.cs
```csharp
using System;
using UnityEngine;
using System.Collections;
using System.Collections.Generic;

public class SceneGame : FScene
{
	public SceneGame() : base()
	{
		Name = "Game";

		mTransitionOn = new FTransitionSlideIn(this, 0.5f, FTransitionDirection.Down);
		mTransitionOff = new FTransitionSlideOut(this, 0.5f, FTransitionDirection.Left);
	}

	public override void HandleEnter()
	{

	}

	public override void HandleUpdate()
	{
		if( mState != FSceneState.Active )
			return;


	}

	override public void HandleMultiTouch( FTouch[] touches )
	{
		if( mState != FSceneState.Active )
			return;
		
		foreach( FTouch touch in touches )
		{
			// Where was the screen touched
			//Vector2 touchPos = this.GlobalToLocal(touch.position);
			
			if( touch.phase == TouchPhase.Began )
			{
//				FSceneManager.Instance.SetScene( new SceneTest() );
//				FSceneManager.Instance.PushScene( new SceneTest() );
			}
			else if( touch.phase == TouchPhase.Moved )
			{
				
			}
			else if( touch.phase == TouchPhase.Ended )
			{
				
			}
		}
	}
}
```


Thanks
-------------

- @MattRix [https://github.com/MattRix] - Awesome Futile framework
- @ironpencil [https://github.com/ironpencil] - Idea's on how to improve FSceneManager
- @jfleschler [https://github.com/jfleschler] - Code to load Tilemap Atlases
