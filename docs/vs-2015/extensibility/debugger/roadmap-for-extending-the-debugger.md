---
title: Roadmap für die Erweiterung des Debuggers | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695956"
---
# <a name="roadmap-for-extending-the-debugger"></a>Roadmap für die Erweiterung des Debuggers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Diese Dokumentation enthält Anleitungen und Referenzinformationen zum Erweitern des [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] Debuggers mit dem [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die debuggingdokumentation enthält Beispiele, eine umfassende Referenz und einige repräsentative Szenarios, in denen typische Möglichkeiten zum Anpassen des Debuggers aufgezeigt werden.  
  
 Der Compiler und seine Ausgabe bestimmen, was Sie tun müssen, um das Debuggen in Ihrem Produkt zu implementieren. Wenn der Compiler Folgendes:  
  
- Gibt das systemeigene Windows-Betriebssystem an und schreibt. PDB-Datei: Sie können Programme mit dem systemeigenen Code Debug Engine (de) Debuggen, das in integriert ist [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Sie müssen keine de-oder-Ausdrucks Auswertung implementieren. Die Ausdrucks Auswertung wird für die Syntax der Programmiersprache C++ geschrieben.  
  
- Erzeugt die MSIL-Ausgabe (Microsoft Intermediate Language). Sie können Programme mit dem verwalteten Code Debugmodul de Debuggen, das auch in integriert ist [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Daher muss nur eine Ausdrucks Auswertung implementiert werden. Eine Beispiel Ausdrucks Auswertung wird für Sie bereitgestellt. Weitere Informationen finden Sie unter den folgenden Themen:  
  
     [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Ausdrucksauswertungskontext](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Ausdrucksauswertung im Unterbrechungsmodus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Schreiben einer Ausdrucksauswertung für die Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Als Ziel für ein proprietäres Betriebssystem oder eine andere Laufzeitumgebung müssen Sie Ihre eigene de schreiben. Ein Tutorial, das eine einfache de mithilfe von ATL-COM erstellt, wird bereitgestellt. Weitere Informationen finden Sie unter den folgenden Themen:  
  
     [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Tutorial: aufbauen einer Debug-Engine mithilfe von ATL-COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementieren eines Portanbieters](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Beispiele](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
