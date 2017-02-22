---
title: "Gewusst wie: Debuggen &#252;ber ein DLL-Projekt | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], DLLs"
  - "Debuggen von DLLs"
  - "DLL-Projekte, Debuggen"
  - "DLLs, Debuggen von Projekten"
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Debuggen &#252;ber ein DLL-Projekt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um mit dem Debuggen eines DLL\-Projekts zu beginnen, müssen Sie die aufrufende Anwendung in den Projekteigenschaften angeben.  Die Eigenschaftenseiten in C\+\+ unterscheiden sich im Hinblick auf Layout und Inhalt von den Eigenschaftenseiten in C\# und Visual Basic.  
  
 Wenn eine verwaltete DLL von systemeigenem Code aufgerufen wird, und Sie sowohl DLL als auch Code debuggen möchten, können Sie dies in den Projekteigenschaften angeben.  Weitere Informationen finden Sie unter [Gewusst wie: Debuggen im gemischten Modus](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
>  In den Express\-Versionen von Visual Studio kann keine externe aufrufende Anwendung angegeben werden.  Um eine DLL in einer Express\-Version zu debuggen, fügen Sie der Lösung ein ausführbares Projekt hinzu, legen es als Startpunkt für die Lösung fest  und rufen Methoden in der DLL vom ausführbaren Projekt aus auf.  
  
### So geben Sie die aufrufende Anwendung in einem C\+\+\-Projekt an  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus.  Wechseln Sie zur Registerkarte **Debuggen**.  
  
2.  Stellen Sie sicher, dass das Feld **Konfiguration** am oberen Rand des Fensters auf **Debuggen** festgelegt ist.  
  
3.  Wechseln Sie zu **Konfigurationseigenschaften \/ Debuggen**.  
  
4.  Wählen Sie in der Liste **Zu startender Debugger** entweder **Lokaler Windows\-Debugger** oder **Remote\-Windows\-Debugger** aus.  
  
5.  Wählen Sie im Feld **Befehl** oder **Remotebefehl** den vollqualifizierten Pfadnamen der Anwendung.  
  
6.  Fügen Sie im Feld **Befehlsargumente** die notwendigen Programmargumente ein.  
  
### So geben Sie die aufrufende Anwendung in einem C\#\- oder Visual Basic\-Projekt an  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus.  Wechseln Sie zur Registerkarte **Debuggen**.  
  
     Wählen Sie **Externes Programm starten**, und fügen Sie den vollqualifizierten Pfadnamen des Programms ein, das ausgeführt werden soll.  
  
     Wenn Sie die Befehlszeilenargumente für das externe Programm hinzufügen müssen, geben Sie diese im Feld **Befehlszeilenargumente** ein.  
  
2.  Sie können eine Anwendung auch als URL aufrufen.  \(Dies empfiehlt sich u. U., wenn Sie eine verwaltete DLL debuggen, die von einer lokalen ASP.NET\-Anwendung verwendet wird.\)  
  
     Klicken Sie unter **Startaktion** auf das Optionsfeld **Browser mit folgender URL starten:**, und geben Sie die URL ein.  
  
### So debuggen Sie über das DLL\-Projekt  
  
1.  Legen Sie die gewünschten Haltepunkte fest.  
  
2.  Starten Sie das Debuggen \(drücken Sie F5, klicken Sie auf den grünen Pfeil, oder klicken Sie auf **Debuggen \/ Debuggen starten**\).  
  
## Siehe auch  
 [Debuggen von DLL\-Projekten](../debugger/debugging-dll-projects.md)   
 [Projekteinstellungen für C\#\-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Projekteinstellungen für eine Visual Basic\-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Projekteinstellungen für eine C\+\+\-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)