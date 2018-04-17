---
title: 'Vorgehensweise: Hinzufügen und entfernen zugeordneter Ordner | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 43ec8b7c18d99880b1ab932ea28a371a7604b636
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Gewusst wie: Hinzufügen und Entfernen zugeordneter Ordner
  Einige verwendete häufig Ordner in SharePoint, z. B. Bilder und Layouts werden in der Dateihierarchie tief eingebettet. Sie können diese Ordner in einem SharePoint-Projekt für den Zugriff leichter zuordnen. Zugeordnete Ordner sind Ordner in der SharePoint-Projekt, die den physischen Speicherort der Dateien bei der Installation von SharePoint-Server entsprechen.  
  
 Wenn Sie eine SharePoint-Anwendung bereitstellen, wird der Inhalt der zugeordneten Ordner und seinen Unterordnern durch das Lösungspaket (.wsp) auf den Server kopiert werden, SharePoint an der angegebenen Position in der SharePoint-Ordnerstruktur ausgeführt wird. Dieser Speicherort richtet sich nach der **Bereitstellungsspeicherort** -Eigenschaft, die für den zugeordneten Ordner festgelegt ist. Alle Unterordner im zugeordneten Ordner sind relativ zum **Bereitstellungsspeicherort** des zugeordneten Ordners. Beachten Sie, dass die **Bereitstellungsspeicherort** -Eigenschaft, nicht den Namen des Ordners "zugeordneten" bestimmt, wo die Elemente bereitgestellt werden.  
  
 Ein Projekt kann mithilfe von Befehlen auf der Menüleiste oder das Kontextmenü für das Projekt zugeordnete Ordner hinzugefügt werden. Sie können die **Hinzufügen eines SharePoint "Ordner" Abbilder"zugeordnet"** und **Hinzufügen eines SharePoint "Layouts" Ordner** Befehle aus, um diese hinzufügen zugeordnet, Ordnern, die am häufigsten verwendet werden. Sie können eine der anderen verfügbaren SharePoint-Ordner zu Ihrem Projekt zuordnen, mithilfe der **zugeordneten SharePoint-Ordner hinzufügen** Befehl im Kontextmenü, und dann angeben, die Ordner in der **hinzufügen zugeordneten SharePoint-Ordner** (Dialogfeld).  
  
## <a name="adding-mapped-folders-to-a-project"></a>Ein Projekt hinzugefügt zugeordnete Ordner  
 Die folgenden Verfahren wird beschrieben, wie ein visuelles Webpartprojekt zwei zugeordnete Ordner hinzugefügt wird. Um zu starten, erstellen Sie ein visuelles Webpartprojekt.  
  
#### <a name="to-add-mapped-folders-to-a-project"></a>Ein Projekt zugeordnete Ordner hinzu  
  
1.  Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie entweder die **Visual Basic** oder **Visual C#-** Knoten, erweitern Sie die **Office/SharePoint** Knoten, und klicken Sie dann Wählen Sie die **SharePoint-Lösungen** Knoten.  
  
3.  Wählen Sie in der Liste der Projektvorlagen, die **visuelles für SharePoint 2013-Webpart** Vorlage.  
  
4.  In der **Namen** geben **TestProject1**, und wählen Sie dann die **OK** Schaltfläche.  
  
5.  In der **Assistent zum Anpassen von SharePoint**, wählen Sie die **Fertig stellen** Schaltfläche, um die Standardeinstellungen beibehalten.  
  
6.  In **Projektmappen-Explorer**, wählen Sie den Projektknoten, und wählen Sie dann auf der Menüleiste **Projekt**, **Hinzufügen eines SharePoint "Ordner" Abbilder"zugeordnet"**.  
  
     Einen Ordner mit dem Namen **Bilder** in Ihrem Projekt angezeigt und enthält einen Unterordner mit dem Namen TestProject1. Dieser zugeordneten Ordner enthält Bilder für die visuelles Webpartprojekt.  
  
7.  In **Projektmappen-Explorer**, wählen Sie den Projektknoten, und wählen Sie dann auf der Menüleiste **Projekt**, **zugeordneten SharePoint-Ordner hinzufügen** zum Anzeigen der **hinzufügen Zugeordneter SharePoint-Ordner** (Dialogfeld).  
  
8.  Wählen Sie in der Strukturansicht der Ordner, die für die Zuordnung verfügbar sind, die **Ressourcen** Ordner, und wählen Sie dann die **OK** Schaltfläche.  
  
     Einen Ordner mit dem Namen **Ressourcen** in Ihrem Projekt angezeigt wird. In diesem Ordner kann Elemente wie z. B. Zeichenfolgenressourcendateien zu speichern. Unterordner können zum Organisieren von den Inhalt der einen zugeordneten Ordner nützlich sein, aber sie sind nicht automatisch erstellt, wenn Sie einen zugeordneten Ordner hinzufügen, mit der **zugeordneten SharePoint-Ordner hinzufügen** Befehl. Um einen untergeordneten Ordner hinzuzufügen, wählen Sie die **Ressourcen** Ordner, und anschließend auf der Menüleiste die Optionen **Projekt**, **neuer Ordner**.  
  
## <a name="changing-the-deployment-location-of-a-mapped-folder"></a>Ändern den Speicherort für die Bereitstellung der einen zugeordneten Ordner  
 Standardmäßig werden zugeordnete Ordner an einen bestimmten Standort relativ zum Stammpfad Installation SharePoint hinzugefügt, das das Token {SharePointRoot} bezeichnet. Allerdings können Sie diesen Speicherort ändern, indem Sie ändern die **Bereitstellungsspeicherort** Eigenschaft des zugeordneten Ordners. Jeder zugeordnete Ordner verfügt über eine eigene **Bereitstellungsspeicherort** Eigenschaft.  
  
#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>So ändern Sie den Speicherort für die Bereitstellung der einen zugeordneten Ordner  
  
1.  Wählen Sie in das Projekt, das Sie zuvor erstellt haben, einen zugeordneten Ordner aus.  
  
2.  In der **Eigenschaften** Fenster Schaltfläche mit den Auslassungszeichen (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) auf die Schaltfläche der **Bereitstellung Speicherort** Eigenschaft.  
  
3.  In der **zugeordneten SharePoint-Ordner hinzufügen** (Dialogfeld), navigieren Sie zu dem Ordner, zeigen Sie die zugeordneten Ordner möchten.  
  
4.  Wählen Sie den Knoten, und wählen Sie dann die **OK** Schaltfläche.  
  
## <a name="renaming-or-removing-mapped-folders"></a>Das Umbenennen oder entfernen zugeordneter Ordner  
  
#### <a name="to-rename-or-remove-a-mapped-folder"></a>Umbenennen oder entfernen einen zugeordneten Ordner  
  
1.  Wählen Sie in das Projekt, das Sie zuvor erstellt haben, einen zugeordneten Ordner aus.  
  
2.  Um den zugeordneten Ordner umzubenennen, öffnen Sie das Kontextmenü, wählen Sie **umbenennen**, geben Sie den neuen Namen, und wählen Sie dann die EINGABETASTE.  
  
     Als Alternative können Sie festlegen, die zugeordneten Ordner, die Sie umbenennen möchten, öffnen Sie die **Eigenschaften** Fenster, und legen Sie dann den Wert des der **Ordnername** Eigenschaft in den neuen Namen.  
  
3.  Um einen zugeordneten Ordner aus dem Projekt entfernen möchten, öffnen Sie das Kontextmenü, wählen Sie **löschen**, und wählen Sie dann die **OK** Schaltfläche im Dialogfeld, das Entfernen zu bestätigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
  
  