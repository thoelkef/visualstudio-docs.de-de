---
title: -Edit („devenv.exe“)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb5ae37d3e4dc0973320c68f9db169cdbf7d663a
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227680"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Öffnet die angegebene Datei in einer vorhandenen Instanz von Visual Studio.

## <a name="syntax"></a>Syntax

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Argumente

- *File1*

  Dies ist optional. Die Datei, die in einer vorhandenen Instanz von Visual Studio geöffnet werden soll. Wenn keine Instanz von Visual Studio vorhanden ist, wird eine neue Instanz mit einem vereinfachten Fensterlayout erstellt, und das Tool öffnet *File1* in der neuen Instanz.

- *FileN*

  Dies ist optional. Eine oder mehrere zusätzliche Dateien, die in der vorhandenen Instanz von Visual Studio geöffnet werden sollen.

## <a name="remarks"></a>Hinweise

Wenn keine Datei angegeben ist, erhält eine vorhandene Visual Studio-Instanz den Fokus. Wenn keine Datei angegeben und keine Instanz von Visual Studio vorhanden ist, erstellt das Tool eine Instanz mit einem vereinfachten Fensterlayout.

Wenn sich die vorhandene Visual Studio-Instanz in einem modalen Zustand befindet, wird die Datei in der vorhandenen Instanz geöffnet, sobald Visual Studio sich nicht mehr im modalen Zustand befindet. Diese Situation kann beispielsweise auftreten, wenn das [Dialogfeld „Optionen“](../../ide/reference/options-dialog-box-visual-studio.md) geöffnet ist.

## <a name="example"></a>Beispiel

Im ersten Beispiel wird die Datei `MyFile.cs` in einer vorhandenen Instanz von Visual Studio geöffnet. Wenn keine Visual Studio-Instanz vorhanden ist, öffnet das Tool die Datei in einer neuen Instanz. Das zweite Beispiel ähnelt dem ersten, doch werden hier drei Dateien anstelle von nur einer Datei geöffnet.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)