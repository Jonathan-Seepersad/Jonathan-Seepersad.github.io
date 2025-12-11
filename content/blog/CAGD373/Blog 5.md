---
title: "Blog 5"
description: ""
date: 2025-12-10T17:51:48-08:00
image: 
math: 
toc: true
license: false
hidden: false
comments: true
keywords: []
draft: false
---

Not a whole lot of new features came from me this sprint. We happened to have two git branches that people were working on, and when it came time to merge them, we found a couple conflicts. The problem here though is that with Unreal, almost all source files are binary and our git tools don't know how to create diffs of these files. So the result is that it chooses to keep one file and destroys the other, whereas a conflict with text files allow you to accept and reject specific snippets in a file instead.

To solve this issue, I cloned the repository twice (for each branch we are trying to merge), duplicated the problematic files in one project, then migrated them to the other. Once both versions of the files are in the project, I can use Unreal's built in diff tool to see how to merge features from both  object *manually*. Finally I copy over the cooresponding features, delete the duplicate objects, and complete the merge successfully.

-----

Another problem I had to overcome, I realized someone accidentally reimported the model assets in our project (Unreal likes to ask way too often). This caused things like stairs and ramps to lose the custom physics shapes they initially had, causing the player to have trouble walking on them properly. This was solvable once I realized how to revert the changes of specific files to a previous commit.

Makes me realize and appreciate just how powerful Git is... once you know how to use it that is.

-----

Finally, I had to make sure I got in at least one feature. So I tried making (or at least start making) the inventory menu. I don't have a whole lot of requirements for the inventory menu, so I just made sure it:

1. pauses the game
2. displays an icon of all items the player has
3. resumes the game on exit

And so far, it seems to accomplish these goals (but doesn't do much more than that yet). Next steps might be to make the icons look nicer (I just imported the models into blender, created a simple render, then added a white border in Affinity), add text labels to them, and maybe make it so you can click on the items.

{{< video
    src="/blog/CAGD373/Inventory.webm" >}}