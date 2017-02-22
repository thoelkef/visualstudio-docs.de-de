---
title: "Debuggen bereitgestellter Webanwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET-Webanwendungen"
  - "ASP.NET, Debuggen von Webanwendungen"
  - "Debuggen von Webdiensten"
  - "Webdienste, Debuggen"
  - "XML-Webdienste, Debuggen"
  - "XML, Debuggen von Webdiensten"
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen bereitgestellter Webanwendungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine Webanwendung debuggen müssen, die auf einem Produktionsserver ausgeführt wird, sollten Sie besondere Vorsicht walten lassen.  Wenn der Debugger an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess angehängt wird, wird z. B. beim Erreichen eines Haltepunkts der gesamte verwaltete Code im Arbeitsprozess angehalten.  Das Anhalten des gesamten verwalteten Codes im Arbeitsprozess kann zu einem Arbeitsstopp für alle Benutzer des Servers führen.  Wenn Sie auf einem Produktionsserver debuggen, müssen Sie unter allen Umständen die möglichen Auswirkungen auf die Produktion beachten.  
  
 Um eine bereitgestellte und ausgeführte Anwendung über [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu debuggen, müssen Sie den Debugger an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess anhängen und sicherstellen, dass der Debugger auf Symbole für die Anwendung zugreifen kann.  Außerdem müssen Sie die Quelldateien für die Anwendung lokalisieren und öffnen.  Weitere Informationen finden Sie unter [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Gewusst wie: Herausfinden des ASP.NET\-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md) und [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
>  Viele [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendungen verweisen auf DLLs, die Geschäftslogik oder sonstigen nützlichen Code enthalten.  Durch einen solchen Verweis wird die DLL automatisch vom lokalen Computer in den Ordner \\bin des virtuellen Verzeichnisses der Webanwendung kopiert.  Beim Debuggen sollten Sie beachten, dass die Webanwendung nicht auf die Kopie der DLL auf dem lokalen Computer, sondern auf diese Kopie der DLL verweist.  
  
 Das Anhängen an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess unterscheidet sich nicht vom Anhängen an einen beliebigen anderen Remoteprozess.  Wenn das passende Projekt nicht geöffnet ist, wird nach dem Anhängen ein Dialogfeld angezeigt, sobald die Anwendung unterbrochen wird.  Dieses Dialogfeld fordert Sie auf, den Speicherort der Quelldateien der Anwendung anzugeben.  Der im Dialogfeld eingegebene Dateiname muss mit dem Dateinamen übereinstimmen, der in den Debugsymbolen \(auf dem Webserver\) angegeben ist.  Weitere Informationen finden Sie unter [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## Siehe auch  
 [Debuggen von ASP.NET\- und AJAX\-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md)   
 [Gewusst wie: Debuggen für ASP.NET\-Anwendungen aktivieren](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Gewusst wie: Herausfinden des ASP.NET\-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)