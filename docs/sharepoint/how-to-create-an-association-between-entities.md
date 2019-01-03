---
title: 'Vorgehensweise: Erstellen einer Assoziation zwischen Entitäten | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- AssociationGroupTool
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
ms.openlocfilehash: eaaa3f86cc0751b0b80d61555a69aa6bfecda2f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878246"
---
# <a name="how-to-create-an-association-between-entities"></a>Vorgehensweise: Erstellen einer Assoziation zwischen Entitäten
  Sie können Beziehungen zwischen Entitäten in Ihrem Modell Business Data Connectivity (BDC) durch das Erstellen von Zuordnungen definieren. Visual Studio generiert die Methoden, die Consumern des Modells mit Informationen über jede Zuordnung bereitstellen. Diese Methoden können von SharePoint-Webparts, Listen oder benutzerdefinierten Anwendungen zum Anzeigen von datenbeziehungen in einer Benutzeroberfläche (UI) verwendet werden.  
  
 Sie können zwei Arten von Zuordnungen im BDC-Designer erstellen: foreign Key-basierte Zuordnungen und Fremdschlüssel ohne Schlüssel Zuordnungen. Weitere Informationen finden Sie unter [Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md).  
  
### <a name="to-create-an-association-between-entities"></a>Zum Erstellen einer Assoziation zwischen Entitäten  
  
1.  Auf der **BusinessDataConnectivity** Registerkarte die **Toolbox**, wählen Sie die **Zuordnung** Element.  
  
2.  Klicken Sie im BDC-Designer wählen Sie die Quellentität, und wählen Sie dann auf die Zielentität.  
  
     Die **Zuordnungs-Editor** angezeigt wird.  
  
3.  Wenn Sie eine foreign Key-basierten Zuordnung erstellen möchten, wählen Sie die **ist Fremdschlüsselzuordnung** Kontrollkästchen.  
  
    1.  In der **Datenquellen-ID:** Spalte die **Bezeichner Zuordnung** , aktivieren Sie den Bezeichner neben jeder übereinstimmenden Typdeskriptor, der angezeigt wird der **Feld** Spalte.  
  
         Z. B. In der **Datenquellen-ID:** Spalte `ContactID` neben der `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` Typdeskriptor und `ReadItem.salesOrder.SalesOrder.ContactID` Typdeskriptor.  
  
4.  Wenn Sie eine Zuordnung ohne Fremdschlüssel erstellen möchten, deaktivieren Sie die **ist Fremdschlüsselzuordnung** Kontrollkästchen.  
  
5.  Klicken Sie auf die Schaltfläche **OK** .  
  
6.  Im BDC-Designer wird Sie eine Linie, die die Zuordnung darstellt zwischen die Quellentität und die Zielentität angezeigt.  
  
     Visual Studio fügt eine Zuordnung Navigator-Methode, um die Dienstklasse vom die Zielentität und der Dienstklasse der Quellentität. Weitere Informationen zur Zuordnung Navigationsmethoden finden Sie unter [unterstützte Vorgänge](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
7.  Fügen Sie Code, der eine Auflistung von Zielentitäten zurückgibt, in der Zuordnung Navigator-Methode der Quellentität.  
  
8.  Fügen Sie Code, der die verwandten Quellentität zurückgibt, in der Zuordnung Navigator-Methode der Zielentität.  
  
     Beispiele für Zuordnung Navigator-Methoden, finden Sie unter [Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md).  
  
## <a name="see-also"></a>Siehe auch
 [Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Vorgehensweise: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Vorgehensweise: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Vorgehensweise: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Vorgehensweise: Fügen Sie einen Parameter einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)   
 [Vorgehensweise: Definieren des Typdeskriptors für einen parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Exemplarische Vorgehensweise: Erstellen Sie eine externe Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
