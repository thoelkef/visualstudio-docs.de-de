---
title: Visual Studio SDK | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 56
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: efc5a2722757229057a91f5e3a6c2ad3681f5a89
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Das Visual Studio SDK können Sie Visual Studio-Features erweitern oder neue Funktionen in Visual Studio integrieren. Sie können Ihre Erweiterungen für andere Benutzer als auch für Visual Studio Gallery verteilen. Im Folgenden werden einige Möglichkeiten für die Erweiterung von Visual Studio vorgestellt:  
  
-   Hinzufügen von Befehlen, Schaltflächen, Menüs und andere Elemente der Benutzeroberfläche der IDE  
  
-   Toolfenster für neue Funktionen hinzufügen  
  
-   Erweitern von IntelliSense für eine bestimmte Sprache, oder geben Sie IntelliSense für neue Programmiersprachen  
  
-   Verwenden von Glühbirnen um zur Verfügung zu stellen Hinweise und Vorschläge, die Entwicklern helfen, besseren Code schreiben  
  
-   Aktivieren der Unterstützung für eine neue Sprache  
  
-   Fügen Sie einen benutzerdefinierten Projekttyp  
  
-   Erreichen Sie Millionen von Entwicklern über die Visual Studio Gallery  
  
 Wenn Sie Visual Studio-Erweiterung vor nie geschrieben haben, sollte Weitere Informationen finden Sie Informationen zu diesen Funktionen und bei [für Visual Studio-Erweiterungen entwickeln ab](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Das Visual Studio SDK installieren  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installation von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Was ist neu in Visual Studio 2015 SDK  
 Das Visual Studio SDK verfügt über einige neue Features, einschließlich Glühbirnen und neue Projektelemente, mit die Sie Menübefehle, Toolfenstern und Editor-Erweiterung mithilfe eines VSIX-Pakets erstellen können. Weitere Informationen finden Sie unter [What's New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio-Richtlinien für die Gestaltung der Benutzeroberfläche  
 Hervorragende Tipps zum Entwerfen der Benutzeroberfläche für die Erweiterung im [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Außerdem erhalten Sie, wie Sie Ihre Erweiterung eindrucksvoll auf hohe DPI-Geräten mit unserer [Adressierung DPI Probleme](../extensibility/addressing-dpi-issues2.md) Thema.  
  
 Nutzen Sie die [Abbilder und Katalog](../extensibility/image-service-and-catalog.md) für gute Verwaltung und Unterstützung für hohe DPI-Wert und Designs.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Suchen und Installieren von vorhandenen Visual Studio-Erweiterungen  
 Finden Sie in Visual Studio-Erweiterungen der **Erweiterungen und Updates** Dialogfeld auf die **Tools** Menü. Weitere Informationen finden Sie unter [suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md). Sie finden auch die Erweiterungen in der [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK-Referenz  
 Sie finden die Visual Studio-SDK-API-Referenz unter [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK-Beispiele  
 Open-Source-Beispiele für Visual Studio SDK-Erweiterungen finden Sie auf GitHub unter [Visual Studio-Beispiele](https://aka.ms/vs2015sdksamples). Diese GitHub-Repository enthält Beispiele, in denen verschiedene erweiterbare Funktionen in Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Andere Visual Studio SDK-Ressourcen  
 Wenn Sie zu VSSDK Fragen oder Ihre Erfahrungen Erweiterungen entwickeln möchten, können Sie die [Visual Studio Extensibility Forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) oder [ExtendVS Gruppe Chat](https://gitter.im/Microsoft/extendvs).  
  
 Können weitere Informationen finden Sie in der [Arcana VSX-Blog](http://blogs.msdn.com/b/vsx/) und eine Anzahl von Blogs von Microsoft-MVPs geschrieben:  
  
-   [Bevorzugte Visual Studio-Erweiterungen](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Visual Studio-Erweiterbarkeit](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Erweitern von Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Gewusst wie: Migrieren von Erweiterungsprojekte in Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Häufig gestellte Fragen: Konvertieren von Add-Ins in VSPackage-Erweiterungen](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Verwalten von mehreren Threads in verwaltetem Code](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)   
 [Hinzufügen von Befehlen zu Symbolleisten](../extensibility/adding-commands-to-toolbars.md)   
 [Erweitern und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md)   
 [-Editor, und Language Service Extensions](../extensibility/editor-and-language-service-extensions.md)   
 [Erweitern von Projekten](../extensibility/extending-projects.md)   
 [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)   
 [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](../extensibility/creating-custom-project-and-item-templates.md)   
 [Erweitern von Eigenschaften und das Eigenschaftenfenster](../extensibility/extending-properties-and-the-property-window.md)   
 [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Verwalten von VSPackages](../extensibility/managing-vspackages.md)   
 [Visual Studio Shell Isolated](../extensibility/visual-studio-isolated-shell.md)   
 [Lieferung von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)   
 [In der Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Unterstützung für das Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archiv](../extensibility/archive.md)   
 [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md)
