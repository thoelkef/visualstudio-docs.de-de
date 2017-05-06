---
title: "Gewusst wie: Anpassen einer SharePoint-Funktion"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.RAD.FeatureDesigner.SwitchView"
  - "VS.SharePointTools.RAD.featureDesigner.Manifest"
  - "VS.SharePointTools.RAD.FeatureDesignerProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Funktionen"
ms.assetid: e624c546-564b-4c73-9f1b-dc3675e76a55
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Gewusst wie: Anpassen einer SharePoint-Funktion
  Sie können SharePoint\-Funktionen mit dem Funktions\-Designer in Visual Studio erstellen und anpassen.  Beispielsweise können Sie den Funktionsbereich festlegen und weitere Funktionen als Abhängigkeiten hinzufügen.  Standardmäßig wird der Funktions\-Designer geöffnet, wenn Sie im Projektmappen\-Explorer oder im SharePoint\-Paket\-Explorer eine neue Funktion hinzufügen.  
  
## Öffnen des Funktions\-Designers  
 Mit dem Funktions\-Designer können Sie einer Funktion SharePoint\-Projektelemente hinzufügen oder diese aus einer Funktion entfernen.  
  
#### So öffnen Sie den Funktions\-Designer  
  
1.  Erweitern Sie im **Projektmappen\-Explorer** den Eintrag **Funktionen**.  
  
2.  Doppelklicken Sie auf das Element *Feature1*, oder öffnen Sie das Kontextmenü für das Element *Feature1* und wählen Sie dann **Ansicht\-Designer** aus.  
  
## Anzeigen der gepackten Manifestdatei  
 Sie können den Funktions\-Designer verwenden, um die gepackte Manifestdatei für die Funktion \(feature.xml\) zu ändern und zu generieren.  Dann können Sie den XML\-Code für diese Datei in Visual Studio anzeigen.  
  
#### So zeigen Sie die gepackte Manifestdatei an  
  
1.  Wählen Sie im **Funktions\-Designer** die Registerkarte **Manifest** aus.  
  
#### So zeigen Sie die gepackte Manifestdatei mit dem Projektmappen\-Explorer an  
  
1.  Wählen Sie im **Projektmappen\-Explorer** das Symbol **Alle Dateien anzeigen** aus.  
  
2.  Erweitern Sie Funktionen, erweitern Sie FeatureName, erweitern Sie FeatureName.feature und öffnen Sie dann *FeatureName*. Template.xml.  
  
    > [!NOTE]  
    >  Wenn Sie die XML\-Manifestdatei der Funktionsvorlage öffnen, werden die Dateien automatisch überprüft, und die im Fenster Fehlerliste angezeigten Warnungen können ignoriert werden.  
  
## Ändern der Manifestvorlage  
 Sie können den XML\-Code für die Funktionsmanifestdatei im Visual Studio\-XML\-Editor oder im Bereich Manifestvorlage ändern.  Alle Änderungen am XML\-Code werden mit der gepackten Manifestdatei für die Funktion zusammengeführt.  Sie können die Manifestvorlage beispielsweise ändern, um eine Funktionseigenschaft anzupassen.  
  
#### So ändern Sie die Manifestvorlage mit dem XML\-Editor  
  
1.  Wählen Sie im **Funktions\-Designer** die Registerkarte **Manifest** aus, erweitern Sie den Knoten **Optionen bearbeiten**, und anschließend den Link **In XML\-Editor öffnen** aus.  
  
     Änderungen am XML\-Code werden mit der gepackten Manifestdatei zusammengeführt.  
  
#### So ändern Sie die Manifestvorlage im Bereich Manifestvorlage  
  
1.  Wählen Sie im **Funktions\-Designer** die Registerkarte **Manifest** aus, erweitern Sie den Knoten **Optionen bearbeiten**, und ändern Sie anschließend den XML\-Code, der im Bereich Manifestvorlage wird.  
  
     Änderungen am XML\-Code werden im Bereich **Vorschau des verpackten Manifests** angezeigt.  
  
## Überschreiben der gepackten Manifestdatei  
 Sie können den Funktions\-Designer deaktivieren und die Datei feature.xml manuell erstellen.  Wenn Sie dieses Verfahren erstmals ausführen, werden die aktuellen Einstellungen im Funktions\-Designer in der XML\-Datei der Funktionsvorlage gespeichert.  Dann können Sie den XML\-Code ändern oder überschreiben.  
  
> [!NOTE]  
>  Wenn Sie SharePoint\-Projektelemente in der XML\-Datei hinzufügen oder entfernen, während der Funktions\-Designer deaktiviert ist, werden diese Projektelemente nicht verpackt.  
  
#### So überschreiben Sie die gepackte Manifestdatei durch Deaktivieren des Designers  
  
1.  Wählen Sie im **Funktions\-Designer** die Registerkarte **Manifest** aus.  
  
2.  Erweitern Sie den Knoten **Optionen bearbeiten**, wählen Sie den Link **Generierten XML\-Code überschreiben und Manifest im XML\-Editor bearbeiten**, und wählen Sie dann die Schaltfläche **Ja** aus.  
  
     Die Vorlage wird mit der aktuellen gepackten Manifestdatei aktualisiert.  
  
## Aktivieren des Funktions\-Designers  
 Sie können den Funktions\-Designer erneut aktivieren, um die Datei feature.xml anzupassen.  
  
#### So aktivieren Sie den Designer erneut  
  
1.  Wählen Sie unter **Funktions\-Designer** den Link **Verwerfen Sie Manifestbearbeitungen, und aktivieren Sie den Designer erneut**, und wählen Sie dann die Schaltfläche **Ja** aus.  
  
2.  Die Vorlage wird mit dem ursprünglichen Text aktualisiert, und alle Änderungen am XML\-Code gehen verloren.  
  
## Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  