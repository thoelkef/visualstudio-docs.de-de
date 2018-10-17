---
title: T4 CleanUpBehavior-Anweisung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: ee1882b6b63dbb2729070d32fcee7c1e58d280c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263398"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior-Anweisung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn die appDomain nach der Verarbeitung einer Textvorlage gelöscht werden soll, nehmen Sie die folgende Zeile mit auf:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Textvorlagen werden in einer appDomain getrennt vom Hostprozess verarbeitet. In den meisten Fällen wird nach der Verarbeitung einer Textvorlage die jeweilige appDomain erneut verwendet, um die nächste Vorlage zu verarbeiten. Wenn Sie ///CleanupBehavior angeben, wird die appDomain gelöscht und die nächste Vorlage wird in einer neuen appDomain verarbeitet.  
  
 Dadurch verlangsamt sich zwar die Textverarbeitung, es wird jedoch sichergestellt, dass Ressourcen verworfen werden.  
  
 Diese Direktiven funktionieren nur auf dem Visual Studio-Host.



