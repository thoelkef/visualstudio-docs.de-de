---
title: Debug-Engine | Microsoft-Dokumentation
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
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf2335b907601bb17276b06ae1bef033a1641515
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733329"
---
# <a name="debug-engine"></a>Debug-Engine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Debugmodul (DE) arbeitet mit den Interpreter oder das Betriebssystem wie z. B. Ausführung-Steuerelement, Haltepunkte und Ausdruck Auswertung Debugdienste bereit. Die DE ist verantwortlich für die Überwachung des Status eines gedebuggten Programms. Zu diesem Zweck führen Sie die DE unabhängig Methoden, in der unterstützten Runtime verfügbar sein sollen, ob von der CPU oder von APIs durch die Common Language Runtime bereitgestellt wird verwendet.  
  
 Beispielsweise stellt die common Language Runtime (CLR) Mechanismen zum Überwachen von eines laufenden Programms über die ICorDebugXXX-Schnittstellen bereit. Eine bereitgestellten Kompatibilitätsrichtlinie, die die CLR unterstützt werden die entsprechenden ICorDebugXXX Schnittstellen zum Nachverfolgen einer verwalteten Code zu debuggende Programm wird verwendet. Es kommuniziert dann alle Änderungen des Zustands für die Sitzung Debug-Manager (SDM), der solche Informationen an weiterleitet der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
> [!NOTE]
>  Eine Debug-Engine ist eine bestimmte Laufzeit, also das System, in dem das Programm ausgeführt wird debuggten, ausgerichtet. Die CLR ist die Runtime für verwalteten Code, und die Win32-Laufzeit für systemeigene Windows-Anwendungen. Wenn die Sprache, die Sie erstellen eine dieser zwei Laufzeiten, Ziel kann [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] stellt bereits die erforderlichen Debug-Engines bereit. Sie implementieren müssen lediglich eine ausdrucksauswertung.  
  
## <a name="debug-engine-operation"></a>Debug-Engine-Vorgang  
 Die Überwachung Dienste werden über die DE-Schnittstellen implementiert und können dazu führen, dass das debugpaket für den Übergang zwischen verschiedenen Betriebsmodi. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md). Es gibt in der Regel nur eine Implementierung von DE pro-Umgebung ausgeführt.  
  
> [!NOTE]
>  Es gibt separate DE-Implementierungen für Transact-SQL und [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)], VBScript und [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] eine einzelne DE freigeben.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ermöglicht das Debuggen debug-Engines führen Sie eine von zwei Arten: entweder im selben Prozess wie die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] shell oder in demselben Prozess wie das Zielprogramm gedebuggt wird. Die letztgenannte Form tritt gewöhnlich auf, wenn der gedebuggte Prozess tatsächlich ein Skript, die unter einem Interpreter ausgeführt wird, und die Debug-Engine sehr gute Kenntnisse über den Interpreter verfügen muss, um das Skript zu überwachen. Beachten Sie, dass in diesem Fall der Interpreter tatsächlich eine Laufzeit ist. Debug-Engines sind für eine spezifische Runtime-Implementierungen. Darüber hinaus kann die Implementierung von einem einzelnen DE über Prozess- und Computergrenzen hinweg (z. B. remote debugging) geteilt werden.  
  
 Die DE-macht die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugschnittstellen. Die gesamte Kommunikation wird über COM Ob die DE in-Process, Out-of-Process, oder auf einem anderen Computer geladen wird, wirkt es sich nicht Komponente Kommunikation.  
  
 Die DE funktioniert mit einer Expression Evaluator-Komponente der DE für diese bestimmte zur Laufzeit die Syntax von Ausdrücken zu aktivieren. Die DE funktioniert auch mit einer Symbol-Handler-Komponente auf den symbolischen Debuginformationen vom Sprachcompiler generiert werden. Weitere Informationen finden Sie unter [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md) und [Symbolanbieter](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)   
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)   
 [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)

