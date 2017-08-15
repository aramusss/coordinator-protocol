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





