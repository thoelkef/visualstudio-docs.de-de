---
title: Visual Studio-Erweiterungen Protokollversand | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 543f107081a5cc29ac14f1c2ba2e05924b72e353
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="shipping-visual-studio-extensions"></a>Versand von Visual Studio-Erweiterungen
Nachdem Sie die Erweiterung entwickeln abgeschlossen haben, können Sie auf anderen Computern zu installieren, Ihren Freunden und Ihrer Kollegen freigeben oder auf Visual Studio Marketplace zu veröffentlichen. In diesem Abschnitt erläutern wir die Dinge, die Sie zum Veröffentlichen und verwalten die Erweiterung ausführen müssen: Arbeiten mit VSIX-Dateien, Veröffentlichung, zu lokalisieren und zu aktualisieren.  
  
## <a name="working-with-vsix-extensions"></a>Arbeiten mit VSIX-Erweiterungen  
 Sie können ein VSIX-Erweiterungen erstellen, indem Sie ein leeres VSIX-Projekt erstellen, und klicken Sie dann unterschiedliche Vorlagen hinzugefügt. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).  
  
 Können Sie das Format des VSIX-Paket-Projektvorlagen, Vorlagen, VSPackages, Managed Extensibility Framework (MEF) Komponenten, Element **Toolbox** Steuerelemente, Assemblys und benutzerdefinierte Typen (Dies schließt benutzerdefinierte Startseiten). Das VSIX-Format wird die dateibasierte Bereitstellung verwendet. Weitere Informationen zu VSIX-Pakete, finden Sie unter [Aufbau eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md).  
  
 Das VSIX-Format unterstützt nicht die Installation von Codeausschnitten. Bestimmte andere Szenarien, z. B. das Schreiben auf den globalen Assemblycache (GAC) oder in der systemregistrierung wird ebenfalls nicht unterstützt. Wenn Sie in den GAC oder der Registrierung bei der Installation schreiben müssen, müssen Sie Windows Installer verwenden. Weitere Informationen finden Sie unter [Vorbereiten von Erweiterungen für Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Die Erweiterung veröffentlichen Visual Studio Marketplace  
 Sie können die Erweiterung an andere Personen verteilen, einfach durch Senden sie die VSIX-Datei oder nicht auf einem Server ablegen. Die beste Methode zum Abrufen von Code in die Hände für viele Personen ist so lange sie jedoch die [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Visual Studio Marketplace-Erweiterungen sind verfügbar für Visual Studio-Benutzer über **Erweiterungen und Updates**. Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Ein vollständiges Beispiel, das zeigt, wie eine Erweiterung in Visual Studio Marketplace hochladen, finden Sie unter [Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## <a name="private-galleries"></a>Private Galleries  
 Bei der Entwicklung von Steuerelementen, Vorlagen und Tools können Sie diese für Ihre Organisation freigeben, indem sie einen privaten Katalog in Ihrem Intranet bereitgestellt werden. Weitere Informationen finden Sie unter [Private Galleries](../extensibility/private-galleries.md).  
  
## <a name="localizing-your-extension"></a>Lokalisieren die Erweiterung  
 Wenn Sie beabsichtigen, Ihre Erweiterung in anderen Gebietsschemata freigeben, sollten Sie erwägen, Lokalisierung. Eine Erläuterung, welcher Aufwand erforderlich ist, finden Sie unter [VSIX-Pakete zum Lokalisieren von](../extensibility/localizing-vsix-packages.md).  
  
## <a name="updating-and-versioning-your-extension"></a>Aktualisieren und Versionsverwaltung der Erweiterung  
 Nachdem Sie die Erweiterung veröffentlicht haben, wird eine Zeit, wenn Sie es aktualisieren müssen, stammen. Um herauszufinden, wie eine Erweiterung aktualisiert wird, die auf dem Visual Studio Marketplace veröffentlicht wurde, finden Sie unter [Vorgehensweise: Aktualisieren einer Erweiterung](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Sie können eine Erweiterung zu unterstützen mehrere Versionen von Visual Studio festlegen. Weitere Informationen finden Sie unter [unterstützen mehrere Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)|Es wird erläutert, wie die VSIX-Projektvorlage verwenden, um eine benutzerdefinierte Vorlage zu installieren.|  
|[Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)|Beschreibt die Komponenten eines VSIX-Pakets.|  
|[VSIX-Projektvorlage](../extensibility/vsix-project-template.md)|Bietet schrittweise Anleitungen zum Packen und veröffentlichen eine Erweiterung an.|  
|[Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)|Erläutert, wie während des Installationsvorgangs extension.vsixlangpack-Dateien mit lokalisierten Text bereit.|  
|[Vorgehensweise: Aktualisieren einer Erweiterung](../extensibility/how-to-update-a-visual-studio-extension.md)|Beschreibt, wie eine Erweiterung auf Ihrem System aktualisieren und Bereitstellen eines Updates auf eine vorhandene Visual Studio-Erweiterung.|  
|[Gewusst wie: Hinzufügen einer Abhängigkeit zu einem VSIX-Paket](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Beschreibt, wie Verweise auf die VSIX-Pakete hinzufügen.|  
|[Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Erläutert die Erweiterung mit Windows Installer bereitstellen.|  
|[Signieren von VSIX-Paketen](../extensibility/signing-vsix-packages.md)|Erläutert das VSIX-Pakete zu signieren.|  
|[Private Kataloge](../extensibility/private-galleries.md)|Erläutert, wie private Kataloge für Erweiterungen zu erstellen.|  
|[Unterstützen mehrerer Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Veranschaulicht, wie Ihre Erweiterung unterstützt mehrere Versionen von Visual Studio.|
|[Finden von Visual Studio](locating-visual-studio.md)|Beschreibt, wie Visual Studio-Instanzen für die benutzerdefinierte Erweiterung Bereitstellung gefunden.|
