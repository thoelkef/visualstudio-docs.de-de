---
title: 'Vorgehensweise: Anpassen eines SharePoint-Lösungspakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd1ebe9e49a0b3e26d090fdbbdbbe4dd37c0344a
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119213"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Gewusst wie: Anpassen eines SharePoint-Lösungspakets
  Sie können den Paket-Designer zum Erstellen und Anpassen eines Pakets (*.wsp*). Sie können z. B. SharePoint-Projektelemente und Features hinzufügen, die angeben, wenn der Webserver zurückgesetzt, wenn die Lösung bereitgestellt wird, und den Bereitstellungsservertyp festlegen.  
  
## <a name="open-the-package-designer"></a>Öffnen Sie den Paketdesigner  
  
#### <a name="to-open-the-package-designer"></a>Um den Paket-Designer zu öffnen.
  
-   In **Projektmappen-Explorer**, doppelklicken Sie auf **Paket**, oder wählen Sie **Ansicht-Designer** auf das Kontextmenü für **Paket**.  
  
## <a name="view-the-packaged-manifestffile"></a>Die gepackte ManifestfFile anzeigen  
 Sie können den Paket-Designer verwenden, ändern und das Generieren der Manifestdatei für gepackten. Anschließend können Sie den XML-Code für diese Datei in Visual Studio anzeigen.  
  
#### <a name="to-view-the-xml-source-file"></a>Die XML-Quelldatei anzeigen  
  
1.  In der **-Paket-Designer**, wählen Sie **Manifest**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>So zeigen Sie die Manifestdatei für gepackte mit Projektmappen-Explorer  
  
1.  In **Projektmappen-Explorer**, wählen Sie **alle Dateien anzeigen**.  
  
2.  Erweitern Sie Paket "Package.Package", und öffnen Sie dann die *Package.Template.xml* Datei.  
  
    > [!NOTE]  
    >  Wenn Sie die XML-Manifestdatei für die Paket-Vorlage öffnen, die Dateien werden automatisch überprüft, und können Sie ignorieren, die Warnungen, die in das Fenster "Fehlerliste" angezeigt werden.  
  
## <a name="change-the-manifest-template"></a>Ändern Sie die Manifestvorlage  
 Sie können den XML-Code für die App-Pakete Manifestdatei im XML-Editor von Visual Studio oder im Bereich Manifestvorlage ändern. Alle Änderungen an den XML-Code werden in der App-Pakete Manifestdatei für das Paket zusammengeführt.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Die Manifestvorlage zu ändern, indem Sie mit der XML-Editor  
  
1.  In der **-Paket-Designer**, wählen Sie die **Manifest** Registerkarte, erweitern Sie die **Bearbeitungsoptionen** Knoten, und wählen Sie dann die **im XML-Editor geöffnet** Link.  
  
     Änderungen an den XML-Code werden in der Manifestdatei für gepackte zusammengeführt.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>So ändern Sie die Manifestvorlage mithilfe des Bereichs der Manifestvorlage  
  
1.  In der **-Paket-Designer**, wählen Sie die **Manifest** Registerkarte, erweitern Sie die **Bearbeitungsoptionen** Knoten, und klicken Sie dann ändern Sie den XML-Code, der im Manifest der Template angezeigt wird.  
  
     Änderungen an den XML-Code werden angezeigt, der **Vorschau des Paket-Manifest** Bereich.  
  
## <a name="overwrite-the-packaged-manifest-file"></a>Überschreiben Sie die Manifestdatei für gepackte  
 Sie können den Paket-Designer zu deaktivieren und erstellen die *"Manifest.xml"* Datei manuell. Zum ersten Mal ausführen dieser Prozedur werden die aktuellen Einstellungen im Paket-Designer in der Paket-Vorlage XML-Datei gespeichert. Anschließend können Sie ändern oder überschreiben Sie den XML-Code.  
  
> [!NOTE]  
>  Wenn Sie hinzufügen oder Entfernen von SharePoint-Projektelemente und-Funktionen in der XML-Datei während der Paket-Designer deaktiviert ist, sind nicht diese Projektelemente und-Funktionen verpackt.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Paket-manifest-Datei zu überschreiben, durch Deaktivieren des Designers  
  
1.  In der **-Paket-Designer**, wählen Sie die **Manifest** Registerkarte.  
  
2.  Erweitern Sie die **Bearbeitungsoptionen** Knoten, wählen Sie die **überschreiben generierte XML-"und" Bearbeiten Manifest im XML-Editor** verknüpfen, und wählen Sie dann die **Ja** Schaltfläche.  
  
     Die Vorlage wird durch die aktuelle Paket-manifest-Datei aktualisiert.  
  
## <a name="enable-the-package-designer"></a>Aktivieren Sie den Paketdesigner  
 Sie können den Paket-Designer zum Anpassen der *"Manifest.xml"* Datei.  
  
#### <a name="to-re-enable-the-designer"></a>Um den Designer erneut zu aktivieren.  
  
1.  In der **-Paket-Designer**, wählen Sie die **manifestbearbeitungen verwerfen und den Designer erneut zu aktivieren** verknüpfen, und wählen Sie dann die **Ja** Schaltfläche.  
  
     Die Vorlage wird mit dem ursprünglichen Text aktualisiert, und alle Änderungen an den XML-Code gehen verloren.  
  
## <a name="see-also"></a>Siehe auch
 [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
