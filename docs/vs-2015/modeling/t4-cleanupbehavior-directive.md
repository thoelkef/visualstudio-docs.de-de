---
title: T4 CleanUpBehavior-Anweisung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9b9138ab564c7597715537216333f1efd0f3fc5a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515363"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior-Anweisung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [T4 CleanUpBehavior-Anweisung](https://docs.microsoft.com/visualstudio/modeling/t4-cleanupbehavior-directive).  
  
Wenn die appDomain nach der Verarbeitung einer Textvorlage gelöscht werden soll, nehmen Sie die folgende Zeile mit auf:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Textvorlagen werden in einer appDomain getrennt vom Hostprozess verarbeitet. In den meisten Fällen wird nach der Verarbeitung einer Textvorlage die jeweilige appDomain erneut verwendet, um die nächste Vorlage zu verarbeiten. Wenn Sie ///CleanupBehavior angeben, wird die appDomain gelöscht und die nächste Vorlage wird in einer neuen appDomain verarbeitet.  
  
 Dadurch verlangsamt sich zwar die Textverarbeitung, es wird jedoch sichergestellt, dass Ressourcen verworfen werden.  
  
 Diese Direktiven funktionieren nur auf dem Visual Studio-Host.



