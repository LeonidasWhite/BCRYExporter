# BCRYExporter
This is ported version of BCRYExporter for Cryengine 5 from https://github.com/AFCStudio/BCRYExporter for Blender 2.80
 
<b>Installation:</b>
Copy `io_bcry_exporter` folder to blender_path\Scripts\Addons directory.

<b>Example:</b> C:\Users\ `Your_User_Name` \AppData\Roaming\Blender Foundation\Blender\2.80\scripts\addons

<b>Documentation:</b> maybe soon

<b>Tested:</b>
1) Export static geometry (support box, sphere, capsule, cylinder and mesh collision types). (see example)
2) Export usual and custom normal shading for objects. (see example)
3) Export skeleton(chr), skeleton radgoll settings, skin.
4) Export Animated Mesh (CGA) with single or multiple animations. (see example)
5) Export branch for touch vegetation. (see example)
6) Export animation through Limit with Values.
7) All other utilities (Export, configuration, bone utilities, mesh utilities, material utilities, UDP).

<b>Not tested but must work:</b>
1) Export breakable joint

<b>What's new:</b>
1) Now you can add collision object to selected objects (not only for active)
2) Add "Mesh collision" (Recommended use less than 256 vertices and convex hull shape, but concave support too)
3) Blender 2.80 has new type of grouping objects instead layer and group - Collection. Now when you create export node, BCRY exporter create cry_exporter_nodes collection. All export nodes inside this collection are exported when you call export.

<b>Menu</b>: Blender 2.80 has Quick Favorite menu which called by "Q" key. But there is not way to add to quick favorite from python code. I added this menu in Configuration section. You can do right mouse click on them and set "Add to Quick favorite".

<b>About Mesh collision</b>: Now when you click to create Mesh button (in Cry Utilities):
In Object Mode:
1) Will be create the same mesh with wire display type. You can use separate checkbox in advanced options menu to separate new mesh into loose parts. (Multiple selected objects support)
In Edit mode:
1) Blender now supports multiedit by core. You can select many objects and change mode to EDIT. Then you can select through link (key 'L') a part of this mesh and click Mesh button to separate selected part as a mesh collision. Multiple selected meshes supports too. The current mode state will be save. The objects without selected vertices will be ignored.

<b>Known issues/limitation:</b>
1) Custom split normal doesn't support Sharp edges in skin node. <br> <b>Solution:</b> Add Edge split modifier before Armature modifier, set up and apply. The skin mesh will be rip in Sharp edges places.
2) There is no way to set active any collection, so be careful that current active collection be unhide and not disable. Otherwise you can expect Error that Object is Null. I put in some operators code which set Master collection(Scene Collection) active.
3) In some cases when you modify the armature as add bones through edit_bones.new() method or other way BCRYExporter will be export armature with broken bones hierarchy. I think that is Blender bug because I nothing changed in export code except fix errors with Bmesh convertation. <br> <b>Solution:</b> I added a button in Bone utilities: Rebuild-armature. It rebuild selected armature from zero and copy all bones parameters: name, matrix, roll, parent, some properties and custom properties then delete old bones. It don't copy bone constraints at the moment.<br> <b>IMPORTANT:</b> vertex groups renames too, but only if the object is a children of this armature. Do skin object a child of armature before use this button.

Enjoy.
