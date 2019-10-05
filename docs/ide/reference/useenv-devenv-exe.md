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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16443b30ccf6ba03a01df0234695d27e4cd909af
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186484"
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

## <a name="remarks"></a>Anmerkungen

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
