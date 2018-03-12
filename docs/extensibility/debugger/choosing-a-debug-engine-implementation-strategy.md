---
title: "Auswählen einer Strategie für Debug-Modul Implementierung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fae5211ac270832f07038faafbd6f5bc463d3944
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Auswählen einer Strategie für Debug-Engine-Implementierung
Verwenden Sie die Architektur zur Laufzeit zum Bestimmen der Strategie für die Implementierung der Debug-Modul (DE). Debugging-Modul kann im Prozess an das Programm debuggten, als in-Process-Debug-Manager für Visual Studio-Sitzung (SDM) oder Out-of-Process, beide Zertifikate erstellt werden. Die folgenden Richtlinien sollten Sie eines der folgenden drei Strategien auswählen können.  
  
## <a name="guidelines"></a>Richtlinien  
 Es ist zwar möglich, für das DE Out-of-Process werden die SDM sowohl das Programm, das gedebuggt werden, ist in der Regel keinen Grund dafür. Aufrufe über Prozessgrenzen hinweg sind relativ langsam.  
  
 Debuggen Module sind bereits für die systemeigenen Win32-Laufzeitumgebung und für die common Language Runtime-Umgebung verfügbar. Wenn Sie die DE für einer dieser Umgebungen ersetzen müssen, müssen Sie DE in-Process mit dem SDM erstellen.  
  
 Andernfalls können Sie auswählen zwischen DE erstellen, auf die SDM in-Process "oder" in-Process an das Programm, das gedebuggt werden. Es ist wichtig zu berücksichtigen, ob die ausdrucksauswertung die de häufig Zugriff auf den Symbolspeicher Programm benötigt, und gibt an, ob die Symbolspeicher in den Arbeitsspeicher für den schnellen Zugriff geladen werden kann. Beachten Sie auch Folgendes ein:  
  
-   Erstellen Sie wenn es sich nicht viele Aufrufe zwischen der ausdrucksauswertung und den Symbolspeicher oder der Symbolspeicher in SDM-Speicherbereich gelesen werden kann, DE in-Process, das SDM. Sie müssen die SDM die CLSID des Debugging-Modul zurückgeben, wenn es für Ihr Programm anfügt. Die SDM verwendet diese CLSID zum Erstellen einer in-Process-Instanz, die de.  
  
-   Wenn das Programm den Symbolspeicher Zugriff auf die DE aufgerufen werden muss, erstellen Sie DE in-Process mit dem Programm an. In diesem Fall erstellt die Anwendung die Instanz des DE.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)