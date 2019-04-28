---
title: Visual Studio-SDK | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de690ea6b077ea0c0dc7c6b65f34c68c95e41081
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553665"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK können Sie die Visual Studio-Features erweitern oder neue Features in Visual Studio integrieren. Sie können Ihre Erweiterungen für andere Benutzer sowie für Visual Studio Marketplace verteilen. Im Folgenden werden einige Möglichkeiten für die Erweiterung von Visual Studio vorgestellt:

- Fügen Sie Befehle, Schaltflächen, Menüs und andere Elemente der Benutzeroberfläche der IDE

- Toolfenster für die neue Funktionalität hinzufügen

- Erweitern Sie IntelliSense für eine bestimmte Sprache, oder geben Sie IntelliSense für neue Programmiersprachen

- Verwenden von Glühbirnen um zur Verfügung zu stellen Hinweise und Empfehlungen, die Entwicklern helfen, besseren Code schreiben

- Aktivieren der Unterstützung für eine neue Sprache

- Hinzufügen eines benutzerdefinierten Projekttyps

- Erreichen Sie Millionen von Entwicklern über den Visual Studio Marketplace

  Wenn Sie Visual Studio-Erweiterung vor nie geschrieben haben, sollte Weitere Informationen finden Sie Informationen zu diesen Features und zur [ab Visual Studio-Erweiterungen entwickeln](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Installieren des Visual Studio SDK
 Visual Studio SDK ist ein optionales Feature in Visual Studio-Setup. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Neuerungen in Visual Studio 2017 SDK
 Visual Studio SDK verfügt über einige neue Features wie z. B. das VSIX-v3-Format sowie wichtige Änderungen, die möglicherweise zum Aktualisieren Ihrer Erweiterungs. Weitere Informationen finden Sie unter [Neuigkeiten in Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio Richtlinien zur benutzerfreundlichkeit
 Erhalten Sie nützliche Tipps zum Entwerfen der Benutzeroberflächenautomatisierungs für die Erweiterung im [Richtlinien zur benutzerfreundlichkeit Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

 Außerdem erhalten Sie, wie Sie eine Erweiterung, die auf hohe DPI-Geräten mit hervorragend aussehen machen die [Adresse DPI-Probleme](../extensibility/addressing-dpi-issues2.md) Artikel.

 Profitieren Sie von der [Image, Dienst und Katalog](../extensibility/image-service-and-catalog.md) für gute Verwaltung und Unterstützung für hohe DPI-Werte und Designs.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Suchen Sie und installieren Sie die vorhandene Visual Studio-Erweiterungen
 Sie finden die Visual Studio-Erweiterungen in der **Erweiterungen und Updates** -Dialogfeld auf die **Tools** im Menü. Weitere Informationen finden Sie unter [suchen und Verwenden des Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md). Sie erhalten auch Erweiterungen in der [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK-Referenz
 Sie finden die Visual Studio SDK-API-Referenz unter [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK-Beispiele
 Open-Source-Beispiele für Visual Studio SDK-Erweiterungen finden Sie auf GitHub unter [Visual Studio-Beispiele](https://aka.ms/vs2015sdksamples). Dieses GitHub-Repository enthält Beispiele für die verschiedenen erweiterbare Funktionen in Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Andere Visual Studio SDK-Ressourcen
 Wenn Sie zu Visual Studio SDK PASST Fragen, oder Ihre Erfahrungen mit dem Entwickeln von Erweiterungen freigeben möchten, können Sie die [Visual Studio Extensibility Forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) oder [ExtendVS Gitter-Chatroom](https://gitter.im/Microsoft/extendvs).

 Können weitere Informationen finden Sie in der [VSX Arcana Blog](https://blogs.msdn.microsoft.com/vsx/) und eine Reihe von Blogs von Microsoft-MVPs geschrieben:

- [Bevorzugten Visual Studio-Erweiterungen](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)

- [Visual Studio-Erweiterbarkeit](http://www.visualstudioextensibility.com/overview/vs/)

- [Erweitern von Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Siehe auch
- [Erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Vorgehensweise: Migrieren von Erweiterungsprojekten zu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [HÄUFIG GESTELLTE FRAGEN: Konvertieren von Add-Ins in VSPackage-Erweiterungen](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)
- [Verwalten von mehreren Threads in verwaltetem code](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [Hinzufügen von Befehlen zu Symbolleisten](../extensibility/adding-commands-to-toolbars.md)
- [Erweitern und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md)
- [Service-Erweiterungen, Editoren und Sprachen](../extensibility/editor-and-language-service-extensions.md)
- [Erweitern von Projekten](../extensibility/extending-projects.md)
- [Erweitern von benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)
- [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](../extensibility/creating-custom-project-and-item-templates.md)
- [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md)
- [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)
- [Verwalten von VSPackages](../extensibility/managing-vspackages.md)
- [Visual Studio isolated shell](/visualstudio/extensibility/shell/visual-studio-isolated-shell)
- [Senden von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
- [Im Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Unterstützung für das Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Archiv](../extensibility/archive.md)
- [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md)
