---
title: 'Vorgehensweise: Erstellen einer Assoziation zwischen Entitäten | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: c341586fbd2a22f38385a6c613058318f5c2d6a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-association-between-entities"></a>Gewusst wie: Erstellen einer Assoziation zwischen Entitäten
  Sie können Beziehungen zwischen Entitäten in Ihrem Modell Business Data Connectivity (BDC) durch das Erstellen von Zuordnungen definieren. Methoden, die Consumern des Modells mit Informationen über jede Zuordnung bereitstellen, generiert Visual Studio. Diese Methoden können von SharePoint-Webparts, Listen oder benutzerdefinierten Anwendungen zum Anzeigen von datenbeziehungen in einer Benutzeroberfläche (UI) verwendet werden.  
  
 Sie können zwei Arten von Zuordnungen im BDC-Designer erstellen: foreign Key-basierte Zuordnungen und Fremdschlüssel Zuordnungen. Weitere Informationen finden Sie unter [erstellen eine Zuordnung zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md).  
  
### <a name="to-create-an-association-between-entities"></a>So erstellen eine Zuordnung zwischen Entitäten  
  
1.  Auf der **BusinessDataConnectivity** auf der Registerkarte die **Toolbox**, wählen Sie die **Zuordnung** Element.  
  
2.  Wählen Sie auf dem BDC-Designer die Quellentität, und wählen Sie dann auf die Zielentität.  
  
     Die **Zuordnungs-Editor** angezeigt wird.  
  
3.  Wenn Sie eine foreign Key-basierte Zuordnung erstellen möchten, wählen Sie die **ist Foreign Key Association** Kontrollkästchen.  
  
    1.  In der **Datenquellen-ID:** Spalte die **Bezeichner zuordnen** table, wählen Sie den Bezeichner neben jeder übereinstimmenden Typdeskriptor, die in angezeigt wird der **Feld** Spalte.  
  
         Beispielsweise ist In der **Datenquellen-ID:** Spalte `ContactID` neben der `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` Typdeskriptor und `ReadItem.salesOrder.SalesOrder.ContactID` Typdeskriptor.  
  
4.  Wenn Sie eine Zuordnung ohne Fremdschlüssel erstellen möchten, deaktivieren Sie die **ist Foreign Key Association** Kontrollkästchen.  
  
5.  Klicken Sie auf die Schaltfläche **OK** .  
  
6.  Im BDC-Designer wird Sie eine Linie, die Zuordnung darstellt, zwischen die Quellentität und der Zielentität angezeigt.  
  
     Visual Studio fügt eine Zuordnung Navigator-Methode, um die Dienstklasse der Zielentität und die Dienstklasse der Quellentität. Weitere Informationen zur Zuordnung Navigationsmethoden finden Sie unter [unterstützte Vorgänge](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
7.  Fügen Sie Code, der eine Auflistung von Zielentitäten zurückgibt, in der Zuordnung Navigator-Methode der Quellentität.  
  
8.  Fügen Sie Code, der die verwandten Quellentität zurückgibt, in der Zuordnung Navigator-Methode der Zielentität.  
  
     Beispiele für Methoden der Zuordnung Navigator, finden Sie unter [erstellen eine Zuordnung zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Vorgehensweise: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Vorgehensweise: hinzufügen eine bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Vorgehensweise: hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Vorgehensweise: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Vorgehensweise: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)   
 [Vorgehensweise: Definieren des Typdeskriptors eines Parameters](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  