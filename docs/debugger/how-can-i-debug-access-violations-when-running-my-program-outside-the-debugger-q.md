---
title: "Wie können Zugriffsverletzungen, die beim Ausführen des Programms außerhalb des Debuggers auftreten, gedebuggt werden? | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0af98932a940126c8f7288d7b5c830bb40f270fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Wie können Zugriffsverletzungen, die beim Ausführen des Programms außerhalb des Debuggers auftreten, gedebuggt werden?
## <a name="problem-description"></a>Problembeschreibung  
 Das Programm läuft in der Visual Studio-Umgebung einwandfrei. Wird es jedoch eigenständig unter dem Windows-Betriebssystem ausgeführt, generiert es eine Zugriffsverletzung. Wie kann dieses Problem behoben werden?  
  
## <a name="solution"></a>Lösung  
 Legen Sie die [Just-in-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md) aus, und Ihr Programm im eigenständigen Modus ausgeführt, bis die zugriffsverletzung auftritt. Klicken Sie auf die **Zugriffsverletzung** (Dialogfeld), klicken Sie auf **"Abbrechen"** um den Debugger starten.  
  
 Weitere Informationen finden Sie im Knowledge Base-Artikel Q133174, "How to Locate Where a General Protection (GP) Fault Occurs" (nur auf Englisch verfügbar). Sie finden Knowledge Base-Artikeln auf der MSDN Library-CD oder durch Suchen [http://support.microsoft.com/](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von systemeigenem Code häufig gestellte Fragen](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)