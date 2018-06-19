---
title: Was&#39;s in der Visual Studio 2015 SDK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6488f28f2963e17c716c2e9d395ddf77f270e7b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144706"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Was&#39;s in der Visual Studio 2015 SDK
Das Visual Studio SDK hat die folgenden neuen und aktualisierten Features für Visual Studio 2015 und Visual Studio 2015, aktualisiert Visual Studio 2017.  
  
## <a name="vs-2015-sdk-update-1"></a>Visual Studio 2015 SDK Update 1  
 Update 1 enthält Tools, mit denen die Erweiterung auch bei Farbschemas, statusleisteneinstellungen und der Visual Studio-Image-Dienst ordnungsgemäß funktionieren.  
  
 Diese Themen sind unter der [VSSDK Hilfsprogramme](../extensibility/internals/vssdk-utilities.md) Abschnitt:  
  
-   Die [Farbe Designumgebung Tools](../extensibility/internals/color-theming-tools.md) helfen Ihnen beim Erstellen und bearbeiten benutzerdefinierte Farben für Visual Studio.  
  
-   Die [Image Service Tools](../extensibility/internals/image-service-tools.md) können Sie mit Visual Studio-Image Manifestdateien arbeiten.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Neue Methode zum Hinzufügen von Visual Studio SDK zur Visual Studio  
 Ab Visual Studio 2015, müssen Sie das Visual Studio SDK separat herunterladen. Stattdessen können Sie es im Rahmen der normalen Installation installieren, oder Sie können auswählen, es zu einem späteren Zeitpunkt installieren. Beim Öffnen oder erstellen Sie eine VSIX-Projektmappe, werden Sie von Visual Studio aufgefordert, die Visual Studio-Erweiterbarkeitstools installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Neue Methoden zum Erstellen von Erweiterungen  
 Ab Visual Studio 2015 SDK, haben Sie verschiedene Optionen zum Erstellen von Erweiterungen, je nachdem, welche, die Programmiersprache Sie verwenden.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C#- oder Visual Basic  
 Für c# und Visual Basic ist es eine umfangreiche Palette Projektelementvorlagen, mit die Sie VSPackages, Menübefehle, Toolfenster, Editor Klassifizierer, Editorzusatzelemente und Rand editorerweiterungen erstellen können. Sie können einige oder alle dieser standard VSIX-Projekt hinzufügen. Weitere Informationen finden Sie unter:  
  
-   [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Erstellen einer Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     Der VSPackage-Assistent erstellt die Erweiterungen nicht mehr in c# oder Visual Basic.  
  
### <a name="c"></a>C++  
 Die VSPackage-Assistenten für C++ unterstützt Menübefehle, Toolfenster und benutzerdefinierte Editoren. Suchen sie in der **neues Projekt** Dialogfeld in **Visual C++ / Erweiterbarkeit**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>VS-SDK-Verweisassemblys über NuGet  
 Für erhöhte Portabilität und Freigabe von Erweiterungsprojekte können Sie die NuGet-Versionen die Verweisassemblys VS-SDK.  Diese Seiten sind verfügbar, auf [nuget.org](http://www.nuget.org) von veröffentlichten [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) und leicht zu Ihrem Projekt oder einer Projektmappe mithilfe von Visual Studio hinzugefügt werden **verweist auf / Verwalten von NuGet Pakete** Dialogfeld. Sie können einzelne Verweise auf bestimmte Erweiterbarkeit Assemblys hinzugefügt oder das VS-SDK verweist auf die Assemblys, die gleichzeitig mit dem VS-SDK [Meta-Paket](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Weitere Informationen zu NuGet finden Sie unter der [NuGet-Dokumentation](/NuGet) und [Paket-Manager-UI](/NuGet/Tools/Package-Manager-UI) Themen.  
  
 Wenn Sie die NuGet-Versionen die Verweisassemblys VS-SDK verwenden, muss ein anderer Benutzer das VS-SDK, um zu öffnen und erstellen Sie das Projekt zu installieren.  Die NuGet-Verweisassemblys und VS-SDK-Buildtools werden automatisch auf ihrem Computer für dieses Projekt installiert.  
  
 VS-SDK-Elementvorlagen mithilfe von NuGet für ihre Verweise und Tools zu erstellen, damit Sie die Vorteile von NuGet in der Standardeinstellung erhalten.  
  
> [!NOTE]
>  Sie können weiterhin die Verweisassemblys installiert VS-SDK mit Ihren Projekten zu verwenden (befindet sich im \<Visual Studio-Installationspfad > \ VSSDK\VisualStudioIntegration\Common\Assemblies) und vorhandenen Erweiterungsprojekte erübrigt sich werden die Verwendung von NuGet-Pakete aktualisiert.  Das Projekt **verweist auf / Verweis hinzufügen** Dialogfeld weiterhin die Verweisassemblys VS-SDK installiert.  
>   
>  Wenn Sie möchten, ändern vorhandene Projekte zum Verwenden von NuGet finden Sie unter [Vorgehensweise: Migrieren von VSPackages zu Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) die verfügt über einen Abschnitt zum Aktualisieren von Erweiterungsprojekte für NuGet-Pakete.  
  
## <a name="light-bulbs"></a>Glühbirnen  
 Einer der interessantesten neue Methoden zum Schreiben von Code der Erweiterung wird durch das Roslyn-Projekt bereitgestellt. Weitere Informationen finden Sie unter [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Glühbirnen sind ein neues Feature, das mit VSSDK geliefert wird. Es sind Symbole, die in der Visual Studio-Editor verwendet und erweitert, um eine Reihe von Umgestaltung Codeaktionen oder Fehlerbehebungen für Probleme, die den integrierten Code-Analyzer identifizierte anzuzeigen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Glühbirne Vorschläge](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Aktualisierter Benutzer Erfahrung Richtlinien  
 Entwerfen von Features oder neue Erweiterungen für Visual Studio? Sehen Sie sich die aktualisierten und erweiterten [Visual Studio-Umgebung Leitfäden](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Finden Sie die [Farbe Token](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [Schriftgrade Ihren Bedürfnissen](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [layoutspezifikationen für Dialogfeld](../extensibility/ux-guidelines/layout-for-visual-studio.md), und andere Hinweise zum müssen Sie die neue Benutzeroberfläche nahtlos mit Visual Studio integrieren.