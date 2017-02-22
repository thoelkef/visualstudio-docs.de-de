---
title: "Gewusst wie: Verwenden von &quot;Bearbeiten und Fortfahren&quot; (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
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
  - "Bearbeiten und Fortfahren [C#], Informationen über Bearbeiten und Fortfahren"
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Verwenden von &quot;Bearbeiten und Fortfahren&quot; (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit Bearbeiten und Fortfahren für C\# können Sie beim Debuggen Codeänderungen im Unterbrechungsmodus vornehmen.  Die Änderungen können übernommen werden, ohne die Debugsitzung anhalten und neu starten zu müssen.  
  
 Bearbeiten und Fortfahren wird automatisch aufgerufen, wenn Sie im Unterbrechungsmodus Änderungen vornehmen und anschließend einen Ausführungsbefehl des Debuggers wählen, wie beispielsweise **Weiter**, **Schritt** oder **Nächste Anweisung festlegen**, oder wenn Sie im Debuggerfenster eine Funktion auswerten.  
  
> [!NOTE]
>  Die Funktion "Bearbeiten und Fortfahren" wird beim Debuggen von Compact Framework, optimiertem Code, gemischtem systemeigenem\/verwaltetem Code und SQL Server Common Language Runtime \(CLR\)\-Integrationscode nicht unterstützt.  Bei dem Versuch, in einem solchen Szenario Codeänderungen vorzunehmen, wird im Debugger ein Dialogfeld mit dem Hinweis angezeigt, dass Bearbeiten und Fortfahren nicht unterstützt wird.  
  
### So rufen Sie Bearbeiten und Fortfahren automatisch auf  
  
1.  Nehmen Sie im Unterbrechungsmodus eine Änderung am Quellcode vor.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Weiter**, **Schritt** oder **Nächste Anweisung festlegen**, oder werten Sie eine Funktion in einem Debuggerfenster aus.  
  
     Der neue Code wird kompiliert, und das Debuggen wird mit neuem Code fortgesetzt.  Einige Änderungen werden von Bearbeiten und Fortfahren nicht unterstützt.  Weitere Informationen finden Sie unter [Unterstützte Codeänderungen \(C\#\)](../debugger/supported-code-changes-csharp.md).  
  
### So aktivieren bzw. deaktivieren Sie "Bearbeiten und Fortfahren"  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie im Dialogfeld **Optionen** den Knoten **Debuggen**, und klicken Sie auf **Bearbeiten und Fortfahren**.  
  
3.  Aktivieren bzw. deaktivieren Sie im Dialogfeld **Optionen** auf der Seite **Bearbeiten und Fortfahren** das Kontrollkästchen **Bearbeiten und Fortfahren aktivieren**.  
  
     Die Einstellungen werden beim Neustarten der Debugsitzung aktiv.  
  
## Siehe auch  
 [Bearbeiten und Fortfahren \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [Unterstützte Codeänderungen \(C\#\)](../debugger/supported-code-changes-csharp.md)   
 [Bearbeiten und Fortfahren: Fehlermeldungen und Warnungen \(C\#\)](../misc/edit-and-continue-errors-and-warnings-csharp.md)