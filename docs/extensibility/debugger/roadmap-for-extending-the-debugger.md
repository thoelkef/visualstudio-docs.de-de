---
title: "Roadmap f&#252;r die Erweiterung des Debuggers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK]-roadmap"
  - "Debugging-SDK, roadmap"
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Roadmap f&#252;r die Erweiterung des Debuggers
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Diese Dokumentation bietet Handbuch und Referenzinformationen zum Erweitern des Debuggers für [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)][!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , das Debuggen, Dokumentation enthält Beispiele, einen umfassenden Verweis und repräsentative einige Szenarien, die zeigen typische Möglichkeiten, den Debugger anzupassen.  
  
 Der Compiler und ihre Ausgabe bestimmen, was Sie tun müssen, um das Debuggen im Produkt zu implementieren.  Wenn der Compiler:  
  
-   Legt das systemeigene Fenster des Betriebssystems an und schreibt, können Sie eine PDB\-Datei mit dem Testprogramme Debuggen Modul mit systemeigenem Code \(DE\), das in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integriert ist.  Sie müssen keine DE oder einen Ausdrucksauswertung zu implementieren.  Die Ausdrucksauswertung wird für die Syntax der C\+\+\-Programmiersprache geschrieben.  
  
-   Erzeugt die Microsoft Intermediate Language \(MSIL\) ausgegeben, können Sie mit dem Testprogramme DE Modul Debuggen von verwaltetem Code, die auch in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integriert ist.  Daher müssen Sie nur einen Ausdrucksauswertung implementieren.  Ein Ausdrucksauswertung Beispiel wird bereitgestellt.  Weitere Informationen finden Sie unter den folgenden Themen:  
  
     [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Ausdrucksauswertungs\-Kontext](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Ausdrucksauswertung im Unterbrechungsmodus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Schreiben eines Common Language Runtime\-Ausdrucksauswerter](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Zielt auf ein herstellereigenes Betriebssystem oder eine beliebige andere Laufzeitumgebung, müssen Sie schreiben, DE besitzen.  Ein Lernprogramm, das ein einfaches DE mit ATL wird bereitgestellt.  Weitere Informationen finden Sie unter den folgenden Themen:  
  
     [Debuggen eines benutzerdefinierten Moduls erstellen](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Lernprogramm: Ein Debuggen Modul mit ATL erstellen](http://msdn.microsoft.com/de-de/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementieren eines Anschluss\-Lieferanten](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Proben](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## Siehe auch  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)