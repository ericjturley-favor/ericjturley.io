# Tips for Code Clarity

## What is appDeployMap here?
![image](https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/c4ff28bf-7184-41cf-93ae-7c6f83aedf2b)

## IDEA can tell us the type
Have it specify it explicitly.  
Also, in the preview, it shows you what you get.
![image](https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/bec70a50-93b5-46e6-8f4b-458e69b81099)

Turns out, it's not actually a `Map`, but a `Map.Entry`.  
That's good to know.

## But an Entry of what?
Looks like the `Entry.Key` came from the previous `groupBy` block.

![image](https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/867f215d-8569-46c1-889e-25e7494a0c1f)

And that was ... an Argo name of some kind.

OK, let's rename it to `argoDeploymentsEntry` for now, to help us understand what we're looking at.

## What do I do with a Map.Entry<String, List\<Deployment>> ?
This is a slightly confusing type. It adds to my "congitive load."   
Can I add some clarity by understanding what this type represents?

YES!

Let's create a "type alias". IDEA can help...

![image](https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/414d2d4c-2894-4731-a360-75932fcf5368)

## TypeAlias

This gives our brain a simpler concept to wrap around:

    typealias AppDeployments = Map.Entry<String, List<Deployment>>

Now that I see it, I see that `appDeployMap` wasn't far off.  
Let's rename again with our new understanding:  
![image](https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/bcc79f31-ce8e-44ee-8655-9f5f21ec92ef)
