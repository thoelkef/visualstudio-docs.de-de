---
title: Dateinachverfolgung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51d17894025800acd9c8ab0736ebe92d7f790fc7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31567446"
---
# <a name="file-tracking"></a>Dateinachverfolgung
Die Dateinachverfolgung protokolliert Aufrufe an das Windows-Dateisystem für einen Prozess und dessen untergeordnete Prozesse. Durch das Aufrufen der unten aufgeführten Funktionen wird gesteuert, wann diese Protokollierung aktiviert oder deaktiviert wird, und die zu verwendende Protokolldatei angegeben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Beenden der Nachverfolgung des aktuellen Kontexts.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Fortsetzen der Nachverfolgung nach einem Aufruf von [SuspendTracking](../msbuild/suspendtracking.md)  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Festlegen der Anzahl der Threads, die zur Nachverfolgung verwendet werden sollen.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Beginnen eines neuen Nachverfolgungskontexts.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Beginnen eines neuen Nachverfolgungskontexts mit einem angegebenen Stamm.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Beenden der Nachverfolgung und Freigeben der verwendeten Ressourcen.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Vorübergehendes Anhalten der Nachverfolgung.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Schreiben der Nachverfolgungsprotokolle für alle Kontexte.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Schreiben des Nachverfolgungsprotokolls für den aktuellen Kontext.