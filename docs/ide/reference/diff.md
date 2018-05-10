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
ms.openlocfilehash: 6cbf0f8f9fa2e97908e2ae13e3961382a7250a91
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
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