---
title: "Integrieren von Geschäftsdaten in SharePoint | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c054049c09f13c224ee4f0bb3021af1121f5cea8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="integrating-business-data-into-sharepoint"></a>Integrieren von Geschäftsdaten in SharePoint
  Sie können die Geschäftsdaten in SharePoint integrieren. Geschäftsdaten können von Back-End-serveranwendungen stammen, z. B. [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel und SAP, oder einen Webdienst. Benutzer können anzeigen, hinzufügen, aktualisieren oder Löschen von Geschäftsdaten mithilfe von externen Listen oder Geschäftsdaten-Webparts in SharePoint.  Benutzer können auch diese Daten in einer Microsoft Office-Anwendung wie Microsoft Outlook offline zugreifen. Weitere Informationen finden Sie unter [, können Sie externe Daten anzeigen](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Um Daten in SharePoint integrieren möchten, erstellen Sie ein Modell für den Business Data Connectivity (BDC)-Dienst. Der BDC-Dienst ist eine Anwendung in SharePoint, die Informationen zu Daten in Geschäftsanwendungen speichert. Weitere Informationen finden Sie unter [Business Data Connectivity (BDC)-Dienst](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Modelle in Visual Studio  
 Modellen in Visual Studio ermöglichen Ihnen das Schreiben von benutzerdefiniertem Code zum Abrufen und Aktualisieren von Daten aus Back-End-Datenquellen. Sie können auch die aggregierte Daten aus mehreren Datenquellen. Beispielsweise können Sie anzeigen, eine Liste von Kunden, die Daten aus einer [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] Datenbank und einen Webdienst.  
  
 Sie können auch Modelle importieren, die bereits in SharePoint bereitgestellt werden. Nachdem Sie ein Modell importiert haben, können Sie benutzerdefinierten Code hinzufügen oder verwenden Sie Visual Studio zum Packen und Bereitstellen des Modells auf mehrere SharePoint-Serverfarmen. Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="designing-a-model-in-visual-studio"></a>Entwerfen eines Modells in Visual Studio  
 Sie können ein Modell entwerfen, mit einem Designer und mehrere Toolfenster. Wenn Sie das Modell entwerfen, generiert Visual Studio das Modell-XML. Weitere Informationen finden Sie unter [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Ein Modell enthält Entitäten und Methoden.  
  
### <a name="entities"></a>Entitäten  
 Eine Entität beschreibt eine Auflistung von Feldern. Eine Entität kann z. B. eine Tabelle in einer Datenbank darstellen. Eine Entität wird als eine externe Inhaltstypen in SharePoint angezeigt. Weitere Informationen zu externen Inhaltstypen finden Sie unter [was externe Inhaltstypen sind?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Methoden  
 Eine Methode ermöglicht die Consumer des zum Ausführen einer Aktion für die Felder einer Entität eine externe Inhaltstypen. Z. B. eine Updater-Methode ermöglichen Benutzern das Ändern der Adresse möglicherweise und Geburtsdatum eines Kunden an, in dem `Address` und `BirthDate` sind Felder von der `Customer` Entität.  
  
 Visual Studio generiert eine Dienst-Codedatei für jede Entität im Modell an. Wenn Sie eine Methode mit dem Modell hinzufügen, generiert Visual Studio eine entsprechende Methode in der Codedatei des Diensts an. Fügen Sie Code hinzu, um die entsprechende Aufgabe auszuführen. Wenn Sie das Modell eine Creator-Methode hinzugefügt haben, generiert der Visual Studio eine Creator-Methode in der Codedatei des Diensts an. Diese Methode wird von den BDC-Dienst aufgerufen, wenn ein Benutzer klickt der **neues Element** Schaltfläche in einer Liste, die für das Modell basiert. Deshalb fügen Sie Code, der Ersteller-Methode, die neue Daten an eine Datenquelle hinzugefügt. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)|Zeigt, wie ein neues Modell erstellen oder Importieren eines Modells, das Sie in SharePoint zu exportieren.|  
|[Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)|Es wird erläutert, wie die Elemente eines Modells mithilfe von Visual Studio-Entwurfstools entwerfen.|  
|[Wann Vs mit SharePoint Designer. Visual Studio bei Erstellung-Lösungen, die mithilfe von BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Hilft Ihnen bei der Entscheidung, ob Visual Studio verwenden, oder verwenden Sie SharePoint-Designer zum Erstellen eines Modells für die BDC.|  
  
  