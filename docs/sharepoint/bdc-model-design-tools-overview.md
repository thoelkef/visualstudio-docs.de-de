---
title: Übersicht über die für die BDC-Modell-Designtools | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb2f257feaa8faa6acf58c8e8763d15d08a1079e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596567"
---
# <a name="bdc-model-design-tools-overview"></a>Übersicht über Entwurfstools für BDC-Modell
  Sie können ein Business Data Connectivity (BDC)-Modell mit dem BDC-Designer, entwerfen die **BDC-Methodendetails** Fenster und die **BDC-Explorer**.

 Die **BDC-Explorer** ermöglicht es Ihnen, das Modell durchsuchen, suchen das Modell und Typdeskriptoren zu definieren.

## <a name="bdc-designer"></a>BDC-Designer
 BDC-Designer können Sie zum Definieren von Entitäten im Modell und deren Beziehungen visuell miteinander anordnen. Verwenden Sie den BDC-Designer, um die folgenden Aufgaben auszuführen:

- Entitäten mit dem Modell hinzufügen.

- Entfernen Sie Entitäten aus dem Modell an.

- Definieren Sie Beziehungen zwischen Entitäten.

  Um den BDC-Designer zu öffnen, doppelklicken Sie auf die Modelldatei in Ihrem Projekt, oder öffnen Sie das Kontextmenü für die Modelldatei, und wählen Sie dann **öffnen**. Hinzufügen einer Entität für das Modell durch Ziehen oder Kopieren einer **Entität** aus der **Toolbox** in den Designer. Wählen Sie zum Erstellen einer Zuordnung zwischen zwei Entitäten die **Zuordnung** steuern, der **Toolbox**, wählen Sie die erste Entität, und wählen Sie dann die zweite Entität.

## <a name="bdc-method-details-window"></a>Fenster "BDC Method Details"
 Verwenden der **BDC-Methodendetails** Fenster zu definieren, die Parameter, die Instanzen Filterdeskriptoren einer Methode.

 Sie können schnell generieren Finder, spezifische Finder, Ersteller, Aktualisierung und Deleter-Methoden in der **BDC-Methodendetails** Fenster. Wenn Sie diese Methoden generieren, fügt Visual Studio Metadaten, z. B. Parameter, Instanzen und Typdeskriptoren, an die Methode an. Sie können diese Metadaten, um Ihr jeweiliges Szenario zu erfüllen.

 Zum Öffnen der **BDC-Methodendetails** wählen Sie in der Menüleiste **Ansicht** > **Other Windows** > **BDC-Methodendetails** .

 Anzeigen von Methoden in der **BDC-Methodendetails** Fenster, wählen Sie die Entität im BDC-Designer. Die Methoden der ausgewählten Entität angezeigt, der **BDC-Methodendetails** Fenster. Wenn Sie keine Entität im BDC-Designer auswählen der **BDC-Methodendetails** Fenster werden keine Informationen angezeigt.

 Erweitern oder reduzieren Sie Knoten in der **BDC-Methodendetails** Fenster zum Definieren von Parametern, Instanzen und Filterdeskriptoren. Verwenden der **BDC-Explorer** typbeschreibungen definiert.

## <a name="bdc-explorer"></a>BDC-Explorer
 Die **BDC-Explorer** zeigt die Elemente, die das Modell bilden. Zum Öffnen der **BDC-Explorer**, wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** > **BDC-Explorer**. Um das Modell zu durchsuchen, erweitern Sie Knoten in der **BDC-Explorer**. Jeder Knoten stellt ein Element im XML-Datei des Modells dar.

 Auswählen von Knoten in der **BDC-Explorer**, Eigenschaften der einzelnen Knoten, die Sie auswählen, werden in der **Eigenschaften** Fenster. Viele dieser Eigenschaften entsprechen den Attributen in der Datei des Modells. Sie können das Modell suchen, indem Sie das Suchfeld am oberen Rand verwenden die **BDC-Explorer**.

> [!NOTE]
>  Die **BDC-Explorer** Bezeichner, benutzerdefinierte Eigenschaften, lokalisierte Zeichenfolgen, Zuordnungsgruppen, Aktionen, Filterdeskriptoren, Zugriffssteuerungslisten für die Aktion und die Werte der Standardparameter nicht angezeigt.

### <a name="define-type-descriptors"></a>Definieren von typbeschreibungen
 Verwenden der **BDC-Explorer** typbeschreibungen definiert. Der BDC-Explorer können Sie definieren einen Typdeskriptor einmal, und klicken Sie dann wiederverwenden, Typdeskriptor an anderer Stelle in Ihrem Modell. Zu diesem Zweck einen Typdeskriptor kopieren und fügen Sie es auf alle anderen Parameter, oder Typdeskriptor.

> [!NOTE]
>  Änderungen an einer ursprünglichen Typdeskriptor wirken sich nicht auf die Kopien von diesem Typdeskriptor aus.

 Weitere Informationen finden Sie unter [Vorgehensweise: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)
- [Vorgehensweise: Hinzufügen einer Entitätstyps zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Vorgehensweise: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Vorgehensweise: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)
- [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)
- [Vorgehensweise: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)
- [Exemplarische Vorgehensweise: Erstellen Sie eine externe Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
