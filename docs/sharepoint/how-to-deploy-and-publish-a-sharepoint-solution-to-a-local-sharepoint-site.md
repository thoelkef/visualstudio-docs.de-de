---
title: "Gewusst wie: Bereitstellen und Ver&#246;ffentlichen einer SharePoint-L&#246;sung auf einer lokalen SharePoint-Website | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Bereitstellen [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Bereitstellen"
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Gewusst wie: Bereitstellen und Ver&#246;ffentlichen einer SharePoint-L&#246;sung auf einer lokalen SharePoint-Website
  Sie können SharePoint\-Lösungen auf einem lokalen SharePoint\-Server auf dem Entwicklungscomputer bereitstellen oder veröffentlichen.  Der Bereitstellungsprozess wird die WSP\-Datei auf den SharePoint\-Server kopiert, die Lösung installiert und aktiviert die Funktionen.  Der Veröffentlichungsprozess kopiert nur die WSP\-Datei auf dem SharePoint\-Server und installiert sie.  Sie müssen ihn manuell aktivieren, um es in SharePoint zu aktivieren.  
  
## So stellen Sie eine SharePoint\-Lösung auf dem lokalen SharePoint\-Server bereit  
  
1.  Wählen Sie im **Projektmappen\-Explorer** das Projekt aus, das Sie bereitstellen möchten.  
  
2.  Wählen Sie in der Menüleiste **Projektmappe bereitstellen**, **Erstellen** aus.  
  
     Die WSP\-Datei wird erstellt und auf dem lokalen SharePoint\-Server installiert.  Außerdem werden die Funktionen aktiviert.  
  
## So stellen Sie eine SharePoint\-Lösung in einen lokalen SharePoint\-Server veröffentlichen  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das SharePoint\-Projekt, das Sie veröffentlichen und dann **Veröffentlichen** auswählen möchten.  
  
2.  Im Dialogfeld **Veröffentlichen** wählen Sie das Optionsfeld **Im Dateisystem veröffentlichen** aus.  
  
3.  Im Textfeld **Zielort** geben Sie einen lokalen Pfad ein, und wählen Sie dann die Schaltfläche **Veröffentlichen** aus.  
  
     Der Veröffentlichungsstatus wird im Visual Studio\-Fenster **Ausgabe**.  Wenn der Prozess abgeschlossen ist, wird die Projektmappendatei \(.wsp\) auf dem lokalen SharePoint\-Server installiert.  Sie muss jedoch noch aktiviert sein, in SharePoint verwendet werden.  Wenn die Lösungsdatei bereits vorhanden ist, tritt ein Fehler auf und fragt, ob Sie die vorhandene Datei überschreiben möchten.  Weitere Informationen über das Aktualisieren des Pakets, finden Sie im Abschnitt über den Paketen des Upgrades in [Gewusst wie: Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## Siehe auch  
 [Gewusst wie: Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remoteserver](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Erstellen von SharePoint-Lösungspaketen](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Gewusst wie: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Gewusst wie: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  