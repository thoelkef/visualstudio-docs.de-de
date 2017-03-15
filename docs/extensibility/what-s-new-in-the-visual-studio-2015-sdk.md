---
title: Neuigkeiten in Visual Studio 2015 SDK | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 13
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
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 8d77fce54b12b90f6a2632fd1c1741990be42a08
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Was ist neu in Visual Studio 2015 SDK
Das Visual Studio SDK hat die folgenden neuen und aktualisierten Features für Visual Studio 2015 und Visual Studio 2015, aktualisiert Visual Studio 2017.  
  
## <a name="vs-2015-sdk-update-1"></a>Visual Studio 2015 SDK-Update 1  
 Update 1 enthält Tools, mit denen die Erweiterung funktioniert gut mit Farbschemas und der Visual Studio-Image-Dienst.  
  
 Diese Themen sind unter dem [VSSDK Dienstprogramme](../extensibility/internals/vssdk-utilities.md) Abschnitt:  
  
-   Die [Farbe Designs Tools](../extensibility/internals/color-theming-tools.md) erstellen und Bearbeiten von Farben für Visual Studio.  
  
-   Die [Tools für Image](../extensibility/internals/image-service-tools.md) können Sie mit Visual Studio Bild manifest-Dateien arbeiten.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Neue Möglichkeit für das Visual Studio SDK Visual Studio hinzufügen  
 In Visual Studio 2015 beginnen, müssen Sie das Visual Studio SDK separat heruntergeladen werden. Stattdessen können Sie es als Teil der normalen Installation installieren, oder Sie können auch später auf installieren. Beim Öffnen oder erstellen Sie eine VSIX-Projektmappe, werden Sie von Visual Studio aufgefordert, die Visual Studio Extensibility Tools zu installieren. Weitere Informationen finden Sie unter [Installation von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Neue Methoden zum Erstellen von Erweiterungen  
 Starten in Visual Studio 2015 SDK, stehen Ihnen verschiedene Optionen zum Erstellen von Erweiterungen, je nachdem, welche, die Programmiersprache Sie verwenden.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C#- oder Visual Basic  
 Für c# und Visual Basic ist es eine Vielzahl von Projektelementvorlagen, die VSPackages, Menübefehle, Toolfenster, Editor Klassifizierer, Editorzusatzelemente und Erweiterungen des Rand-Editors erstellen können. Sie können einige oder alle dieser standard VSIX-Projekt hinzufügen. Weitere Informationen finden Sie unter:  
  
-   [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Erstellen eine Erweiterung mit einer Elementvorlage-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Erstellen eine Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     Der VSPackage-Assistent erstellt die Erweiterungen nicht mehr in c# oder Visual Basic.  
  
### <a name="c"></a>C++  
 Für C++ Menübefehle, Toolfenstern und benutzerdefinierte Editoren VSPackage-Assistenten unterstützt. Suchen sie in der **neues Projekt** Dialogfeld in **Visual C++ / Erweiterbarkeit**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Visual Studio SDK-Verweisassemblys über NuGet  
 Für mehr Portabilität und gemeinsame Nutzung von Erweiterungsprojekte können Sie die NuGet-Versionen von Visual Studio SDK-Verweisassemblys.  Diese stehen auf ["NuGet.org"](http://www.nuget.org) erschienen [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) und können problemlos hinzugefügt werden Projekts oder der Projektmappe mithilfe von Visual Studio **verweist / verwalten NuGet-Pakete** Dialogfeld. Sie können einzelne Verweise auf Erweiterbarkeit Assemblys hinzugefügt oder das Visual Studio-SDK verweist auf die Assemblys, die gleichzeitig mit dem Visual Studio SDK [Meta-Paket](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Weitere Informationen zu NuGet finden Sie unter [NuGet-Übersicht](http://docs.nuget.org/) und [Verwalten von NuGet-Paketen mithilfe des Dialogs](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
 Wenn Sie die NuGet-Versionen von Visual Studio SDK-Verweisassemblys verwenden, muss ein anderer Benutzer installieren das SDK Visual Studio öffnen und das Projekt zu erstellen.  Die NuGet-Verweisassemblys und Visual Studio SDK-Buildtools werden auf ihrem Computer für das Projekt automatisch installiert.  
  
 Visual Studio SDK Elementvorlagen Verwenden von NuGet für ihre Verweise und Buildtools und die Vorteile von NuGet standardmäßig.  
  
> [!NOTE]
>  Sie können weiterhin die installierte Visual Studio SDK-Verweisassemblys mit Ihren Projekten verwenden (befindet sich unter \<Visual Studio-Installationspfad > \ VSSDK\VisualStudioIntegration\Common\Assemblies) und vorhandenen Erweiterungsprojekte müssen nicht aktualisiert werden, um das NuGet-Pakete verwenden.  Das Projekt **verweist / Verweis hinzufügen** Dialogfeld weiterhin die Verweisassemblys für die VS-SDK installiert.  
>   
>  Wenn Sie möchten, ändern vorhandene Projekte NuGet verwenden, finden Sie unter [Gewusst wie: Migrieren von VSPackages zu Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) der verfügt über einen Abschnitt zum Aktualisieren von Erweiterungsprojekte auf NuGet-Pakete.  
  
## <a name="light-bulbs"></a>Glühbirnen  
 Eine der interessantesten neuen Arten Erweiterungscode schreiben wird durch das Roslyn-Projekt bereitgestellt. Weitere Informationen finden Sie unter [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Glühbirnen sind ein neues Feature, das mit VSSDK geliefert wird. Es sind Symbole, die in der Visual Studio-Editor verwendet und erweitert, um einen Satz von Umgestaltung Codeaktionen oder Korrekturen für Probleme, die von den integrierten Code-Analyzer angezeigt. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Glühbirne Vorschläge](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Aktualisierte User Experience Guidelines  
 Entwerfen von Features oder neue Erweiterungen für Visual Studio? Sehen Sie sich die aktualisierten und erweiterte [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Finden Sie die [Farbe Token](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [Schriftgrade](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [Dialogfeld layoutspezifikationen](../extensibility/ux-guidelines/layout-for-visual-studio.md), sowie andere Prozessleitfäden Sie die neue Benutzeroberfläche nahtlos mit Visual Studio integrieren müssen.
