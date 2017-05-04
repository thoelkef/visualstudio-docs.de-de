---
title: "Gewusst wie: Hinzuf&#252;gen einer Deleter-Methode | Microsoft Docs"
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
  - "BDC [SharePoint-Entwicklung in Visual Studio], Deleter"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Löschen von Daten"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Löschen von Entitätsinstanzen"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Entfernen von Daten"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Deleter"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Löschen von Daten"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Löschen von Entitätsinstanzen"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Entfernen von Daten"
ms.assetid: 3362eaf4-5dc7-4450-9009-b296308ae61f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Gewusst wie: Hinzuf&#252;gen einer Deleter-Methode
  Sie können es einem Endbenutzer ermöglichen, einen Datensatz aus einer externen Liste auf einer SharePoint\-Website zu löschen, indem Sie dem Modell eine *Deleter*\-Methode hinzufügen.  Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### So erstellen Sie eine Deleter\-Methode  
  
1.  Wählen Sie im BDC\-Designer eine Entität aus.  
  
2.  Klicken Sie auf der Menüleiste **Weitere Fenster**, **BDC\-Methodendetails**, **Ansicht** aus.  
  
     Das Fenster **BDC\-Methodendetails** wird geöffnet.  Weitere Informationen über dieses Fenster finden Sie unter [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der Liste **Methode hinzufügen** wählen Sie **Deleter\-Methode erstellen** aus.  
  
     Mit Visual Studio werden dem Modell die folgenden Elemente hinzugefügt.  Diese Elemente werden im Fenster **BDC\-Methodendetails** angezeigt.  
  
    -   Eine Methode mit dem Namen **Delete**.  
  
    -   Ein Eingabeparameter für die Methode.  
  
    -   Ein Typdeskriptor für den Parameter.  
  
    -   Eine Methodeninstanz für die Methode.  
  
     Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü der Dienstcodedatei, die für die Entität generiert wurde, und dann **Code anzeigen** aus.  
  
     Die Codedatei für den Entitätsdienst wird im Code\-Editor geöffnet.  Weitere Informationen zur Codedatei für den Entitätsdienst finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Fügen Sie der Deleter\-Methode Code hinzu, um einen Datensatz zu löschen.  Im folgenden Beispiel wird unter Verwendung der AdventureWorks\-Beispieldatenbank für SQL Server ein Zeilenelement aus einem Verkaufsauftrag gelöscht.  
  
    > [!NOTE]  
    >  Die Methode in diesem Beispiel verwendet zwei Eingabeparameter.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert des Felds `ServerName` durch den Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#6](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## Siehe auch  
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
  