---
title: Visual Studio SDK | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: "56"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fbf9ab21b494bfc8b26251a8bdb79c16f81dc05d
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Das Visual Studio SDK können Sie die Visual Studio-Features erweitern oder neue Funktionen in Visual Studio integrieren. Sie können Ihre Erweiterungen an andere Benutzer als auch für Visual Studio Marketplace verteilen. Im Folgenden werden einige Möglichkeiten für die Erweiterung von Visual Studio vorgestellt:  
  
-   Hinzufügen von Befehlen, Schaltflächen, Menüs und andere Elemente der Benutzeroberfläche der IDE  
  
-   Toolfenster, für die neue Funktionalität hinzufügen  
  
-   Erweitern von IntelliSense für eine bestimmte Sprache aus, oder geben Sie IntelliSense für neue Programmiersprachen  
  
-   Verwenden von Glühbirnen um zur Verfügung zu stellen Hinweise und Vorschläge, die Entwicklern zu helfen, besseren Code schreiben  
  
-   Aktivieren der Unterstützung für eine neue Sprache  
  
-   Hinzufügen eines benutzerdefinierten Projekttyps  
  
-   Erreichen von Millionen von Entwicklern über den Visual Studio Marketplace  
  
 Wenn Sie eine Visual Studio-Erweiterung, bevor Sie nie geschrieben haben, sollten, finden Sie weitere Informationen zu diesen Features und zur [starten Visual Studio-Erweiterungen entwickeln](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Installieren von Visual Studio SDK  
 Das Visual Studio SDK ist ein optionales Feature in Visual Studio-Setup. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Was ist neu in Visual Studio 2017 SDK  
 Das Visual Studio SDK verfügt über einige neuen Funktionen wie das VSIX-v3-Format sowie wichtige Änderungen, die erforderlich sein, die die Erweiterung zu aktualisieren. Weitere Informationen finden Sie unter [Neuigkeiten in der Visual Studio-SDK 2017](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio-Leitfäden für Erfahrung  
 Erhalten Sie hilfreiche Tipps zum Entwerfen der Benutzeroberflächenautomatisierungs für die Erweiterung im [Visual Studio-Umgebung Leitfäden](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Sie können auch erfahren, wie Sie die Erweiterung auf hoher DPI-Geräten mit bestechenden unsere [DPI-Probleme Adressierung](../extensibility/addressing-dpi-issues2.md) Thema.  
  
 Nutzen Sie die [Bilddienst und Katalog](../extensibility/image-service-and-catalog.md) für große Bild Verwaltungs- und Unterstützung für hohen dpi-WERTEN und Designs.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Suchen und Installieren von vorhandenen Visual Studio-Erweiterungen  
 Finden Sie in Visual Studio-Erweiterungen der **Erweiterungen und Updates** -Dialogfeld auf die **Tools** Menü. Weitere Informationen finden Sie unter [suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md). Sie erhalten auch Erweiterungen in der [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK-Referenz  
 Sie finden die Visual Studio-SDK-API-Referenz unter [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK-Beispiele  
 Open-Source-Beispiele von VS-SDK-Erweiterungen finden Sie auf GitHub unter [Visual Studio-Beispiele](https://aka.ms/vs2015sdksamples). Diese GitHub-Repository enthält Beispiele, in denen verschiedene erweiterbare Funktionen in Visual Studio veranschaulichen.  
  
## <a name="other-visual-studio-sdk-resources"></a>Andere Visual Studio SDK-Ressourcen  
 Wenn Sie Fragen zu VSSDK haben oder Ihre Erfahrungen mit dem Entwickeln von Erweiterungen freigeben möchten, können Sie die [Visual Studio Extensibility Forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) oder [ExtendVS Gitter Raum](https://gitter.im/Microsoft/extendvs).  
  
 Können weitere Informationen finden Sie in der [VSX Arcana Blog](http://blogs.msdn.com/b/vsx/) und eine Reihe von Blogs von Microsoft-MVPs geschrieben:  
  
-   [Meine Visual Studio-Erweiterungen](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Visual Studio-Erweiterbarkeit](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Erweitern von Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Vorgehensweise: Migrieren Sie zu Visual Studio 2017 Erweiterungsprojekte](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [Häufig gestellte Fragen: Konvertieren-Add-ins in VSPackage-Erweiterungen](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Verwalten von mehreren Threads in verwaltetem Code](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)   
 [Hinzufügen von Befehlen zu Symbolleisten](../extensibility/adding-commands-to-toolbars.md)   
 [Erweitern und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md)   
 [Editor und Spracherweiterungen-Dienst](../extensibility/editor-and-language-service-extensions.md)   
 [Erweitern von Projekten](../extensibility/extending-projects.md)   
 [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)   
 [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](../extensibility/creating-custom-project-and-item-templates.md)   
 [Erweitern von Eigenschaften und des Fensters Eigenschaften](../extensibility/extending-properties-and-the-property-window.md)   
 [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Verwenden und die Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Verwalten von VSPackages](../extensibility/managing-vspackages.md)   
 [Visual Studio isolierte Shell](../extensibility/visual-studio-isolated-shell.md)   
 [Versand von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)   
 [In der Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Unterstützung für das Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archiv](../extensibility/archive.md)   
 [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md)
