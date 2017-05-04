---
title: "Gewusst wie: Erstellen einer Assoziation zwischen Entit&#228;ten | Microsoft Docs"
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
  - "AssociationGroupTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [SharePoint-Entwicklung in Visual Studio], Zuordnen von externen Inhaltstypen"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Zuordnungen zwischen Entitäten"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Erstellen einer Zuordnung"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Verwandte Entitäten"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Zuordnen von externen Inhaltstypen"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Zuordnungen zwischen Entitäten"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Erstellen einer Zuordnung"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Verwandte Entitäten"
ms.assetid: 0c095df8-1f40-4c4d-9fed-e125a8429724
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Gewusst wie: Erstellen einer Assoziation zwischen Entit&#228;ten
  Sie können im Business Data Connectivity \(BDC\)\-Modell Beziehungen zwischen Entitäten definieren, indem Sie Zuordnungen erstellen.  Visual Studio generiert Methoden, die Consumern des Modells zu jeder Zuordnung Informationen bereitstellen.  Diese Methoden können von SharePoint\-Webparts, Listen oder benutzerdefinierten Anwendungen verwendet werden, um Datenbeziehungen in einer Benutzeroberfläche anzuzeigen \(UI\).  
  
 Sie können im BDC\-Designer zwei Typen von Zuordnungen erstellen: auf Fremdschlüsseln basierte Zuordnungen und Zuordnungen ohne Fremdschlüssel.  Weitere Informationen finden Sie unter [Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md).  
  
### So erstellen Sie eine Zuordnung zwischen Entitäten  
  
1.  Auf der Registerkarte **BusinessDataConnectivityWerkzeugkasten**, wählen Sie das Element **Zuordnung** aus.  
  
2.  Wählen Sie im BDC\-Designer die Quellentität aus, und klicken Sie dann auf die Zielentität aus.  
  
     Der **Zuordnungs\-Editor** wird angezeigt.  
  
3.  Wenn Sie eine fremdschlüsselbasierte Zuordnung erstellen möchten, aktivieren Sie das Kontrollkästchen **Ist Foreign Key Association**.  
  
    1.  In der Spalte **Quell\-ID** der Tabelle **Bezeichnerzuordnung**, wählen Sie den Bezeichner neben jedem entsprechenden Typdeskriptor aus, der in der Spalte **Feld** wird.  
  
         Wählen Sie in der Spalte **Quell\-ID** beispielsweise `ContactID` neben dem `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID`\-Typdeskriptor und dem `ReadItem.salesOrder.SalesOrder.ContactID`\-Typdeskriptor aus.  
  
4.  Wenn Sie eine Zuordnung ohne Fremdschlüssel erstellen möchten, deaktivieren Sie das Kontrollkästchen **Ist Foreign Key Association**.  
  
5.  Klicken Sie auf die Schaltfläche **OK**.  
  
6.  Im BDC\-Designer wird eine Zeile angezeigt, die die Zuordnung zwischen der Quellentität und der Zielentität darstellt.  
  
     Visual Studio fügt der Dienstklasse der Zielentität und der Dienstklasse der Quellentität eine Zuordnungsnavigatormethode hinzu.  Weitere Informationen zu Zuordnungsnavigationsmethoden, Sie finden. [Unterstützte Vorgänge](http://go.microsoft.com/fwlink/?LinkId=169286)  
  
7.  Fügen Sie in der Zuordnungsnavigatormethode der Quellentität Code hinzu, mit dem eine Auflistung von Zielentitäten zurückgegeben wird.  
  
8.  Fügen Sie in der Zuordnungsnavigatormethode der Zielentität Code hinzu, mit dem die verknüpfte Quellentität zurückgegeben wird.  
  
     Beispiele für Zuordnungsnavigatormethoden finden Sie unter [Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md).  
  
## Siehe auch  
 [Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  