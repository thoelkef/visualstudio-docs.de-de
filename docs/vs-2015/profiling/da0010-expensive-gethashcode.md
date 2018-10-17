---
title: 'DA0010: Speicherintensive GetHashCode-Funktionen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7eae8083b070e97fdc4a37fd44c278801dea3c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267723"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Speicherintensive GetHashCode-Funktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation für Visual Studio 2017 finden Sie unter [DA0010: speicherintensive GetHashCode-Funktionen](https://docs.microsoft.com/visualstudio/profiling/da0010-expensive-gethashcode) auf docs.microsoft.com.  

  

|||  
|-|-|  
|Regel-ID|DA0010|  
|Kategorie|.NET Framework-Verwendung|  
|Profilerstellungsmethoden|Sampling<br /><br /> .NET-Arbeitsspeicher|  
|Meldung|GetHashCode-Funktionen dürfen nicht speicherintensiv sein und keinen Speicher belegen. Reduzieren Sie daher, wenn möglich, die Komplexität der Hashcodefunktionen.|  
|Nachrichtentyp|Warnung|  
  
## <a name="cause"></a>Ursache  
 Aufrufe der GetHashCode-Methode des Typs machen einen großen Teil der Profilerstellungsdaten aus, oder die Methode belegt Arbeitsspeicher.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Hashing ist eine Technik, mit deren Hilfe Sie ein bestimmtes Element in einer Auflistung mit vielen Elementen schnell finden können. Da Hashtabellen sehr groß sein können und hohe Zugriffsraten unterstützen müssen, sollten sie auch effizient konzipiert sein. Folglich sollten GetHashCode-Methoden in .NET Framework keinen Speicherplatz belegen. Wenn Speicherplatz belegt wird, wird die Belastung des Garbage Collectors größer, wodurch die Methode unter Umständen nur mit einer Verzögerung ausgeführt werden kann, wenn es nötig sein sollte, die Garbage Collection aufgrund der Reservierungsanforderung auszuführen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Verringern Sie die Komplexität der Methode.

