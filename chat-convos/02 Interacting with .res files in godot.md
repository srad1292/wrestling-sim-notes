>input
>In godot, is it possible to query .res files.  For example, Let's say you had a .res file for a wrestler named 'bob'.  Let's say you had .res files for each championship like 'tag title', 'world title', 'intercontinental title', and 'hardcore title'.  Each title would have an array of events like 'wrestler A lost to wrestler B'.  Would it be possible to find any title .res file that references wrestler 'bob'

Yes, it is possible to query .res files in Godot. [One way to do this is to use the ResourceLoader class](https://docs.godotengine.org/en/stable/classes/class_resourceloader.html)[1](https://docs.godotengine.org/en/stable/classes/class_resourceloader.html), which can load resources from the res:// path. You can use the ResourceLoader.exists() method to check if a resource exists for a given path, and the ResourceLoader.load() method to load the resource into memory. For example, you could write something like this in GDScript:

```gdscript
# Define the paths to the wrestler and title resources
var wrestler_path = "res://wrestlers/bob.res"
var title_paths = ["res://titles/tag_title.res", "res://titles/world_title.res", "res://titles/intercontinental_title.res", "res://titles/hardcore_title.res"]

# Check if the wrestler resource exists and load it
if ResourceLoader.exists(wrestler_path):
    var wrestler = ResourceLoader.load(wrestler_path)
else:
    print("Wrestler resource not found")

# Loop through the title resources and check if they reference the wrestler
for title_path in title_paths:
    if ResourceLoader.exists(title_path):
        var title = ResourceLoader.load(title_path)
        # Assume that the title resource has an array of events as a property
        var events = title.events
        # Loop through the events and check if they contain the wrestler's name
        for event in events:
            if wrestler.name in event:
                print("Title %s references wrestler %s" % [title.name, wrestler.name])
    else:
        print("Title resource not found")
```

This code will print out any title that references the wrestler ‘bob’ in its events array. You can modify this code to suit your needs and logic. I hope this helps you with your project. 😊



> Input 
> Is it possible to load each resource in "res://titles" without specfifying individual files?

Yes, it is possible to load each resource in “res://titles” without specifying individual files. [You can use the Directory class](https://ask.godotengine.org/5175/how-to-get-all-the-files-inside-a-folder)[1](https://ask.godotengine.org/5175/how-to-get-all-the-files-inside-a-folder) to list all the files in a folder and filter them by extension. For example, you could write something like this in GDScript:

```gdscript
# Define the path to the titles folder
var titles_path = "res://titles"

# Create a Directory object
var dir = Directory.new()

# Open the titles folder
if dir.open(titles_path) == OK:
    # List all the files in the folder
    dir.list_dir_begin()
    var file_name = dir.get_next()
    while file_name != "":
        # Check if the file name ends with .res
        if file_name.ends_with(".res"):
            # Load the resource from the file
            var title = ResourceLoader.load(titles_path + "/" + file_name)
            # Do something with the title resource
            print(title.name)
        # Get the next file name
        file_name = dir.get_next()
else:
    print("Failed to open titles folder")
```

This code will print out the name of each title resource in the “res://titles” folder. You can modify this code to suit your needs and logic. I hope this helps you with your project. 😊


> Input
> Going back to your first answer.  Is loading and searching a bunch of .res files slower than using sqlite in godot?

That’s a good question. The answer may depend on several factors, such as the size and complexity of the data, the frequency and type of queries, and the performance of the device running the game. In general, SQLite is a fast and reliable database engine that can handle large amounts of data efficiently. It also offers many features and options to customize and optimize the queries. On the other hand, loading and searching .res files may be simpler and more convenient, especially if the data is not very large or complex, and does not change frequently. However, it may also be slower and less flexible than using SQLite, as it requires loading the entire resource into memory and iterating over its properties.

To compare the two methods more precisely, you may need to do some benchmarking and testing with your own data and queries. You can also check out some tutorials and examples of using SQLite in Godot, such as or . You can also read more about resources in Godot in or . I hope this helps you with your project. 😊


> Input
> One more questions.  If I were to include a dictionary in a .res file, do I benefit from keeping the key names as short as possible?

That’s a good question. The answer may depend on how you are using the dictionary in your .res file. If you are only accessing the dictionary values by their keys, then the length of the key names should not matter much, as long as they are unique and consistent. However, if you are iterating over the dictionary keys or values, or converting the dictionary to a string, then the length of the key names may affect the performance and memory usage of your game. In general, shorter key names will result in smaller strings and faster iteration, while longer key names may provide more readability and clarity. You may want to balance these trade-offs depending on your needs and preferences.

You can read more about dictionaries in Godot in or . I hope this helps you with your project. 😊


>Input 
>So the key names don't effect the size of the .res file itself?

The key names may affect the size of the .res file itself, but not by much. The .res file format is a binary format that stores the resource data in a compact and efficient way. The key names are stored as strings, which are encoded using UTF-8. This means that each character in the key name takes up one byte, unless it is a special character that requires more bytes. For example, the key name “name” would take up 4 bytes, while the key name “名前” would take up 6 bytes. However, the size of the .res file also depends on the type and value of the resource data, which may take up much more space than the key names. For example, an image resource may take up several kilobytes or megabytes, depending on its resolution and compression.

[You can check the size of your .res files by looking at their properties in your file manager, or by using the OS.get_file_size() method in GDScript](https://docs.godotengine.org/en/stable/tutorials/io/data_paths.html)[1](https://docs.godotengine.org/en/stable/tutorials/io/data_paths.html). You can also compare the size of your .res files with other formats, such as JSON or SQLite, to see which one is more suitable for your needs. You can read more about the .res file format in or . I hope this helps you with your project. 😊
