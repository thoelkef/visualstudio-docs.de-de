---
title: 'Exemplarische Vorgehensweise: Erstellen einer Anwendung | Microsoft-Dokumentation'
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 485c8445f24dbd0aaec501649885df50d173347a
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="walkthrough-building-an-application"></a>Exemplarische Vorgehensweise: Erstellen einer Anwendung

Wenn Sie diese exemplarische Vorgehensweise durchführen, werden Sie mit einigen der bei der Erstellung von Anwendungen mit Visual Studio konfigurierbaren Optionen vertrauter. Sie führen die folgenden Aufgaben für eine Beispielanwendung aus: Erstellen einer benutzerdefinierten Buildkonfiguration, Ausblenden bestimmter Warnmeldungen und Verbessern der Buildausgabeinformationen.

## <a name="install-the-sample-application"></a>Installieren der Beispielanwendung

Laden Sie das Beispiel [Introduction to Building WPF Applications (Einführung in das Erstellen von WPF-Anwendungen)](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) herunter. Entscheiden Sie sich zwischen C# und Visual Basic. Wenn der Download der ZIP-Datei abgeschlossen ist, extrahieren Sie diese, und öffnen Sie die Datei **ExpenseItIntro.sln** mit Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Erstellen einer benutzerdefinierten Buildkonfiguration

Wenn Sie eine Projektmappe erstellen, werden Debug- und Releasebuildkonfigurationen und ihre Standardplattformziele für die Projektmappe automatisch definiert. Sie können diese Konfigurationen dann anpassen oder eigene Konfigurationen erstellen. Buildkonfigurationen geben den Buildtyp an. Buildplattformen geben das Betriebssystem an, auf das eine Anwendung für diese Konfiguration ausgerichtet ist. Weitere Informationen finden Sie unter [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md), [Grundlagen zu Buildplattformen](../ide/understanding-build-platforms.md) und [Gewusst wie: Festlegen von Debug- und Releasekonfigurationen in Visual Studio](../debugger/how-to-set-debug-and-release-configurations.md).

Sie können Konfigurationen und Plattformeinstellungen mithilfe des Dialogfelds **Konfigurations-Manager** ändern oder erstellen. In dieser Prozedur erstellen Sie eine Buildkonfiguration zum Testen.

### <a name="to-create-a-build-configuration"></a>So erstellen Sie eine Buildkonfiguration

1. Öffnen Sie das Dialogfeld **Konfigurations-Manager**.

   ![Menü „Build“, Konfigurations-Manager-Befehl](../ide/media/buildwalk_configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  

1. Wählen Sie in der Liste **Konfiguration der aktuellen Projektmappe** den Eintrag **\<Neu…\>** aus.

1. Geben Sie im Dialogfeld **Neue Projektmappenkonfiguration** den Namen `Test` für die neue Konfiguration ein, kopieren Sie die Einstellungen aus der vorhandenen Debugkonfiguration, und wählen Sie dann die Schaltfläche **OK** aus.

   ![Dialogfeld „Neue Projektmappenkonfiguration“](../ide/media/buildwalk_newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  

1. Wählen Sie in der Liste **Aktive Projektmappenplattform** den Eintrag **\<Neu…\>** aus.

1. Wählen Sie im Dialogfeld **Neue Projektmappenplattform** die Option **x64** aus, und kopieren Sie keine der Einstellungen der x86-Plattform.

   ![Dialogfeld „Neue Projektmappenplattform“](../ide/media/buildwalk_newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  

1. Klicken Sie auf die Schaltfläche **OK** .

   Die aktive Projektmappenkonfiguration wurde für einen Test mit der aktiven, auf x64- festgelegten Projektmappenplattform geändert.

   ![Konfigurations-Manager mit Testkonfiguration](../ide/media/buildwalk_configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  

1. Klicken Sie auf **Schließen**.

Sie können die aktive Projektmappenkonfiguration schnell überprüfen oder ändern, indem Sie die Liste **Projektmappenkonfigurationen** auf der Symbolleiste **Standard** verwenden.
  
![Standardsymbolleiste der Projektmappenkonfiguration](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
## <a name="build-the-application"></a>Erstellen der Anwendung

Danach erstellen Sie die Projektmappe mit der benutzerdefinierten Buildkonfiguration.
  
### <a name="to-build-the-solution"></a>So erstellen Sie die Projektmappe
  
-   Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.
  
    Im Fenster **Ausgabe** wird das Ergebnis des Builds angezeigt. Der Buildvorgang war erfolgreich.
  
## <a name="hide-compiler-warnings"></a>Ausblenden von Compilerwarnungen

Als Nächstes wird Code eingeführt, der eine Warnung auslöst und vom Compiler generiert werden soll.

1. Öffnen Sie die Datei **ExpenseReportPage.xaml.cs** im C#-Projekt. Fügen Sie folgenden Code in die **ExpenseReportPage**-Methode ein: `int i;`.

    ODER

    Öffnen Sie im Visual Basic-Projekt die Datei **ExpenseReportPage.xaml.vb**. Fügen Sie im benutzerdefinierten Konstruktor **Public Sub New** den folgenden Code hinzu: `Dim i`.

1. Erstellen Sie die Projektmappe.

Im Fenster **Ausgabe** wird das Ergebnis des Builds angezeigt. Der Build wurde erfolgreich abgeschlossen, aber es wurden Warnungen ausgelöst:

![Ausgabefenster Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")

![Ausgabefenster Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")

Sie können bestimmte Warnungen während eines Builds vorübergehend ausblenden, anstatt sie die Buildausgabe durcheinanderbringen zu lassen.

### <a name="to-hide-a-specific-c-warning"></a>So blenden Sie eine bestimmte C#-Warnung aus

1. Wählen Sie im **Projektmappen-Explorer** den Projektknoten der obersten Ebene aus.

1. Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaftenseiten**.
  
     Der **Projekt-Designer** wird geöffnet.

1. Klicken Sie auf die Seite **Erstellen**, und geben Sie im Feld **Warnungen unterdrücken** die Warnungsnummer **0168** an.
  
     ![Seite „Erstellen“, Projekt-Designer](../ide/media/buildwalk_csharpsupresswarnings.png "BuildWalk_CsharpSupressWarnings")  
  
     Weitere Informationen finden Sie unter [Seite „Erstellen“, Projekt-Designer (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Erstellen Sie die Projektmappe.
  
     Im Fenster **Ausgabe** werden nur Zusammenfassungsinformationen für den Build angezeigt.
  
     ![Ausgabefenster, Visual C&#35;-Buildwarnungen](../ide/media/buildwalk_visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
### <a name="to-suppress-all-visual-basic-build-warnings"></a>So unterdrücken Sie alle Visual Basic-Buildwarnungen

1. Wählen Sie im **Projektmappen-Explorer** den Projektknoten der obersten Ebene aus.

1. Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaftenseiten**.
  
     Der **Projekt-Designer** wird geöffnet.

1. Aktivieren Sie auf der Seite **Kompilieren** das Kontrollkästchen **Alle Warnungen deaktivieren**.
  
     ![Seite „Kompilieren“, Projekt-Designer](../ide/media/buildwalk_vbsupresswarnings.png "BuildWalk_VBSupressWarnings")  
  
     Weitere Informationen finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

1. Erstellen Sie die Projektmappe.
  
 Im Fenster **Ausgabe** werden nur Zusammenfassungsinformationen für den Build angezeigt.
  
 ![Ausgabefenster, Visual Basic-Buildwarnungen](../ide/media/buildwalk_visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Unterdrücken von Compiler-Warnungen](../ide/how-to-suppress-compiler-warnings.md).
  
## <a name="display-additional-build-details-in-the-output-window"></a>Anzeigen zusätzlicher Builddetails im Ausgabefenster

Sie können die Menge der im Fenster **Ausgabe** angezeigten Informationen über den Buildprozess ändern. Buildausführlichkeit wird normalerweise auf „Minimal“ festgelegt. Das bedeutet, dass im Fenster **Ausgabe** nur eine Zusammenfassung des Buildprozesses zusammen mit allen Warnungen oder Fehlern mit hoher Priorität angezeigt wird. Sie können mithilfe von [Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) weitere Informationen zum Build anzeigen lassen.
  
> [!IMPORTANT]
>  Wenn Sie weitere Informationen anzeigen, dauert der Abschluss des Builds länger.
  
### <a name="to-change-the-amount-of-information-in-the-output-window"></a>So ändern Sie die Informationsmenge im Ausgabefenster

1. Öffnen Sie das Dialogfeld **Optionen**.
  
     ![Befehl „Optionen“ im Menü „Tools“](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")  

1. Wählen Sie die Kategorie **Projekte und Projektmappen**, und wählen Sie dann die Seite **Erstellen und Ausführen** aus.

1. Wählen Sie in der Liste **Ausführlichkeit der MSBuild-Projektbuildausgabe** die Option **Normal** und dann die Schaltfläche **OK** aus.

1. Wählen Sie in der Menüleiste **Build**, **Projektmappe bereinigen** aus.

1. Erstellen Sie die Projektmappe, und überprüfen Sie dann die Informationen im Fenster **Ausgabe**.
  
     Die Buildinformationen umfassen die Uhrzeit, zu der der Build gestartet wurde (am Anfang), und die Reihenfolge, in der die Dateien verarbeitet wurden. Diese Informationen umfassen auch die von Visual Studio beim Build ausgeführt Compeliersyntax.
  
     Im C#-Build führt die Option [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) z.B. den von Ihnen zuvor in diesem Thema angegebenen Warnungscode 1762 zusammen mit drei weiteren Warnungen auf.
  
     Im Visual Basic-Build umfasst [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) keine bestimmten auszuschließenden Warnungen, sodass keine Warnungen angezeigt werden.
  
    > [!TIP]
    > Sie können den Inhalt des Fensters **Ausgabe** durchsuchen, wenn Sie das Dialogfeld **Suchen** mithilfe der Tastenkombination STRG+F anzeigen.

Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md).
  
## <a name="create-a-release-build"></a>Erstellen eines Releasebuilds

Sie können eine Version der Beispielanwendung erstellen, die für das Versenden optimiert wird. Beim Releasebuild geben Sie an, dass die ausführbare Datei auf eine Netzwerkfreigabe kopiert wird, bevor der Build gestartet wird.

Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Buildausgabeverzeichnisses](../ide/how-to-change-the-build-output-directory.md) und [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="to-specify-a-release-build-for-visual-basic"></a>So geben Sie einen Releasebuild für Visual Basic an

1. Öffnen Sie den **Projekt-Designer**.
  
     ![Menü „Ansicht“, Befehl „Eigenschaftenseiten“](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  

1. Wählen Sie die Seite **Kompilieren** aus.

1. Wählen Sie in der Liste **Konfiguration** die Option **Release** aus.

1. Wählen Sie in der Liste **Plattform** die Option **x86** aus.

1. Geben Sie im Feld **Buildausgabepfad** einem Netzwerkpfad an.

     Sie können z.B. \\\myserver\builds angeben.

    > [!IMPORTANT]
    > Möglicherweise wird ein Meldungsfeld angezeigt, in dem davor gewarnt wird, dass die von Ihnen angegebene Netzwerkfreigabe eventuell kein vertrauenswürdiger Speicherort ist. Wenn Sie dem angegebenen Speicherort vertrauen, wählen Sie im Meldungsfeld die Schaltfläche **OK** aus.

1. Erstellen Sie die Anwendung.

     ![Befehl „Projektmappe erstellen“ im Menü „Erstellen“](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  

### <a name="to-specify-a-release-build-for-c"></a>So geben Sie einen Releasebuild für C# an #

1. Öffnen Sie den **Projekt-Designer**.
  
     ![Menü „Ansicht“, Befehl „Eigenschaftenseiten“](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  

1. Wählen Sie die Seite **Erstellen** aus.

1. Wählen Sie in der Liste **Konfiguration** die Option **Release** aus.

1. Wählen Sie in der Liste **Plattform** die Option **x86** aus.

1. Geben Sie im Feld **Ausgabepfad** einen Netzwerkpfad an.
  
     Sie könnten z.B. \\\myserver\builds angeben.
  
    > [!IMPORTANT]
    > Möglicherweise wird ein Meldungsfeld angezeigt, in dem davor gewarnt wird, dass die von Ihnen angegebene Netzwerkfreigabe eventuell kein vertrauenswürdiger Speicherort ist. Wenn Sie dem angegebenen Speicherort vertrauen, wählen Sie im Meldungsfeld die Schaltfläche **OK** aus.

1. Legen Sie auf der **Symbolleiste „Standard“** die Projektmappenkonfiguration auf **Release** und die Projektmappenplattformen auf **x86** fest.

1. Erstellen Sie die Anwendung.

     ![Befehl „Projektmappe erstellen“ im Menü „Erstellen“](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  

   Die ausführbare Datei wird auf den von Ihnen angegebenen Netzwerkpfad kopiert. Der Pfad ist \\\myserver\builds\\*Dateiname*.exe.

Herzlichen Glückwunsch: Sie haben diese exemplarische Vorgehensweise erfolgreich abgeschlossen.
  
## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Erstellen eines Projekts (C++)](/cpp/ide/walkthrough-building-a-project-cpp)  
[Übersicht über die Vorkompilierung von ASP.NET-Webanwendungsprojekten](http://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)  
[Exemplarische Vorgehensweise: Verwenden von MSBuild](../msbuild/walkthrough-using-msbuild.md)
