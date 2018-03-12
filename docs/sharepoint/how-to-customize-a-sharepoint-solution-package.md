---
title: "Vorgehensweise: Anpassen eines SharePoint-Lösungspakets | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 277ceea1b908c5819608a1bdf1d6be97c2f6ce77
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Gewusst wie: Anpassen eines SharePoint-Lösungspakets
  Sie können den Paket-Designer zum Erstellen und Anpassen eines Lösungspakets (.wsp) verwenden. Sie können z. B. SharePoint-Projektelemente und-Funktionen hinzufügen, angeben, wenn der Webserver zurückgesetzt, wenn die Projektmappe bereitgestellt wurde, und den Bereitstellungsservertyp festlegen.  
  
## <a name="opening-the-package-designer"></a>Öffnen die Paket-Designer  
  
#### <a name="to-open-the-package-designer"></a>Öffnen Sie die Paket-Designer  
  
-   In **Projektmappen-Explorer**, doppelklicken Sie auf **Paket**, oder wählen Sie **Sicht-Designer** auf das Kontextmenü für **Paket**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Anzeigen der App-Manifest-Datei  
 Die Paket-Designer können Sie ändern und die App-manifest-Datei zu generieren. Anschließend können Sie den XML-Code für diese Datei in Visual Studio anzeigen.  
  
#### <a name="to-view-the-xml-source-file"></a>So zeigen Sie die XML-Quelldatei an  
  
1.  In der **Paket-Designer**, wählen Sie **Manifest**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>So zeigen Sie die gepackte Manifestdatei mit Projektmappen-Explorer  
  
1.  In **Projektmappen-Explorer**, wählen Sie **alle Dateien anzeigen**.  
  
2.  Erweitern Sie Paket, erweitern Sie "Package.Package", und öffnen Sie dann die Datei Package.Template.xml.  
  
    > [!NOTE]  
    >  Wenn Sie die XML-Manifestdatei für die Paket-Vorlage öffnen, die Dateien automatisch überprüft werden, und können Sie ignorieren, die Warnungen, die im Fenster "Fehlerliste" angezeigt werden.  
  
## <a name="changing-the-manifest-template"></a>Ändern der Manifest-Vorlage  
 Sie können den XML-Code für die gepackte Manifestdatei im XML-Editor von Visual Studio oder im Manifestvorlage ändern. Alle Änderungen an den XML-Code werden in der App-Manifestdatei für das Paket zusammengeführt.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>So ändern Sie das manifest Vorlage mithilfe der XML-Editor  
  
1.  In der **Paket-Designer**, wählen Sie die **Manifest** Registerkarte, erweitern Sie die **Bearbeitungsoptionen** Knoten, und wählen Sie dann die **im XML-Editor geöffnet** Link.  
  
     Änderungen an der XML-Code werden in der App-manifest-Datei zusammengeführt.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>So ändern Sie das manifest Vorlage Manifestvorlage im Bereich ""  
  
1.  In der **Paket-Designer**, wählen Sie die **Manifest** Registerkarte, erweitern Sie die **Bearbeitungsoptionen** Knoten, und ändern Sie das XML, das im Bereich Manifestvorlage angezeigt wird.  
  
     Änderungen an der XML-Code angezeigt, der **Vorschau der App-Paket-Manifest** Bereich.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Überschreiben die App-Manifest-Datei  
 Sie können die Paket-Designer deaktivieren und die Datei "Manifest.xml" manuell erstellen. Zum ersten Mal ausführen dieser Prozedur werden die aktuellen Einstellungen im Paket-Designer in der Paket-Vorlage XML-Datei gespeichert. Sie können dann ändern oder den XML-Code überschreiben.  
  
> [!NOTE]  
>  Wenn Sie hinzufügen oder Entfernen von SharePoint-Projektelemente und-Funktionen in der XML-Datei während der Paket-Designer deaktiviert ist, werden nicht diese-Projektelemente und-Funktionen verpackt.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Um App-manifest-Datei zu überschreiben, durch Deaktivieren des Designers  
  
1.  In der **Paket-Designer**, wählen Sie die **Manifest** Registerkarte.  
  
2.  sein.  
  
3.  Erweitern Sie die **Bearbeitungsoptionen** Knoten, wählen Sie die **überschreiben generierte XML und bearbeiten Manifest in der XML-Editor** verknüpfen, und wählen Sie dann die **Ja** Schaltfläche.  
  
     Die Vorlage wird durch die aktuelle App-manifest-Datei aktualisiert.  
  
## <a name="enabling-the-package-designer"></a>Aktivieren die Paket-Designer  
 Sie können die Paket-Designer zum Anpassen der Datei "Manifest.xml" erneut aktivieren.  
  
#### <a name="to-re-enable-the-designer"></a>Um den Designer erneut zu aktivieren.  
  
1.  In der **Paket-Designer**, wählen Sie die **manifest Änderungen verwerfen und erneutes Aktivieren der Designer** verknüpfen, und wählen Sie dann die **Ja** Schaltfläche.  
  
     Die Vorlage wird mit dem ursprünglichen Text aktualisiert, und alle Änderungen an der XML-Code gehen verloren.  
  
## <a name="see-also"></a>Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  