---
title: "Gewusst wie: Hinzuf&#252;gen einer Updater-Methode"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [SharePoint-Entwicklung in Visual Studio], Updater"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Aktualisieren von Daten"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Aktualisieren von Entitätsinstanzen"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Updater"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Aktualisieren von Daten"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Aktualisieren von Entitätsinstanzen"
ms.assetid: c97e443c-58dc-4f8f-8cbd-0d52d8a6a06b
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Gewusst wie: Hinzuf&#252;gen einer Updater-Methode
  Sie können es Benutzern ermöglichen, Geschäftsdaten in einer externen SharePoint\-Liste zu aktualisieren, indem Sie eine *Updater*\-Methode erstellen.  Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### So erstellen Sie eine Updater\-Methode  
  
1.  Wählen Sie im BDC\-Designer eine Entität aus.  
  
2.  Klicken Sie auf der Menüleiste **Weitere Fenster**, **BDC\-Methodendetails**, **Ansicht** aus.  
  
     Das Fenster BDC\-Methodendetails wird geöffnet.  Weitere Informationen über dieses Fenster finden Sie unter [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der Liste **Methode hinzufügen** wählen Sie **Updater\-Methode erstellen** aus.  
  
     Mit Visual Studio werden dem Modell die folgenden Elemente hinzugefügt.  Diese Elemente werden im Fenster BDC\-Methodendetails angezeigt.  
  
    -   Eine Methode, die dem Namen **Aktualisieren**.  
  
    -   Ein Eingabeparameter für die Methode.  
  
    -   Ein Typdeskriptor für den Parameter.  Standardmäßig verwendet Visual Studio den Entitätstypdeskriptor, den Sie für die Finder\-Methode definiert haben \(zum Beispiel: Kontakt\).  
  
    -   Eine Methodeninstanz für die Methode.  
  
     Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
    > [!NOTE]  
    >  Wenn der Bezeichner des Entitätstyps ein Feld in einer Datenbanktabelle darstellt, die nicht automatisch generiert wird, legen Sie die Eigenschaft **Pre\-Updater\-Feld** auf **True** fest.  
  
4.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü der Dienstcodedatei, die für die Entität generiert wurde, und dann **Code anzeigen** aus.  
  
     Die Codedatei für den Entitätsdienst wird im Code\-Editor geöffnet.  Weitere Informationen zu dieser Datei, finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Fügen Sie der Daten aktualisieren Update\-Methode hinzu.  Im folgenden Beispiel werden Informationen für einen Kontakt in der AdventureWorks\-Beispieldatenbank für SQL Server aktualisiert.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert des Felds `ServerName` durch den Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#5)]  
  
## Siehe auch  
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [How to: Add an Updater Method](../sharepoint/how-to-add-an-updater-method.md)   
 [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
  