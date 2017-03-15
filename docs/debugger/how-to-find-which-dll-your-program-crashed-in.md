---
title: "Gewusst wie: Feststellen, welche DLL zum Absturz des Programms gef&#252;hrt hat | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dll"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, DLL-Abstürze"
  - "Debuggen [Visual Studio], DLL-Abstürze"
  - "DLLs, Ladereihenfolge von"
  - "Fehler [Debugger], DLL-Abstürze"
  - "Modulliste (Dialogfeld)"
  - "Module (Fenster)"
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Gewusst wie: Feststellen, welche DLL zum Absturz des Programms gef&#252;hrt hat
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Wenn die Anwendung während des Aufrufs einer System\-DLL oder des Codes eines anderen Benutzers abstürzt, muss herausgefunden werden, welche DLL zur Zeit des Absturzes aktiv war.  Wenn Sie feststellen, dass eine DLL außerhalb der eigenen Anwendung abgestürzt ist, kann die Ursache mithilfe des Fensters **Module** ermittelt werden.  
  
### So ermitteln Sie im Fenster "Module" die Stelle, die einen Absturz verursacht hat  
  
1.  Notieren Sie die Adresse, an der der Absturz stattgefunden hat.  
  
2.  Wählen Sie im Menü **Debuggen** die Option **Fenster** aus, und klicken Sie auf **Module**.  
  
3.  Suchen Sie im Fenster **Module** die Spalte **Adresse**.  Zur Anzeige der Spalte müssen Sie möglicherweise die Bildlaufleiste verwenden.  
  
4.  Klicken Sie im oberen Spaltenbereich auf die Schaltfläche **Adresse**, um die DLLs der Adresse nach zu sortieren.  
  
5.  Durchsuchen Sie die sortierte Liste nach der DLL, in deren Adressbereich die vom Absturz betroffene Stelle zu finden ist.  
  
6.  Namen und Pfad der DLL finden Sie in der Spalte **Name** bzw. **Pfad**.  
  
## Siehe auch  
 [Gewusst wie: Debuggen von systemeigenen DLLs](../debugger/how-to-debug-native-dlls.md)   
 [Gewusst wie: Verwenden des Fensters Module](../debugger/how-to-use-the-modules-window.md)