# BCRYExporter
This is ported version of BCRYExporter for Cryengine 5 from https://github.com/AFCStudio/BCRYExporter for Blender 2.80
 
Installation
Copy io_bcry_exporter folder to blender_path\Scripts\Addons directory.
Example: C:\Users\%Your_User_Name%\AppData\Roaming\Blender Foundation\Blender\2.80\scripts\addons

Documentation: maybe soon

Tested:
1) Export static geometry (support box, sphere, capsule, cylinder and not a prim collision types)
2) Export skeleton, skeleton radgoll, skin, chr.
3) Export animation through Limit with Values
4) All other utilities (Export, configuration, bone utilities, mesh utilities, material utilities, UDP)

Not tested but must work:
1) Export breakable joint and branch, but all errors in operators was fixed.

What's new:
1) Now you can add collision object to selected objects (not only for active)
2) Add "not a prim collision" (cryengine see it as a mesh collision. Recommended use less than 256 vertices and convex hull, but concave support too)
3) Blender 2.80 has new type of grouping objects instead layer and group - Collection. Now when you create export node, BCRY exporter create cry_exporter_nodes collection. All export nodes inside this collection are exported when you call export.

Menu: Blender 2.80 has Quick Favourite menu which called by "Q" key. But there is not way to add to quick favourite from python code. I added this menu in Configuration section. You can do right mouse click on them and set "Add to Quick favourite".

Known issues/limitation:
1) Custom split normal doesn't support Sharp edges in skin node. Solution: Add Edge split modifier before Armature modifier, set up and apply. The skin mesh will be rip in Sharp edges places.
2) There is no way to set active any collection, so be careful that current active collection be unhide and not disable. Otherwise you can expect Error that Object is Null. I put in some operators code which set Master collection(Scene Collection) active.

Enjoy.
