---
title: 'Gewusst wie: Unterdrücken von Compilerwarnungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8555c07dc62237ba202487340ad77b5e04a77e4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590836"
---
# <a name="how-to-suppress-compiler-warnings"></a>Gewusst wie: Unterdrücken von Compiler-Warnungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [wie: Unterdrücken von Compilerwarnungen](https://docs.microsoft.com/visualstudio/ide/how-to-suppress-compiler-warnings).  
  
Sie können ein Buildprotokoll von Clutter befreien, indem Sie angeben, dass eine oder mehrere Arten von Compilerwarnungen nicht enthalten sein sollen. Beispielsweise können Sie diese Technik verwenden, um einige, aber nicht alle Informationen zu überprüfen, die automatisch erzeugt werden, wenn Sie die Ausführlichkeit des Buildprotokolls auf „Normal“, „Detailliert“ oder „Diagnose“ festlegen. Weitere Informationen zur Ausführlichkeit finden Sie unter [Gewusst wie: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>So unterdrücken Sie bestimmte Warnungen für Visual C# oder F#  
  
1.  Wählen Sie im **Projektmappen-Explorer** das Projekt aus, in dem Sie Warnungen unterdrücken möchten.  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaftenseiten**.  
  
3.  Wählen Sie die Seite **Erstellen** aus.  
  
4.  Geben Sie im Feld **Warnungen unterdrücken** durch Semikola getrennt die Fehlercodes der Warnungen an, die unterdrückt werden sollen, und erstellen Sie die Projektmappe dann erneut.  
  
### <a name="to-suppress-specific-warnings-for-visual-c"></a>So unterdrücken Sie bestimmte Warnungen für Visual C++  
  
1.  Wählen Sie im **Projektmappen-Explorer** das Projekt oder die Quelldatei aus, für das bzw. die Sie Warnungen unterdrücken möchten.  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaftenseiten**.  
  
3.  Wählen Sie die Kategorie **Konfigurationseigenschaften** aus, wählen Sie die Kategorie **C/C++** und dann die Seite **Erweitert** aus.  
  
4.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Geben Sie im Feld **Bestimmte Warnungen deaktivieren** die Fehlercodes der Warnungen an, die Sie unterdrücken möchten, durch Semikola getrennt.  
  
    -   Wählen Sie im Feld **Bestimmte Warnungen deaktivieren** den Befehl **Bearbeiten** aus, um weitere Optionen anzuzeigen.  
  
5.  Wählen Sie die Schaltfläche **OK** aus, und erstellen Sie die Projektmappe dann erneut.  
  
## <a name="suppressing-warnings-for-visual-basic"></a>Unterdrücken von Warnungen für Visual Basic  
 Sie können bestimmte Compilerwarnungen für Visual Basic unterdrücken, indem Sie die VBPROJ-Datei für das Projekt bearbeiten. Sie können ferner die [Seite „Kompilieren“, Projekt-Designer](../ide/reference/compile-page-project-designer-visual-basic.md) verwenden, um Warnungen nach Kategorie zu unterdrücken. Weitere Informationen finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>So unterdrücken Sie bestimmte Warnungen für Visual Basic  
  
1.  Wählen Sie im **Projektmappen-Explorer** das Projekt aus, in dem Sie Warnungen unterdrücken möchten.  
  
2.  Wählen Sie in der Menüleiste **Projekt**, **Projekt entladen** aus.  
  
3.  Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie dann **Bearbeiten**_Projektname_**.vbproj** aus.  
  
     Die Projektdatei wird im Code-Editor geöffnet.  
  
4.  Suchen Sie das Element `<NoWarn></NoWarn>` in der Buildkonfiguration, die Sie zum Erstellen verwenden.  
  
     Das folgende Beispiel zeigt das Element `<NoWarn></NoWarn>` in fetter Textschriftart für die Debug-Buildkonfiguration auf einer x86-Plattform:  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn></NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  Fügen Sie als Wert des `<NoWarn>`-Elements eine oder mehrere Warnungsnummern hinzu. Wenn Sie mehrere Warnungsnummern angeben, trennen Sie diese durch Kommas, wie im folgenden Beispiel zu sehen.  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn>40059,42024</NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
6.  Speichern Sie die Änderungen an der VBPROJ-Datei.  
  
7.  Wählen Sie in der Menüleiste **Projekt**, **Projekt erneut laden** aus.  
  
8.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe neu erstellen** aus.  
  
     Das Fenster **Ausgabe** zeigt die von Ihnen angegebenen Warnungen jetzt nicht mehr an.  
  
 Weitere Informationen finden Sie unter [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md)   
 [Gewusst wie: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)



