---
title: Neues in Visual Studio 2015 SDK | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c419800a92f25ce4531c351d4131acf119633ccb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957320"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Was&#39;Neues in Visual Studio 2015 SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK hat die folgenden neuen und aktualisierten Funktionen für Visual Studio 2015, Visual Studio 2017 und Visual Studio 2015 aktualisiert.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Ab Visual Studio 2017, Überprüfung von benutzerdefinierten Projekt- und Elementvorlagen nicht mehr erfolgt. Stattdessen muss die Erweiterung vorlagenmanifestdateien bereitstellen, die den Installationsspeicherort der diese Vorlagen zu beschreiben. Sie können Visual Studio 2017 verwenden, um Ihre VSIX-Erweiterungen zu aktualisieren. Wenn Sie die Erweiterung, die mit MSI bereitstellen, müssen Sie die vorlagenmanifestdateien manuell generieren. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Das manifest Vorlagenschema finden Sie unter [Visual Studio-Manifest Schemareferenz zu Vorlagen](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>Visual Studio 2015 SDK-Update 1
 Update 1 umfasst Tools, mit denen die Erweiterung funktioniert gut mit Farbdesigns und der Visual Studio-Image-Dienst.

 Diese Themen sind unter der [VSSDK-Hilfsprogramme](../extensibility/internals/vssdk-utilities.md) Abschnitt:

-   Die [Tools für Farbdesigns](../extensibility/internals/color-theming-tools.md) erstellen und Bearbeiten von Farben für Visual Studio.

-   Die [Bilddienste](../extensibility/internals/image-service-tools.md) können Sie mit Visual Studio-Image-manifest-Dateien arbeiten.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Neue Möglichkeit zum Hinzufügen von Visual Studio SDK für Visual Studio
 Ab Visual Studio 2015, müssen Sie das Visual Studio SDK separat herunterladen. Stattdessen können Sie sie als Teil der normal-Installation installieren, oder Sie können auch später auf installieren. Wenn Sie zu öffnen oder erstellen Sie eine VSIX-Projektmappe, fordert Visual Studio Sie Visual Studio-Erweiterbarkeitstools installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Neue Methoden zum Erstellen von Erweiterungen
 Ab Visual Studio 2015 SDK können, müssen Sie verschiedene Optionen zum Erstellen von Erweiterungen, je nachdem, welche, die Programmiersprache Sie verwenden.

### <a name="visual-c-and-visual-basic"></a>Visual C#- oder Visual Basic
 Für C# und Visual Basic ist es eine Vielzahl von Projektelementvorlagen, mit die Sie VSPackages, Menübefehle, Toolfenster, Editor-Klassifizierer, Editorzusatzelemente und Rand editorerweiterungen erstellen können. Sie können einige oder alle diese zum standard VSIX-Projekt hinzufügen. Weitere Informationen finden Sie unter:

-   [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)

-   [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)

-   [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)

-   [Erstellen einer Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     Der VSPackage-Assistent erstellt die Erweiterungen nicht mehr in C# oder Visual Basic.

### <a name="c"></a>C++
 Für C++ Menübefehle, Toolfenster und benutzerdefinierte Editoren des VSPackage-Assistenten unterstützt. Suchen sie in der **neues Projekt** Dialogfeld **Visual C++ / Erweiterbarkeit**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Visual Studio SDK-Verweisassemblys über NuGet
 Für mehr Portabilität und Freigabe von Erweiterungsprojekten können Sie die NuGet-Versionen, der die VS-SDK-Verweisassemblys.  Diese stehen auf [nuget.org](http://www.nuget.org) herausgegebene [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) und können problemlos zu Ihrem Projekt oder eine Projektmappe mit dem Visual Studio hinzugefügt werden **verweist auf / Verwalten von NuGet Pakete** Dialogfeld. Sie können einzelne Verweise auf bestimmte erweiterbarkeitsassemblys hinzugefügt oder das VS-SDK verweist auf die Assemblys, die gleichzeitig mit dem Visual Studio-SDK [metapaket](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Weitere Informationen zu NuGet finden Sie unter [NuGet-Übersicht](http://docs.nuget.org/) und [Verwalten von NuGet-Paketen mithilfe des Dialogfelds](http://docs.nuget.org/Consume/Package-Manager-Dialog).

 Wenn Sie die NuGet-Versionen, der die VS-SDK-Verweisassemblys verwenden, muss ein anderer Benutzer nicht installieren Sie das VS SDK zum Öffnen und erstellen Sie das Projekt.  Die Verweisassemblys für NuGet und Visual Studio SDK-Buildtools werden automatisch auf ihrem Computer für dieses Projekt installiert.

 Die Elementvorlagen für Visual Studio-SDK verwenden Sie NuGet, für deren Verweise und Buildtools, damit Sie die Vorteile von NuGet standardmäßig erhalten.

> [!NOTE]
>  Sie können weiterhin die Installation von Visual Studio SDK-Verweisassemblys mit Ihren Projekten zu verwenden (befindet sich im \<Visual Studio-Installationspfad > \ VSSDK\VisualStudioIntegration\Common\Assemblies) und vorhandenen Erweiterungsprojekte müssen nicht gleich die Verwendung von NuGet-Pakete aktualisiert.  Das Projekt **verweist auf / Verweis hinzufügen** Dialogfeld weiterhin die Installation von Visual Studio SDK-Verweisassemblys verwenden.
>
>  Wenn Sie möchten, ändern Sie Ihre vorhandenen Projekte zur Verwendung von NuGet finden [Vorgehensweise: Migrieren von VSPackages zu Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) die weist den Abschnitt zum Aktualisieren von Erweiterungsprojekten auf NuGet-Pakete.

## <a name="light-bulbs"></a>Glühbirnen
 Eine der interessantesten neuen Möglichkeiten des Schreibens von Code für wird durch das Roslyn-Projekt bereitgestellt. Weitere Informationen finden Sie unter [Roslyn](https://github.com/dotnet/Roslyn).

 Glühbirnen sind ein neues Feature, das mit das VS SDK geliefert wird. Sie sind in Visual Studio-Editor verwendeten Symbole, die erweitert werden, um einen Satz von Umgestaltung Codeaktionen oder Fehlerbehebungen für Probleme, die den integrierten Code-Analyzer identifizierte anzuzeigen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Aktualisierte Richtlinien zur Benutzerfreundlichkeit
 Entwerfen von Features oder neue Erweiterungen für Visual Studio ein? Sehen Sie sich die aktualisierten und erweiterten [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Finden Sie die [Farbe Token](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [Schriftgrade Ihren Bedürfnissen entsprechend](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [layoutspezifikationen für Dialogfeld](../extensibility/ux-guidelines/layout-for-visual-studio.md), und bewährten Leitfäden stammen, Sie Ihre neue Benutzeroberfläche in Visual Studio nahtlos zu integrieren müssen.
