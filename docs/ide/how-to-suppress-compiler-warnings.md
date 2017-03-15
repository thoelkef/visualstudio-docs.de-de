---
title: "Gewusst wie: Unterdr&#252;cken von Compiler-Warnungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Gewusst wie: Unterdr&#252;cken von Compiler-Warnungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können declutter ein Buildprotokoll, indem Sie eine oder mehrere Arten Compilerwarnungen angeben, die Sie sie nicht enthalten soll.  Beispielsweise können Sie diese Technik, einige jedoch nicht alle Informationen zu überprüfen, die automatisch wenn Sie das Buildprotokollausführlichkeitsgrad zu normalen, zu zu ausführlichen oder Diagnose generiert wird.  Weitere Informationen zu den Ausführlichkeitsgrad, finden Sie unter [Gewusst wie: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
### Um bestimmte Warnungen für Visual C\# oder F\# unterdrücken  
  
1.  In **Projektmappen\-Explorer** wählen Sie das Projekt, in dem Sie Warnungen unterdrücken möchten.  
  
2.  Klicken Sie auf der Menüleiste wählen Sie **Ansicht**, **Eigenschaftenseiten** aus.  
  
3.  Wählen Sie die Seite **Build** aus.  
  
4.  Im Feld geben Sie die **Warnungen unterdrücken** Fehlercodes der Warnungen, die Sie unterdrücken möchten an, durch Semikolons getrennt, und erstellen Sie dann die Projektmappe neu.  
  
### Um bestimmte Warnungen für Visual C\+\+ unterdrücken  
  
1.  In **Projektmappen\-Explorer** wählen Sie das Projekt oder die Quelldatei aus, in denen Sie Warnungen unterdrücken möchten.  
  
2.  Klicken Sie auf der Menüleiste wählen Sie **Ansicht**, **Eigenschaftenseiten** aus.  
  
3.  Wählen Sie die Kategorie **Konfigurationseigenschaften** aus, wählen Sie die **C\/C\+\+** Kategorie aus, und wählen Sie dann die Seite **Erweitert** aus.  
  
4.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Im Feld geben Sie die **Bestimmte Warnungen deaktivieren** Fehlercodes der Warnungen, die Sie unterdrücken möchten an, getrennt durch ein Semikolon.  
  
    -   Im Feld **Bestimmte Warnungen deaktivieren** wählen Sie **Bearbeiten**, um weitere Optionen anzuzeigen.  
  
5.  Wählen Sie die Schaltfläche **OK** aus, und erstellen Sie dann die Projektmappe neu.  
  
## Unterdrücken von Warnungen für Visual Basic  
 Sie können bestimmte Compilerwarnungen für Visual Basic ausblenden, indem Sie die VBPROJ\-Datei für das Projekt bearbeiten.  Sie können [Seite Kompilieren, Projekt\-Designer](../ide/reference/compile-page-project-designer-visual-basic.md) auch verwenden, um Warnungen nach Kategorie zu unterdrücken.  Weitere Informationen finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
#### Um bestimmte Warnungen für Visual Basic unterdrücken  
  
1.  In **Projektmappen\-Explorer** wählen Sie das Projekt, in dem Sie Warnungen unterdrücken möchten.  
  
2.  Klicken Sie auf der Menüleiste wählen Sie **Projekt**, **Projekt entladen** aus.  
  
3.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Bearbeiten***Projektname***.vbproj** aus.  
  
     Die Projektdatei wird im Code\-Editor geöffnet.  
  
4.  Suchen Sie das `<NoWarn></NoWarn>`\-Element in der Buildkonfiguration, mit der Sie erstellen.  
  
     Im folgenden Beispiel wird das `<NoWarn></NoWarn>`\-Element in fett formatiertem Text für die Debugbuildkonfiguration auf einer x86\-Plattform an:  
  
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
        <NoWarn> </NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  Fügen Sie eine oder mehrere Warnungsnummern als Wert des \- Elements hinzu. `<NoWarn>` Wenn Sie mehrere Warnungsnummern angeben, trennen Sie diese durch ein Komma, wie im folgenden Beispiel gezeigt.  
  
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
  
6.  Speichern Sie die Änderungen an der VBPROJ\-Datei.  
  
7.  Klicken Sie auf der Menüleiste wählen Sie **Projekt**, **Projekt erneut laden** aus.  
  
8.  Klicken Sie auf der Menüleiste wählen Sie **Build**, **Projektmappe neu erstellen** aus.  
  
     Das Fenster zeigt den **Ausgabe** diesen Warnungen Sie nicht mehr angegebenen an.  
  
 Weitere Informationen finden Sie unter [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md)   
 [Gewusst wie: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)