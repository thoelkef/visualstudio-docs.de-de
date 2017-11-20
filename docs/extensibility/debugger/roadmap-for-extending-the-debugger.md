---
title: "Roadmap für die Erweiterung des Debuggers | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af86f2b8daeffeb700b619c4ba0d9cbb00700dd8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="roadmap-for-extending-the-debugger"></a>Roadmap für die Erweiterung des Debuggers
Diese Dokumentation enthält Handbuch und Verweis Informationen zum Erweitern der [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] debugger mit dem [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Debuggen die Dokumentation enthält Beispiele, die eine umfassende Referenz und mehrere repräsentative Szenarien, die zum Anpassen des Debuggers auf welche Weise zu veranschaulichen.  
  
 Der Compiler und dessen Ausgabe bestimmen, was Sie tun können, um das Debuggen in das Produkt zu implementieren müssen. Wenn der Compiler:  
  
-   Als Ziel verwendet das systemeigene Windows-Betriebssystem und schreibt eine. PDB-Datei können Sie Programme debuggen, mit der nativen Code Debugging-Modul (DE), das in integriert ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Sie müssen kein Ausdrucksauswertungsfehler DE oder einen Ausdruck zu implementieren. Die ausdrucksauswertung wird für die Syntax der Programmiersprache C++ geschrieben.  
  
-   Microsoft intermediate Language (MSIL) auszugeben, Debuggen von Programmen mit der verwalteter Code Debugmodul DE, die auch in integriert ist erzeugt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Daher müssen Sie nur eine ausdrucksauswertung implementieren. Eine Beispiel-ausdrucksauswertung wird für Sie bereitgestellt. Weitere Informationen finden Sie unter den folgenden Themen:  
  
     [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Ausdrucksauswertungskontext](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Ausdrucksauswertung im Unterbrechungsmodus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Schreiben einer Ausdrucksauswertung für die Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Ziele eine proprietäre Betriebssystemkomponente oder einer anderen Laufzeit-Umgebung müssen Sie eigene DE schreiben. Ein Lernprogramm, das eine einfache DE Verwendung von ATL-COM erstellt wird bereitgestellt. Weitere Informationen finden Sie unter den folgenden Themen:  
  
     [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Lernprogramm: Erstellen einer Debugging-Modul unter Verwendung von ATL-COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementieren eines Portanbieters](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Beispiele](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)