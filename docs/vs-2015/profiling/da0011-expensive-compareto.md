---
title: 'DA0011: Speicherintensive CompareTo-Funktionen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 281bdbb3ba974b3aacb9c349575727675bb59305
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58354744"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Speicherintensive CompareTo-Funktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [DA0011: speicherintensive CompareTo-Funktionen](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto) auf docs.microsoft.com.  
  
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
