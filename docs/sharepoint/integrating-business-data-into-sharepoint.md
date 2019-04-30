---
title: Integrieren von Geschäftsdaten in SharePoint | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fbbdba27b5ccc52e64575aad018af4ca20cf2e14
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008792"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrieren von Geschäftsdaten in SharePoint
  Sie können die Geschäftsdaten in SharePoint integrieren. Geschäftsdaten können von Back-End-Server-Anwendungen stammen, z. B. [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel und SAP, oder einen Webdienst. Benutzer können anzeigen, hinzufügen, aktualisieren oder Löschen von Unternehmensdaten mithilfe von externen Listen oder Geschäftsdaten-Webparts in SharePoint.  Benutzer können auch diese Daten in einer Microsoft Office-Anwendung wie Microsoft Outlook offline zugreifen. Weitere Informationen finden Sie unter [, können Sie externe Daten anzeigen](http://go.microsoft.com/fwlink/?LinkId=169295).

 Erstellen Sie ein Modell für den Business Data Connectivity (BDC)-Dienst, um Daten in SharePoint zu integrieren. Der BDC-Dienst ist eine Anwendung in SharePoint, die Informationen zu Daten in Business-Anwendungen gespeichert. Weitere Informationen finden Sie unter [Business Data Connectivity (BDC)-Dienst](http://go.microsoft.com/fwlink/?LinkID=169276).

## <a name="models-in-visual-studio"></a>Modelle in Visual Studio
 Modelle in Visual Studio können Sie zum Schreiben von benutzerdefinierten Codes zum Abrufen und Aktualisieren von Daten aus Back-End-Datenquellen. Sie können auch die aggregierte Daten aus mehreren Datenquellen. Beispielsweise können Sie anzeigen, eine Liste von Kunden, die Daten aus einer [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] -Datenbank und einen Webdienst.

 Sie können auch Modelle importieren, die bereits in SharePoint bereitgestellt werden. Nachdem Sie ein Modell importiert haben, können Sie benutzerdefinierten Code hinzufügen oder verwenden Sie einfach die Visual Studio zum Packen und Bereitstellen des Modells für mehrere SharePoint-Serverfarmen. Weitere Informationen finden Sie unter [erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Entwerfen eines Modells in Visual Studio
 Sie können ein Modell entwerfen, mit einem Designer und mehrere Toolfenster. Wenn Sie das Modell entwerfen, generiert Visual Studio das Modell-XML. Weitere Informationen finden Sie unter [BDC-Modell-Designtools Übersicht](../sharepoint/bdc-model-design-tools-overview.md).

 Ein Modell enthält Entitäten und Methoden.

### <a name="entities"></a>Entitäten
 Eine Entität beschreibt eine Auflistung von Feldern. Beispielsweise kann eine Entität eine Tabelle in einer Datenbank darstellen. Eine Entität wird als ein externer Inhaltstyp in SharePoint angezeigt. Weitere Informationen zu externen Inhaltstypen, finden Sie unter [was externe Inhaltstypen sind?](http://go.microsoft.com/fwlink/?LinkId=169293)

### <a name="methods"></a>Methoden
 Eine Methode ermöglicht die Benutzer von einem externen Inhaltstyp zum Ausführen einer Aktion für die Felder einer Entität. Z. B. eine Updater-Methode können Benutzer die Adresse ändern kann, und Geburtsdatum eines Kunden, in denen `Address` und `BirthDate` sind Felder von der `Customer` Entität.

 Visual Studio generiert eine Authentifizierungsdienst-Codedatei für jede Entität im Modell. Wenn Sie eine Methode für das Modell hinzufügen, generiert Visual Studio eine entsprechende Methode in der Codedatei für den Dienst an. Fügen Sie Code hinzu, um die entsprechende Aufgabe auszuführen. Wenn Sie eine Creator-Methode mit dem Modell hinzufügen, generiert Visual Studio z. B. eine Creator-Methode in Ihrer Dienst-Codedatei. Diese Methode wird von den BDC-Dienst aufgerufen, wenn ein Benutzer klickt der **neues Element** Schaltflächen in der Liste, die für das Modell basiert. Fügen Sie Code aus diesem Grund der Creator-Methode, die neue Daten an eine Datenquelle hinzugefügt. Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)|Zeigt, wie ein neues Modell erstellen oder importieren ein Modells, das Sie aus SharePoint exportieren.|
|[Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)|Es wird erläutert, wie die Elemente eines Modells mithilfe von Visual Studio-Entwurfstools zu entwerfen.|
|[Wann verwenden Sie SharePoint Designer Visual Studio. Visual Studio beim Entwickeln von Lösungen, die mithilfe von BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Hilft Ihnen bei der Entscheidung, ob Visual Studio verwenden, oder verwenden SharePoint Designer zum Erstellen eines Modells für den BDC.|
