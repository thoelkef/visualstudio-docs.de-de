---
title: Visual Studio SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698074"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Mit dem Visual Studio SDK können Sie Visual Studio-Features erweitern oder neue Features in Visual Studio integrieren. Sie können Ihre Erweiterungen an andere Benutzer sowie an den Visual Studio Marketplace verteilen. Im Folgenden werden einige Möglichkeiten für die Erweiterung von Visual Studio vorgestellt:

- Hinzufügen von Befehlen, Schaltflächen, Menüs und anderen UI-Elementen zur IDE

- Hinzufügen von Toolfenstern für neue Funktionen

- Erweitern von IntelliSense für eine bestimmte Sprache oder Bereitstellen von IntelliSense für neue Programmiersprachen

- Verwenden Sie Glühbirnen, um Hinweise und Vorschläge zu geben, die Entwicklern helfen, besseren Code zu schreiben

- Unterstützung für eine neue Sprache aktivieren

- Hinzufügen eines benutzerdefinierten Projekttyps

- Erreichen Sie Millionen von Entwicklern über den Visual Studio Marketplace

  Wenn Sie noch nie eine Visual Studio-Erweiterung geschrieben haben, finden Sie weitere Informationen zu diesen Features und unter [Starten der Entwicklung von Visual Studio-Erweiterungen](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Installieren des Visual Studio SDK
 Das Visual Studio SDK ist eine optionale Funktion in Visual Studio-Setup. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Neuerungen im Visual Studio 2017 SDK
 Das Visual Studio SDK verfügt über einige neue Features, z. B. das VSIX v3-Format sowie änderungen, die möglicherweise eine Aktualisierung der Erweiterung erfordern. Weitere Informationen finden Sie unter [Neuerungen im Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio-Benutzererfahrungsrichtlinien
 Erhalten Sie gute Tipps zum Entwerfen der Benutzeroberfläche für Ihre Erweiterung in [Visual Studio-Benutzeroberflächenrichtlinien](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

 Mit dem Artikel [Address DPI issues](../extensibility/addressing-dpi-issues2.md) können Sie auch erfahren, wie Sie Ihre Erweiterung auf Geräten mit hohem DPI-Wert gut aussehen lassen.

 Nutzen Sie den [Image-Service und -Katalog](../extensibility/image-service-and-catalog.md) für eine hervorragende Bildverwaltung und Unterstützung für hohe DPI und -themen.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Suchen und Installieren vorhandener Visual Studio-Erweiterungen
 Visual Studio-Erweiterungen finden Sie im Dialogfeld **Erweiterungen und Updates** im Menü **Extras.** Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md). Erweiterungen finden Sie auch im [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK-Referenz
 Die Visual Studio SDK-API-Referenz finden Sie unter [Visual Studio SDK Reference](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK-Beispiele
 Open-Source-Beispiele für VS SDK-Erweiterungen finden Sie auf GitHub unter [Visual Studio Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Dieses GitHub-Repository enthält Beispiele, die verschiedene erweiterbare Features in Visual Studio veranschaulichen.

## <a name="other-visual-studio-sdk-resources"></a>Andere Visual Studio SDK-Ressourcen
 Wenn Sie Fragen zum VSSDK haben oder Ihre Erfahrungen mit der Entwicklung von Erweiterungen teilen möchten, können Sie das [Visual Studio Extensibility Forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) oder den [ExtendVS Gitter Chatroom](https://gitter.im/Microsoft/extendvs)verwenden.

 Weitere Informationen finden Sie im [VSX Arcana Blog](https://blogs.msdn.microsoft.com/vsx/) und in einer Reihe von Blogs, die von Microsoft MVPs erstellt wurden:

- [Bevorzugte Visual Studio-Erweiterungen](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Visual Studio-Erweiterbarkeit](http://www.visualstudioextensibility.com/overview/vs/)

- [Erweitern von Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Weitere Informationen

- [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Gewusst wie: Migrieren von Erweiterbarkeitsprojekten zu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Häufig gestellte Fragen: Konvertieren von Add-Ins in VSPackage-Erweiterungen](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [Verwalten mehrerer Threads in verwaltetem Code](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [Hinzufügen von Befehlen zu Symbolleisten](../extensibility/adding-commands-to-toolbars.md)
- [Erweitern und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md)
- [Editor- und Sprachdiensterweiterungen](../extensibility/editor-and-language-service-extensions.md)
- [Erweitern von Projekten](../extensibility/extending-projects.md)
- [Erweitern von Benutzereinstellungen und -optionen](../extensibility/extending-user-settings-and-options.md)
- [Erstellen benutzerdefinierter Projekt- und Elementvorlagen](../extensibility/creating-custom-project-and-item-templates.md)
- [Erweitern von Eigenschaften und dem Eigenschaftenfenster](../extensibility/extending-properties-and-the-property-window.md)
- [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Nutzung und Erbringung von Dienstleistungen](../extensibility/using-and-providing-services.md)
- [Verwalten von VSPackages](../extensibility/managing-vspackages.md)
- [Visual Studio-isolierte Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Visual Studio-Erweiterungen versenden](../extensibility/shipping-visual-studio-extensions.md)
- [Im Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Unterstützung für das Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md)
