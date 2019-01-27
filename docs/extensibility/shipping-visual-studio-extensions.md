---
title: Versand von Visual Studio-Erweiterungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e48df9e255fc433a9e7a5f15e1ed9923b47b7284
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013982"
---
# <a name="shipping-visual-studio-extensions"></a>Bereitstellen von Visual Studio-Erweiterungen
Nachdem Sie die Entwicklung Ihrer Erweiterungs abgeschlossen haben, können Sie auf anderen Computern installieren, mit Ihren Freunden und Kollegen freigeben oder veröffentlichen Sie sie in Visual Studio Marketplace. In diesem Abschnitt erläutern wir all die Dinge zu tun, um das Veröffentlichen und verwalten Ihre Erweiterung benötigten: Arbeiten mit der VSIX-Dateien, die Veröffentlichung, zu lokalisieren und zu aktualisieren.  
  
## <a name="working-with-vsix-extensions"></a>Arbeiten mit der VSIX-Erweiterungen  
 Sie können eine VSIX-Erweiterungen erstellen, indem Sie ein leeres VSIX-Projekt erstellen und dann verschiedene Vorlagen hinzuzufügen. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).  
  
 Können Sie das Format des VSIX-Paket-Projektvorlagen, Vorlagen, VSPackages, Managed Extensibility Framework (MEF) Komponenten, Element **Toolbox** Steuerelemente, Assemblys und benutzerdefinierte Typen (Dies schließt benutzerdefinierte Startseiten). Das VSIX-Format wird die dateibasierte Bereitstellung verwendet. Weitere Informationen zu VSIX-Paketen, finden Sie unter [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md).  
  
 Das VSIX-Format unterstützt die Installation von Codeausschnitten nicht. Es unterstützt auch keine bestimmten anderen Szenarios wie z. B. das Schreiben auf den globalen Assemblycache (GAC) oder in die systemregistrierung. Wenn Sie in den GAC oder die Registrierung bei der Installation schreiben möchten, müssen Sie die Windows Installer verwenden. Weitere Informationen finden Sie unter [Vorbereiten von Erweiterungen für Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Veröffentlichen Sie Ihre Erweiterung in Visual Studio Marketplace  
 Die Erweiterung an andere Personen können Sie einfach durch mailing sie die VSIX-Datei oder das Einfügen in auf einem Server verteilen. Die beste Möglichkeit, Ihren Code in den Händen von viele Leute zu erhalten ist, möchte jedoch die [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Visual Studio Marketplace-Erweiterungen stehen für Visual Studio-Benutzer über **Erweiterungen und Updates**. Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Ein vollständiges Beispiel, das zeigt, wie Sie eine Erweiterung in Visual Studio Marketplace hochladen, finden Sie unter [Exemplarische Vorgehensweise: Veröffentlichung von Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## <a name="private-galleries"></a>Private Galleries  
 Bei der Entwicklung von Steuerelementen, Vorlagen und Tools können Sie sie durch eine Veröffentlichung auf einen privaten Katalog in Ihrem Intranet in Ihrer Organisation freigeben. Weitere Informationen finden Sie unter [Private Galleries](../extensibility/private-galleries.md).  
  
## <a name="localizing-your-extension"></a>Lokalisieren die Erweiterung  
 Wenn Sie planen die Erweiterung in unterschiedlichen Gebietsschemata freigeben, sollten Sie erwägen, Lokalisierung. Eine Erläuterung der welcher Aufwand erforderlich ist, finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).  
  
## <a name="updating-and-versioning-your-extension"></a>Aktualisieren und Versionsverwaltung Ihrer Erweiterung  
 Nachdem Sie die Erweiterung veröffentlicht haben, kommen eine Zeit aus, wenn Sie es aktualisieren müssen. Um herauszufinden, wie Sie eine Erweiterung zu aktualisieren, die in Visual Studio Marketplace veröffentlicht wurde, finden Sie unter [Vorgehensweise: Aktualisieren Sie eine Erweiterung](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Sie können die Erweiterung zur Unterstützung mehrerer Versionen von Visual Studio festlegen. Weitere Informationen finden Sie unter [unterstützt mehrere Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)|Es wird erläutert, wie die VSIX-Projektvorlage verwenden, um eine benutzerdefinierte Projektvorlage zu installieren.|  
|[Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)|Beschreibt die Komponenten eines VSIX-Pakets.|  
|[VSIX-Projektvorlage](../extensibility/vsix-project-template.md)|Bietet schrittweise Anleitungen zum Verpacken und veröffentlichen eine Erweiterung an.|  
|[Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)|Erläutert, wie während des Installationsvorgangs extension.vsixlangpack-Dateien mit lokalisierten Text bereit.|  
|[Vorgehensweise: Aktualisieren Sie eine Erweiterung](../extensibility/how-to-update-a-visual-studio-extension.md)|Beschreibt, wie Sie eine Erweiterung auf Ihrem System zu aktualisieren und wie Sie ein Update auf eine vorhandene Visual Studio-Erweiterung bereitstellen.|  
|[Vorgehensweise: Fügen Sie eine Abhängigkeit zu einem VSIX-Paket](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Beschreibt, wie Verweise auf die VSIX-Pakete hinzufügen.|  
|[Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Erläutert, wie zum Bereitstellen einer Erweiterung mit Windows Installer.|  
|[Signieren von VSIX-Paketen](../extensibility/signing-vsix-packages.md)|Erläutert das VSIX-Pakete zu signieren.|  
|[Private Kataloge](../extensibility/private-galleries.md)|Erläutert, wie private Kataloge für Erweiterungen zu erstellen.|  
|[Unterstützen mehrerer Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Veranschaulicht, wie Ihre Erweiterung unterstützt mehrere Versionen von Visual Studio.|
|[Finden von Visual Studio](locating-visual-studio.md)|Beschreibt, wie Visual Studio-Instanzen für die Bereitstellung von benutzerdefinierten Erweiterungen zu suchen.|
