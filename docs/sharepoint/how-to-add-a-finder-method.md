---
title: "Gewusst wie: Hinzuf&#252;gen einer Finder-Methode | Microsoft Docs"
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
  - "BDC [SharePoint-Entwicklung in Visual Studio], Finder-Methode"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Abrufen von Entitäten"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Zurückgeben von Entitäten"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Finder-Methode"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Abrufen von Entitäten"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Zurückgeben von Entitäten"
ms.assetid: 5de2cae3-d1f7-4a68-aac0-458967aca692
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Gewusst wie: Hinzuf&#252;gen einer Finder-Methode
  Um den Business Data Connectivity\-Dienst zu ermöglichen eine Liste von Entitäten in einem Webpart oder einer Liste anzeigen kann, müssen Sie eine *Finder\-Methode* erstellen.  Eine Finder\-Methode ist eine spezielle Methode, die eine Auflistung von Entitätsinstanzen zurückgibt.  Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### So erstellen Sie eine Finder\-Methode  
  
1.  Wählen Sie im BDC\-Designer eine Entität aus.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Klicken Sie auf der Menüleiste **Weitere Fenster**, **BDC\-Methodendetails**, **Ansicht** aus.  
  
     Das Fenster **BDC\-Methodendetails** wird geöffnet.  Weitere Informationen zum Fenster **BDC\-Methodendetails** finden Sie unter [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der Liste **Methode hinzufügen** wählen Sie **Finder\-Methode erstellen** aus.  
  
     Visual Studio fügt eine Methode, einen Rückgabeparameter und einen Typdeskriptor hinzu.  
  
4.  Konfigurieren Sie den Typdeskriptor als Entitätsauflistungs\-Typdeskriptor.  Weitere Informationen zum Erstellen eines Entitätsauflistungs\-Typdeskriptors finden Sie unter [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Sie müssen diesen Schritt nicht ausführen, wenn Sie der Entität eine bestimmte Finder\-Methode hinzugefügt haben.  Visual Studio verwendet den Typdeskriptor, den Sie in der bestimmten Finder\-Methode definiert haben.  
  
5.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü der Dienstcodedatei, die für die Entität generiert wurde, und dann **Code anzeigen** aus.  Weitere Informationen zur Dienstcodedatei finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Fügen Sie der Finder\-Methode Code hinzu.  Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Ruft Daten aus einer Datenquelle.  
  
    -   Gibt eine Liste von Entitäten an den BDC\-Dienst.  
  
     Im folgenden Beispiel wird eine Auflistung von `Contact`\-Entitäten unter Verwendung von Daten aus der AdventureWorks\-Beispieldatenbank für SQL Server zurückgegeben.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert des Felds `ServerName` durch den Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## Siehe auch  
 [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
  