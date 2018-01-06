---
title: Debuggen des Datenbankmoduls | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 70e572b73f8474f77a17989c790f2e7336f9d7a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debug-engine"></a>Debuggen des Datenbankmoduls
Ein Debugging-Modul (DE) arbeitet mit den Interpreter oder Betriebssystem, z. B. Ausführung-Steuerelement, Haltepunkte und Ausdruck Auswertung Debugdienste bereit. Die DE ist verantwortlich für das Überwachen des Status eines Programms, das gerade gedebuggt wird. Zu diesem Zweck führen Sie verwendet die DE unabhängig Methoden in der unterstützten Runtime verfügbar sind, ob von der CPU oder über APIs durch die Common Language Runtime bereitgestellt.  
  
 Die common Language Runtime (CLR) stellt z. B. Mechanismen, um ein aktives Programm über die Schnittstellen ICorDebugXXX zu überwachen. Eine bereitgestellten Kompatibilitätsrichtlinie, die die CLR unterstützt verwendet die entsprechenden ICorDebugXXX-Schnittstellen zum Nachverfolgen einer verwalteten Code zu debuggenden Programms an. Klicken Sie dann alle Zustandsänderungen in den Sitzung Debug-Manager (SDM), der solche Informationen an weiterleitet kommuniziert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
> [!NOTE]
>  Das Ziel ein Debugging-Modul ist eine bestimmte Laufzeit, d. h. das System, in dem das Programm ausgeführt wird gedebuggten. Die CLR ist die Common Language Runtime für verwalteten Code und die Win32-Laufzeit ist für systemeigene Windows-Anwendungen. Wenn die Sprache, die Sie erstellen eine der folgenden zwei Laufzeiten abzielen kann [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bereits die erforderlichen Debugmodule bereitstellt. Sie implementieren müssen lediglich eine ausdrucksauswertung auf.  
  
## <a name="debug-engine-operation"></a>Debuggen von Datenbankmodul-Vorgang  
 Die Überwachungsdienste werden über die DE-Schnittstellen implementiert und können dazu führen, dass das debugpaket für den Übergang zwischen den verschiedenen Betriebsmodi. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md). Es ist in der Regel nur ein DE-Implementierung pro-Umgebung ausgeführt.  
  
> [!NOTE]
>  Während es separate DE-Implementierungen für Transact-SQL gibt und [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript und [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] Freigeben einer einzelnen Deutschland.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ermöglicht das Debuggen Debuggen Module führen Sie zwei Arten: entweder im gleichen Prozess wie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell oder im selben Prozess wie das Zielprogramm gedebuggt wird. Die letztgenannte Form tritt gewöhnlich auf, wenn der zu debuggende Prozess tatsächlich ein Skript, die unter einem Interpreter ausgeführte und Debugging-Modul fundierte Kenntnisse der der Interpreter verfügen muss, um das Skript zu überwachen. Beachten Sie, dass in diesem Fall der Interpreter tatsächlich eine Laufzeit ist. Debugmodule sind für bestimmte Common Language Runtime-Implementierungen. Darüber hinaus kann die Implementierung einer einzelnen de über Prozess- und Computergrenzen hinweg (z. B. des Remotedebuggens) geteilt werden.  
  
 Die DE macht die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugschnittstellen. Die gesamte Kommunikation wird durch COM Ob die DE in-Process, Out-of-Process oder auf einem anderen Computer geladen wird, beeinflusst nicht Komponente Kommunikation.  
  
 Die DE funktioniert mit einer Expression Evaluator-Komponente so aktivieren Sie die DE für diese bestimmte zur Laufzeit zum besseren Verständnis der Syntax von Ausdrücken. Die DE funktioniert auch mit einer Symbol Handler-Komponente auf den symbolischen Debuginformationen generiert werden, durch den Sprachcompiler. Weitere Informationen finden Sie unter [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md) und [Symbol Anbieter](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)   
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)   
 [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)