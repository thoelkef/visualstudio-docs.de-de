---
title: Visual Studio-SDK | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7554bf39960a55a566b366abc328f54199bd4367
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512386"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Visual Studio SDK](https://docs.microsoft.com/visualstudio/extensibility/visual-studio-sdk).  
  
Visual Studio SDK können Sie die Visual Studio-Features erweitern oder neue Features in Visual Studio integrieren. Sie können Ihre Erweiterungen für andere Benutzer sowie für Visual Studio-Katalog verteilen. Im Folgenden werden einige Möglichkeiten für die Erweiterung von Visual Studio vorgestellt:  
  
-   Fügen Sie Befehle, Schaltflächen, Menüs und andere Elemente der Benutzeroberfläche der IDE  
  
-   Toolfenster für die neue Funktionalität hinzufügen  
  
-   Erweitern Sie IntelliSense für eine bestimmte Sprache, oder geben Sie IntelliSense für neue Programmiersprachen  
  
-   Verwenden von Glühbirnen um zur Verfügung zu stellen Hinweise und Empfehlungen, die Entwicklern helfen, besseren Code schreiben  
  
-   Aktivieren der Unterstützung für eine neue Sprache  
  
-   Hinzufügen eines benutzerdefinierten Projekttyps  
  
-   Erreichen Sie Millionen von Entwicklern über Visual Studio Gallery  
  
 Wenn Sie Visual Studio-Erweiterung vor nie geschrieben haben, sollte Weitere Informationen finden Sie Informationen zu diesen Features und zur [ab, die für Visual Studio-Erweiterungen entwickeln](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Installieren von Visual Studio SDK  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Neuerungen in Visual Studio 2015 SDK  
 Visual Studio SDK verfügt über einige neue Features, einschließlich Glühbirnen und neue Projektelemente, die Ihnen ermöglichen, Menübefehle, Toolfenster und editorerweiterungen, die mithilfe eines VSIX-Pakets zu erstellen. Weitere Informationen finden Sie unter [Neuigkeiten in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Richtlinien zur Benutzerfreundlichkeit in Visual Studio  
 Erhalten Sie nützliche Tipps zum Entwerfen der Benutzeroberflächenautomatisierungs für die Erweiterung im [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Außerdem erhalten Sie, wie Sie eine Erweiterung, die auf hohe DPI-Geräten mit hervorragend aussehen machen unsere [DPI-Probleme Adressierung](../extensibility/addressing-dpi-issues2.md) Thema.  
  
 Profitieren Sie von der [Bilddienst und-Katalog](../extensibility/image-service-and-catalog.md) für gute Verwaltung und Unterstützung für hohe DPI-Werte und Designs.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Suchen und Installieren von vorhandenen Visual Studio-Erweiterungen  
 Sie finden die Visual Studio-Erweiterungen in der **Erweiterungen und Updates** -Dialogfeld auf die **Tools** im Menü. Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md). Sie erhalten auch Erweiterungen in der [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK-Referenz  
 Sie finden die Visual Studio SDK-API-Referenz unter [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK-Beispiele  
 Open-Source-Beispiele für Visual Studio SDK-Erweiterungen finden Sie auf GitHub unter [Visual Studio-Beispiele](https://aka.ms/vs2015sdksamples). Dieses GitHub-Repository enthält Beispiele für die verschiedenen erweiterbare Funktionen in Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Andere Visual Studio SDK-Ressourcen  
 Wenn Sie zu Visual Studio SDK PASST Fragen, oder Ihre Erfahrungen mit dem Entwickeln von Erweiterungen freigeben möchten, können Sie die [Visual Studio Extensibility Forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) oder [ExtendVS Gruppe Chat](https://gitter.im/Microsoft/extendvs).  
  
 Können weitere Informationen finden Sie in der [VSX Arcana Blog](http://blogs.msdn.com/b/vsx/) und eine Anzahl von Blogs von Microsoft-MVPs geschrieben:  
  
-   [Bevorzugten Visual Studio-Erweiterungen](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Visual Studio-Erweiterbarkeit](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Erweitern von Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Vorgehensweise: Migrieren von Erweiterungsprojekten zu Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Häufig gestellte Fragen: Konvertieren von Add-Ins in VSPackage-Erweiterungen](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Verwalten von mehreren Threads in verwaltetem Code](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)   
 [Hinzufügen von Befehlen zu Symbolleisten](../extensibility/adding-commands-to-toolbars.md)   
 [Erweitern und Anpassen von Tool Windows](../extensibility/extending-and-customizing-tool-windows.md)   
 [Editor und Sprachdiensterweiterungen](../extensibility/editor-and-language-service-extensions.md)   
 [Erweitern von Projekten](../extensibility/extending-projects.md)   
 [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)   
 [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](../extensibility/creating-custom-project-and-item-templates.md)   
 [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md)   
 [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)   
 [Erweitern von verbundene Dienste](../extensibility/extending-connected-services.md)   
 [Verwalten von VSPackages](../extensibility/managing-vspackages.md)   
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)   
 [Versand von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)   
 [In Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Unterstützung für Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archiv](../extensibility/archive.md)   
 [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md)

