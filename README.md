# Coordinator Protocol in Swift
In the iOS world, specially since Swift protocols, the coordinator pattern has become more and more popular. 

The Coordinator Pattern decouples totally the flow from the ViewControllers to a Coordinator. This coordinator handles the inputs and outputs of each ViewController, and knows how the app should react to user interaction within those ViewControllers. 

## Why
- Decouples flow from ViewControllers
- More reusability for ViewControllers
- More structured code
- Easier to modify, update or delete flows
- Deeplinks way (really) easier

## Why not
- StoryBoards and Coordinators doesn't do well

## How
- Each Coordinator should control one part of the flow. 
- Each ViewController should have a `delegate`, implemented by the Coordinator. This is should be the only way the ViewController can communicate outside
- If a flow is too big, you should split it with multiple Coordinators. Remember to store them in the `nextCoordinator` property.
- Only one flow should be active at a time - and it's predecessors - (only in special cases such as tabs multiple Coordinators would be alive)
- Do not use the Coordinator as some sort of information container (do not use the Coordinator as a singleton!). When possible, avoid storing temporary information in the Coordinator. 

## Example

In the `AppDelegate` `didFinishLaunchingWithOptions`:

```
let navController = UINavigationController()
appCoordinator = AppCoordinator(navigationController: navController)

window!.rootViewController = navController
window!.makeKeyAndVisible()

DispatchQueue.main.async {
  appCoordinator.start()
}
```





