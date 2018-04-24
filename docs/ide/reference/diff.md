---
title: /Diff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 016de0a06615caab723f83900e8bd4103cb142b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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