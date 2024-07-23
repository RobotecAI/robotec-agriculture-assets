# Repository content

This repository contains O3DE gems with assets that are specific to agriculture

# Type of assets

This repository will host asset gems, containing all types of O3DE objects except for source code. Permitted assets include:
- prefabs
- meshes
- materials and textures
- HDRI maps (*.exr)
- LUA and script canvas scripts
- URDF files

# Repository structure

All the content is divided into O3DE gems. Each gem will contain a set of substantively related assets. The content of these sets must be as narrow as possible. It is preferred to have a few specific gems, e.g. "road signs", "road guardrails", etc. instead of one generic, e.g. "road infrastructure".

This repository contains two types of gems:

## Gems with "raw" assets

The main purpose of these gems is to provide models, materials, and textures (including HDRi maps). If it is applicable, prefabs should be included integrating other objects of asset. The purpose of these prefabs is to facilitate inserting assets on the scene. Such prefabs however must not contain any functionality beyond the absolute minimum necessary to show assets correctly. Prefabs must not contain in particular:
- Physics (rigid bodies, joints, etc.)
- ROS components
- Scripts

Raw-type gems may depend only on official gems distributed with the O3DE engine. These dependencies should be reduced to a minimum. Raw-type gems must not depend on any external gems, including those contained in o3de-extras repository.

## Gems with "working" assets

The purpose of these gems is to provide prefabs prepared to be used in different applications. These prefabs may be built around "raw" assets (hosted in raw-type gems) and should be extended by additional functionality. This may include for example:
- Adding physics structure (rigid bodies, joints, etc.)
- Adding ROS components
- Adding scripts
- Joining multiple prefabs (from raw-type or working-type gems)

Working-type gems must not contain models, materials, or textures. Assets from raw-type gems should be used instead.

Working-type gems may depend on external gems.

# Conventions and guidelines

## General guidelines

Each gem is created according to the official O3DE instructions. All assets will also follow the simulator application requirements, in particular naming convention.

## Folder structure

Each asset is located in a separate folder, a subfolder of the Assets folder.

In the raw-type gems, it is strongly advised to place all files used by the asset in its folder. Two or more assets may share the same files within one gem, e.g. materials and textures. In this case, these files will be located in the folder of one of these assets. It is advised not to use files from different gems, however, if this is necessary, such gem must be listed in the prerequisites and this should be mentioned in the gem's README file.

Assets in the working-type gems may use assets from other gems with no limitations.

Assets containing models (in raw-type gems) must be arranged in the following folder structure:

```
├── [Assets]
│   ├── [AssetName] 
│   │   ├── *.Prefab
│   │   ├── [Models]
│   │   │   ├── *.fbx
│   │   │   ├── [Materials]
│   │   │   │   ├── *.Material
│   │   │   │   ├── [Textures]
│   │   │   │   │   ├── *.png
│   │   │   │   │   ├── *.jpg
```

Other types of assets like textures or prefabs in working-type gems must be located directly in the asset folder.
Gem description

Each gem must include a README file containing:
- description
- all information important when using this gem
- list of prerequisites and relations with other gems

# Licensing

The license should be specified in the gem.json.

All assets in one gem must comply with the same license. This includes also assets that were obtained from external sources (e.g. from internet). In such cases, information about the source and license must be provided in the NOTICE document in top level gem's folder.
