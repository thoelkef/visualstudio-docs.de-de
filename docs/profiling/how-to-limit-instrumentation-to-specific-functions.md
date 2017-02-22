---
title: "Gewusst wie: Beschr&#228;nken der Instrumentation auf bestimmte Funktionen | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Leistungstools, Beschränken der Instrumentation auf Funktionen"
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Beschr&#228;nken der Instrumentation auf bestimmte Funktionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Instrumentation und Datensammlung auf eine oder mehrere Funktionen beschränken, indem Sie Optionen auf der Seite **Erweitert** der Eigenschaftenseiten für die **Leistungssitzung** oder Zielbinärdatei festlegen:  
  
-   Wenn Sie die Funktionen auf der Eigenschaftenseite der Leistungssitzung angeben, werden nur diese Funktionen in allen instrumentierten Binärdateien der Sitzung instrumentiert.  
  
-   Wenn Sie die Funktionen auf der Eigenschaftenseite einer Zielbinärdatei angeben, werden nur die Funktionen aus dieser bestimmten Binärdatei instrumentiert.  Funktionen in anderen Binärdateien der Leistungssitzung werden wie üblich instrumentiert.  
  
 Die Beschränkung der Datensammlung auf diese Weise wird nur unterstützt, wenn die Instrumentationsmethode zur Profilerstellung ausgewählt wird.  
  
> [!NOTE]
>  Sie können auch die Seite **Erweitert** der Eigenschaftenseiten für die Leistungssitzung verwenden, um andere Optionen festzulegen, die für das Befehlszeileninstrumentationstool [VSInstr](../profiling/vsinstr.md) der Profilerstellungstools verfügbar sind.  
  
### So beschränken Sie die Instrumentation auf bestimmte Funktionen in einer Leistungssitzung  
  
1.  Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf den Sitzungsnamen, und klicken Sie dann auf **Eigenschaften**.  
  
     Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.  
  
2.  Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf **Erweitert**.  
  
3.  Verwenden Sie im Textfeld **Zusätzliche Instrumentationsoptionen** die folgende Syntax, um den Namen der Funktionen einzugeben, die Sie instrumentieren möchten:  
  
     **\/include:** `FuncSpec` **\[;** `FuncSpec` **\]** `...`  
  
     `FuncSpec` ist der Namespace\- und Funktionsname.  Er hat das Format `Namespace`**::**`FunctionName`.  Verwenden Sie ein Semikolon, um mehrere Funktionen zu trennen.  Verwenden Sie ein Sternchen \(\*\), um einen Platzhalter für ein oder mehrere Zeichen anzugeben.  **\/include:MyNS::\***  gibt z. B. alle Funktionen im MyNS\-Namespace an.  
  
    > [!NOTE]
    >  Öffnen Sie zum Aufführen der Funktionen in einer Binärdatei ein Eingabeaufforderungsfenster im Installationsverzeichnis der Profilerstellungstools \(in der Regel das Verzeichnis "\\Team Tools\\Performance Tools" im Installationsverzeichnis von [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]\), und geben Sie "vsinstr \/DumpFuncs" ein.  
  
### So beschränken Sie die Instrumentation auf bestimmte Funktionen in einer Binärdatei  
  
1.  Suchen Sie im **Leistungs\-Explorer** im Knoten **Ziele** der Leistungssitzung nach dem Namen der Binärdatei.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Namen der Binärdatei, und klicken Sie dann auf **Eigenschaften**.  
  
     Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.  
  
3.  Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf **Erweitert**.  
  
4.  Verwenden Sie im Textfeld **Zusätzliche Instrumentationsoptionen** die folgende Syntax, um den Namen der Funktionen einzugeben, die Sie instrumentieren möchten:  
  
     **\/include:** `FuncSpec` **\[;** `FuncSpec` **\]** `...`  
  
     `FuncSpec`  ist der Namespace\- und Funktionsname.  Er hat das Format `Namespace`**::**`FunctionName`.  Verwenden Sie ein Semikolon, um mehrere Funktionen zu trennen.  Verwenden Sie ein Sternchen \(\*\), um einen Platzhalter für ein oder mehrere Zeichen anzugeben.  **\/include:MyNS::\***  gibt z. B. alle Funktionen im MyNS\-Namespace an.  
  
    > [!NOTE]
    >  Öffnen Sie zum Aufführen der Funktionen in einer Binärdatei ein Eingabeaufforderungsfenster im Installationsverzeichnis der Profilerstellungstools \(in der Regel das Verzeichnis "\\Team Tools\\Performance Tools" im Installationsverzeichnis von [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]\), und geben Sie "vsinstr \/DumpFuncs" ein.  
  
## Siehe auch  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)   
 [Gewusst wie: Beschränken der Instrumentation auf bestimmte DLLs](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Gewusst wie: Angeben zusätzlicher Instrumentationsoptionen](../profiling/how-to-specify-additional-instrumentation-options.md)