---
title: Zeilenansicht - Samplingdaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07ad23e1b7b466965efe16c23f92adc6b9f676dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511612"
---
# <a name="lines-view---sampling-data"></a>Zeilenansicht - Samplingdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Zeilenansicht - Samplingdaten](https://docs.microsoft.com/visualstudio/profiling/lines-view-sampling-data).  
  
In der Zeilenansicht der Samplingdaten werden die Leistungsdaten für die Anweisungen aufgeführt, die ausgeführt wurden, als die Samplings bei der Profilerstellung erfasst wurden.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten. Eine Anweisung wird mit dem Folgenden identifiziert:  
  
-   Die Quelldatei, die die Funktionsanweisung enthält.  
  
-   Die Funktion, die die Anweisung enthält.  
  
-   Die Quellzeile, an der die Anweisung beginnt.  
  
-   Das Zeichen in der Quellzeile, an dem die Anweisung beginnt.  
  
-   Die Quellzeile, an der die Anweisung endet.  
  
-   Das Zeichen in der Quellzeile, an dem die Anweisung endet.  
  
 Die Zeilennamensspalte, die eine sortierbare Verkettung der Bezeichnerdaten bereitstellt.  
  
 Per Definition ruft eine Anweisung keine anderen Funktionen auf. Daher sind nur exklusive Werte aufgeführt.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Funktionszeile enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktionszeile enthält.|  
|**Quelldatei**|Die Quelldatei, die die Funktionszeile enthält.|  
|**Funktionsname**|Der Name der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Funktionsadresse**|Die Startadresse der Funktion.|  
|**Quellanfangszeile**|Die Nummer der Anfangszeile in der Quelldatei, an der dieses Sampling erfasst wurde.|  
|**Quellendzeile**|Die Endzeilennummer der Quelldatei, an der dieses Sampling erfasst wurde.|  
|**Quellanfangszeichen**|Der Offset des Startzeichens in der Quelldateizeile, an dem dieses Sampling erfasst wurde.|  
|**Quellendzeichen**|Der Offset des Endzeichens der Quelldateizeile, an dem dieses Sampling erfasst wurde.|  
|**Zeilenname**|Ein vom Profiler generierter Bezeichner der Zeile mit folgender Syntax:`Source File`**;[**`Line Number Start`**,**`Character Start`**]->;[**`Line Number End`**,**`Character End`**]**|  
|**Exklusive Samplings**|Die Anzahl von Samplings, die während der Ausführung der Funktionszeile gesammelt wurden.|  
|**Exklusive Samplings %**|Der Prozentsatz aller Samplings bei der Profilerstellung, die gesammelt wurden, als die Funktionszeile ausgeführt wurde.|  
  
## <a name="see-also"></a>Siehe auch  
 [Zeilenansicht - Sampling](../profiling/lines-view-dotnet-memory-sampling-data.md)



