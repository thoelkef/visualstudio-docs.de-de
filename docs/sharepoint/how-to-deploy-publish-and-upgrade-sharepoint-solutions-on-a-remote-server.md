---
title: "Gewusst wie: Bereitstellen, Ver&#246;ffentlichen und Aktualisieren von SharePoint-L&#246;sungen auf einem Remoteserver | Microsoft Docs"
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
helpviewer_keywords: 
  - "Bereitstellen [SharePoint-Entwicklung in Visual Studio]"
  - "Remotebereitstellung [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Bereitstellen"
  - "SharePoint-Entwicklung in Visual Studio, Remotebereitstellung"
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Gewusst wie: Bereitstellen, Ver&#246;ffentlichen und Aktualisieren von SharePoint-L&#246;sungen auf einem Remoteserver
  Zusätzlich zum Bereitstellen von SharePoint\-Lösungen auf dem lokalen System, können Sie Sandbox SharePoint\-Lösungen auf Remotesites den oder zu SharePoint\-Websites local veröffentlichen.  Remote\- Der Veröffentlichungsprozess wird die WSP\-Datei auf den SharePoint\-Server kopiert, die Lösung installiert und aktiviert Sie anschließend, um die Projektmappe zu aktivieren.  Sie können eine für SharePoint\-Lösungs\-Installation auch aktualisieren, nachdem Änderungen daran vorgenommen wurden.  
  
## So eine Sandbox SharePoint\-Lösung auf einem Remotewebserver SharePoint\-Server veröffentlichen  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das Sandboxing SharePoint\-Projekt, das Sie veröffentlichen möchten, und wählen Sie dann **Veröffentlichen** aus.  
  
2.  Im Dialogfeld **Veröffentlichen** wählen Sie das Optionsfeld **In SharePoint veröffentlichen** aus, und geben Sie eine URL für eine Veröffentlichungssite Online, wie im folgenden Beispiel ein: https:\/\/mytestsite.sharepoint.microsoftonline.com.  
  
3.  Wählen Sie das Optionsfeld **Lösungskatalog nach der Veröffentlichung im Browser öffnen**, um die Liste von Projektmappen auf der Seite **Lösungskatalog** anzuzeigen, nachdem Sie veröffentlicht haben.  
  
4.  Wählen Sie die Schaltfläche **Veröffentlichen** aus.  
  
5.  Melden Sie sich an Benutzerauthentifizierung Remoteserver, wenn erforderlich ist.  
  
     Der Veröffentlichungsstatus wird im Visual Studio\-Fenster **Ausgabe**.  Wenn der Prozess abgeschlossen ist, wird die Projektmappendatei \(.wsp\) auf dem SQL\-Remoteserver SharePoint\-Server installiert.  Sie muss jedoch noch aktiviert sein, bevor sie in SharePoint verwendet werden kann.  
  
6.  Auf der Seite **Lösungskatalog** wählen Sie die SharePoint\-Anwendung und anschließend auf dem Menüband, die Schaltfläche **Aktivieren** aus.  
  
7.  Im Dialogfeld **Lösung aktivieren** auf dem Menüband, wählen Sie die Schaltfläche **Aktivieren** erneut aus.  
  
     Die Spalte **Status** auf der Seite **Lösungskatalog** gibt an, dass die Anwendung aktiv ist.  
  
## So eine Sandbox SharePoint\-Lösung auf einem SharePoint\-Server aktualisieren  
 Wenn eine SharePoint\-Lösung Sandkasten bereits auf einem Remoteserver veröffentlicht wird, aktiviert der folgende Prozess Sie, um ihn zu aktualisieren, nachdem Sie die Anwendung in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vornehmen.  
  
1.  Nennen Sie das SharePoint\-Paket in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Dazu, **Projektmappen\-Explorer** auszuführen öffnen das Paket.  Sie wird auf **Paket\-Explorer**.  
  
2.  In **Paket\-Explorer** im Feld **Name**, Änderung der Paketname an einem eindeutigen Namen.  
  
3.  Speichern Sie das Projekt.  
  
4.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Veröffentlichen** aus.  
  
5.  Im Dialogfeld **Veröffentlichen** wählen Sie das Optionsfeld **In SharePoint veröffentlichen** und dann, wenn die URL für den Remoteserver, in dem die Lösung gespeichert wird, fehlt, geben Sie ihn ein.  
  
6.  Wählen Sie das Optionsfeld **Lösungskatalog nach der Veröffentlichung im Browser öffnen**, um die Liste von Projektmappen auf der Seite **Lösungskatalog** anzuzeigen, nachdem Sie veröffentlicht haben.  
  
7.  Wählen Sie die Schaltfläche **Veröffentlichen** aus.  
  
8.  Melden Sie sich an Benutzerauthentifizierung Remoteserver, wenn erforderlich ist.  
  
     Wenn Sie beim Remoteserver kürzlich angemeldet haben, ist möglicherweise die Authentifizierung nicht erforderlich.  
  
     Wenn die frühere Version der Anwendung, die den gleichen Namen vorhanden ist, auf dem SharePoint\-Server vorhanden ist, erhalten Sie eine Fehlermeldung, dass ein Paket mit dem gleichen Namen bereits auf dem SharePoint\-Server vorhanden ist.  Sie müssen das Paket mit einem eindeutigen Namen umbenennen, bevor Sie sie veröffentlichen.  
  
9. Wählen Sie die neue Anwendung in SharePoint, und dann, auf dem Menüband aus, wählen Sie die Schaltfläche **Upgrade** aus.  
  
10. Im Dialogfeld **Lösung aktualisieren** auf dem Menüband, wählen Sie die Schaltfläche **Upgrade** erneut aus.  Die Spalte **Status** auf der Seite **Lösungskatalog** sollte jetzt angeben, dass die Anwendung aktiv ist.  
  
     Die alte Version der Projektmappe wird deaktiviert, wird die neue Version der Projektmappe mit den Daten aktualisiert, die aus der alten Projektmappe beibehalten werden, und die neue Lösung besteht in SharePoint aktiviert.  
  
## Siehe auch  
 [Gewusst wie: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Erstellen von SharePoint-Lösungspaketen](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Gewusst wie: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Gewusst wie: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  