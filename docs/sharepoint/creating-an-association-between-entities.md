---
title: Erstellen einer Assoziation zwischen Entitäten | Microsoft-Dokumentation
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c285b699487bd761447e5fbdf6ccd77987a8c0a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952892"
---
# <a name="create-an-association-between-entities"></a>Erstellen einer Assoziation zwischen Entitäten
  Sie können Beziehungen zwischen Entitäten in Ihrem Modell Business Data Connectivity (BDC) durch das Erstellen von Zuordnungen definieren. Visual Studio generiert die Methoden, die Consumern des Modells mit Informationen über jede Zuordnung bereitstellen. Diese Methoden können von SharePoint-Webparts, Listen oder benutzerdefinierten Anwendungen zum Anzeigen von datenbeziehungen in einer Benutzeroberfläche (UI) verwendet werden.

## <a name="create-an-association"></a>Erstellen einer Zuordnung
 Erstellen Sie eine Zuordnung, indem Sie auswählen der **Zuordnung** -Steuerelement in Visual Studio **Toolbox**, wählen Sie die erste Entität (die Quellentität genannt), und wählen Sie dann die zweite Entität (wird aufgerufen, die Zielentität). Sie können die Details der Zuordnung im Definieren der **Zuordnungs-Editor**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer Assoziation zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md).

## <a name="association-methods"></a>Zuordnungsmethoden
 Anwendungen wie SharePoint Geschäftsdaten-Webparts nutzen Zuordnungen durch Aufrufen der Methoden in der Dienstklasse, die einer Entität. Sie können die Methoden auf die Dienstklasse einer Entität hinzufügen, wählen sie in der **Zuordnungs-Editor**.

 In der Standardeinstellung die **Zuordnungs-Editor** Fügt eine Zuordnung Navigation-Methode für die Quell- und Entitäten hinzu. Eine Zuordnung Navigation-Methode in der Quellentität kann Kunden zum Abrufen einer Liste von Zielentitäten. Eine Zuordnung Navigation-Methode in der Zielentität ermöglicht es Consumern, die Quellentität abzurufen, die mit einer Zielentität verknüpft.

 Sie müssen jede dieser Methoden, um die entsprechenden Informationen zurückzugeben. den Code hinzufügen. Sie können auch andere Arten von Methoden zum unterstützen komplexere Szenarien hinzufügen. Weitere Informationen über jede dieser Methoden finden Sie unter [unterstützte Vorgänge](http://go.microsoft.com/fwlink/?LinkId=169286).

## <a name="types-of-associations"></a>Typen von Zuordnungen
 Sie können zwei Arten von Zuordnungen im BDC-Designer erstellen: foreign Key-basierte Zuordnungen und Fremdschlüssel ohne Schlüssel Zuordnungen.

### <a name="foreign-key-based-association"></a>Foreign Key-basierte Zuordnung
 Sie können eine foreign Key-basierten Zuordnung erstellen, indem Sie einen Bezeichner in der Quellentität Deskriptoren in der Zielentität definierte Typ. Diese Beziehung ermöglicht es Consumern des Modells, um eine verbesserte Benutzeroberfläche für ihre Benutzer bereitzustellen. Beispielsweise ein Formular in Outlook, die Benutzer einen Auftrag erstellen, der Kunden in einer Dropdown-Liste angezeigt werden können. oder eine Liste der Aufträge in SharePoint, die Benutzern ermöglicht, eine Profilseite für einen Kunden zu öffnen.

 Um eine foreign Key-basierten Zuordnung zu erstellen, verknüpfen Sie Bezeichner, und Typdeskriptoren Sie, die den gleichen Namen und Typ aufweisen. Beispielsweise können Sie eine foreign Key-basierten Zuordnung zwischen erstellen eine `Contact` Entität und eine `SalesOrder` Entität. Die `SalesOrder` Entität gibt eine `ContactID` Typdeskriptor als Teil der Rückgabeparameter der Finder oder spezifische Finder-Methode. Beide Typdeskriptoren angezeigt, der **Zuordnungs-Editor**. Erstellen Sie eine foreign Key-basierte Beziehung zwischen der `Contact` Entität und `SalesOrder` Entität, wählen Sie die `ContactID` Bezeichner neben jedem dieser Felder.

 Fügen Sie Code, der Zuordnung Navigator-Methode der Quellentität, die eine Auflistung von Zielentitäten zurückgibt. Im folgende Beispiel werden die Aufträge für einen Kontakt zurückgegeben.

 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]

 Fügen Sie Code, der Zuordnung Navigator-Methode der Zielentität, die eine Quellentität zurückgibt. Das folgende Beispiel gibt die wenden Sie sich an, die sich auf die Bestellung beziehen.

 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]

### <a name="foreign-keyless-association"></a>Zuordnung ohne Fremdschlüssel
 Sie können eine Zuordnung erstellen, ohne das Zuordnen von Bezeichnern zum Feld Typdeskriptoren. Erstellen Sie diese Art von Zuordnung aus, wenn die Quellentität keine direkte Beziehung mit der Zielentität. Z. B. eine `SalesOrderDetail` Tabelle besitzt keinen Fremdschlüssel, der einen Primärschlüssel in zugeordnet ist eine `Contact` Tabelle.

 Wenn Sie Informationen anzeigen möchten die `SalesOrderDetail` Tabelle, die Beziehung zu einer `Contact`, können Sie eine Zuordnung ohne Fremdschlüssel zwischen Erstellen der `Contact` Entität und `SalesOrderDetail` Entität.

 In der Zuordnung Navigation-Methode, der die `Contact` Entität Zurückgeben der `SalesOrderDetail` Entitäten durch Verknüpfen von Tabellen oder durch Aufrufen einer gespeicherten Prozedur.

 Das folgende Beispiel gibt die Details aller Bestellungen durch Verknüpfen von Tabellen zurück.

 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]

 In der Zuordnung Navigation-Methode, der die `SalesOrderDetail` Entität zurückgeben, die zugehörigen `Contact`. Dies wird im folgenden Beispiel veranschaulicht:

 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]

## <a name="see-also"></a>Siehe auch
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Vorgehensweise: Erstellen einer Assoziation zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md)
