---
title: "Erstellen einer Assoziation zwischen Entit&#228;ten"
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
  - "VS.SharePointTools.BDC.Association_Dialog"
dev_langs: 
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
ms.assetid: c908448c-13d3-4d2f-89ad-8d709b2958fb
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Erstellen einer Assoziation zwischen Entit&#228;ten
  Sie können im Business Data Connectivity \(BDC\)\-Modell Beziehungen zwischen Entitäten definieren, indem Sie Zuordnungen erstellen.  Visual Studio generiert Methoden, die Consumern des Modells zu jeder Zuordnung Informationen bereitstellen.  Diese Methoden können von SharePoint\-Webparts, Listen oder benutzerdefinierten Anwendungen verwendet werden, um Datenbeziehungen in einer Benutzeroberfläche anzuzeigen \(UI\).  
  
## Erstellen einer Zuordnung  
 Erstellen Sie eine Zuordnung, indem Sie das Steuerelement **Zuordnung** in Visual Studio **Werkzeugkasten** auswählen, die erste Entität \(als Quellentität bezeichnet\), und dann die zweite Entität klicken \(als Zielentität bezeichnet\).  Sie können die Details der Zuordnung im **Zuordnungs\-Editor** definieren.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen einer Assoziation zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## Zuordnungsmethoden  
 Anwendungen wie SharePoint Geschäftsdaten\-Webparts nutzen Zuordnungen durch Aufruf von Methoden in der Dienstklasse einer Entität.  Sie können der Dienstklasse einer Entität Methoden hinzufügen, indem Sie sie im **Zuordnungs\-Editor** auswählen.  
  
 Standardmäßig fügt der **Zuordnungs\-Editor** den Quell\- und Zielentitäten eine Zuordnungsnavigationsmethode hinzu.  Eine Zuordnungsnavigationsmethode in der Quellentität ermöglicht es Consumern, eine Liste von Zielentitäten abzurufen.  Eine Zuordnungsnavigationsmethode in der Zielentität ermöglicht es Consumern, die Quellentität abzurufen, die sich auf eine Zielentität bezieht.  
  
 Sie müssen jeder dieser Methoden Code hinzufügen, um die entsprechenden Informationen zurückzugeben.  Sie können auch andere Typen von Methoden hinzufügen, um erweiterte Szenarios zu unterstützen.  Weitere Informationen zu diesen Methoden finden, Sie [Unterstützte Vorgänge](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## Typen von Zuordnungen  
 Sie können im BDC\-Designer zwei Typen von Zuordnungen erstellen: auf Fremdschlüsseln basierte Zuordnungen und Zuordnungen ohne Fremdschlüssel.  
  
### Auf Fremdschlüsseln basierte Zuordnung  
 Sie können eine auf Fremdschlüsseln basierte Zuordnung erstellen, indem Sie in der Quellentität einen Bezeichner mit in der Zielentität definierten Typdeskriptoren verknüpfen.  Diese Beziehung ermöglicht es Consumern des Modells, ihren Benutzern eine verbesserte Benutzeroberfläche bereitzustellen.  Beispiele: Ein Formular in Outlook, das es einem Benutzer ermöglicht, einen Auftrag zu erstellen, in dem die Kunden in einer Dropdownliste angezeigt werden, oder eine Liste von Aufträgen in SharePoint, die es Benutzern ermöglicht, eine Profilseite für einen Kunden zu öffnen.  
  
 Um eine auf Fremdschlüsseln basierte Zuordnung zu erstellen, verknüpfen Sie Bezeichner und Typdeskriptoren, die denselben Namen und Typ aufweisen.  Sie können z. B. eine auf Fremdschlüsseln basierte Zuordnung zwischen einer `Contact`\-Entität und einer `SalesOrder`\-Entität erstellen.  Die `SalesOrder`\-Entität gibt einen `ContactID`\-Typdeskriptor als Teil des Rückgabeparameters von Finder\- oder spezifischen Finder\-Methoden zurück.  Beide Typdeskriptoren werden im **Zuordnungs\-Editor** angezeigt.  Um eine auf Fremdschlüsseln basierte Beziehung zwischen der `Contact` \- Entität und `SalesOrder` \- Entität zu erstellen, wählen Sie den `ContactID` \- Bezeichner neben jedem dieser Felder.  
  
 Fügen Sie in der Zuordnungsnavigatormethode der Quellentität Code hinzu, mit dem eine Auflistung von Zielentitäten zurückgegeben wird.  Im folgenden Beispiel werden die Aufträge für einen Kontakt zurückgegeben.  
  
 [!code-csharp[SP_BDC#7](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#7)]  
  
 Fügen Sie in der Zuordnungsnavigatormethode der Zielentität Code hinzu, mit dem eine verknüpfte Quellentität zurückgegeben wird.  Im folgenden Beispiel wird der Kontakt zurückgegeben, der sich auf den Auftrag bezieht.  
  
 [!code-csharp[SP_BDC#8](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#8)]  
  
### Zuordnung ohne Fremdschlüssel  
 Sie können eine Zuordnung erstellen, ohne Feldtypdeskriptoren Bezeichner zuzuordnen.  Erstellen Sie diese Art von Zuordnung, wenn die Quellentität keine direkte Beziehung mit der Zielentität aufweisen soll.  Eine `SalesOrderDetail`\-Tabelle verfügt z. B. nicht über einen Fremdschlüssel, der einem Primärschlüssel in einer `Contact`\-Tabelle zugeordnet ist.  
  
 Wenn Sie Informationen in der Tabelle `SalesOrderDetail` anzeigen, die sich auf einen `Contact` beziehen, können Sie eine Zuordnung ohne Fremdschlüssel zwischen der `Contact`\-Entität und der `SalesOrderDetail`\-Entität erstellen.  
  
 Geben Sie in der Zuordnungsnavigationsmethode der `Contact`\-Entität die `SalesOrderDetail`\-Entitäten zurück, indem Sie Tabellen verknüpfen oder eine gespeicherte Prozedur aufrufen.  
  
 Im folgenden Beispiel werden Details aller Aufträge zurückgegeben, indem Tabellen verknüpft werden.  
  
 [!code-csharp[SP_BDC#9](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#9)]  
  
 Geben Sie in der Zuordnungsnavigationsmethode der `SalesOrderDetail`\-Entität den verwandten `Contact` zurück.  Das folgende Beispiel veranschaulicht dies.  
  
 [!code-csharp[SP_BDC#10](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## Siehe auch  
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Gewusst wie: Erstellen einer Assoziation zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md)  
  
  