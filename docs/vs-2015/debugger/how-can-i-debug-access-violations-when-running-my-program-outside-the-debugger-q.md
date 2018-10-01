---
title: Wie können Zugriffsverletzungen, die beim Ausführen des Programms außerhalb des Debuggers auftreten, gedebuggt werden? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1525061210c6ef7cdda32c6204648c3944f4b889
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510273"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Wie können Zugriffsverletzungen, die beim Ausführen des Programms außerhalb des Debuggers auftreten, gedebuggt werden?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [wie kann ich Debuggen Zugriff Verstöße beim Ausführen Mein Programm außerhalb Debugger?](https://docs.microsoft.com/visualstudio/debugger/how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger-q).  
  
Problembeschreibung  
 Das Programm läuft in der Visual Studio-Umgebung einwandfrei. Wird es jedoch eigenständig unter dem Windows-Betriebssystem ausgeführt, generiert es eine Zugriffsverletzung. Wie kann dieses Problem behoben werden?  
  
## <a name="solution"></a>Lösung  
 Legen Sie die [Just-in-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md) aus, und Ihr Programm im eigenständigen Modus ausgeführt, bis die zugriffsverletzung auftritt. Klicken Sie auf die **Zugriffsverletzung** Dialogfeld klicken Sie auf **Abbrechen** den Debugger starten.  
  
 Weitere Informationen finden Sie im Knowledge Base-Artikel Q133174, "How to Locate Where a General Protection (GP) Fault Occurs" (nur auf Englisch verfügbar). Sie finden Knowledge Base-Artikel auf der MSDN Library-CD oder durch Suchen [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code häufig gestellte Fragen](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)



