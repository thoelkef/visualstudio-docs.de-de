---
title: 'Vorgehensweise: Unterdrücken von Compilerwarnungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90a5624997a3f2a6719ccd174abee39798f1c488
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782086"
---
# <a name="how-to-suppress-compiler-warnings"></a>Gewusst wie: Unterdrücken von Compiler-Warnungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
1. Wählen Sie im **Projektmappen-Explorer** das Projekt aus, in dem Sie Warnungen unterdrücken möchten.  
  
2. Wählen Sie in der Menüleiste **Projekt**, **Projekt entladen** aus.  
  
3. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie dann **Bearbeiten**_Projektname_**.vbproj** aus.  
  
    Die Projektdatei wird im Code-Editor geöffnet.  
  
4. Suchen Sie das Element `<NoWarn></NoWarn>` in der Buildkonfiguration, die Sie zum Erstellen verwenden.  
  
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
  
5. Fügen Sie als Wert des `<NoWarn>`-Elements eine oder mehrere Warnungsnummern hinzu. Wenn Sie mehrere Warnungsnummern angeben, trennen Sie diese durch Kommas, wie im folgenden Beispiel zu sehen.  
  
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
  
6. Speichern Sie die Änderungen an der VBPROJ-Datei.  
  
7. Wählen Sie in der Menüleiste **Projekt**, **Projekt erneut laden** aus.  
  
8. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe neu erstellen** aus.  
  
    Das Fenster **Ausgabe** zeigt die von Ihnen angegebenen Warnungen jetzt nicht mehr an.  
  
   Weitere Informationen finden Sie unter [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md)   
 [Gewusst wie: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)
