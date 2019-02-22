---
title: 'Vorgehensweise: Erstellen eines BDC-Modells | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d82678df0da5932dd33c08a6e3066462df204f6e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596502"
---
# <a name="how-to-create-a-bdc-model"></a>Vorgehensweise: Erstellen eines BDC-Modells
  Sie können ein BDC (Business Data Connectivity)-Modell erstellen, indem Sie die Vorlage für diesen Vorlagentyp verwenden und dann das Modell zu einem SharePoint-Projekt hinzufügen. Weitere Informationen finden Sie unter [erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md). Weitere Informationen zum Entwerfen des Modells finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-bdc-project"></a>So erstellen Sie ein BDC-Projekt

1.  Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

    > [!NOTE]
    >  Wenn die IDE mit Visual Basic-entwicklungseinstellungen festgelegt ist, wählen Sie **Datei** > **neues Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2.  Entweder unter **Visual Basic** oder **Visual C#-**, wählen Sie **Office/SharePoint**, **SharePoint-Lösungen**.

3.  In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2013 - leeres Projekt** Element aus, und wählen Sie dann die **OK** Schaltfläche.

     Die **SharePoint Customization Wizard** wird geöffnet.

4.  Auf der **Geben Sie die Website und Sicherheitsebene für debugging** Seite, geben Sie die URL der SharePoint-Website auf dem lokalen Computer, wählen Sie die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche.

     Sie werden das Modell auf der von Ihnen angegebenen SharePoint-Website testen.

    > [!IMPORTANT]
    >  Sie müssen das Projekt als Farmlösung bereitstellen, da BDC-Modelle ausschließlich Farmlösungen unterstützen.

     Ein leeres SharePoint-Projekt wurde erstellt.

5.  Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

6.  In der **neues Element hinzufügen** Dialogfeld auf die **Office/SharePoint** Knoten.

7.  Wählen Sie in der Liste der SharePoint-Vorlagen, **Business Data Connectivity-Modell (nur Farmlösung)**.

8.  In der **Namen** Feld Geben Sie einen Namen für das BDC-Modell, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Ein **Business Data Connectivity-Modells** Element wird dem Projekt hinzugefügt. Standardmäßig wird das Modell im BDC-Designer angezeigt. Weitere Informationen finden Sie unter [erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Siehe auch
- [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Vorgehensweise: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Vorgehensweise: Verwenden Sie eine Ressourcendatei zum Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Vorgehensweise: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
