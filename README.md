# create_URDF
Documentation on how to build our URDF from STL file

## Resources

- [Webgraphviz](http://www.webgraphviz.com/)
- [Joint2Graphviz repo zip](https://github.com/yanshil/Joint2Graphviz)
- [Fusion2PyBullet repo zip](https://github.com/yanshil/Fusion2PyBullet)
- [fusion2urdf](https://github.com/syuntoku14/fusion2urdf) <-- deprecated

## Prepare STL
As stated in the [Fusion2PyBullet repo](https://github.com/yanshil/Fusion2PyBullet), we must **prepare our STL** file properly.
1. All bodies/peaces/future links must be **components**.
2. Add physical materials
3. Add **joint** to connect all components. In fusion you can select various type of joint (static, rotational, etc...) and also the pivot point.
4. Call one componet as `base_link`
5. Remove links of comonents (if the are right clik on it and press Break Link)
5. Check STL joint-link structure using [Webgraphviz](http://www.webgraphviz.com/). Here how:
    - Download [Joint2Graphviz repo](https://github.com/yanshil/Joint2Graphviz) as a ZIP.
    - Extract the ZIP in a known directory.
    - Open terminal:

        ```powershell
        cd <path to Joint2Graphviz>

        Copy-Item ".\Joint2Graphviz-master\" -Destination "${env:APPDATA\Autodesk\Autodesk Fusion 360\API\Scripts\" -Recurse
        ```

        For me was:
        ```powershell
         cd C:\Users\orlan\OneDrive\Desktop\side_projects\Joint2Graphviz-master

         Copy-Item "..\Joint2Graphviz-master\" -Destination "..\..\..\..\AppData\Roaming\Autodesk\Autodesk Fusion 360\API\Scripts\" -Recurse
        ```
    - Now the script to create a `.txt` file for your link graph is added to fusion
    - Open fusion
    - Open the file of the robot
    - Go to utility > Addins
    - Under `My Script` you should see `Joint2Graphviz`
    - Press it. It will create a `graph.txt` (see mine [here](https://github.com/botzo-team/create_URDF/blob/main/test_urdf_exporter/graph.txt))
    <p align="center">
        <img src="https://github.com/botzo-team/create_URDF/blob/main/test_urdf_exporter/graph_from_webgraphviz.png" alt="Graph Image" width="200"/>
    </p>

    - Copy and pase the text content to [Webgraphviz](http://www.webgraphviz.com/) and check your robot tf structure to be valid.

**(for more infors check [Joint2Graphviz readme](https://github.com/yanshil/Joint2Graphviz))**

## Export URDF

1. Download [Fusion2PyBullet](https://github.com/yanshil/Fusion2PyBullet) as a ZIP
2. Extract the ZIP in a known directory.
3. Open terminal:

    ```powershell
    cd <path to Fusion2PyBullet>

    Copy-Item ".\URDF_Exporter\" -Destination "${env:APPDATA}\Autodesk\Autodesk Fusion 360\API\Scripts\" -Recurse
    ```

    For me was:
    ```powershell
        PS C:\Users\orlan\OneDrive\Desktop\side_projects\Fusion2PyBullet-master> Copy-Item ".\Bullet_URDF_Exporter\" -Destination "..\..\..\..\AppData\Roaming\Autodesk\Autodesk Fusion 360\API\Scripts\" -Recurse
    ```
4. Open fusion > utils > addins > my scripts > Bullet_URDF_Exporter
5. My URDF [here](https://github.com/botzo-team/create_URDF/blob/main/final_leg.zip)

**(for more infors check [fusion2urdf readme](https://github.com/syuntoku14/fusion2urdf/blob/master/README.md) or [Fusion2PyBullet readme](https://github.com/yanshil/Fusion2PyBullet/blob/master/README.md))**