---
title: Auswählen einer Implementierungsstrategie für die Debug-Engine | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b71176d7cc8f60393a42e3d300e84c2c2de5ef05
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945917"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Auswählen einer Implementierungsstrategie für die Debug-engine
Verwenden Sie die Run-Time-Architektur, um Ihre Implementierungsstrategie für die Debug-Engine (DE) festzulegen. Sie können die Debug-Engine-in-Process an das Programm erstellen, die Sie debuggen. Erstellen Sie die Debug-Engine im Prozess in der Visual Studio sitzungsbasierter Debug-Manager (SDM). Alternativ können die Debug-Engine-Out-of-Process zu erstellen. Die folgenden Richtlinien sollten Sie für diese drei Strategien für die Auswahl helfen.  
  
## <a name="guidelines"></a>Richtlinien  
 Es ist zwar möglich, für das DE Out-of-Process-sein, das SDM und das Programm, das Sie Debuggen, ist in der Regel keinen Grund dafür. Aufrufe über Prozessgrenzen hinweg sind relativ langsam.  
  
 Debuggen von Engines sind bereits verfügbar, für die systemeigene Win32-Laufzeitumgebung und der common Language Runtime-Umgebung. Wenn Sie die DE für entweder Umgebung ersetzen müssen, sollten Sie die DE in-Process mit dem SDM erstellen.  
  
 Andernfalls Sie erstellen Sie entweder die DE in-Process an das SDM oder in-Process an das Programm Sie debuggen. Sie müssen überlegen, ob es sich bei die ausdrucksauswertung des DE häufig Zugriff auf den Symbolspeicher Programm benötigt. Oder, wenn der Speicher den schnellen Zugriff auf der Symbolspeicher geladen werden kann. Berücksichtigen Sie auch die folgenden Methoden:  
  
-   Erstellen Sie wenn nicht viele Aufrufe zwischen der ausdrucksauswertung und den Symbolspeicher vorhanden sind, oder der Symbolspeicher in den Speicherbereich SDM gelesen werden kann, die DE in-Process an das SDM. Sie müssen die CLSID des Debug-Engine, das SDM zurückkehren, wenn es in Ihr Programm angefügt wird. Das SDM verwendet diese CLSID zum Erstellen einer in-Process-Instanz des DE.  
  
-   Wenn das Programm den Zugriff auf das Symbol Store die DE aufgerufen werden muss, erstellen Sie die DE in-Process mit dem Programm an. In diesem Fall erstellt das Programm die Instanz des DE.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)