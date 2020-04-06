---
title: Versand Visual Studio Erweiterungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767bb24bb5cb47f1af1452aa04ebdc91c778e284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700114"
---
# <a name="shipping-visual-studio-extensions"></a>Bereitstellen von Visual Studio-Erweiterungen
Nachdem Sie die Erweiterung entwickelt haben, können Sie sie auf anderen Computern installieren, sie für Ihre Freunde und Kollegen freigeben oder im Visual Studio Marketplace veröffentlichen. In diesem Abschnitt erklären wir Ihnen alles, was Sie tun müssen, um Ihre Erweiterung zu veröffentlichen und zu verwalten: Arbeiten mit .vsix-Dateien, Veröffentlichen, Lokalisieren und Aktualisieren.

## <a name="working-with-vsix-extensions"></a>Arbeiten mit VSIX-Erweiterungen
 Sie können eine VSIX-Erweiterung erstellen, indem Sie ein leeres VSIX-Projekt erstellen und dann verschiedene Elementvorlagen hinzufügen. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

 Sie können das VSIX-Format verwenden, um Projektvorlagen, Elementvorlagen, VSPackages, MEF-Komponenten (Managed Extensibility Framework), Toolbox-Steuerelemente, Assemblys und benutzerdefinierte Typen zu verpacken (einschließlich benutzerdefinierter Startseiten für Visual Studio 2017). **Toolbox** Das VSIX-Format verwendet die dateibasierte Bereitstellung. Weitere Informationen zu VSIX-Paketen finden Sie unter [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md).

 Das VSIX-Format unterstützt die Installation von Codeausschnitten nicht. Bestimmte andere Szenarien wie das Schreiben in den globalen Assemblycache (GAC) oder in die Systemregistrierung werden nicht unterstützt. Wenn Sie in der Installation in den GAC oder die Registrierung schreiben müssen, müssen Sie Windows Installer verwenden. Weitere Informationen finden Sie unter [Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Veröffentlichen der Erweiterung im Visual Studio Marketplace
 Sie können Ihre Erweiterung an andere Personen verteilen, indem Sie ihnen einfach die .vsix-Datei zusenden oder auf einem Server einstellen. Aber der beste Weg, um Ihren Code in die Hände von vielen Menschen zu bekommen, ist es, ihn auf dem [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)zu setzen. Visual Studio Marketplace-Erweiterungen sind Visual Studio-Benutzern über **Erweiterungen und Updates**verfügbar. Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).

 Ein vollständiges Beispiel zum Hochladen einer Erweiterung in den Visual Studio Marketplace finden Sie unter [Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 Beim Entwickeln von Steuerelementen, Vorlagen und Tools können Sie diese für Ihre Organisation freigeben, indem Sie sie in einer privaten Galerie in Ihrem Intranet veröffentlichen. Weitere Informationen finden Sie unter [Private Galerien](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Lokalisieren Ihrer Erweiterung
 Wenn Sie die Erweiterung in verschiedenen Gebietsschemas freigeben möchten, sollten Sie die Lokalisierung in Betracht ziehen. Eine Erläuterung zu den beteiligten Paketen finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Aktualisieren und Versionieren Ihrer Erweiterung
 Nachdem Sie Ihre Erweiterung veröffentlicht haben, wird es eine Zeit, wenn Sie es aktualisieren müssen. Informationen zum Aktualisieren einer Erweiterung, die im Visual Studio Marketplace veröffentlicht wurde, finden Sie unter [Gewusst wie: Aktualisieren einer Erweiterung](../extensibility/how-to-update-a-visual-studio-extension.md).

 Sie können die Erweiterung so festlegen, dass sie mehrere Versionen von Visual Studio unterstützt. Weitere Informationen finden Sie unter [Unterstützung mehrerer Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)|Erläutert, wie die VSIX-Projektvorlage zum Installieren einer benutzerdefinierten Projektvorlage verwendet wird.|
|[Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)|Beschreibt die Komponenten eines VSIX-Pakets.|
|[VSIX-Projektvorlage](../extensibility/vsix-project-template.md)|Enthält Schritt-für-Schritt-Anleitungen zum Verpacken und Veröffentlichen einer Erweiterung.|
|[Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)|Erläutert, wie lokalisierter Text für den Installationsprozess mithilfe von extension.vsixlangpack-Dateien verwendet wird.|
|[Vorgehensweise: Aktualisieren einer Erweiterung](../extensibility/how-to-update-a-visual-studio-extension.md)|Beschreibt, wie sie eine Erweiterung auf Ihrem System aktualisieren und wie ein Update für eine vorhandene Visual Studio-Erweiterung bereitgestellt wird.|
|[Gewusst wie: Hinzufügen einer Abhängigkeit zu einem VSIX-Paket](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Beschreibt das Hinzufügen von Verweisen auf VSIX-Bereitstellungspakete.|
|[Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Erläutert, wie Sie Ihre Erweiterung mit Windows Installer bereitstellen.|
|[Signieren von VSIX-Paketen](../extensibility/signing-vsix-packages.md)|Erläutert das Signieren von VSIX-Paketen.|
|[Private Kataloge](../extensibility/private-galleries.md)|Erläutert, wie private Galerien für Erweiterungen erstellt werden.|
|[Unterstützen mehrerer Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Zeigt, wie Ihre Erweiterung mehrere Versionen von Visual Studio unterstützt.|
|[Finden von Visual Studio](locating-visual-studio.md)|Beschreibt, wie Visual Studio-Instanzen für die bereitstellung benutzerdefinierter Erweiterungen gesucht werden.|
