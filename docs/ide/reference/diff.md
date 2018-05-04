---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81c70c238a4503fbd05249ef6522cf020c00221c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="diff"></a>/Diff
Vergleicht zwei Dateien. Die Unterschiede werden in einem speziellen Visual Studio-Fenster angezeigt.

## <a name="syntax"></a>Syntax

```
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