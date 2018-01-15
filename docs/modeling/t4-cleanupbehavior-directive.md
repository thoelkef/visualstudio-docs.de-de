---
title: T4 CleanUpBehavior-Direktive | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f773f04799ec1ec975626699f37089c3c5b59b2d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior-Anweisung
Wenn die appDomain nach der Verarbeitung einer Textvorlage gelöscht werden soll, nehmen Sie die folgende Zeile mit auf:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Textvorlagen werden in einer appDomain getrennt vom Hostprozess verarbeitet. In den meisten Fällen wird nach der Verarbeitung einer Textvorlage die jeweilige appDomain erneut verwendet, um die nächste Vorlage zu verarbeiten. Wenn Sie ///CleanupBehavior angeben, wird die appDomain gelöscht und die nächste Vorlage wird in einer neuen appDomain verarbeitet.  
  
 Dadurch verlangsamt sich zwar die Textverarbeitung, es wird jedoch sichergestellt, dass Ressourcen verworfen werden.  
  
 Diese Direktiven funktionieren nur auf dem Visual Studio-Host.