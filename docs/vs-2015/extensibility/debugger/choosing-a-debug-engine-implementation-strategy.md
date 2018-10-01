---
title: Auswählen einer Implementierungsstrategie für die Debug-Engine | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8a9e449fddad18c3ff0e95786ab852745407e6a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512155"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Auswählen einer Implementierungsstrategie für die Debug-Engine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Auswählen einer Strategie für Debug-Engine-Implementierung](https://docs.microsoft.com/visualstudio/extensibility/debugger/choosing-a-debug-engine-implementation-strategy).  
  
Verwenden Sie die Run-Time-Architektur, um Ihre Implementierungsstrategie für die Debug-Engine (DE) festzulegen. Die Debug-Engine kann in-Process an das Programm debuggten, werden auf den Visual Studio sitzungsbasierter Debug-Manager (SDM) oder Out-of-Process zu in-Process erstellt werden. Die folgenden Richtlinien sollen Sie zum Auswählen dieser drei Strategien unterstützen.  
  
## <a name="guidelines"></a>Richtlinien  
 Es ist zwar möglich, für das DE Out-of-Process-sein, sowohl das SDM und das Programm debuggt werden, besteht in der Regel kein Grund dafür. Aufrufe über Prozessgrenzen hinweg sind relativ langsam.  
  
 Debuggen von Engines sind bereits verfügbar, für die systemeigene Win32-Laufzeitumgebung und für die common Language Runtime-Umgebung. Wenn Sie die DE für einer dieser Umgebungen ersetzen müssen, müssen Sie die DE in-Process mit dem SDM erstellen.  
  
 Andernfalls können Sie auswählen zwischen der DE Erstellen von in-Process, das SDM oder in-Process an das Programm debuggt werden. Es ist wichtig zu berücksichtigen, ob die ausdrucksauswertung des DE häufig Zugriff auf den Symbolspeicher Programm benötigt, und gibt an, ob die Symbolspeicher in den Arbeitsspeicher für schnellen Zugriff geladen werden kann. Beachten Sie auch Folgendes ein:  
  
-   Erstellen Sie wenn nicht viele Aufrufe zwischen der ausdrucksauswertung und den Symbolspeicher vorhanden sind, oder der Symbolspeicher in den Speicherbereich SDM gelesen werden kann, die DE in-Process an das SDM. Sie müssen die CLSID des Debug-Engine, das SDM zurückkehren, wenn es in Ihr Programm angefügt wird. Das SDM verwendet diese CLSID zum Erstellen einer in-Process-Instanz des DE.  
  
-   Wenn das Programm den Zugriff auf das Symbol Store die DE aufgerufen werden muss, erstellen Sie die DE in-Process mit dem Programm an. In diesem Fall erstellt das Programm die Instanz des DE.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

