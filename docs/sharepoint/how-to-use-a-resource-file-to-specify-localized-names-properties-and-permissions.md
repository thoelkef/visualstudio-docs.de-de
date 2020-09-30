---
title: Verwenden einer Ressourcen Datei in einem SharePoint-Projekt | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1693308c591e60a2df0e4d8e18ece8cc9b598fd2
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585744"
---
# <a name="how-to-use-a-resource-file-in-a-sharepoint-project"></a>Verwenden einer Ressourcen Datei in einem SharePoint-Projekt

  Mithilfe einer Ressourcen Datei können Sie lokalisierte Namen bereitstellen, Eigenschaften definieren und Berechtigungs-Tor-Objekte anwenden, die in einem Business Data Connectivity (BDC)-Modell definiert sind. Zum Angeben dieser Informationen fügen Sie ein **Business Data Connectivity-Ressourcen** Element zu einem Projekt hinzu, das ein **Business Data Connectivity-Modell** Element enthält. Anschließend geben Sie Namen, Eigenschaften und Berechtigungen an, indem Sie den XML-Code für die Ressourcen Datei bearbeiten.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>So fügen Sie einem SharePoint-Projekt eine BDC-Ressourcen Datei hinzu

1. Erweitern Sie in **Projektmappen-Explorer**den Ordner für das SharePoint-Projekt, und wählen Sie dann den Ordner aus, der das BDC-Modell enthält.

2. Wählen Sie in der Menüleiste **Projekt**  >  **Neues Element hinzufügen**aus.

3. Erweitern Sie den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

4. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die **Option Business Data Connectivity-Ressourcen Element**aus.

5. Geben Sie im Feld **Name** den Namen der Ressourcen Datei an, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

     Eine Ressourcen Datei mit der Erweiterung. bdcr wird dem Projekt hinzugefügt und zum Bearbeiten geöffnet.

6. Fügen Sie XML hinzu, um die lokalisierten Namen, Eigenschaften und Berechtigungen zu definieren, die Sie für das BDC-Modell verwenden möchten.

     Weitere Informationen zum Definieren dieser Elemente finden Sie unter [Modell-und Ressourcen Dateien](/previous-versions/office/developer/sharepoint-2010/aa674515(v=office.14)).

## <a name="see-also"></a>Weitere Informationen
- [How to: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)
- [Vorgehensweise: Einschließen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
