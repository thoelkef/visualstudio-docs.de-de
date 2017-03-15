---
title: "Gewusst wie: Aktivieren und Deaktivieren von &quot;Bearbeiten und Fortfahren&quot; | Microsoft Docs"
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
  - "/INCREMENTAL (Linkeroption)"
  - "Codeänderungen übernehmen (Befehl)"
  - "Unterbrechungsmodus, Übernehmen von Codeänderungen"
  - "Codeänderungen, Übernehmen im Unterbrechungsmodus"
  - "Bearbeiten und Fortfahren, Übernehmen von Codeänderungen"
  - "Bearbeiten und Fortfahren, Deaktivieren"
  - "Bearbeiten und Fortfahren, Aktivieren"
  - "Sprungbefehl"
  - "INCREMENTAL (Linkeroption)"
  - "Schrittbefehl"
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Aktivieren und Deaktivieren von &quot;Bearbeiten und Fortfahren&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Zur Entwurfszeit kann "Bearbeiten und Fortfahren" im Dialogfeld **Optionen** aktiviert oder deaktiviert werden.  Sie können diese Einstellung nicht ändern, während Sie debuggen.  
  
 Die Funktion "Bearbeiten und Fortfahren" funktioniert nur in Debugversionen.  Bei systemeigenem C\+\+ muss die \/INCREMENTAL\-Option verwendet werden, damit "Bearbeiten und Fortfahren" funktioniert.  
  
## Prozeduren  
  
#### So aktivieren bzw. deaktivieren Sie "Bearbeiten und Fortfahren"  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Öffnen Sie im Dialogfeld **Optionen** den Knoten **Debugging**, und wählen Sie die Kategorie **Bearbeiten und Fortfahren** aus.  
  
3.  Mit dem Kontrollkästchen **Bearbeiten und Fortfahren aktivieren** können Sie die Funktion aktivieren.  Deaktivieren Sie das Kontrollkästchen, wenn Sie die Funktion deaktivieren möchten.  
  
    > [!NOTE]
    >  Wenn IntelliTrace aktiviert ist und Sie IntelliTrace\-Ereignisse und Aufrufinformationen erfassen, wird "Bearbeiten und Fortfahren" deaktiviert.  Weitere Informationen finden Sie unter [Konfigurieren von IntelliTrace zum Sammeln von Debuginformationen](http://msdn.microsoft.com/de-de/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 ["Bearbeiten und Fortfahren"](../debugger/edit-and-continue.md)   
 [Bearbeiten und Fortfahren, Debuggen, Dialogfeld "Optionen"](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)