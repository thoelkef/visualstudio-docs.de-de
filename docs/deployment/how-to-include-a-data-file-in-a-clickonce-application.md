---
title: "How to: Include a Data File in a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, data"
  - "deploying applications [ClickOnce], data files"
  - "data access, ClickOnce applications"
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Include a Data File in a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Jeder von Ihnen installierten [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung wird auf dem lokalen Datenträger des Zielcomputers ein Datenverzeichnis zugewiesen, in dem die Anwendung die anwendungsspezifischen Daten verwalten kann.  Datendateien beliebigen Typs sind zulässig: Textdateien, XML\-Dateien und sogar Microsoft Access\-Datenbankdateien \(.mdb\).  In den folgenden Verfahren wird demonstriert, wie Sie einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung eine Datendatei eines beliebigen Typs hinzufügen können.  
  
### So schließen Sie eine Datendatei mit "Mage.exe" ein  
  
1.  Fügen Sie die Datendatei in das Anwendungsverzeichnis ein, in dem sich auch die übrigen Anwendungsdateien befinden.  
  
     Beim Anwendungsverzeichnis handelt es sich normalerweise um ein Verzeichnis, dessen Bezeichnung der aktuellen Version der Bereitstellung entspricht, z. B. v1.0.0.0.  
  
2.  Aktualisieren Sie das Anwendungsmanifest, sodass die Datendatei aufgelistet wird.  
  
     **mage \-u v1.0.0.0\\Application.manifest \-FromDirectory v1.0.0.0**  
  
     Durch diesen Vorgang wird die Liste der Dateien im Anwendungsmanifest erneut erstellt. Darüber hinaus werden Hashsignaturen automatisch generiert.  
  
3.  Öffnen Sie das Anwendungsmanifest in einem Text\- oder XML\-Editor Ihrer Wahl, und suchen Sie das `file`\-Element für die neu hinzugefügte Datei.  
  
     Wenn Sie eine XML\-Datei mit dem Namen `Data.xml` hinzugefügt haben, ist diese mit der im folgenden Codebeispiel vergleichbar.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Fügen Sie diesem Element das Attribut `type` hinzu, und geben Sie den Wert `data` an.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Signieren Sie zuerst das Anwendungsmanifest mit Ihrem Schlüsselpaar oder Zertifikat und dann das Bereitstellungsmanifest erneut.  
  
     Das Bereitstellungsmanifest muss erneut signiert werden, da der zugehörige Hash des Anwendungsmanifests geändert wurde.  
  
     **mage \-s app manifest \-cf cert\_file \-pwd password**  
  
     **mage \-u deployment manifest \-appm app manifest**  
  
     **mage \-s deployment manifest \-cf certfile \-pwd password**  
  
### So schließen Sie eine Datendatei mit "MageUI.exe" ein  
  
1.  Fügen Sie die Datendatei in das Anwendungsverzeichnis ein, in dem sich auch die übrigen Anwendungsdateien befinden.  
  
2.  Beim Anwendungsverzeichnis handelt es sich normalerweise um ein Verzeichnis, dessen Bezeichnung der aktuellen Version der Bereitstellung entspricht, z. B. v1.0.0.0.  
  
3.  Klicken Sie im Menü **Datei** auf **Öffnen**, um das Anwendungsmanifest zu öffnen.  
  
4.  Wählen Sie die Registerkarte **Dateien** aus.  
  
5.  Geben Sie im Textfeld oben auf der Registerkarte das Verzeichnis ein, das die Anwendungsdateien enthält, und klicken Sie dann auf **Auffüllen**.  
  
     Die Datendatei wird im Raster angezeigt.  
  
6.  Legen Sie den Wert für den **Dateityp** der Datendatei auf **Daten** fest.  
  
7.  Speichern Sie das Anwendungsmanifest, und signieren Sie die Datei erneut.  
  
     MageUI.exe fordert Sie zum erneuten Signieren der Datei auf.  
  
8.  Signieren Sie das Bereitstellungsmanifest erneut.  
  
     Das Bereitstellungsmanifest muss erneut signiert werden, da der zugehörige Hash des Anwendungsmanifests geändert wurde.  
  
## Siehe auch  
 [Zugreifen auf lokale und Remotedaten in einer ClickOnce\-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)