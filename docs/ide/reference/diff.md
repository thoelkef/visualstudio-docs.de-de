---
title: /Diff | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 14deeec64d4645135f19587997844bfdd0b18cd5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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