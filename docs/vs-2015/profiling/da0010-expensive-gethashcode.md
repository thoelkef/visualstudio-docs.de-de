---
title: 'DA0010: Speicherintensive GetHashCode-Funktionen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a0a2947f0bd6758de62a4a11d78390d38a503271
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919028"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Speicherintensive GetHashCode-Funktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [DA0010: teure GetHashCode](/visualstudio/profiling/da0010-expensive-gethashcode).  

|||  
|-|-|  
|Regel-ID:|DA0010|  
|Kategorie|.NET Framework-Verwendung|  
|Profilerstellungsmethoden|Sampling<br /><br /> .NET-Arbeitsspeicher|  
|Meldung|GetHashCode-Funktionen dürfen nicht speicherintensiv sein und keinen Speicher belegen. Reduzieren Sie daher, wenn möglich, die Komplexität der Hashcodefunktionen.|  
|Meldungstyp|Warnung|  
  
## <a name="cause"></a>Ursache  
 Aufrufe der GetHashCode-Methode des Typs machen einen großen Teil der Profilerstellungsdaten aus, oder die Methode belegt Arbeitsspeicher.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Hashing ist eine Technik, mit deren Hilfe Sie ein bestimmtes Element in einer Auflistung mit vielen Elementen schnell finden können. Da Hash Tabellen sehr groß sein können und hohe Zugriffsraten unterstützen müssen, sollten Hash Tabellen äußerst effizient sein. Folglich sollten GetHashCode-Methoden in .NET Framework keinen Speicherplatz belegen. Wenn Speicherplatz belegt wird, wird die Belastung des Garbage Collectors größer, wodurch die Methode unter Umständen nur mit einer Verzögerung ausgeführt werden kann, wenn es nötig sein sollte, die Garbage Collection aufgrund der Reservierungsanforderung auszuführen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Verringern Sie die Komplexität der Methode.
