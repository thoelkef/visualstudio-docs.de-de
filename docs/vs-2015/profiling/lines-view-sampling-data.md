---
title: Zeilenansicht - Samplingdaten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2e5511e9e2e1c863db8f696a70195573d75429f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841284"
---
# <a name="lines-view---sampling-data"></a>Zeilenansicht - Samplingdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Zeilenansicht der Samplingdaten werden die Leistungsdaten für die Anweisungen aufgeführt, die ausgeführt wurden, als die Samplings bei der Profilerstellung erfasst wurden.  
  
> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Informationen hierzu finden Sie unter [Performance Tools on Windows 8 and Windows Server 2012 applications (Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen)](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten. Eine Anweisung wird mit dem Folgenden identifiziert:  
  
- Die Quelldatei, die die Funktionsanweisung enthält.  
  
- Die Funktion, die die Anweisung enthält.  
  
- Die Quellzeile, an der die Anweisung beginnt.  
  
- Das Zeichen in der Quellzeile, an dem die Anweisung beginnt.  
  
- Die Quellzeile, an der die Anweisung endet.  
  
- Das Zeichen in der Quellzeile, an dem die Anweisung endet.  
  
  Die Zeilennamensspalte, die eine sortierbare Verkettung der Bezeichnerdaten bereitstellt.  
  
  Per Definition ruft eine Anweisung keine anderen Funktionen auf. Daher sind nur exklusive Werte aufgeführt.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Name des Prozesses.|  
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
|**Zeilenname**|Ein vom Profiler generierter Bezeichner der Zeile mit folgender Syntax:`Source File` **;[** `Line Number Start` **,** `Character Start` **]->;[** `Line Number End` **,** `Character End` **]**|  
|**Exklusive Samplings**|Die Anzahl von Samplings, die während der Ausführung der Funktionszeile gesammelt wurden.|  
|**Exklusive Samplings %**|Der Prozentsatz aller Samplings bei der Profilerstellung, die gesammelt wurden, als die Funktionszeile ausgeführt wurde.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lines View – Sampling (Zeilenansicht – Sampling)](../profiling/lines-view-dotnet-memory-sampling-data.md)
