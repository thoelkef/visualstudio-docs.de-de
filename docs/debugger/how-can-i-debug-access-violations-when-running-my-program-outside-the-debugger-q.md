---
title: Debuggen von zugriffsverletzungen bei der Ausführung einer app außerhalb des Debuggers | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b65c10b07b93e657a9e3cb9da5f94d5c9b14362
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854021"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Wie können Zugriffsverletzungen, die beim Ausführen des Programms außerhalb des Debuggers auftreten, gedebuggt werden?

## <a name="problem-description"></a>Problembeschreibung  
 Das Programm läuft in der Visual Studio-Umgebung einwandfrei. Wird es jedoch eigenständig unter dem Windows-Betriebssystem ausgeführt, generiert es eine Zugriffsverletzung. Wie kann dieses Problem behoben werden?  
  
## <a name="solution"></a>Lösung  
 Legen Sie die Option für das [Just-In-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md) fest, und führen Sie das Programm im eigenständigen Modus aus, bis eine Zugriffsverletzung auftritt. Dann können Sie im Dialogfeld **Zugriffsverletzung** auf **Abbrechen** klicken, um den Debugger zu starten.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugging Native Code FAQs (Häufig gestellte Fragen zum Debuggen von nativem Code)](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)