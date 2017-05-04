---
title: "Ver&#246;ffentlichungsassistent (Office-Entwicklung in Visual Studio) | Microsoft Docs"
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
  - "VST.ProjectProperties.PublishWizard"
  - "VST.PublishWizard.Publish.2007System"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ClickOnce-Bereitstellung [Office-Entwicklung in Visual Studio], Webpublishing-Assistent"
  - "Bereitstellen von Anwendungen [Office-Entwicklung in Visual Studio], Webpublishing-Assistent"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Webpublishing-Assistent"
  - "Webpublishing-Assistent, Office-Projektmappen"
ms.assetid: 793314b6-b6a6-4509-8f1c-dd9466cf5190
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Ver&#246;ffentlichungsassistent (Office-Entwicklung in Visual Studio)
  Verwenden Sie **Webpublishing\-Assistent**, um die Projektmappendateien an einen bestimmten Speicherort kopiert, erstellen Sie die Manifestdateien und erstellen Sie ein Setupprogramm.  
  
 Um diesen Assistenten, auf dem **Erstellen** Menü zuzugreifen, wählen Sie **Veröffentlichen** *SolutionName*.  Sie können auf den **Webpublishing\-Assistenten** auch vom **Projektmappen\-Explorer** aus zugreifen.  Öffnen Sie das Kontextmenü für den Projektknoten, und wählen Sie dann **Veröffentlichen**aus.  
  
 In jedem der folgenden Abschnitte wird eine Seite des Assistenten beschrieben.  
  
## Wo möchten Sie die Anwendung veröffentlichen?  
 **Veröffentlichungsort für diese Anwendung angeben**  
 Erforderlich.  Beim Veröffentlichungsort handelt es sich um das Verzeichnis, in das der **Webpublishing\-Assistent** die Projektmappendateien, wie Manifeste, Assemblys, temporäre Zertifikate und andere Dateien, aus dem Build kopiert.  Sie müssen über Schreibzugriff für dieses Verzeichnis verfügen.  
  
 Geben Sie den Speicherort als dem Datenträger des, Dateifreigabe, FTP\-Site oder eine Website URL ein, oder klicken Sie auf die Schaltfläche **Durchsuchen** für den Speicherort zu suchen.  Der Pfad kann folgende Formate aufweisen:  
  
-   Einen relativen oder absoluten Pfad im Windows\-Standardformat, wie C:\\Deploy\\MyApplication oder \\MyApplication  
  
-   Einen UNC \(Universal Naming Convention\)\-Pfad, wie \\\\ServerName\\MyApplication\\  
  
-   Eine URL einer Website, z. B. http:\/\/www.microsoft.com\/MyApplication.  
  
 Standardmäßig ist der Veröffentlichungsort *http:\/\/localhost\/Projektname\/* wenn Sie IIS installiert haben, oder das Verzeichnis publish\\, wenn IIS nicht installiert ist.  
  
> [!NOTE]  
>  Wird auf dem Zielcomputer Windows Vista ausgeführt, sind noch weitere Aspekte zu berücksichtigen.  Sie benötigen auf dem Computer mit dem Betriebssystem Windows Vista Administratorrechte, um die Option für lokale Veröffentlichung nutzen zu können.  Zudem ist der Standardspeicherort immer das Verzeichnis *publish\\*, unabhängig davon, ob IIS installiert ist.  
  
## Wie lautet der Standardinstallationspfad auf Endbenutzercomputern?  
 Der Installationspfad ist optional.  Auf Wunsch können Sie den Installationspfad später festlegen.  Ausführlichere Informationen finden Sie unter [Gewusst wie: Ändern des Installationspfads einer Office\-Projektmappe](http://msdn.microsoft.com/de-de/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 Der Installationspfad ist das Verzeichnis, von dem der Endbenutzer die Anpassung installiert.  Es handelt sich zudem um den Pfad, der von der Projektmappe für die Suche nach Updates verwendet wird.  Der **Webpublishing\-Assistent** stellt die Projektmappe nur dann an diesem Speicherort bereit, wenn der Pfad mit dem Pfad identisch ist, den Sie auf der vorherigen Seite im Feld **Veröffentlichungsort für diese Anwendung angeben** eingegeben haben.  
  
 **Von einer Website**  
 Geben Sie die URL an, der die Endbenutzer folgen sollen, um die Projektmappe zu installieren.  
  
 **Von UNC\-Pfad oder Dateifreigabe**  
 Geben Sie den UNC\-Pfad an, dem die Endbenutzer folgen sollen, um die Projektmappe zu installieren.  
  
 **Von CD\-ROM oder DVD\-ROM**  
 Für diese Option ist kein Installationspfad erforderlich.  
  
 Visual Studio brennt die CD oder die DVD nicht.  Sie müssen die Ausgabe manuell auf eine CD oder DVD kopieren.  
  
## Siehe auch  
 [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Veröffentlichungsseite, Projekt-Designer &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  