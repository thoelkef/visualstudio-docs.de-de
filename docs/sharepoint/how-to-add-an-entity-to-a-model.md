---
title: "Gewusst wie: Hinzuf&#252;gen einer Entit&#228;t zu einem Modell"
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
  - "EntityTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [SharePoint-Entwicklung in Visual Studio], Hinzufügen einer Entität"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Entität"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Hinzufügen einer Entität"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Entität"
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Gewusst wie: Hinzuf&#252;gen einer Entit&#228;t zu einem Modell
  Um eine Entität zu erstellen, fügen Sie einem Entitätssteuerelement von **Werkzeugkasten** in Visual Studio auf den Business Data Connectivity \(BDC\)\- \- Designer hinzu.  
  
### So fügen Sie dem Modell eine Entität hinzu  
  
1.  Erstellen Sie ein BDC\-Projekt, oder öffnen Sie ein vorhandenes BDC\-Projekt.  Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  In **Werkzeugkasten** aus der Gruppe **BusinessDataCatalog**, fügen Sie einem Steuerelement **Entität** auf den Designer hinzu.  
  
     Die neue Entität wird im Designer angezeigt.  Visual Studio fügt dem XML der BDC\-Modelldatei im Projekt ein `<Entity>`\-Element hinzu.  Weitere Informationen zu den Attributen eines Entity\-Elements, Sie finden [Entität](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  Klicken Sie im Designer öffnen Sie das Kontextmenü für die Entität, wählen Sie **Hinzufügen** und wählen Sie dann **Bezeichner** aus.  
  
     Ein neuer Bezeichner wird für die Entität angezeigt.  
  
    > [!NOTE]  
    >  Sie können den Namen der Entität und den Bezeichner im Fenster **Eigenschaften** ändern.  
  
4.  Definieren Sie die Felder der Entität in einer Klasse.  Sie können dem Projekt entweder eine neue Klasse hinzufügen oder eine vorhandene Klasse verwenden, die mit anderen Tools wie dem Object Relational Designer \(O\/R\-Designer\) erstellt wurde.  Im folgenden Beispiel wird eine Entitätsklasse mit dem Namen Contact veranschaulicht.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/cs/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/vb/bdcmodel1/contact.vb#1)]  
  
## Siehe auch  
 [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  