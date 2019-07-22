# BCRYExporter
This is ported version of BCRYExporter for Cryengine 5 from https://github.com/AFCStudio/BCRYExporter for Blender 2.80
 
<b>Installation:</b>
Copy `io_bcry_exporter` folder to blender_path\Scripts\Addons directory.

<b>Example:</b> C:\Users\%Your_User_Name%\AppData\Roaming\Blender Foundation\Blender\2.80\scripts\addons

<b>Documentation:</b> maybe soon

<b>Tested:</b>
1) Export static geometry (support box, sphere, capsule, cylinder and not a prim collision types)
2) Export skeleton, skeleton radgoll, skin, chr.
3) Export animation through Limit with Values
4) All other utilities (Export, configuration, bone utilities, mesh utilities, material utilities, UDP)

<b>Not tested but must work:</b>
1) Export breakable joint and branch, but all errors in operators was fixed.

<b>What's new:</b>
1) Now you can add collision object to selected objects (not only for active)
2) Add "not a prim collision" (cryengine see it as a mesh collision. Recommended use less than 256 vertices and convex hull, but concave support too)
3) Blender 2.80 has new type of grouping objects instead layer and group - Collection. Now when you create export node, BCRY exporter create cry_exporter_nodes collection. All export nodes inside this collection are exported when you call export.

<b>Menu</b>: Blender 2.80 has Quick Favorite menu which called by "Q" key. But there is not way to add to quick favorite from python code. I added this menu in Configuration section. You can do right mouse click on them and set "Add to Quick favorite".

<b>About Notaprim collision</b>: Now when you click to create notaprim - blender will create the same "wired" box. You must delete this box in edit mode and add any mesh which you want to be a collision (as example a separate part from original object). In future I will update pipeline of this button.

<b>Known issues/limitation:</b>
1) Custom split normal doesn't support Sharp edges in skin node. <br> <b>Solution:</b> Add Edge split modifier before Armature modifier, set up and apply. The skin mesh will be rip in Sharp edges places.
2) There is no way to set active any collection, so be careful that current active collection be unhide and not disable. Otherwise you can expect Error that Object is Null. I put in some operators code which set Master collection(Scene Collection) active.
3) In some cases as add bones through edit_bones.new() method or other way modification of the armature it will be export armature with broken bones hierarchy. I think that is Blender bug because I nothing changed in export code except fix errors with Bmesh convertation. <br> <b>Solution:</b> I added a button in Bone utilities: Rebuild-armature. It rebuild selected armature from zero and copy all bones parameters: name, matrix, roll, parent, some properties and custom properties then delete old bones. It don't copy bone constraints at the moment.<br> <b>IMPORTANT:</b> vertex groups renames too, but only if the object is a children of this armature. Do skin object a child of armature before use this button.

Enjoy.
