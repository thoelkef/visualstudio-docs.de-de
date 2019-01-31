---
title: Dateinachverfolgung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5afc245bd16954ba348b4ec581238bf17e5d994
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758712"
---
# <a name="file-tracking"></a>Dateinachverfolgung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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
