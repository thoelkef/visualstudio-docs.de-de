---
title: "Integrieren von Gesch&#228;ftsdaten in SharePoint | Microsoft Docs"
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
  - "BDC [SharePoint-Entwicklung in Visual Studio], Aggregieren von Daten"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Geschäftsdaten"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Erstellen eines Modells"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Daten"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Aggregieren von Daten"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Geschäftsdaten"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Erstellen eines Modells"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Daten"
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Integrieren von Gesch&#228;ftsdaten in SharePoint
  Sie können Geschäftsdaten in SharePoint integrieren.  Geschäftsdaten können von Back\-End\-Serveranwendungen wie [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel und SAP oder einem Webdienst stammen.  Benutzer können Geschäftsdaten mithilfe von externen Listen oder Geschäftsdatenwebparts in SharePoint anzeigen, hinzufügen, aktualisieren oder löschen. Benutzer können auch offline in einer Microsoft Office\-Anwendung wie Microsoft Outlook auf diese Daten zugreifen.  Weitere Informationen finden Sie unter [Wenn Sie externe Daten anzeigen können](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Um Daten in SharePoint zu integrieren, erstellen Sie ein Modell für den Business Data Connectivity \(BDC\)\-Dienst.  Der BDC\-Dienst ist eine Anwendung in SharePoint, die Informationen zu Daten in Geschäftsanwendungen speichert.  Weitere Informationen finden Sie unter [Business Data Connectivity \(BDC\)\- \- Dienst](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## Modelle in Visual Studio  
 Modelle in Visual Studio ermöglichen es Ihnen, benutzerdefinierten Code zu schreiben, um Daten aus Back\-End\-Datenquellen abzurufen und zu aktualisieren.  Sie können auch Daten aus mehreren Datenquellen aggregieren.  Beispielsweise können Sie eine Liste von Kunden anzeigen, die Daten aus einer [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]\-Datenbank und einem Webdienst enthält.  
  
 Darüber hinaus können Sie Modelle importieren, die bereits in SharePoint bereitgestellt wurden.  Nachdem Sie ein Modell importiert haben, können Sie benutzerdefinierten Code hinzufügen oder Visual Studio verwenden, um das Modell zu verpacken und in mehreren SharePoint\-Serverfarmen bereitzustellen.  Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## Entwerfen eines Modells in Visual Studio  
 Sie können ein Modell mit einem Designer und mehreren Toolfenstern entwerfen.  Während Sie das Modell entwerfen, generiert Visual Studio das Modell\-XML.  Weitere Informationen finden Sie unter [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Ein Modell enthält Entitäten und Methoden.  
  
### Entitäten  
 Eine Entität beschreibt eine Auflistung von Feldern.  Eine Entität kann z. B. eine Tabelle in einer Datenbank darstellen.  Eine Entität wird in SharePoint als externer Inhaltstyp angezeigt.  Weitere Informationen zu externen Inhaltstypen, finden Sie unter [Was sind externe Inhaltstypen?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### Methoden  
 Eine Methode ermöglicht es den Consumern eines externen Inhaltstyps, eine Aktion für die Felder einer Entität auszuführen.  Eine Updater\-Methode könnte es Benutzern beispielsweise ermöglichen, die Adresse und das Geburtsdatum eines Kunden zu ändern, wobei `Address` und `BirthDate` Felder der `Customer`\-Entität sind.  
  
 Visual Studio generiert eine Dienstcodedatei für jede Entität im Modell.  Wenn Sie dem Modell eine Methode hinzufügen, generiert Visual Studio eine entsprechende Methode in der Dienstcodedatei.  Fügen Sie jeder Methode Code hinzu, um die entsprechende Aufgabe auszuführen.  Wenn Sie dem Modell beispielsweise eine Creator\-Methode hinzufügen, generiert Visual Studio eine Creator\-Methode in der Dienstcodedatei.  Diese Methode wird vom BDC\-Dienst aufgerufen, wenn ein Benutzer in einer Liste, die auf dem Modell basiert, auf die Schaltfläche **Neues Element** klickt.  Fügen Sie der Creator\-Methode daher Code hinzu, mit dem einer Datenquelle neue Daten hinzugefügt werden.  Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)|Erläutert, wie ein neues Modell erstellt wird oder wie ein aus SharePoint exportiertes Modell importiert wird.|  
|[Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)|Erklärt, wie die Elemente eines Modells mit Visual Studio\-Entwurfstools entworfen werden.|  
|[Wann SharePoint Designer in Visual Studio verwendet, sofern Lösungen mit BCS erstellt werden](http://go.microsoft.com/fwlink/?LinkID=183448)|Hilft Ihnen bei der Entscheidung, ob Sie Visual Studio oder SharePoint Designer verwenden sollten, um ein Modell für die BDC zu erstellen.|  
  
  