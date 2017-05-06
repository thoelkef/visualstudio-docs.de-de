---
title: "Gewusst wie: Anpassen eines SharePoint-L&#246;sungspakets"
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
  - "VS.SharePointTools.RAD.PackageDesignerAdvanced"
  - "VS.SharePointTools.RAD.PackageDesigner.Manifest"
  - "VS.SharePointTools.RAD.PackageDesignerProperties"
  - "VS.SharePointTools.RAD.PackageDesigner.SwitchView"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Pakete"
ms.assetid: fd365f8c-8a80-4ce8-8e28-c0eb609f12f3
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Gewusst wie: Anpassen eines SharePoint-L&#246;sungspakets
  Sie können den Paket\-Designer verwenden, um ein Paket \(.wsp\) zu erstellen und anzupassen.  Sie können z. B. SharePoint\-Projektelemente und \-Funktionen hinzufügen, angeben, ob der Webserver beim Bereitstellen der Lösung zurückgesetzt werden soll, und den Bereitstellungsservertyp festlegen.  
  
## Öffnen des Paket\-Designers  
  
#### So öffnen Sie den Paket\-Designer  
  
-   Doppelklicken Sie in **Projektmappen\-Explorer** auf **Paket** oder wählen Sie im Kontextmenü für **PaketAnsicht\-Designer** aus.  
  
## Anzeigen der gepackten Manifestdatei  
 Sie können den Paket\-Designer verwenden, um die gepackte Manifestdatei zu ändern und zu generieren.  Dann können Sie den XML\-Code für diese Datei in Visual Studio anzeigen.  
  
#### So zeigen Sie die XML\-Quelldatei an  
  
1.  Wählen Sie im **Paket\-DesignerManifest** aus.  
  
#### So zeigen Sie die gepackte Manifestdatei mit dem Projektmappen\-Explorer an  
  
1.  Wählen Sie im **Projektmappen\-ExplorerAlle Dateien anzeigen** aus.  
  
2.  Erweitern Sie Paket, Erweitern Sie Package.package und öffnen Sie dann die Package.Template.xml\-Datei.  
  
    > [!NOTE]  
    >  Wenn Sie die XML\-Datei zum Manifest der Paketvorlage öffnen, werden die Dateien automatisch überprüft, und Sie können die Warnungen ignorieren, die im Fenster Fehlerliste angezeigt werden.  
  
## Ändern der Manifestvorlage  
 Sie können den XML\-Code für die gepackte Manifestdatei im Visual Studio\-XML\-Editor oder im Bereich Manifestvorlage ändern.  Alle Änderungen am XML\-Code werden mit der gepackten Manifestdatei für das Paket zusammengeführt.  
  
#### So ändern Sie die Manifestvorlage mit dem XML\-Editor  
  
1.  Wählen Sie im **Paket\-Designer** die Registerkarte **Manifest** aus, erweitern Sie den Knoten **Optionen bearbeiten**, und anschließend den Link **In XML\-Editor öffnen** aus.  
  
     Änderungen am XML\-Code werden mit der gepackten Manifestdatei zusammengeführt.  
  
#### So ändern Sie die Manifestvorlage im Bereich Manifestvorlage  
  
1.  Wählen Sie im **Paket\-Designer** die Registerkarte **Manifest** aus, erweitern Sie den Knoten **Optionen bearbeiten**, und ändern Sie anschließend den XML\-Code, der im Bereich Manifestvorlage wird.  
  
     Änderungen am XML\-Code werden im Bereich **Vorschau des verpackten Manifests** angezeigt.  
  
## Überschreiben der gepackten Manifestdatei  
 Sie können den Paket\-Designer deaktivieren und die Datei manifest.xml manuell erstellen.  Wenn Sie dieses Verfahren erstmals ausführen, werden die aktuellen Einstellungen im Paket\-Designer in der XML\-Datei der Paketvorlage gespeichert.  Dann können Sie den XML\-Code ändern oder überschreiben.  
  
> [!NOTE]  
>  Wenn Sie SharePoint\-Projektelemente und \- Funktionen in der XML\-Datei hinzufügen oder entfernen, während der Paket\-Designer deaktiviert ist, werden diese Projektelemente und Funktionen nicht verpackt.  
  
#### So überschreiben Sie die gepackte Manifestdatei durch Deaktivieren des Designers  
  
1.  Wählen Sie im **Paket\-Designer** die Registerkarte **Manifest** aus.  
  
2.  .  
  
3.  Erweitern Sie den Knoten **Optionen bearbeiten**, wählen Sie den Link **Generierten XML\-Code überschreiben und Manifest im XML\-Editor bearbeiten**, und wählen Sie dann die Schaltfläche **Ja** aus.  
  
     Die Vorlage wird mit der aktuellen gepackten Manifestdatei aktualisiert.  
  
## Aktivieren des Paket\-Designers  
 Sie können den Paket\-Designer erneut aktivieren, um die Datei manifest.xml anzupassen.  
  
#### So aktivieren Sie den Designer erneut  
  
1.  Wählen Sie unter **Paket\-Designer** den Link **Verwerfen Sie Manifestbearbeitungen, und aktivieren Sie den Designer erneut**, und wählen Sie dann die Schaltfläche **Ja** aus.  
  
     Die Vorlage wird mit dem ursprünglichen Text aktualisiert, und alle Änderungen am XML\-Code gehen verloren.  
  
## Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  