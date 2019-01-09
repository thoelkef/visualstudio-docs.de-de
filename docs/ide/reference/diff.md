---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf58c25611fd52c6e8db8e8210101e1c80153275
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844537"
---
# <a name="diff"></a>/Diff
Vergleicht zwei Dateien. Die Unterschiede werden in einem speziellen Visual Studio-Fenster angezeigt.

## <a name="syntax"></a>Syntax

```cmd
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>Argumente
 `SourceFile`

 Erforderlich. Der vollständige Pfad und der Name der ersten zu vergleichenden Datei

 `TargetFile`

 Erforderlich. Der vollständige Pfad und der Name der zweiten zu vergleichenden Datei

 `SourceDisplayName`

 Dies ist optional. Der Anzeigename der ersten Datei

 `TargetDisplayName`

 Dies ist optional. Der Anzeigename der zweiten Datei