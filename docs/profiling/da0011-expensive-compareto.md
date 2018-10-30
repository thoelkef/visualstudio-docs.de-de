---
title: 'DA0011: Speicherintensive CompareTo-Funktionen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f6137c07ac6b920234a9772764b5ad758efdb1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818847"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Speicherintensive CompareTo-Funktionen

|||  
|-|-|  
|Regel-ID|DA0011|  
|Kategorie|.NET Framework-Verwendung|  
|Profilerstellungsmethoden|Sampling<br /><br /> .NET-Arbeitsspeicher|  
|Meldung|CompareTo-Funktionen dürfen nicht speicherintensiv sein und keinen Speicher belegen. Reduzieren Sie daher, wenn möglich, die Komplexität der CompareTo-Funktionen.|  
|Regeltyp|Warnung|  

## <a name="cause"></a>Ursache  
 Die CompareTo-Methode des Typs ist aufwändig oder belegt Arbeitsspeicher.  

## <a name="rule-description"></a>Regelbeschreibung  
 CompareTo-Methoden sollten effizient sein und keinen Arbeitsspeicher zuordnen.  

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Verringern Sie die Komplexität der CompareTo-Methode.