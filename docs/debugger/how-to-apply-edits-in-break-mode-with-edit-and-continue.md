---
title: "Gewusst wie: Anwenden von Bearbeitungen im Unterbrechungsmodus mithilfe von &quot;Bearbeiten und Fortfahren&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "Unterbrechungsmodus, Übernehmen von Codeänderungen"
  - "Code, Bearbeiten im Unterbrechungsmodus"
  - "Verfassen von Code, Bearbeiten im Unterbrechungsmodus"
  - "Bearbeiten und Fortfahren [Visual Basic], Übernehmen von Bearbeitungen im Unterbrechungsmodus"
  - "Bearbeiten und Fortfahren, Übernehmen von Bearbeitungen im Unterbrechungsmodus"
  - "Bearbeiten, Unterbrechungsmodus"
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# Gewusst wie: Anwenden von Bearbeitungen im Unterbrechungsmodus mithilfe von &quot;Bearbeiten und Fortfahren&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können mit Bearbeiten und Fortfahren den Code im Unterbrechungsmodus bearbeiten und anschließend fortfahren, ohne die Codeausführung anzuhalten und erneut starten zu müssen.  
  
 Bearbeiten und Fortfahren steht in den folgenden Debugszenarios nicht zur Verfügung:  
  
-   Debuggen im gemischten Modus \(systemeigen\/verwaltet\).  
  
-   SQL\-Debuggen.  
  
-   Debuggen eines  Dr.Watson\-Dumps.  
  
-   Bearbeiten von Code nach einer nicht behandelten Ausnahme, wenn die Option **Aufrufliste für unbehandelte Ausnahmen entladen** nicht aktiviert ist.  
  
-   Debuggen einer eingebetteten Laufzeitanwendung.  
  
-   Debuggen einer Anwendung mit **Anfügen an** anstatt die Anwendung über das Menü **Debuggen** mit dem Befehl **Starten** auszuführen.  
  
-   Debuggen von optimiertem Code.  
  
-   Debuggen von verwaltetem Code, wenn das Ziel eine 64\-Bit\-Anwendung ist.  Wenn Sie Bearbeiten und Fortfahren verwenden möchten, müssen Sie das Ziel auf x86 festlegen.  \(*Projekt***Eigenschaften**, Registerkarte **Kompilieren**, **Erweiterte Compilereinstellungen**.\).  
  
-   Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.  
  
### So bearbeiten Sie Code im Unterbrechungsmodus  
  
1.  Wechseln Sie in den Unterbrechungsmodus, indem Sie folgendermaßen vorgehen:  
  
    -   Legen Sie einen Haltepunkt im Code fest, wählen Sie im Menü **Debuggen** den Befehl **Debuggen starten**, und warten Sie, bis die Anwendung auf den Haltepunkt trifft.  
  
         – oder –  
  
    -   Fangen Sie mit dem Debuggen an, und wählen Sie anschließend im Menü **Debuggen** den Befehl **Alle unterbrechen**.  
  
         – oder –  
  
    -   Wenn eine Ausnahme ausgelöst wird, wählen Sie im **Ausnahmen\-Assistenten** den Befehl **Bearbeiten aktivieren**.  
  
2.  Nehmen Sie die gewünschten zulässigen Codeänderungen vor.  
  
     Weitere Informationen finden Sie unter [Nicht unterstützte Bearbeitungen beim Bearbeiten und Fortsetzen in Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Bei dem Versuch, mit Bearbeiten und Fortfahren eine nicht zulässige Änderung vorzunehmen, wird die bearbeitete Stelle violett wellenförmig unterstrichen, und in der Aufgabeliste wird eine Aufgabe angezeigt.  Sie können mit der Codeausführung erst fortfahren, nachdem Sie die nicht zulässige Codeänderung rückgängig gemacht haben.  
  
3.  Klicken Sie im Menü **Debuggen** auf **Weiter**, um mit der Ausführung fortzufahren.  
  
     Der Code wird nun einschließlich der vorgenommenen Änderungen ausgeführt, die jetzt Teil des Projekts sind.  
  
## Siehe auch  
 [Nicht unterstützte Bearbeitungen beim Bearbeiten und Fortsetzen in Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Bearbeiten und Fortfahren \(Visual Basic\)](../debugger/edit-and-continue-visual-basic.md)