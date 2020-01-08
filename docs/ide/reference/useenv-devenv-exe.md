---
title: -UseEnv („devenv.exe“)
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35808b27964b3ca8fa0488f1be2ce6dc5530b3dd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596394"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Startet Visual Studio und lädt bestimmte Umgebungsvariablen für die Kompilierung.

> [!NOTE]
> Dieser Schalter wird mit der Workload **Desktopentwicklung mit C++** installiert.

## <a name="syntax"></a>Syntax

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumente

- *SolutionName*

  Der vollständige Pfad und Name einer Projektmappendatei

- *ProjectName*

  Der vollständige Pfad und Name einer Projektdatei

## <a name="remarks"></a>Hinweise

Dieser Schalter wirkt sich auf die Visual Studio-IDE in den Projekteigenschaften für **VC++-Verzeichnisse** aus. Wenn Sie den Schalter `/UseEnv` angeben, zeigt der Knoten **VC++-Verzeichnisse** die Werte für die Umgebungsvariablen PATH, INCLUDE, LIBPATH und LIB. (Er zeigt auch Werte für **Quellverzeichnisse** und **Ausschließbare Verzeichnisse**.) Andernfalls ersetzt der Knoten die Umgebungsvariablen durch fünf Verzeichniswerte: **Ausführbare Verzeichnisse**, **Includeverzeichnisse**, **Verweisverzeichnisse**, **Bibliotheksverzeichnisse** und **WinRT-Bibliotheksverzeichnisse**.

> [!TIP]
> Sie können auf die Projekteigenschaften zugreifen, indem Sie mit der rechten Maustaste auf ein C++-Projekt klicken und **Eigenschaften** auswählen. Wählen Sie im Dialogfeld **Eigenschaftenseiten** die Option **Konfigurationseigenschaften** und dann **VC++-Verzeichnisse** aus.

Wenn ein Projektname mit diesem Schalter angegeben wird, zeigt das Tool die Umgebungsvariablen für alle Projekte in der übergeordneten Projektmappe des Projekts an.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird Visual Studio gestartet, und die Umgebungsvariablen werden in die Eigenschaftenseiten der Projektmappe `MySolution` geladen.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [Eigenschaftenseite „VC++-Verzeichnisse“ (Windows)](/cpp/build/reference/vcpp-directories-property-page)
