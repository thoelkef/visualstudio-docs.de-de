---
title: "Gewusst wie: Hinzuf&#252;gen einer Creator-Methode"
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
  - "BDC [SharePoint-Entwicklung in Visual Studio], Hinzufügen von Entitäten"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Hinzufügen von Entitätsinstanzen"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Creator"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Hinzufügen von Entitäten"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Hinzufügen von Entitätsinstanzen"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Creator"
ms.assetid: 52f0382f-10a0-4a51-83fe-6f22f4647df8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Gewusst wie: Hinzuf&#252;gen einer Creator-Methode
  Mit einer Creator\-Methode werden der Datenquelle einer Entität neue Daten hinzugefügt.  Der Business Data Connectivity \(BDC\)\- \- Dienst ruft diese Methode auf, wenn Benutzer die Schaltfläche **Neues Element** auf dem Menüband einer Liste auswählen, die auf dem Modell basiert.  Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### So fügen Sie eine Creator\-Methode hinzu  
  
1.  Wählen Sie im BDC\-Designer eine Entität aus.  
  
2.  Klicken Sie auf der Menüleiste **Weitere Fenster**, **BDC\-Methodendetails**, **Ansicht** aus.  
  
     Das Fenster **BDC\-Methodendetails** wird geöffnet.  Weitere Informationen über dieses Fenster, finden Sie unter [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der Liste **Methode hinzufügen** wählen Sie **Creator\-Methode erstellen** aus.  
  
     Visual Studio werden dem Modell die folgenden Elemente hinzu, und diese Elemente werden im Fenster **BDC\-Methodendetails**.  
  
    -   Eine Methode mit dem Namen **Create**.  
  
    -   Ein Eingabeparameter für die Methode.  
  
    -   Ein Rückgabeparameter für die Methode.  
  
    -   Typdeskriptoren für die Parameter.  
  
    -   Eine Methodeninstanz für die Methode.  
  
     Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü der Dienstcodedatei, die für die Entität generiert wurde, und dann **Code anzeigen** aus.  
  
     Die Codedatei für den Entitätsdienst wird im Code\-Editor geöffnet.  Weitere Informationen zur Codedatei für den Entitätsdienst finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Fügen Sie der Creator\-Methode Code hinzu, mit dem der Datenquelle Daten hinzugefügt werden.  Im folgenden Beispiel wird ein Kontakt der AdventureWorks\-Beispieldatenbank für SQL Server hinzu.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert des Felds `ServerName` durch den Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#4)]  
  
## Siehe auch  
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
  