---
title: "Gewusst wie: Einf&#252;gen einer benutzerdefinierten Assembly in eine BDC-Funktion"
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
  - "VS.SharePointTools.BDC.Add_Assemblies_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [SharePoint-Entwicklung in Visual Studio], Hinzufügen eines Verweises"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Benutzerdefinierte Assembly"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Hinzufügen eines Verweises"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Benutzerdefinierte Assembly"
ms.assetid: 2ddf44b9-5f51-4bca-b8bb-94c4bbd1c5f3
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Gewusst wie: Einf&#252;gen einer benutzerdefinierten Assembly in eine BDC-Funktion
  Das Projekt kann innerhalb einer Projektmappe Verweise auf Assemblys aus anderen Projekten enthalten.  Sie müssen diese Assemblys jedoch im Dialogfeld **Assemblys, auf die verwiesen wird, LobSystems zuweisen** der Funktionsdatei des Projekts hinzufügen.  
  
### So schließen Sie eine benutzerdefinierte Assembly in eine Business Data Connectivity \(BDC\)\-Funktion ein  
  
1.  Wählen Sie im **Projektmappen\-Explorer** den Ordner aus, der das BDC\-Modell enthält.  
  
2.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.  
  
3.  Im Fenster **Eigenschaften** wählen Sie die Eigenschaft **Assemblys** und dann die Schaltfläche mit den drei Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](~/sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")\).  
  
     Das Dialogfeld **Assemblys, auf die verwiesen wird, LobSystems zuweisen** wird angezeigt.  
  
4.  In der Liste **Assembly auswählen** wählen Sie die benutzerdefinierte Assembly aus.  
  
    > [!NOTE]  
    >  Assemblys werden nur dann im Dialogfeld **Assemblys, auf die verwiesen wird, LobSystems zuweisen** angezeigt, wenn Sie einen Verweis auf das Projekt mit der Assembly hinzugefügt haben.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds "Verweise hinzufügen"](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  In Gruppe **Verweiseigenschaften** öffnen Sie die Liste, die für die Eigenschaft **LobSystem\-Bereich** wird, wählen das LOB\-System der Methoden, die die benutzerdefinierte Assembly verwendet wird, und wählen Sie dann die Schaltfläche **OK**.  
  
    > [!NOTE]  
    >  Um Code in einer benutzerdefinierten Assembly debuggen zu können, müssen Sie die Assembly zum Projektmappenpaket hinzufügen.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen und Entfernen zusätzlicher Assemblys](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## Siehe auch  
 [Gewusst wie: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Gewusst wie: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Gewusst wie: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  