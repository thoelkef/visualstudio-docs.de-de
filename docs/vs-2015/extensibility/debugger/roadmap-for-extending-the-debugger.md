---
title: Roadmap für die Erweiterung des Debuggers | Microsoft-Dokumentation
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
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fce5c11b5393bb8e3887b1369866a5f0906195d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242100"
---
# <a name="roadmap-for-extending-the-debugger"></a>Roadmap für die Erweiterung des Debuggers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Diese Dokumentation enthält Referenz und Handbuch Informationen zum Erweitern der [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] debugger mit dem [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuggen die Dokumentation enthält Beispiele, eine umfassende Referenz und mehrere repräsentative Szenarien, in denen veranschaulicht typische Verwendungsweisen des Debuggers anzupassen.  
  
 Dem Compiler und die Ausgabe bestimmen, was Sie tun, um das Debuggen in Ihrem Produkt zu implementieren. Wenn Ihr Compiler:  
  
-   Betrifft das native Windows-Betriebssystem und schreibt ein. PDB-Datei können Sie Programme debuggen, mit der nativen Code Debug-Engine (DE), integriert in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Sie müssen sich nicht zum Implementieren einer ausdrucksauswertung DE oder einen Ausdruck. Die ausdrucksauswertung wird für die Syntax der Programmiersprache C++ geschrieben.  
  
-   Erzeugt die Microsoft intermediate Language (MSIL) auszugeben, können Sie Programme debuggen, mit verwaltetem Code Debug-Engine DE, die auch in integriert ist [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Daher müssen Sie nur eine ausdrucksauswertung implementieren. Eine Beispiel-ausdrucksauswertung wird für Sie bereitgestellt. Weitere Informationen finden Sie unter den folgenden Themen:  
  
     [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Ausdrucksauswertungskontext](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Ausdrucksauswertung im Unterbrechungsmodus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Schreiben einer Ausdrucksauswertung für die Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Ziele eine proprietäre Betriebssystemkomponente oder eine andere Runtime-Umgebung müssen Sie Ihre eigenen DE zu schreiben. Ein Tutorial, erstellen eine einfache DE Verwendung von ATL-COM, wird bereitgestellt. Weitere Informationen finden Sie unter den folgenden Themen:  
  
     [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Tutorial: Erstellen einer Debug-Engine, die Verwendung von ATL-COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementieren eines Portanbieters](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Beispiele](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

