---
title: 'Vorgehensweise: Hinzufügen und entfernen zugeordneter Ordner | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d5d1acc40b23c979a5746c50be50a584d11112b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966912"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Gewusst wie: Hinzufügen und entfernen zugeordneter Ordner
  Einige verwendete häufig Ordner in SharePoint, wie z. B. Bilder und Layouts, tief in der Dateihierarchie eingebettet sind. Sie können diese Ordner in einem SharePoint-Projekt leichter Zugriffsberechtigung zuordnen. Zugeordnete Ordner sind Ordner in der SharePoint-Projekt, die den physischen Speicherort der Dateien bei der Installation von SharePoint-Server entsprechen.

 Wenn Sie eine SharePoint-Anwendung bereitstellen, den Inhalt der zugeordnete Ordner und alle Unterordner, die durch das Lösungspaket (.wsp) auf den Server kopiert werden, SharePoint an der angegebenen Position in der Struktur der SharePoint-Ordner ausgeführt wird. Dieser Speicherort richtet sich nach der **Bereitstellungsspeicherort** -Eigenschaft, die für den zugeordneten Ordner festgelegt ist. Alle Unterordner im zugeordneten Ordner sind relativ zum **Bereitstellungsspeicherort** des zugeordneten Ordners. Beachten Sie, dass die **Bereitstellungsspeicherort** nicht den Namen des zugeordneten Ordners, der Eigenschaft wird festgelegt, wo die Elemente bereitgestellt werden.
Sie können mithilfe von Befehlen auf der Menüleiste oder im Kontextmenü für das Projekt zugeordnete Ordner zu einem Projekt hinzufügen. Können Sie die **SharePoint hinzufügen "Images" zugeordneter Ordner** und **SharePoint hinzufügen "Layouts" Ordner** Befehle aus, um diese hinzufügen zugeordneten Ordnern, die am häufigsten verwendet werden. Sie können eine der anderen verfügbaren SharePoint-Ordner zu Ihrem Projekt zuordnen, mit der **zugeordneten SharePoint-Ordner hinzufügen** Befehl im Kontextmenü auf, und klicken Sie dann angeben die Ordner in der **hinzufügen zugeordneten SharePoint-Ordner** Dialogfeld.

## <a name="add-mapped-folders-to-a-project"></a>Fügen Sie zugeordneter Ordner zu einem Projekt hinzu.
 Das folgende Verfahren wird beschrieben, wie einer visuellen Webpartprojekts zwei zugeordnete Ordner hinzugefügt. Um zu starten, erstellen Sie einen visuellen Webpartprojekts.

#### <a name="to-add-mapped-folders-to-a-project"></a>Ein Projekt zugeordnete Ordner hinzu

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. In der **neues Projekt** Dialogfeld erweitern Sie entweder die **Visual Basic** oder **Visual C#**  Knoten, erweitern Sie die **Office/SharePoint** Knoten, und wählen Sie dann die **SharePoint-Lösungen** Knoten.

3. Wählen Sie in der Liste der Projektvorlagen, die **visuelles für SharePoint 2013-Webpart** Vorlage.

4. In der **Namen** geben **TestProject1**, und wählen Sie dann die **OK** Schaltfläche.

5. In der **SharePoint Customization Wizard**, wählen Sie die **Fertig stellen** Schaltfläche, um die Standardeinstellungen beibehalten.

6. In **Projektmappen-Explorer**, wählen Sie den Projektknoten und anschließend auf der Menüleiste die Optionen **Projekt** > **SharePoint hinzufügen "Images" zugeordneter Ordner**.

     Ein Ordner mit dem Namen **Images** in Ihrem Projekt angezeigt wird, und enthält einen Unterordner mit dem Namen TestProject1. Diese zugeordneten Ordner enthält Bilder für die visuellen Webpartprojekts.

7. In **Projektmappen-Explorer**, wählen Sie den Projektknoten und anschließend auf der Menüleiste die Optionen **Projekt** > **zugeordneten SharePoint-Ordner hinzufügen** zum Anzeigen der  **Fügen Sie zugeordneter SharePoint-Ordner** Dialogfeld.

8. Wählen Sie in der Strukturansicht der Ordner, die für die Zuordnung verfügbar sind, die **Ressourcen** Ordner, und wählen Sie dann die **OK** Schaltfläche.

     Ein Ordner mit dem Namen **Ressourcen** in Ihrem Projekt angezeigt wird. In diesem Ordner kann Elemente wie z. B. Zeichenfolgenressourcendateien zu speichern. Unterordner für den Inhalt eines zugeordneten Ordners organisieren nützlich sein können, aber sie sind nicht automatisch erstellt, wenn Sie einen zugeordneten Ordner hinzufügen, mit der **zugeordneten SharePoint-Ordner hinzufügen** Befehl. Um einen untergeordneten Ordner hinzuzufügen, wählen die **Ressourcen** Ordner und anschließend auf der Menüleiste die Optionen **Projekt** > **neuer Ordner**.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Ändern Sie den Speicherort für die Bereitstellung eines zugeordneten Ordners
 Standardmäßig zugeordnete Ordner hinzugefügt werden, zu einer bestimmten Stelle relativ zu der SharePoint-stamminstallationspfad der das Token \<SharePointRoot > bezeichnet. Allerdings können Sie diesen Speicherort ändern, durch Ändern der **Bereitstellungsspeicherort** Eigenschaft des zugeordneten Ordners. Jeder zugeordnete Ordner verfügt über eine eigene **Bereitstellungsspeicherort** Eigenschaft.

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>So ändern Sie den Speicherort für die Bereitstellung eines zugeordneten Ordners

1. Wählen Sie im Projekt, das Sie zuvor erstellt haben, einen zugeordneten Ordner.

2. In der **Eigenschaften** Fenster, wählen Sie die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) auf auf die Schaltfläche der **Bereitstellung Speicherort** Eigenschaft.

3. In der **zugeordneten SharePoint-Ordner hinzufügen** wechseln in den Ordner, den zugeordneten Ordner, zeigen soll, Sie im Dialogfeld.

4. Wählen Sie den Knoten, und wählen Sie dann die **OK** Schaltfläche.

## <a name="rename-or-remove-mapped-folders"></a>Umbenennen Sie oder entfernen Sie zugeordneter Ordner

#### <a name="to-rename-or-remove-a-mapped-folder"></a>Umbenennen oder entfernen einen zugeordneten Ordner

1. Wählen Sie im Projekt, das Sie zuvor erstellt haben, einen zugeordneten Ordner.

2. Wenn den zugeordneten Ordner umbenennen möchten, öffnen das Kontextmenü, und wählen **umbenennen**, geben Sie den neuen Namen ein, und wählen Sie dann die EINGABETASTE.

     Als Alternative können Sie den zugeordneten Ordner an, die Sie umbenennen möchten, öffnen Sie die **Eigenschaften** Fenster, und legen Sie dann den Wert des der **Ordnername** Eigenschaft, um den neuen Namen.

3. Um einen zugeordneten Ordner aus dem Projekt entfernen möchten, öffnen das Kontextmenü, und wählen **löschen**, und wählen Sie dann die **OK** Schaltfläche im Dialogfeld, das Entfernen zu bestätigen.

## <a name="see-also"></a>Siehe auch
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
