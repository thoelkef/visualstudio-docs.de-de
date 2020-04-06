---
title: Debug-Engine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4cb00796f8db23a43cd81a06d80d0fac40f075e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739067"
---
# <a name="debug-engine"></a>Debug-Engine
Ein Debugmodul (DE) arbeitet mit dem Interpreter oder Betriebssystem zusammen, um Debugdienste wie Ausführungssteuerung, Haltepunkte und Ausdrucksauswertung bereitzustellen. Die DE ist für die Überwachung des Status eines zu debuggenden Programms verantwortlich. Um dies zu erreichen, verwendet die DE alle Methoden, die ihr in der unterstützten Laufzeit zur Verfügung stehen, sei es von der CPU oder von APIs, die von der Laufzeit bereitgestellt werden.

 Beispielsweise stellt die Common Language Runtime (CLR) Mechanismen zum Überwachen eines laufenden Programms über die ICorDebugXXX-Schnittstellen bereit. Eine DE, die die CLR unterstützt, verwendet die entsprechenden ICorDebugXXX-Schnittstellen, um die Nachverfolgung eines zu debuggenden verwalteten Codeprogramms zu behalten. Anschließend werden alle Statusänderungen an den Sitzungsdebug-Manager (SDM) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] weitergeleitet, der diese Informationen an die IDE weiterleitet.

> [!NOTE]
> Ein Debugmodul zielt auf eine bestimmte Laufzeit ab, d. h. auf das System, in dem das debugge Programm ausgeführt wird. Die CLR ist die Laufzeit für verwalteten Code, und die Win32-Laufzeit ist für systemeigene Windows-Anwendungen. Wenn die von Ihnen erstellte Sprache auf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eine dieser beiden Laufzeiten abzielen kann, werden bereits die erforderlichen Debug-Engines bereitstellt. Alles, was Sie implementieren müssen, ist ein Ausdrucksbewerter.

## <a name="debug-engine-operation"></a>Debug-Engine-Betrieb
 Die Überwachungsdienste werden über die DE-Schnittstellen implementiert und können dazu führen, dass das Debugpaket zwischen verschiedenen Betriebsmodi wechselt. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md). Es gibt in der Regel nur eine DE-Implementierung pro Laufzeitumgebung.

> [!NOTE]
> Zwar gibt es separate DE-Implementierungen [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]für Transact-SQL und VBScript und [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] eine einzelne DE.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Das Debuggen ermöglicht es Debugmodulen, eine von zwei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Möglichkeiten auszuführen: entweder im gleichen Prozess wie die Shell oder im gleichen Prozess wie das zu debuggende Zielprogramm. Letzteres Formular tritt in der Regel auf, wenn es sich bei dem zu debuggenden Prozess tatsächlich um ein Skript handelt, das unter einem Interpreter ausgeführt wird. Das Debugmodul muss über intime Kenntnisse des Interpreters verfügen, um das Skript überwachen zu können. In diesem Fall ist der Interpreter eigentlich eine Laufzeit; Debug-Engines sind für bestimmte Laufzeitimplementierungen. Darüber hinaus kann die Implementierung einer einzelnen DE über Prozess- und Maschinengrenzen verteilt werden (z. B. Remote-Debugging).

 Die DE macht [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Debugging-Schnittstellen verfügbar. Die gesamte Kommunikation erfolgt über COM. Ob die DE in-Process, out-of-Process oder auf einem anderen Computer geladen wird, wirkt sich nicht auf die Komponentenkommunikation aus.

 Die DE arbeitet mit einer Ausdrucksauswertungskomponente, um die DE für diese bestimmte Laufzeit zu aktivieren, um die Syntax von Ausdrücken zu verstehen. Die DE arbeitet auch mit einer Symbolhandlerkomponente, um auf die symbolischen Debuginformationen zuzugreifen, die vom Sprachcompiler generiert werden. Weitere Informationen finden Sie unter [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md) und [Symbolanbieter](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
- [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)
- [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)
