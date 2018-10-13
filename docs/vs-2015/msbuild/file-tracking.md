---
title: Dateinachverfolgung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 179124c09e0846cbbf649a819bd8c954b5a72e7a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228188"
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



