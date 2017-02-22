---
title: "Gewusst wie: Debuggen von ASP.NET-Ausnahmen | Microsoft Docs"
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
  - "ASP.NET, Ausnahmen"
  - "Debuggen [Visual Studio], ASP.NET-Ausnahmen"
  - "Ausnahmen, ASP.NET"
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Debuggen von ASP.NET-Ausnahmen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Debuggen von Ausnahmen ist ein wichtiger Teil bei der Entwicklung einer robusten [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendung.  Allgemeine Informationen über das Debuggen von Ausnahmen finden Sie unter [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Zum Debuggen von nicht behandelten [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Ausnahmen muss sichergestellt sein, dass der Debugger dort anhält.  Die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Laufzeit verfügt über einen Ausnahmehandler der obersten Ebene.  Daher wird der Debugger bei Ausnahmefehlern standardmäßig nie unterbrochen.  Um den Debugger beim Auslösen einer Ausnahme zu unterbrechen, müssen Sie die Einstellung **Unterbrechen bei folgendem Ausnahmezustand: Ausgelöst** für die jeweilige Ausnahme im Dialogfeld **Ausnahmen** auswählen.  
  
 Falls Nur mein Code aktiviert ist, hält der Debugger bei **Unterbrechen bei folgendem Ausnahmezustand: Ausgelöst** nicht sofort an, wenn eine Ausnahme in einer .NET Framework\-Methode oder anderem Systemcode ausgelöst wird.  Stattdessen wird die Ausführung fortgesetzt, bis der Debugger auf Nicht\-Systemcode trifft, und dann unterbrochen.  Folglich müssen Sie den Systemcode nicht schrittweise durchlaufen, wenn eine Ausnahme auftritt.  
  
 Die Einstellung Nur mein Code stellt Ihnen eine weitere Option zur Verfügung, die sogar noch nützlicher sein kann: **Unterbrechen bei folgendem Ausnahmezustand: Vom Benutzercode unbehandelt**.  Bei dieser Einstellung für eine Ausnahme unterbricht der Debugger die Ausführung im Benutzercode nur, wenn die Ausnahme nicht durch den Benutzercode abgefangen und behandelt wird.  Diese Einstellung neutralisiert die Wirkung des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Ausnahmehandlers der obersten Ebene, da dieser kein benutzerdefinierter Code ist.  
  
### So aktivieren Sie Debuggen der ASP.NET\-Ausnahmen mit Nur mein Code  
  
1.  Klicken Sie im Menü **Debuggen** auf **Ausnahmen**.  
  
     Das Dialogfeld **Ausnahmen** wird angezeigt.  
  
2.  Wählen Sie in der Zeile **Common Language Runtime\-AusnahmenAusgelöst** oder **Vom Benutzercode unbehandelt** aus.  
  
     Wenn Sie die Einstellung **Vom Benutzercode unbehandelt** verwenden möchten, muss **Nur mein Code** aktiviert werden.  
  
### Empfohlene Vorgehensweise für die ASP.NET\-Ausnahmebehandlung  
  
-   Platzieren Sie `try … catch`\-Blöcke für Code, der Ausnahmen auslösen kann, die Sie vorhersehen und behandeln können.  Wenn die Anwendung beispielsweise Aufrufe an einen XML\-Webdienst sendet oder direkt an einen SQL Server, sollte dieser Code in **try … catch**\-Blöcken stehen, weil dadurch eine ganze Anzahl Ausnahmen ausgelöst werden kann.