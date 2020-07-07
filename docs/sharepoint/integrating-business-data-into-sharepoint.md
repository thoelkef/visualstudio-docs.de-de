---
title: Integrieren von Geschäftsdaten in SharePoint | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: b4bbfb681a0dac0825bf7af4f1f27ab1c1b50053
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016313"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrieren von Geschäftsdaten in SharePoint
  Sie können Geschäftsdaten in SharePoint integrieren. Geschäftsdaten können von Back-End-Server Anwendungen wie [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)] , Siebel und SAP oder einem Webdienst stammen. Benutzer können Geschäftsdaten anzeigen, hinzufügen, aktualisieren oder löschen, indem Sie externe Listen oder Geschäftsdaten Webparts in SharePoint verwenden.  Benutzer können auf diese Daten auch offline in einer Microsoft Office Anwendung wie Microsoft Outlook zugreifen. Weitere Informationen finden Sie unter [wo können externe Daten angezeigt](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14))werden.

 Um Daten in SharePoint zu integrieren, erstellen Sie ein Modell für den Business Data Connectivity (BDC)-Dienst. Der BDC-Dienst ist eine Anwendung in SharePoint, die Informationen zu Daten in Geschäftsanwendungen speichert. Weitere Informationen finden Sie [unter Business Data Connectivity (BDC)-Dienst](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Modelle in Visual Studio
 Modelle in Visual Studio ermöglichen das Schreiben von benutzerdefiniertem Code zum Abrufen und Aktualisieren von Daten aus Back-End-Datenquellen. Sie können auch Daten aus mehreren Datenquellen aggregieren. Beispielsweise können Sie eine Liste von Kunden anzeigen, die Daten aus einer [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] Datenbank und einem Webdienst enthält.

 Sie können auch Modelle importieren, die bereits in SharePoint bereitgestellt wurden. Nachdem Sie ein Modell importiert haben, können Sie benutzerdefinierten Code hinzufügen oder einfach Visual Studio verwenden, um das Modell in mehreren SharePoint-Serverfarmen zu verpacken und bereitzustellen. Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Entwerfen eines Modells in Visual Studio
 Ein Modell kann mithilfe eines Designers und mehrerer Tool Fenster entworfen werden. Wenn Sie das Modell entwerfen, generiert Visual Studio die Modell-XML-Datei. Weitere Informationen finden Sie unter [Übersicht über die Entwurfs Tools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md).

 Ein Modell enthält Entitäten und Methoden.

### <a name="entities"></a>Entitäten
 Eine Entität beschreibt eine Auflistung von Feldern. Beispielsweise kann eine Entität eine Tabelle in einer Datenbank darstellen. Eine Entität wird in SharePoint als externer Inhaltstyp angezeigt. Weitere Informationen zu externen Inhaltstypen finden Sie unter [Was sind externe Inhaltstypen?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>Methoden
 Eine-Methode ermöglicht es den Consumern eines externen Inhaltstyps, eine Aktion für die Felder einer Entität auszuführen. Beispielsweise können Benutzer mit einer Updater-Methode die Adresse und das Geburtsdatum eines Kunden ändern, wobei `Address` und die `BirthDate` Felder der `Customer` Entität sind.

 Visual Studio generiert eine Dienst Codedatei für jede Entität im Modell. Wenn Sie dem Modell eine Methode hinzufügen, generiert Visual Studio eine entsprechende Methode in der Dienst Codedatei. Fügen Sie jeder Methode Code hinzu, um die entsprechende Aufgabe auszuführen. Wenn Sie dem Modell beispielsweise eine Creator-Methode hinzufügen, generiert Visual Studio in ihrer Dienst Code Datei eine Ersteller-Methode. Diese Methode wird vom BDC-Dienst aufgerufen, wenn ein Benutzer auf die Schaltfläche **Neues Element** in einer Liste klickt, die auf dem Modell basiert. Fügen Sie daher der Creator-Methode Code hinzu, der einer Datenquelle neue Daten hinzufügt. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)|Zeigt, wie Sie ein neues Modell erstellen oder ein Modell importieren, das Sie aus SharePoint exportieren.|
|[Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)|Erläutert das Entwerfen der Elemente eines Modells mithilfe der Visual Studio-Entwurfs Tools.|
|[Verwendungsmöglichkeiten von SharePoint Designer und Visual Studio bei der Erstellung von Lösungen mit BCS](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Hilft Ihnen bei der Entscheidung, ob Sie Visual Studio verwenden oder SharePoint Designer verwenden möchten, um ein Modell für den BDC zu erstellen.|
