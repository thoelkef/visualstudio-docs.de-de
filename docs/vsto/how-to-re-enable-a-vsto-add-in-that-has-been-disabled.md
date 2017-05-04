---
title: "Gewusst wie: Erneutes Aktivieren eines VSTO-Add-Ins, das deaktiviert wurde | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Warning.DisabledAddIn"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Deaktivierte Add-Ins"
  - "Add-Ins [Office-Entwicklung in Visual Studio], Deaktiviert"
  - "Add-Ins [Office-Entwicklung in Visual Studio], Aktivieren"
ms.assetid: 69719a0a-984c-42cd-80a2-1367c866e5df
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Gewusst wie: Erneutes Aktivieren eines VSTO-Add-Ins, das deaktiviert wurde
  VSTO\-Add\-Ins, die ein unerwartetes Verhalten aufweisen, können von Microsoft Office\-Anwendungen deaktiviert werden. Wenn Ihr VSTO\-Add\-In beim Debuggen von der Anwendung nicht geladen wird, wurde das VSTO\-Add\-In von der Anwendung möglicherweise hart oder weich deaktiviert.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## Hart deaktivierte VSTO\-Add\-Ins  
 Die harte Deaktivierung kann auftreten, wenn ein VSTO\-Add\-In zur unerwarteten Beendigung einer Anwendung führt. Sie kann auch auf dem Entwicklungscomputer auftreten, wenn Sie den Debugger beenden, während der <xref:Microsoft.Office.Tools.AddIn.Startup>\-Ereignishandler im VSTO\-Add\-In ausgeführt wird.  
  
#### So aktivieren Sie ein VSTO\-Add\-In erneut  
  
1.  Klicken Sie in der Anwendung auf Registerkarte **Datei**.  
  
2.  Klicken Sie auf die Schaltfläche *ApplicationName***\-Optionen**.  
  
3.  Klicken Sie im Bereich "Kategorien" auf **Add\-Ins**.  
  
4.  Überprüfen Sie im Detailbereich, ob das VSTO\-Add\-In in der Liste **Deaktivierte Anwendungs\-Add\-Ins** angezeigt wird.  
  
     In der Spalte **Name** ist der Name der Assembly und in der Spalte **Speicherort** der vollständige Pfad des Anwendungsmanifests angegeben.  
  
5.  Klicken Sie im Feld **Verwalten** auf **Deaktivierte Elemente**, und klicken Sie dann auf **Gehe zu**.  
  
6.  Wählen Sie das VSTO\-Add\-In aus, und klicken Sie auf **Aktivieren**.  
  
7.  Klicken Sie auf **Schließen**.  
  
## Weich deaktivierte VSTO\-Add\-Ins  
 Die weiche Deaktivierung kann auftreten, wenn ein VSTO\-Add\-In einen Fehler erzeugt, der nicht zur unerwarteten Beendigung der Anwendung führt. Ein VSTO\-Add\-In kann von einer Anwendung z. B. weich deaktiviert werden, wenn es einen Ausnahmefehler auslöst, während der <xref:Microsoft.Office.Tools.AddIn.Startup>\-Ereignishandler ausgeführt wird.  
  
> [!NOTE]  
>  Beim erneuten Aktivieren eines weich deaktivierten VSTO\-Add\-Ins versucht die Anwendung sofort, das VSTO\-Add\-In zu laden. Wenn das Problem, das anfänglich zur weichen Deaktivierung des VSTO\-Add\-Ins durch die Anwendung geführt hat, nicht behoben wurde, wird das VSTO\-Add\-In von der Anwendung erneut weich deaktiviert.  
  
#### So aktivieren Sie ein VSTO\-Add\-In erneut  
  
1.  Klicken Sie in der Anwendung auf Registerkarte **Datei**.  
  
2.  Klicken Sie auf die Schaltfläche *ApplicationName***\-Optionen**.  
  
3.  Klicken Sie im Bereich "Kategorien" auf **Add\-Ins**.  
  
4.  Überprüfen Sie im Detailbereich, ob das VSTO\-Add\-In in der Liste **Inaktive Anwendungs\-Add\-Ins** angezeigt wird.  
  
     In der Spalte **Name** ist der Name der Assembly und in der Spalte **Speicherort** der vollständige Pfad des Anwendungsmanifests angegeben.  
  
5.  Klicken Sie im Feld **Verwalten** auf **COM\-Add\-Ins**, und klicken Sie dann auf **Gehe zu**.  
  
6.  Aktivieren Sie im Dialogfeld **COM\-Add\-Ins** das Kontrollkästchen neben dem deaktivierten VSTO\-Add\-In.  
  
7.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Debuggen von Office-Projekten](../vsto/debugging-office-projects.md)   
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  