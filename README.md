# Ambient NPC Behavior Framework — Unreal Engine Sample

An Unreal Engine sample project demonstrating integration of the [Ambient NPC Behavior Framework](https://github.com/EricBL3/ambient-npc-behavior-framework) — a C++ shared library for memory-driven ambient NPC behavior.

This project is intended as a concrete starting point for anyone looking to integrate the framework into an Unreal Engine project. The wrapper module under `AmbientNpcUnrealSample/Source/AmbientNpcUnrealSample/Framework/` can be used in other projects as-is. The code under `AmbientNpcUnrealSample/Source/AmbientNpcUnrealSample/Demo/` is specific to this sample scene.

Full documentation, video demos, and the associated paper are available at the [project webpage](https://www.csd.uwo.ca/~ebuitron/).

## Requirements

- Unreal Engine 5.7.4+
- Windows (x64) or macOS (Apple Silicon / arm64)
- No additional dependencies — the precompiled framework binary is included in `AmbientNpcUnrealSample/ThirdParty/AmbientNpcBehaviorFramework/`

> **Important:** When running the demo in the Unreal Editor in Windows, use **Standalone Game** or **New Editor Window** play mode. Running in the default **Selected Viewport** mode may cause the editor to freeze when stopping play due to a known audio subsystem issue in this version of Unreal Engine.

## Opening and Running the Project

1. Clone this repository:
```
   git clone https://github.com/EricBL3/ambient-npc-behavior-unreal-sample.git
```
2. Open `AmbientNpcUnrealSample.uproject` in Unreal Engine. Allow it to compile shaders on first launch.
3. Open the demo level at `AmbientNpcUnrealSample/Content/DemoScene.umap`.
4. Set play mode to **Standalone Game** or **New Editor Window**, then press Play.

## Repository Structure

```
AmbientNpcUnrealSample/
  Source/
    AmbientNpcUnrealSample/
      Framework/                                    # Reusable wrapper module. Copy this into your own project
      Demo/                                         # Sample-specific logic
  Content/                                          # Unreal assets and demo level
  ThirdParty/
    AmbientNpcBehaviorFramework/
      Win64/
        AmbientCoreFramework.dll                    # Windows x64
      Mac/
        libAmbientCoreFramework.dylib               # macOS arm64
      BehaviorFrameworkInterface.h                  # Public C API header
      LICENSE                                       # Apache License 2.0 (framework)
      NOTICE                                        # Attribution notice (framework)
  Configs/                                          # JSON behavior configuration files loaded at runtime
LICENSE                                           # Apache License 2.0 (this sample project)
NOTICE                                            # Attribution notice (this sample project)
```

## Demo

[VIDEO will be added soon]

The demo features 5 characters exhibiting ambient behavior driven by the memory-driven selection algorithm. The video also shows which files to modify when adding new actions, characters, or behavior configurations.

## Adapting This Project

To use the wrapper module in a different Unreal project:
1. Copy `Source/AmbientNpcUnrealSample/Framework/` into your project's source module
2. Copy the contents of `AmbientNpcUnrealSample/ThirdParty/AmbientNpcBehaviorFramework/` into the same folder structure in your project
3. Create an instance of the following classes: `BehaviorFrameworkManagerBase, AmbientEntityBase, BehavioralEntityBase`
4. Create a `BehaviorFrameworkConfig` DataAsset with the configuration for the framework and the references to the json configuration files from `AmbientNpcUnrealSample/Configs/`.
5.  Setup a scene asset with the script that implements `BehaviorFrameworkManagerBase` and reference the DataAsset created in the previous step.
6.  Setup a scene asset for each framework or behavioral entity with the script that implements `AmbientEntityBase` (for framework entities) or `BehavioralEntityBase` (for behavioral entities). Add a reference to the appropriate entity json configuration file from `AmbientNpcUnrealSample/Configs/`.

## Framework

The `AmbientNpcUnrealSample/ThirdParty/AmbientNpcBehaviorFramework/` directory contains a precompiled binary of the [Ambient NPC Behavior Framework](https://github.com/EricBL3/ambient-npc-behavior-framework) at version 1.0.0, redistributed under the Apache License 2.0. See `AmbientNpcUnrealSample/ThirdParty/AmbientNpcBehaviorFramework/LICENSE` and `AmbientNpcUnrealSample/ThirdParty/AmbientNpcBehaviorFramework/NOTICE` for details.

## Citation

If you use this project in your research, please cite the associated paper:

Eric Buitron-Lopez and Roberto Solis-Oba, "A Memory-Driven Action Selection Framework for Scalable Ambient NPC Behavior," to appear in *Proceedings of the 2026 IEEE Conference on Games (CoG)*, Madrid, Spain, September 1–4, 2026.

```bibtex
@inproceedings{buitronlopez2026,
    author    = {Buitron-Lopez, Eric and Solis-Oba, Roberto},
    title     = {A Memory-Driven Action Selection Framework for Scalable Ambient {NPC} Behavior},
    booktitle = {Proceedings of the 2026 IEEE Conference on Games (CoG)},
    year      = {2026},
    note      = {To appear}
}
```

## License

This sample project is licensed under the Apache License 2.0. See [LICENSE](LICENSE) for details.

The framework binary in `AmbientNpcUnrealSample/ThirdParty/AmbientNpcBehaviorFramework/` is a separate component licensed under the Apache License 2.0 by Eric Buitron Lopez. See `AmbientNpcUnrealSample/ThirdParty/AmbientNpcBehaviorFramework/LICENSE` and `AmbientNpcUnrealSample/ThirdParty/AmbientNpcBehaviorFramework/NOTICE` for details.
