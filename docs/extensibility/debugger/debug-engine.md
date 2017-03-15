---
title: "Debug-Modul | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule"
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Debug-Modul
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Debuggen Modul \(DE\) arbeitet mit dem Interpreter oder dem Betriebssystem Debugdienste wie Haltepunkte Execution Control und Ausdrucksauswertung bereitzustellen.  DE ist zum Überwachen des Zustands eines Programms, das gedebuggt wird.  Um dies zu erreichen Sie dies, welche Methoden verwendet DE in der unterstützten Laufzeit zur Verfügung stehen, ob der CPUs oder APIs von der Laufzeit angegeben.  
  
 Zum Beispiel stellt die Mechanismen der Common Language Runtime \(CLR\) aufgerufen, um einen ausgeführten Programms durch die ICorDebugXXX\-Schnittstellen zu überwachen.  DE, das die CLR unterstützt, wird die entsprechende ICorDebugXXX\-Schnittstellen, um eine verwaltete Code programm nachzuverfolgen, das gedebuggt wird.  Es gibt dann alle auf das Debuggen von Zustandsänderungen Manager der Sitzung \(SDM\), der solche Informationen an das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE weiterleitet.  
  
> [!NOTE]
>  Ein Modul Debuggen einer bestimmten Laufzeit verwendet das heißt das System an, in dem die gedebuggte Programm ausgeführt wird.  CLR ist die Laufzeit für verwalteten Code, und Win32\-Laufzeit ist für systemeigenen Windows\-Anwendungen.  Wenn die Sprache, die Sie können auf einen dieser beiden Laufzeiten erstellen, stellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bereits über die erforderlichen Debugmodule.  Sämtlicher, den Sie implementieren müssen, ist ein Ausdrucksauswertung.  
  
## Multithreaded Modul\-Vorgang  
 Die Dienste werden durch Überwachen interfaces implementiert und DE können das Debuggen Paket für den Übergang zwischen verschiedenen Betriebsweisen verursachen.  Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).  Es gibt in der Regel nur ein DE implementation pro Laufzeitumgebung.  
  
> [!NOTE]
>  Während es separates DE implementations für Transact\-SQL und gibt [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]und VBScript, geben [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] einzelnes DE frei.  
  
 Debuggen aktiviert[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] von Modulen, um eine der beiden folgenden Arten ausgeführt werden: entweder im gleichen Prozess wie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell oder im gleichen Prozess der das Ziel programm, das gedebuggt wird.  Das letzte Formular tritt in der Regel auf, wenn der Prozess, der gedebuggt wird, tatsächlich ein Skript, der unter einem Interpreter ist, und das Debugmodul muss vertrautes Wissen des Interpreters verfügen, um das Skript zu überwachen.  Beachten Sie, dass in diesem Fall der Interpreter ist eigentlich eine Laufzeit. Debuggen von Modulen sind für bestimmte Implementierungen zur Laufzeit.  Darüber hinaus kann die Implementierung der einzelnen DE über Prozess\- und Grenzen Computer \(z. B. Remotedebugging\) aufgeteilt werden.  
  
 DE macht die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugschnittstellen.  Die Kommunikation erfolgt über COM.  Ob das prozessinterne geladenes DE ist prozessextern oder auf einem anderen Computer wirkt er kein Bestandteil der Remotehostkommunikation.  
  
 DE funktioniert mit einer Komponente für die Ausdrucksauswertung zur Laufzeit bestimmten während dieser DE zu ermöglichen, die Syntax von Ausdrücken zu verstehen.  DE kann auch mit einem Symbol für die Stammkomponente symbolischen Debuginformationen zugreifen, die durch Sprachcompiler generiert werden.  Weitere Informationen finden Sie unter [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md) und [Symbol\-Anbieter](../../extensibility/debugger/symbol-provider.md).  
  
## Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)   
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator.md)   
 [Symbol\-Anbieter](../../extensibility/debugger/symbol-provider.md)