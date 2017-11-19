---
title: 'Vorgehensweise: Anpassen einer SharePoint-Funktion | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, features
ms.assetid: e624c546-564b-4c73-9f1b-dc3675e76a55
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d81a65a8030fd77ead1362602b0e16f474ef410c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Gewusst wie: Anpassen einer SharePoint-Funktion
  Sie können erstellen und Anpassen von SharePoint-Funktionen mit dem Funktions-Designer in Visual Studio. Sie können z. B. Legen Sie den Funktionsbereich und fügen Sie andere Funktionen als Abhängigkeiten hinzu. Standardmäßig wird der Funktions-Designer geöffnet, wenn Sie ein neues Feature in Projektmappen-Explorer oder im SharePoint-Paket-Explorer hinzufügen.  
  
## <a name="opening-the-feature-designer"></a>Öffnen des Funktions-Designers  
 Sie können hinzufügen oder Entfernen von SharePoint-Projektelemente einer Funktion mit dem Funktions-Designer.  
  
#### <a name="to-open-the-feature-designer"></a>Zum Öffnen des Funktions-Designers  
  
1.  In **Projektmappen-Explorer**, erweitern Sie **Funktionen**.  
  
2.  Doppelklicken Sie auf die *Feature1* Element, oder öffnen Sie das Kontextmenü für die *Feature1* Element, und wählen Sie dann **Sicht-Designer**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Anzeigen der App-Manifest-Datei  
 Die Funktions-Designer können Sie ändern und die App-Manifestdatei für das Feature (feature.xml) zu generieren. Anschließend können Sie den XML-Code für diese Datei in Visual Studio anzeigen.  
  
#### <a name="to-view-the-packaged-manifest-file"></a>So zeigen Sie die App-Manifestdatei an  
  
1.  In der **Funktions-Designer**, wählen Sie die **Manifest** Registerkarte.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>So zeigen Sie die gepackte Manifestdatei mit Projektmappen-Explorer  
  
1.  In **Projektmappen-Explorer**, wählen Sie die **alle Dateien anzeigen** Symbol.  
  
2.  Erweitern Sie Funktionen FeatureName, FeatureName.feature erweitern, und öffnen Sie dann die *FeatureName*. Template.XML-Datei.  
  
    > [!NOTE]  
    >  Wenn Sie die Funktion manifest XML-Datei der Vorlage öffnen, wird automatisch die Dateien überprüft werden, und die Warnungen, die im Fenster "Fehlerliste" angezeigt werden können ignoriert werden.  
  
## <a name="changing-the-manifest-template"></a>Ändern der Manifest-Vorlage  
 Sie können den XML-Code für die Feature-Manifestdatei im XML-Editor von Visual Studio oder im Manifestvorlage ändern. Alle Änderungen an den XML-Code wird mit der App-manifest-Datei zusammengeführt, für die Funktion. Beispielsweise empfiehlt es sich manifest Vorlage zum Anpassen einer Feature-Eigenschaft zu ändern.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>So ändern Sie das manifest Vorlage mithilfe der XML-Editor  
  
1.  In der **Funktions-Designer**, wählen Sie die **Manifest** Registerkarte, erweitern Sie die **Bearbeitungsoptionen** Knoten, und wählen Sie dann die **im XML-Editor geöffnet** Link.  
  
     Änderungen an der XML-Code werden in der App-manifest-Datei zusammengeführt.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>So ändern Sie das manifest Vorlage Manifestvorlage im Bereich ""  
  
1.  In der **Funktions-Designer**, wählen Sie die **Manifest** Registerkarte, erweitern Sie die **Bearbeitungsoptionen** Knoten, und ändern Sie das XML, das im Bereich Manifestvorlage angezeigt wird.  
  
     Änderungen an der XML-Code angezeigt, der **Vorschau der App-Paket-Manifest** Bereich.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Überschreiben die App-Manifest-Datei  
 Sie können dem Funktions-Designer deaktivieren und die Datei feature.xml manuell erstellen. Zum ersten Mal ausführen dieser Prozedur werden die aktuellen Einstellungen im Funktions-Designer in der Funktion XML-Datei gespeichert. Sie können dann ändern oder den XML-Code überschreiben.  
  
> [!NOTE]  
>  Wenn Sie hinzufügen oder Entfernen von SharePoint-Projektelemente in der XML-Datei während der Funktions-Designer deaktiviert ist, werden diese Projektelemente nicht gepackt.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Um App-manifest-Datei zu überschreiben, durch Deaktivieren des Designers  
  
1.  In der **Funktions-Designer**, wählen Sie die **Manifest** Registerkarte.  
  
2.  Erweitern Sie die **Bearbeitungsoptionen** Knoten, wählen Sie die **überschreiben generierte XML und bearbeiten Manifest in der XML-Editor** verknüpfen, und wählen Sie dann die **Ja** Schaltfläche.  
  
     Die Vorlage wird durch die aktuelle App-manifest-Datei aktualisiert.  
  
## <a name="enabling-the-feature-designer"></a>Aktivieren der Funktions-Designer  
 Sie können die Funktions-Designer zum Anpassen der Datei "Feature.xml" erneut aktivieren.  
  
#### <a name="to-re-enable-the-designer"></a>Um den Designer erneut zu aktivieren.  
  
1.  In der **Funktions-Designer**, wählen Sie die **manifest Änderungen verwerfen und erneutes Aktivieren der Designer** verknüpfen, und wählen Sie dann die **Ja** Schaltfläche.  
  
2.  Die Vorlage wird mit dem ursprünglichen Text aktualisiert, und alle Änderungen an der XML-Code gehen verloren.  
  
## <a name="see-also"></a>Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  