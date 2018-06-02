---
title: Erstellen einer Assoziation zwischen Entitäten | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3d0475653fe3c5950e39e9f8293d5179e9380db6
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692170"
---
# <a name="creating-an-association-between-entities"></a>Erstellen einer Assoziation zwischen Entitäten
  Sie können Beziehungen zwischen Entitäten in Ihrem Modell Business Data Connectivity (BDC) durch das Erstellen von Zuordnungen definieren. Methoden, die Consumern des Modells mit Informationen über jede Zuordnung bereitstellen, generiert Visual Studio. Diese Methoden können von SharePoint-Webparts, Listen oder benutzerdefinierten Anwendungen zum Anzeigen von datenbeziehungen in einer Benutzeroberfläche (UI) verwendet werden.  
  
## <a name="create-an-association"></a>Erstellen Sie eine Zuordnung
 Erstellen Sie eine Zuordnung, indem Sie auswählen der **Zuordnung** Steuerelement in Visual Studio **Toolbox**, die erste Entität (die Quellentität genannt) auswählen, und drücken Sie dann die zweite Entität (aufgerufen, die Zielentität). Sie können die Details der Zuordnung im Definieren der **Zuordnungs-Editor**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer Assoziation zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## <a name="association-methods"></a>Zuordnung von Methoden
 Anwendungen wie SharePoint Geschäftsdaten-Webparts belegen Zuordnungen durch Aufrufen der Methoden in der Dienstklasse einer Entität. Sie können Methoden auf die Dienstklasse einer Entität hinzufügen, indem Sie sie in Auswählen der **Zuordnungs-Editor**.  
  
 Wird standardmäßig die **Zuordnungs-Editor** Fügt eine Zuordnung Navigation-Methode für die Quell- und Ziel-Entitäten. Eine Zuordnung Navigation-Methode in der Quellentität ermöglicht Consumern, eine Liste von Zielentitäten abzurufen. Eine Zuordnung Navigation-Methode in der Zielentität ermöglicht es Consumern, die Quellentität abzurufen, die auf eine Zielentität bezieht.  
  
 Sie müssen jede dieser Methoden, um die entsprechenden Informationen zurückzugeben Code hinzufügen. Sie können auch andere Arten von Methoden zum Unterstützen von komplexeren Szenarien hinzufügen. Weitere Informationen zu jeder dieser Methoden finden Sie unter [unterstützte Vorgänge](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## <a name="types-of-associations"></a>Typen von Zuordnungen
 Sie können zwei Arten von Zuordnungen im BDC-Designer erstellen: foreign Key-basierte Zuordnungen und Fremdschlüssel Zuordnungen.  
  
### <a name="foreign-key-based-association"></a>Foreign Key-basierte Zuordnung
 Sie können eine foreign Key-basierte Zuordnung erstellen, indem Sie einen Bezeichner in der Quellentität in die Zielentität definierten Deskriptoren eingeben. Diese Beziehung ermöglicht es Consumern des Modells, ihren Benutzern eine verbesserte Benutzeroberfläche bereitzustellen. Angenommen, ein Formular in Outlook, mit der Benutzer einen Auftrag erstellen, der Kunden in einer Dropdownliste angezeigt werden können. oder eine Liste der Aufträge in SharePoint, die Benutzern ermöglicht, eine Seite "Profil" für einen Kunden zu öffnen.  
  
 Um eine foreign Key-basierte Zuordnung zu erstellen, verknüpfen Sie Bezeichner und Typdeskriptoren Sie, die den gleichen Namen und Typ aufweisen. Beispielsweise können Sie eine foreign Key-basierten Zuordnung zwischen erstellen eine `Contact` Entität und eine `SalesOrder` Entität. Die `SalesOrder` Entität gibt eine `ContactID` Typdeskriptor als Teil der Rückgabeparameter der Finder oder bestimmten Finder-Methode. Beide Typdeskriptoren angezeigt, der **Zuordnungs-Editor**. So erstellen eine foreign Key-basierte Beziehung zwischen der `Contact` Entität und `SalesOrder` Entität, wählen Sie die `ContactID` Bezeichner neben jeder dieser Felder.  
  
 Fügen Sie Code zur Zuordnung Navigator-Methode der Quellentität, die eine Auflistung von Zielentitäten zurückgibt. Im folgende Beispiel werden die Aufträge für einen Kontakt zurückgegeben.  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 Fügen Sie Code zur Zuordnung Navigator-Methode der Zielentität, die eine Quellentität zurückgibt. Das folgende Beispiel gibt den Kontakt, der die dem Auftrag zugeordnet ist.  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>Zuordnung ohne Fremdschlüssel
 Sie können eine Zuordnung erstellen, ohne das Zuordnen von Bezeichnern zum Feld Typdeskriptoren. Erstellen Sie diese Art von Zuordnung, wenn die Quellentität keine direkte Beziehung mit der Zielentität. Z. B. eine `SalesOrderDetail` Tabelle besitzt keinen Fremdschlüssel, der auf einen Primärschlüssel in ordnet eine `Contact` Tabelle.  
  
 Wenn Sie Informationen anzeigen möchten die `SalesOrderDetail` Tabelle, die mit verknüpft eine `Contact`, können Sie eine Zuordnung ohne Fremdschlüssel zwischen erstellen die `Contact` Entität und `SalesOrderDetail` Entität.  
  
 In der Zuordnung Navigation-Methode der `Contact` Entität return der `SalesOrderDetail` Entitäten, indem Sie Tabellen verknüpfen oder durch Aufrufen einer gespeicherten Prozedur.  
  
 Im folgende Beispiel gibt Details aller Verkaufsaufträge zurück, indem Sie Tabellen verknüpfen.  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 In der Zuordnung Navigation-Methode der `SalesOrderDetail` Entität zurück, den zugehörigen `Contact`. Dies wird im folgenden Beispiel veranschaulicht:  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>Siehe auch
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Vorgehensweise: Erstellen einer Assoziation zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md)  
  
 