# UNITY STYLE GUIDE

This style guide is written with best practice and readability in mind.

- [Project Style Guide](#project-style-guide)
- [C# Style Guide](#c-style-guide)

# Project Style Guide

## Table of Contents
- [Folder Structure](#folder-structure)
  + [Assets](#assets-folder)
  + [Build](#build-folder)
- [File Naming](#file-naming)
  + [Prefabs](#prefabs)
  + [Materials](#materials)
  + [Models](#models)
  + [Textures](#textures)
  + [Audio](#audio)

## Folder structure

### Assets Folder
- Assets
  + Animations: Animation clips
  + Editor
  + Fonts
  + Materials
  + Models
  + Prefabs
  + Scenes
  + Scripts
  + Audio
  + Textures
  + Shaders
  + VFX
  
> **_NOTE:_**  Do not create folders called **Assets** or **AssetTypes**.

### Build Folder
Create a folder 'Build' inside the root folder.
- Root
  + Assets
  + Packages
  + ProjectSettings
  + **Build**

## File Naming
File naming is simple, always use **PascalCase**. Make sure that the name makes sense and are descriptive of what they are.

> **_NOTE:_**  Never uses spaces, unicode characters or other symbols.

### Prefabs
Use **PascalCase**, no prefix or suffix.

### Materials

**Material Prefixes**
| Prefix | Material|
|:-------|:-------|
| MAT_   | Material |
| MI_    | Material Instance |

### Models
File extension: **FBX**

**Models Prefixes**
| Prefix | Mesh|
|:-------|:-------|
| SM_    | Static |
| CHAR_    | Character |
| ANIM_    | Animation |

Use **Y up** and **-Z forward** for exporting.

### Textures
File extension: **PNG** or **TGA**

**Texture Suffixes**
| Suffix | Texture|
|:-------|:-------|
| _AL    | Albedo |
| _SP    | Specular |
| _S     | Smoothness |
| _MT    | Metalic |
| _N     | Normal |
| _H     | Height |
| _DP    | Displacemnent |
| _EM    | Emission |
|_AO     | Ambient Occlusion |
| _M     | Mask |
| _UI     | UI |

**RGBA Mask or Channel packing**
| Channel | Property|
|:-------|:-------|
| Red    | Metallic |
| Green    | Occlusion |
| Blue    | N/A |
| Alpha    | Smoothness |

[For more information, see the Unity documention](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@7.1/manual/lit-shader.html#channel-packing)

### Audio
File extension: **WAV**

**Audio Prefixes**
| Prefix | Texture|
|:-------|:-------|
| SX_    | SFX |
| MX_    | Music |
| DX_     | Dialogue |

# C# Style Guide

This C# style guide is to keep the code consistent and to improve the readability.

## Inspiration

This style guide is based on C# and Unity conventions. 

## Table of Contents

- [Nomenclature](#nomenclature)
  + [Namespaces](#namespaces)
  + [Classes & Interfaces](#classes--interfaces)
  + [Methods](#methods)
  + [Fields](#fields)
  + [Parameters](#parameters)
  + [Actions](#actions)
  + [Arrays](#arrays)
  + [Misc](#misc)
- [Declarations](#declarations)
  + [Access Level Modifiers](#access-level-modifiers)
  + [Fields & Variables](#fields--variables)
  + [Classes](#classes)
  + [Interfaces](#interfaces)
  + [Functions](#functions)
- [Spacing](#spacing)
  + [Indentation](#indentation)
  + [Line Length](#line-length)
  + [Vertical Spacing](#vertical-spacing)
- [Brace Style](#brace-style)
- [Switch Statements](#switch-statements)
- [Language](#language)


## Nomenclature

On the whole, naming should follow C# standards.

### Namespaces

Namespaces are all **PascalCase**, multiple words concatenated together, without hyphens ( - ) or underscores ( \_ ). The exception to this rule are acronyms like GUI or HUD, which can be uppercase:

**AVOID**:

```csharp
com.name.game.hud.healthbar
```

**PREFER**:

```csharp
Name.Game.HUD.Healthbar
```

### Classes & Interfaces

Classes and interfaces are written in **PascalCase**. For example `RadialSlider`.

For certain purposes we use the following naming conventions:
- `XxxManager`, for manager scripts that controls a specific workflow (usely only one instance of)
- `XxxController`, for scripts controlling a game object
- `XxxItem`, for in-game item instance
- `XxxSettings`, for setting scripts
- `XeeEditor`, for editor-only scripts

### Methods

Methods are written in **PascalCase**. For example `DoSomething()`. 

### Fields

All non-static public fields are written **PascalCase**, all non-static private/protected fields are written **_camelCase**.
For example:

```csharp
public class MyClass 
{
    public int PublicField;
    int _packagePrivate;
    private int _myPrivate;
    protected int _myProtected;
}
```

**AVOID:**

```csharp
int _myPrivateVariable
```

**PREFER:**

```csharp
private int _myPrivateVariable
```

Static fields should be written in **PascalCase**:

```csharp
public static int TheAnswer = 42;
```
### Properties

All properties are written in **PascalCase**. For example:

```csharp
public int PageNumber 
{
    get { return _pageNumber; }
    set { pageNumber = value; }
}
```

### Parameters

Parameters are written in **camelCase**.

**AVOID:**

```csharp
void DoSomething(Vector3 Location)
```

**PREFER:**

```csharp
void DoSomething(Vector3 location)
```

Single character values are to be avoided except for temporary looping variables.

### Actions

Actions are written in **PascalCase**. For example:

```csharp
public event Action<int> ValueChanged;
```

### Arrays

Arrays should be named as a plural noun.

**AVOID:**

```csharp
TargetList
HatArray
EnemyPlayerArray
```  

**PREFER:**

```csharp
Targets
Hats
EnemyPlayers
```

### Misc

In code, acronyms should be treated as words. For example:

**AVOID:**

```csharp
XMLHTTPRequest
String URL
findPostByID
```  

**PREFER:**

```csharp
XmlHttpRequest
String url
findPostById
```

## Declarations

### Access Level Modifiers

Access level modifiers should be explicitly defined for classes, methods and member variables.

### Fields & Variables

Prefer single declaration per line.

**AVOID:**

```csharp
string _username, _twitterHandle;
```

**PREFER:**

```csharp
string _username;
string _twitterHandle;
```

### Classes

Exactly one class per source file, although inner classes are encouraged where scoping appropriate.

### Interfaces

All interfaces should be prefaced with the letter **I**. 

**AVOID:**

```csharp
RadialSlider
```

**PREFER:**

```csharp
IRadialSlider
```

### Functions

The functionality of the function should give a good assumption. All functions and events perform some form of action, whether its getting info, calculating data, or causing something to explode. Therefore, all functions should start with verbs.

**AVOID:**

```csharp
CameraOffset
```

**PREFER:**

```csharp
GetCameraOffset
```

#### Boolean Functions

A boolean functions should ask a question.

**AVOID:**

```csharp
Dead
Visibility
```

**PREFER:**

```csharp
IsDead
IsVisible
```

## Spacing

Spacing is especially important, as code needs to be easily readable. 

### Indentation

Indentation should be done using **tabs** — never spaces.  

#### Blocks

Indentation for blocks uses **1 tab** for optimal readability:

**AVOID:**

```csharp
for (int i = 0; i < 10; ++i) 
{
  Debug.Log("index=" + i);
}
```

**PREFER:**

```csharp
for (int i = 0; i < 10; ++i) 
{
    Debug.Log("index=" + i);
}
```

### Line Length

Lines should be no longer than **100** characters long.

### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity 
and organization. Whitespace within methods should separate functionality, but 
having too many sections in a method often means you should refactor into
several methods.


## Brace Style

All braces get their own line as it is a C# convention:

**AVOID:**

```csharp
class MyClass {
    void DoSomething() {
        if (someTest) {
          // ...
        } else {
          // ...
        }
    }
}
```

**PREFER:**

```csharp
class MyClass
{
    void DoSomething()
    {
        if (someTest)
        {
          // ...
        }
        else
        {
          // ...
        }
    }
}
```

Conditional statements are always required to be enclosed with braces,
irrespective of the number of lines required.

**AVOID:**

```csharp
if (someTest)
    doSomething();  

if (someTest) doSomethingElse();
```

**PREFER:**

```csharp
if (someTest) 
{
    DoSomething();
}  

if (someTest)
{
    DoSomethingElse();
}
```

A **return** is the exception and can be written on a single line:

```csharp
if(someTest) return;
```

## Switch Statements

Switch-statements come with `default` case by default (heh). If the `default` case is never reached, be sure to remove it.

**AVOID:**  
  
```csharp
switch (variable) 
{
    case 1:
        break;
    case 2:
        break;
    default:
        break;
}
```

**PREFER:**  
  
```csharp
switch (variable) 
{
    case 1:
        break;
    case 2:
        break;
}
```

## Language

Use US English spelling.

**AVOID:**

```csharp
string colour = "red";
```

**PREFER:**

```csharp
string color = "red";
```

The exception here is `MonoBehaviour` as that's what the class is actually called.

Single line comments should include a space after the slashes.

## Comments

Only use comments when necessary.
```csharp
// Single line comment
```

**TODO** comments should also include a space after the slashes, followed by a colon.
```csharp
// TODO: Example of a reminder
```
