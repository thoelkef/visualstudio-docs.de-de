---
title: 'Vorgehensweise: Anpassen eines SharePoint-Features | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e54d2dc388ca308e037fb8ff918f521ee16e9092
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067260"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Vorgehensweise: Anpassen einer SharePoint-Funktion
  Sie können erstellen und Anpassen von SharePoint-Funktionen mithilfe der Funktions-Designer in Visual Studio. Sie können z. B. Festlegen des Gültigkeitsbereichs der Funktion und weitere Funktionen als Abhängigkeiten hinzufügen. Standardmäßig wird die Funktions-Designer geöffnet, wenn Sie ein neues Feature in Projektmappen-Explorer oder im SharePoint-Paket-Explorer hinzufügen.

## <a name="opening-the-feature-designer"></a>Öffnen die Funktions-Designer
 Sie können die hinzufügen oder Entfernen von SharePoint-Projektelemente, einer Funktion, die mit der Funktions-Designer.

#### <a name="to-open-the-feature-designer"></a>Um die Funktions-Designer zu öffnen.

1. In **Projektmappen-Explorer**, erweitern Sie **Features**.

2. Doppelklicken Sie auf die *Feature1* Element, oder öffnen Sie das Kontextmenü für die *Feature1* Element aus, und wählen Sie dann **Ansicht-Designer**.

## <a name="view-the-packaged-manifest-file"></a>Die Manifestdatei für gepackte anzeigen
 Können Sie die Funktions-Designer ändern, und Generieren der Manifestdatei für gepackten für das Feature (*"Feature.xml"*). Anschließend können Sie den XML-Code für diese Datei in Visual Studio anzeigen.

#### <a name="to-view-the-packaged-manifest-file"></a>Die Manifestdatei für gepackte anzeigen

1. In der **Funktions-Designer**, wählen Sie die **Manifest** Registerkarte.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>So zeigen Sie die Manifestdatei für gepackte mit Projektmappen-Explorer

1. In **Projektmappen-Explorer**, wählen Sie die **alle Dateien anzeigen** Symbol.

2. Erweitern Sie Features FeatureName, FeatureName.feature erweitern und anschließend öffnen Sie dann die  *\<FeatureName >. Template.XML* Datei.

    > [!NOTE]
    >  Wenn Sie die Funktion Vorlage XML-Manifestdatei öffnen, die Dateien werden automatisch überprüft, und die Warnungen, die in das Fenster "Fehlerliste" angezeigt werden, können ignoriert werden.

## <a name="change-the-manifest-template"></a>Ändern Sie die Manifestvorlage
 Sie können den XML-Code für die Manifestdatei des Features, in der XML-Editor von Visual Studio oder im Bereich Manifestvorlage ändern. Alle Änderungen an den XML-Code wird in der Manifestdatei für gepackte zusammengeführt, für die Funktion. Beispielsweise empfiehlt es sich so ändern Sie die Manifestvorlage um eine Funktionseigenschaft anzupassen.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Die Manifestvorlage zu ändern, indem Sie mit der XML-Editor

1. In der **Funktions-Designer**, wählen Sie die **Manifest** Registerkarte, erweitern Sie die **Bearbeitungsoptionen** Knoten, und wählen Sie dann die **im XML-Editor geöffnet** Link.

     Änderungen an den XML-Code werden in der Manifestdatei für gepackte zusammengeführt.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>So ändern Sie die Manifestvorlage mithilfe des Bereichs der Manifestvorlage

1. In der **Funktions-Designer**, wählen Sie die **Manifest** Registerkarte, erweitern Sie die **Bearbeitungsoptionen** Knoten, und klicken Sie dann ändern Sie den XML-Code, der im Manifest der Template angezeigt wird.

     Änderungen an den XML-Code werden angezeigt, der **Vorschau des Paket-Manifest** Bereich.

## <a name="overwrite-the-packaged-manifest-file"></a>Überschreiben Sie die Manifestdatei für gepackte
 Sie können der Funktions-Designer zu deaktivieren, und erstellen die *"Feature.xml"* Datei manuell. Zum ersten Mal ausführen dieser Prozedur werden die aktuellen Einstellungen in der Funktions-Designer in der Funktion Vorlage XML-Datei gespeichert. Anschließend können Sie ändern oder überschreiben Sie den XML-Code.

> [!NOTE]
>  Wenn Sie hinzufügen oder Entfernen von SharePoint-Projektelemente in der XML-Datei während der Funktions-Designer deaktiviert ist, werden diese Projektelemente nicht gepackt.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Paket-manifest-Datei zu überschreiben, durch Deaktivieren des Designers

1. In der **Funktions-Designer**, wählen Sie die **Manifest** Registerkarte.

2. Erweitern Sie die **Bearbeitungsoptionen** Knoten, wählen Sie die **überschreiben generierte XML-"und" Bearbeiten Manifest im XML-Editor** verknüpfen, und wählen Sie dann die **Ja** Schaltfläche.

     Die Vorlage wird durch die aktuelle Paket-manifest-Datei aktualisiert.

## <a name="enable-the-feature-designer"></a>Aktivieren Sie die Funktions-Designer
 Sie können die Funktions-Designer zum Anpassen der *"Feature.xml"* Datei.

#### <a name="to-re-enable-the-designer"></a>Um den Designer erneut zu aktivieren.

1. In der **Funktions-Designer**, wählen Sie die **verwerfen manifestbearbeitungen, und aktivieren Sie den Designer erneut** verknüpfen, und wählen Sie dann die **Ja** Schaltfläche.

2. Die Vorlage wird mit dem ursprünglichen Text aktualisiert, und alle Änderungen an den XML-Code gehen verloren.

## <a name="see-also"></a>Siehe auch
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
