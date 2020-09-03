---
title: Versand Erweiterungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c7154395be43f6a0b07e9f2557d94fa594ef5ba4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150796"
---
# <a name="shipping-visual-studio-extensions"></a>Bereitstellen von Visual Studio-Erweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Hinweis**: die Visual Studio Gallery wird durch das Visual Studio Marketplace ersetzt. Weitere Informationen finden Sie in der neuesten Version dieses Themas.

Nachdem Sie die Entwicklung der Erweiterung abgeschlossen haben, können Sie Sie auf anderen Computern installieren, Sie für Ihre Freunde und Kollegen freigeben oder in der Visual Studio Gallery veröffentlichen. In diesem Abschnitt werden alle Aufgaben erläutert, die Sie zum Veröffentlichen und Verwalten Ihrer Erweiterung ausführen müssen: Arbeiten mit VSIX-Dateien, veröffentlichen, lokalisieren und aktualisieren.

## <a name="working-with-vsix-extensions"></a>Arbeiten mit VSIX-Erweiterungen
 Sie können VSIX-Erweiterungen erstellen, indem Sie ein leeres VSIX-Projekt erstellen und diesem dann unterschiedliche Element Vorlagen hinzufügen. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

 Sie können das VSIX-Format verwenden, um Projektvorlagen, Element Vorlagen, VSPackages, Managed Extensibility Framework (MEF)-Komponenten, **Toolbox** -Steuerelemente, Assemblys und benutzerdefinierte Typen (einschließlich benutzerdefinierter Start Seiten) zu verpacken. Das VSIX-Format verwendet die dateibasierte Bereitstellung. Weitere Informationen zu VSIX-Paketen finden Sie unter [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md).

 Das VSIX-Format unterstützt die Installation von Code Ausschnitten nicht. Außerdem werden bestimmte andere Szenarien, z. b. das Schreiben in den globalen Assemblycache (GAC) oder die Systemregistrierung, nicht unterstützt. Wenn Sie in der-Installation in den GAC oder die Registrierung schreiben müssen, müssen Sie die Windows Installer verwenden. Weitere Informationen finden Sie unter [Vorbereiten von Erweiterungen für Windows Installer Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-gallery"></a>Veröffentlichen der Erweiterung in der Visual Studio Gallery
 Sie können Ihre Erweiterung einfach an andere Personen verteilen, indem Sie Sie per e-Mail an die vsix-Datei senden oder auf einem Server platzieren. Doch die beste Methode, um Ihren Code in die Hand zu bringen, ist die [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Visual Studio Gallery-Erweiterungen sind für Visual Studio-Benutzer durch **Erweiterungen und Updates**verfügbar. Weitere Informationen [finden Sie untersuchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).

 Ein vollständiges Beispiel, das zeigt, wie eine Erweiterung in die Visual Studio Gallery hochgeladen wird, finden Sie unter Exemplarische Vorgehensweise [: Veröffentlichen einer Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 Beim Entwickeln von Steuerelementen, Vorlagen und Tools können Sie diese für Ihre Organisation freigeben, indem Sie Sie in einem privaten Katalog im Intranet veröffentlichen. Weitere Informationen finden Sie unter [private Galerien](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Lokalisieren der Erweiterung
 Wenn Sie beabsichtigen, ihre Erweiterung in verschiedenen Gebiets Schemas freizugeben, sollten Sie diese lokalisieren. Eine Erläuterung dazu, was beteiligt ist, finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Aktualisieren und Versionsverwaltung ihrer Erweiterung
 Nachdem Sie Ihre Erweiterung veröffentlicht haben, kommt es zu einem Zeitpunkt, an dem Sie Sie aktualisieren müssen. Informationen dazu, wie Sie eine Erweiterung aktualisieren, die in der Visual Studio Gallery veröffentlicht wurde, finden Sie unter Gewusst [wie: Aktualisieren einer Erweiterung](../extensibility/how-to-update-a-visual-studio-extension.md).

 Sie können die Erweiterung so festlegen, dass mehrere Versionen von Visual Studio unterstützt werden. Weitere Informationen finden Sie [unter unterstützen mehrerer Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)|Erläutert, wie die VSIX-Projektvorlage verwendet wird, um eine benutzerdefinierte Projektvorlage zu installieren.|
|[Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)|Beschreibt die Komponenten eines VSIX-Pakets.|
|[VSIX-Projektvorlage](../extensibility/vsix-project-template.md)|Enthält Schritt-für-Schritt-Anleitungen zum Verpacken und Veröffentlichen einer Erweiterung.|
|[Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)|Erläutert das Bereitstellen von lokalisiertem Text für den Installationsprozess mithilfe von Extension. vsixlangpack-Dateien.|
|[Vorgehensweise: Aktualisieren einer Erweiterung](../extensibility/how-to-update-a-visual-studio-extension.md)|Hier wird beschrieben, wie Sie eine Erweiterung auf Ihrem System aktualisieren und ein Update für eine vorhandene Visual Studio-Erweiterung bereitstellen.|
|[Gewusst wie: Hinzufügen einer Abhängigkeit zu einem VSIX-Paket](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Beschreibt das Hinzufügen von verweisen zu VSIX-Bereitstellungs Paketen.|
|[Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Erläutert, wie Sie die Erweiterung mit Windows Installer bereitstellen.|
|[Signieren von VSIX-Paketen](../extensibility/signing-vsix-packages.md)|Erläutert, wie VSIX-Pakete signiert werden.|
|[Private Kataloge](../extensibility/private-galleries.md)|Erläutert, wie private Galerien für Erweiterungen erstellt werden.|
|[Unterstützen mehrerer Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Zeigt, wie die Erweiterung mehrere Versionen von Visual Studio unterstützt.|
