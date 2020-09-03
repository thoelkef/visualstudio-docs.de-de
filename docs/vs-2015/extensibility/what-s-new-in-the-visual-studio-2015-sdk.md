---
title: Neues im Visual Studio 2015 SDK | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d47e40a5c38eeb7898aa179282fa55bbe17ef1d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917334"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Neuerungen in Visual Studio 2015 SDK&#39;s
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Visual Studio SDK verfügt über die folgenden neuen und aktualisierten Features für Visual Studio 2015, Visual Studio 2015 und Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Ab Visual Studio 2017 werden keine Scans nach benutzerdefinierten Projekt- und Elementvorlagen mehr durchgeführt. Die Erweiterung muss nun Vorlagenmanifestdateien mit dem Installationspfad dieser Vorlagen enthalten. Sie können Ihre VSIX-Erweiterungen mithilfe von Visual Studio 2017 aktualisieren. Wenn Sie eine Erweiterung über eine MSI-Datei bereitstellen, müssen Sie die Vorlagenmanifestdateien manuell generieren. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt-und Elementvorlagen für Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Das Vorlagen Manifest-Schema ist in der [Schema Referenz für den Visual Studio-Vorlagen Manifest](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)dokumentiert.

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK-Update 1
 Update 1 umfasst Tools, die die Funktionsweise ihrer Erweiterung mit Farb Designs und dem Visual Studio-Image Dienst unterstützen.

 Diese Themen finden Sie im Abschnitt [VSSDK-Hilfsprogramme](../extensibility/internals/vssdk-utilities.md) :

- Die [Tools](../extensibility/internals/color-theming-tools.md) für die Farbbearbeitung helfen Ihnen beim Erstellen und Bearbeiten benutzerdefinierter Farben für Visual Studio.

- Mit den [Image Service-Tools](../extensibility/internals/image-service-tools.md) können Sie mit Visual Studio-Image Manifest-Dateien arbeiten.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Neue Möglichkeit zum Hinzufügen des Visual Studio SDK zu Visual Studio
 Ab Visual Studio 2015 müssen Sie das Visual Studio SDK nicht separat herunterladen. Stattdessen können Sie Sie im Rahmen des normalen Installationsvorgangs installieren, oder Sie können Sie später installieren. Wenn Sie eine VSIX-Projekt Mappe öffnen oder erstellen, werden Sie von Visual Studio aufgefordert, den Visual Studio-Erweiterungstools zu installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Neue Methoden zum Erstellen von Erweiterungen
 Beginnend mit dem Visual Studio 2015 SDK haben Sie verschiedene Optionen zum Erstellen von Erweiterungen, je nachdem, welche Programmiersprache Sie verwenden.

### <a name="visual-c-and-visual-basic"></a>Visual C#- oder Visual Basic
 Für c# und Visual Basic gibt es eine vollständige Palette von Projekt Element Vorlagen, mit denen Sie VSPackages, Menübefehle, Tool Fenster, editorklassifizierer, Editor-Zusatzelemente und Editor-Rand Erweiterungen erstellen können. Sie können dem VSIX-Standard Projekt beliebige oder alle diese hinzufügen. Weitere Informationen finden Sie unter:

- [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Erstellen einer Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     Der VSPackage-Assistent erstellt keine Erweiterungen mehr in c# oder Visual Basic.

### <a name="c"></a>C++
 Für C++ unterstützt der VSPackage-Assistent Menübefehle, Tool Fenster und benutzerdefinierte Editoren. Suchen Sie im Dialogfeld " **Neues Projekt** " in **Visual C++/Erweiterbarkeit**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>VS SDK-Verweisassemblys über nuget
 Um die Portabilität und die Freigabe von Erweiterbarkeits Projekten zu erhöhen, können Sie die nuget-Versionen der vs SDK-Verweisassemblys verwenden.  Diese sind auf [nuget.org](https://www.nuget.org/) verfügbar, die von [visualstudioextensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) veröffentlicht werden, und können Ihrem Projekt oder ihrer Projekt Mappe problemlos über das Dialogfeld Visual Studio **-Verweise/-Verwalten von nuget-Paketen** hinzugefügt werden. Sie können einzelne Verweise auf bestimmte Erweiterbarkeits Assemblys hinzufügen oder alle vs SDK-Verweisassemblys gleichzeitig mithilfe des vs SDK- [Meta-Pakets](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)hinzufügen. Weitere Informationen zu nuget finden Sie unter [nuget-Übersicht](/nuget/) und [Verwalten von nuget-Paketen mithilfe des Dialog](/nuget/consume-packages/install-use-packages-visual-studio)Felds.

 Wenn Sie die nuget-Versionen der vs SDK-Verweisassemblys verwenden, muss ein anderer Benutzer das vs SDK nicht installieren, um das Projekt zu öffnen und zu erstellen.  Die nuget-Verweisassemblys und vs SDK-Buildtools werden automatisch für dieses Projekt auf dem Computer installiert.

 Die vs SDK-Element Vorlagen verwenden nuget für Ihre Verweise und Buildtools, sodass Sie die Vorteile von nuget standardmäßig erhalten.

> [!NOTE]
> Sie können weiterhin die von vs SDK installierten Verweisassemblys mit ihren Projekten verwenden (befindet sich unter \<Visual Studio Install Location> \ vssdk\visualstudiointegration\common\assemblys), und vorhandene Erweiterbarkeits Projekte müssen nicht aktualisiert werden, um nuget-Pakete zu verwenden.  Im Dialogfeld Projekt **Verweise/Verweis hinzufügen** werden weiterhin die von vs SDK installierten Verweisassemblys verwendet.
>
> Wenn Sie Ihre vorhandenen Projekte für die Verwendung von nuget ändern möchten, finden Sie weitere Informationen unter Gewusst [wie: Migrieren von VSPackages zu Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) , das einen Abschnitt zum Aktualisieren von Erweiterungs Projekten auf nuget-Pakete enthält.

## <a name="light-bulbs"></a>Glühbirnen
 Eine der aufregendsten neuen Methoden zum Schreiben von Erweiterungs Code wird vom Roslyn-Projekt bereitgestellt. Weitere Informationen finden Sie unter [Roslyn](https://github.com/dotnet/Roslyn).

 Glühbirnen sind ein neues Feature, das mit dem VSSDK ausgeliefert wird. Dabei handelt es sich um Symbole, die im Visual Studio-Editor verwendet werden, um eine Reihe von coderefactoring-Aktionen oder Fehlerbehebungen für Probleme anzuzeigen, die von den integrierten Code Analysen identifiziert werden. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Anzeigen von Glühbirnen Vorschlägen](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Aktualisierte Richtlinien für die Benutzer Darstellung
 Entwerfen neuer Erweiterungen oder Features für Visual Studio Sehen Sie sich die aktualisierten und erweiterten [Visual Studio-Richtlinien](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)für die Benutzer Leistung an.  Sie finden die [farbtokens](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [Schriftgrößen](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [layoutlayoutspezifikationen](../extensibility/ux-guidelines/layout-for-visual-studio.md)und andere Anleitungen, die Sie benötigen, um Ihre neue Benutzeroberfläche nahtlos in Visual Studio zu integrieren.
