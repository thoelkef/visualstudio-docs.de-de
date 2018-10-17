---
title: Roadmap für die Erweiterung des Debuggers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f9272728f79e402800c56f6e8c9ce0fc008e3ad
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370866"
---
# <a name="roadmap-for-extending-the-debugger"></a>Roadmap für die Erweiterung des Debuggers
Diese Dokumentation enthält Referenz und Handbuch Informationen zum Erweitern der [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] debugger mit dem [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen die Dokumentation enthält Beispiele, eine umfassende Referenz und mehrere repräsentative Szenarien, in denen veranschaulicht typische Verwendungsweisen des Debuggers anzupassen.  
  
 Dem Compiler und die Ausgabe bestimmen, was erforderlich ist, um in Ihrem Produkt Debuggen einzurichten. Wenn Ihr Compiler:  
  
-   Betrifft das native Windows-Betriebssystem und schreibt eine *. PDB* -Datei können Sie Programme debuggen, mit der nativen Code Debug-Engine (DE), integriert in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Sie müssen keine ausdrucksauswertung DE oder einen Ausdruck zu implementieren. Die ausdrucksauswertung wird für die Syntax der Programmiersprache C++ geschrieben.  
  
-   Erzeugt die Microsoft intermediate Language (MSIL) auszugeben, können Sie Programme debuggen, mit verwaltetem Code Debug-Engine DE, die auch in integriert ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Daher müssen Sie nur eine ausdrucksauswertung implementieren. Eine Beispiel-ausdrucksauswertung wird für Sie bereitgestellt. Weitere Informationen finden Sie unter den folgenden Themen:  
  
     [Auswertung von Ausdrücken](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Ausdrucksauswertungskontext](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Ausdrucksauswertung im Unterbrechungsmodus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Schreiben Sie eine common Language Runtime-ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Ziele eine proprietäre Betriebssystemkomponente oder eine andere Runtime-Umgebung müssen Sie Ihre eigenen DE zu schreiben. Ein Tutorial, erstellen eine einfache DE Verwendung von ATL-COM, wird bereitgestellt. Weitere Informationen finden Sie unter den folgenden Themen:  
  
     [Erstellen einer benutzerdefinierten Debug-engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Tutorial: Erstellen einer Debug-Engine, die Verwendung von ATL-COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementieren eines portanbieters](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Beispiele](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)