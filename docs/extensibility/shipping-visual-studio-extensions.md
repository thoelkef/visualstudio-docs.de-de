---
title: "Lieferung von Visual Studio-Erweiterungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX-Bereitstellung"
  - "VSIX-Bereitstellung"
  - "Satelliten-DLLs in VSIX-Paketen"
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Lieferung von Visual Studio-Erweiterungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nachdem Sie die Entwicklung Ihrer Erweiterungs abgeschlossen haben, können Sie auf anderen Computern installieren, gemeinsam mit Ihren Freunden und Kollegen oder veröffentlichen Sie sie in der Visual Studio Gallery. In diesem Abschnitt wird erläutert, all die Dinge, die Sie erledigen möchten, um zu veröffentlichen und verwalten Ihre Erweiterung: Arbeiten mit VSIX\-Dateien, Veröffentlichung, zu lokalisieren und zu aktualisieren.  
  
## Arbeiten mit VSIX\-Erweiterungen  
 Sie können ein VSIX\-Erweiterungen erstellen, indem ein leeres VSIX\-Projekt erstellen und dann verschiedene Elementvorlagen hinzugefügt. Weitere Informationen finden Sie unter [VSIX\-Projektvorlage](../extensibility/vsix-project-template.md).  
  
 Sie können das VSIX\-Format Paket Projektvorlagen, Vorlagen, VSPackages, Managed Extensibility Framework \(MEF\)\-Komponenten, Artikel **Toolbox** Steuerelemente, Assemblys und benutzerdefinierte Typen \(einschließlich benutzerdefinierte Startseiten\). Das VSIX\-Format verwendet dateibasierte Bereitstellung. Weitere Informationen zu VSIX\-Paketen finden Sie unter [Anatomie eines VSIX\-Pakets](../extensibility/anatomy-of-a-vsix-package.md).  
  
 Das VSIX\-Format unterstützt nicht die Installation von Codeausschnitten. Bestimmte andere Szenarien, z. B. schreiben, die den globalen Assemblycache \(GAC\) oder der Registrierung wird ebenfalls nicht unterstützt. Wenn Sie in den GAC oder die Registrierung bei der Installation schreiben müssen, müssen Sie Windows Installer verwenden. Weitere Informationen finden Sie unter [Vorbereiten von Erweiterungen für Windows Installer\-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## Veröffentlichen Sie Ihre Erweiterung in der Visual Studio Gallery  
 Sie können die Erweiterung an andere Personen verteilen, einfach durch e\-Mail die VSIX\-Datei oder auf einem Server eingefügt. Die beste Methode zum Abrufen von Code in die Hände von viele Leute ist, möchte jedoch die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847). Visual Studio Gallery Erweiterungen stehen für Visual Studio\-Benutzer über **Erweiterungen und Updates**. Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio\-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Ein vollständiges Beispiel, das zeigt, wie eine Erweiterung in der Visual Studio Gallery hochladen, finden Sie unter [Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio\-Erweiterungs](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## Private Galerien  
 Bei der Entwicklung von Steuerelementen, Vorlagen und Tools können Sie diese auf Nachrichten mit einem privaten Katalog in Ihrem Intranet Ihrer Organisation freigeben. Weitere Informationen finden Sie unter [Private Galerien](../extensibility/private-galleries.md).  
  
## Lokalisieren die Erweiterung  
 Wenn Sie beabsichtigen, Ihre Erweiterung in unterschiedlichen Gebietsschemata freigeben, sollten Sie Lokalisierung. Eine Erläuterung der einzelnen Schritte finden Sie unter [Lokalisieren von VSIX\-Paketen](../extensibility/localizing-vsix-packages.md).  
  
## Aktualisieren und Versionen der Erweiterung  
 Nachdem Sie die Erweiterung veröffentlicht haben, kommen eine Zeit, die Sie aktualisieren möchten. Um herauszufinden, wie Sie eine Erweiterung zu aktualisieren, die in der Visual Studio Gallery veröffentlicht wurde, finden Sie unter [Gewusst wie: Aktualisieren einer Erweiterung](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Sie können die Erweiterung zur Unterstützung mehrerer Versionen von Visual Studio festlegen. Weitere Informationen finden Sie unter [Unterstützung von mehreren Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Erste Schritte mit der VSIX\-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)|Erläutert die VSIX\-Projektvorlage verwenden, um eine benutzerdefinierte Projektvorlage zu installieren.|  
|[Anatomie eines VSIX\-Pakets](../extensibility/anatomy-of-a-vsix-package.md)|Beschreibt die Komponenten eines VSIX\-Pakets.|  
|[VSIX\-Projektvorlage](../extensibility/vsix-project-template.md)|Bietet eine schrittweise Anleitung zum Verpacken und veröffentlichen eine Erweiterung an.|  
|[Lokalisieren von VSIX\-Paketen](../extensibility/localizing-vsix-packages.md)|Erläutert die lokalisierten Text für den Installationsvorgang mit extension.vsixlangpack\-Dateien bereitstellen.|  
|[Gewusst wie: Aktualisieren einer Erweiterung](../extensibility/how-to-update-a-visual-studio-extension.md)|Beschreibt, wie eine Erweiterung auf Ihrem System aktualisiert und wie Sie ein Update für eine vorhandene Visual Studio\-Erweiterung bereitstellen.|  
|[Gewusst wie: hinzufügen eine Abhängigkeit zu einem VSIX\-Paket](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Beschreibt, wie Verweise auf die VSIX\-Pakete hinzufügen.|  
|[Vorbereiten von Erweiterungen für Windows Installer\-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Erläutert, wie die Erweiterung mit Windows Installer bereitstellen.|  
|[Signieren von VSIX\-Paketen](../extensibility/signing-vsix-packages.md)|Erläutert das VSIX\-Pakete zu signieren.|  
|[Private Galerien](../extensibility/private-galleries.md)|Erstellen Sie private Kataloge für Erweiterungen erläutert.|  
|[Unterstützung von mehreren Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Veranschaulicht, wie Ihre Erweiterung Unterstützung mehrerer Versionen von Visual Studio.|