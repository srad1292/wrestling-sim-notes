> Input
   Can you write an example godot .res file for a wrestling move with the following key-value pairs: name="Suplex", category="Suplex", style="Throw", damage="5", difficulty="3"

```gdscript
[gd_resource type="Resource" load_steps=2 format=2]

[resource]

name = "Suplex"
category = "Suplex"
style = "Throw"
damage = 5
difficulty = 3
```



>Input
  Can you tell me what "load_step=2" and "format=2" means?

"Certainly! In a Godot `.res` file, the `load_steps` property specifies the number of steps required to load the resource. [The value of `2` indicates that the resource is loaded in two steps: first, the resource is loaded into memory, and then it is initialized](https://docs.godotengine.org/en/stable/tutorials/scripting/resources.html) [1](https://docs.godotengine.org/en/stable/tutorials/scripting/resources.html).

The `format` property specifies the version of the `.res` file format used to store the resource. [The value of `2` indicates that the resource is stored in the Godot 3.x format](https://docs.godotengine.org/en/stable/tutorials/scripting/resources.html) [1](https://docs.godotengine.org/en/stable/tutorials/scripting/resources.html).

I hope this helps clarify what these properties mean!"


>Input 
  One more questions. Let's say I then create a Wrestler resource. His name would be "Bob". How would I create a list of moves that "Bob" knows which link to multiple resource files like the one you created for the suplex move

"To create a list of moves that “Bob” knows, you can use a `Dictionary` resource in Godot. A `Dictionary` is a collection of key-value pairs, where each key is unique and maps to a value. In this case, you can use the name of each move as the key and the corresponding `.res` file as the value.

Here’s an example of how you can create a `Dictionary` resource for Bob’s moves:"

```gdscript
[gd_resource type="Dictionary" load_steps=2 format=2]

[resource]

moves = {
    "Suplex": preload("res://suplex.res"),
    "Armbar": preload("res://armbar.res"),
    "Chokeslam": preload("res://chokeslam.res")
}

```

"This file defines a new `Dictionary` resource with three keys: `"Suplex"`, `"Armbar"`, and `"Chokeslam"`. Each key maps to a `.res` file that defines the corresponding move.

You can then load this resource in your game and access Bob’s moves using the `moves` property. For example, to get the `Suplex` move, you can use:"

```gdscript
var suplex = $Bob.moves["Suplex"]
```


> Input
> One last question. Let's say in the game, the user decides to add the move "Legdrop" to the list of moves that "Bob" knows. How would I do that in gdscript

```gdscript
var legdrop = preload("res://legdrop.res")
$Bob.moves["Legdrop"] = legdrop
```


> Input
> I've been looking into using .res aka resource files in Godot for every wrestler, move, etc in a game.  Is there a number where the amount of resource files begins to hurt performance or memory?

When it comes to using resource files in Godot, there is no specific number that can be considered as a threshold for hurting performance or memory. However, it is important to note that the more resources you have, the more memory they will consume. This can lead to longer loading times and higher memory usage.

[Godot’s documentation suggests that you should **only load resources when they are needed** and **unload them when they are no longer needed**](https://docs.godotengine.org/en/stable/tutorials/scripting/resources.html) [1](https://docs.godotengine.org/en/stable/tutorials/scripting/resources.html). This can help reduce memory usage and improve performance.

[Additionally, Godot 4.0 introduces a new feature called **Custom Resources** which allows you to create your own resource classes](https://docs.godotengine.org/en/stable/tutorials/scripting/resources.html) [2](https://ezcha.net/news/3-1-23-custom-resources-are-op-in-godot-4). This can help you organize your resources more efficiently and reduce the number of files you need to manage.

I hope this helps!