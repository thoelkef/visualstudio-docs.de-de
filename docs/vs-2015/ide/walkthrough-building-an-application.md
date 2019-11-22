---
title: 'Exemplarische Vorgehensweise: Erstellen einer Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2d9b958dacfb35877abc9ad1e83a349e43a7af0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296877"
---
# <a name="walkthrough-building-an-application"></a>Exemplarische Vorgehensweise: Erstellen einer Anwendung

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Indem Sie diese exemplarische Vorgehensweise abschließen, werden Sie mit einigen der bei der Erstellung von Anwendungen mit Visual Studio konfigurierbaren Optionen vertrauter. Sie führen unter anderem die folgenden Aufgaben für eine Beispielanwendung aus: Erstellen einer benutzerdefinierten Buildkonfiguration, Ausblenden bestimmter Warnmeldungen und Verbessern der Buildausgabeinformationen.

Dieses Thema enthält folgende Abschnitte:

[Installieren der Beispielanwendung](../ide/walkthrough-building-an-application.md)

[Erstellen einer benutzerdefinierten Buildkonfiguration](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)

[Erstellen der Anwendung](../ide/walkthrough-building-an-application.md#BKMK_building)

[Ausblenden von Compilerwarnungen](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)

[Anzeigen zusätzlicher Builddetails im Ausgabefenster](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)

[Erstellen eines Releasebuilds](../ide/walkthrough-building-an-application.md)

#### <a name="to-install-the-sample-application"></a>So Installieren Sie die Beispielanwendung

1. Wählen Sie auf der Menüleiste **Tools**, **Erweiterungen und Updates** aus.

2. Wählen Sie die Kategorie **Online** und dann die Kategorie **Beispielgalerie** aus.

3. Geben Sie zum Suchen des Beispiels `Introduction` in das Suchfeld ein.

    ![Extensions and Updates dialog box](../ide/media/buildwalk-extensionsdialogsampledownload.png "BuildWalk_ExtensionsDialogSampleDownload")

4. Wählen Sie in der Ergebnisliste entweder **Einführung in das Erstellen von WPF-Anwendungen (Visual C#)** oder **Einführung in das Erstellen von WPF-Anwendungen (Visual Basic)** aus.

5. Klicken Sie auf die Schaltfläche **Herunterladen**, und wählen Sie dann die Schaltfläche **Schließen** aus.

   Das Beispiel für die Einführung zum Erstellen von WPF-Anwendungen wird im Dialogfeld **Neues Projekt** angezeigt.

#### <a name="to-create-a-solution-for-the-sample-application"></a>So erstellen Sie eine Projektmappe für die Beispielanwendung

1. Öffnen Sie das Dialogfeld **Neues Projekt**.

     ![Wählen Sie in der Menüleiste „Datei > Neu > Projekt“ aus.](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. Wählen Sie in der Kategorie **Installiert** die Kategorie **Beispiele** aus, um das Beispiel für die Einführung zum Erstellen von WPF-Anwendungen anzuzeigen.

3. Geben Sie der Projektmappe bei Visual C# den Namen `IntroWPFcsharp`.

     ![New Project dialog box, Installed Samples](../ide/media/buildwalk-newprojectdlgintrotowpfsample.png "BuildWalk_NewProjectdlgIntrotoWPFsample")

     ODER

     Geben Sie der Projektmappe bei Visual Basic den Namen `IntroWPFvb`.

     ![New Project dialog box, Visual Basic Sample](../ide/media/buildwalk-newprojectdlgintrotowpfsamplevb.png "BuildWalk_NewProjectdlgIntrotoWPFsampleVB")

4. Klicken Sie auf die Schaltfläche **OK** .

## <a name="BKMK_CreateBuildConfig"></a> Erstellen einer benutzerdefinierten Buildkonfiguration

Wenn Sie eine Projektmappe erstellen, werden Debug- und Releasebuildkonfigurationen und ihre Standardplattformziele für die Projektmappe automatisch definiert. Sie können diese Konfigurationen dann anpassen oder eigene Konfigurationen erstellen. Buildkonfigurationen geben den Buildtyp an. Buildplattformen geben das Betriebssystem an, auf das eine Anwendung für diese Konfiguration ausgerichtet ist. Weitere Informationen finden Sie unter [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md), [Grundlagen zu Buildplattformen](../ide/understanding-build-platforms.md) und [Debug and Release Project Configurations (Debug- und Releaseprojektkonfigurationen)](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

Sie können Konfigurationen und Plattformeinstellungen mithilfe des Dialogfelds **Konfigurations-Manager** ändern oder erstellen. In dieser Prozedur erstellen Sie eine Buildkonfiguration zum Testen.

#### <a name="to-create-a-build-configuration"></a>So erstellen Sie eine Buildkonfiguration

1. Öffnen Sie das Dialogfeld **Konfigurations-Manager**.

    ![Build menu, Configuration Manager command](../ide/media/buildwalk-configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")

2. Wählen Sie in der Liste **Konfiguration der aktuellen Projektmappe** den Eintrag **Neu** aus.

3. Geben Sie im Dialogfeld **Neue Projektmappenkonfiguration** den Namen `Test` für die neue Konfiguration ein, kopieren Sie die Einstellungen aus der vorhandenen Debugkonfiguration, und wählen Sie dann die Schaltfläche **OK** aus.

    ![New Solution Configuration Dialog Box](../ide/media/buildwalk-newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")

4. Wählen Sie in der Liste **Aktive Projektmappenplattform** den Eintrag **Neu** aus.

5. Wählen Sie im Dialogfeld **Neue Projektmappenplattform** die Option **x64** aus, und kopieren Sie keine der Einstellungen der x86-Plattform.

    ![New Solution Platform Dialog Box](../ide/media/buildwalk-newsolutionplatform.png "BuildWalk_NewSolutionPlatform")

6. Klicken Sie auf die Schaltfläche **OK** .

   Die aktive Projektmappenkonfiguration wurde für einen Test mit der aktiven, auf x64- festgelegten Projektmappenplattform geändert.

   ![Configuration Manager with Test configuration](../ide/media/buildwalk-configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")

   Sie können die aktive Projektmappenkonfiguration schnell überprüfen oder ändern, indem Sie die Liste **Projektmappenkonfigurationen** auf der Symbolleiste **Standard** verwenden.

   ![Solution Configuration option Standard Toolbar](../ide/media/buildwalk-standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")

## <a name="BKMK_building"></a> Erstellen der Anwendung

Danach erstellen Sie die Projektmappe mit der benutzerdefinierten Buildkonfiguration.

#### <a name="to-build-the-solution"></a>So erstellen Sie die Projektmappe

- Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.

  Im Fenster **Ausgabe** wird das Ergebnis des Builds angezeigt. Der Build ist erfolgreich, doch wurden einige Warnmeldungen erzeugt.

  Abbildung 1: Visual Basic-Warnungen

  ![Output Window Visual Basic](../ide/media/buildwalk-vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")

  Abbildung 2: Visual C#-Warnungen

  ![Output Window Visual C&#35;](../ide/media/buildwalk-csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")

## <a name="BKMK_hidewarning"></a> Ausblenden von Compilerwarnungen

Sie können bestimmte Warnungen während eines Builds vorübergehend ausblenden, anstatt sie die Buildausgabe durcheinanderbringen zu lassen.

#### <a name="to-hide-a-specific-visual-c-warning"></a>So blenden Sie eine bestimmte Visual C#-Warnung aus

1. Wählen Sie im **Projektmappen-Explorer** den Projektknoten der obersten Ebene aus.

2. Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaftenseiten**.

     Der **Projekt-Designer** wird geöffnet.

3. Wählen Sie die Seite **Erstellen**, und geben Sie im Feld **Warnungen unterdrücken** die Warnungsnummer `1762` an.

     ![Build page, Project Designer](../ide/media/buildwalk-csharpsuppresswarnings.png "BuildWalk_CsharpSuppressWarnings")

     Weitere Informationen finden Sie unter [Seite „Erstellen“, Projekt-Designer (C#)](../ide/reference/build-page-project-designer-csharp.md).

4. Erstellen Sie die Projektmappe.

     Im Fenster **Ausgabe** werden nur Zusammenfassungsinformationen für den Build angezeigt.

     ![Output Window, Visual C&#35; Build Warnings](../ide/media/buildwalk-visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")

#### <a name="to-suppress-all-visual-basic-build-warnings"></a>So unterdrücken Sie alle Visual Basic-Buildwarnungen

1. Wählen Sie im **Projektmappen-Explorer** den Projektknoten der obersten Ebene aus.

2. Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaftenseiten**.

    Der **Projekt-Designer** wird geöffnet.

3. Aktivieren Sie auf der Seite **Kompilieren** das Kontrollkästchen **Alle Warnungen deaktivieren**.

    ![Compile page, Project Designer](../ide/media/buildwalk-vbsuppresswarnings.png "BuildWalk_VBSuppressWarnings")

    Weitere Informationen finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Erstellen Sie die Projektmappe.

   Im Fenster **Ausgabe** werden nur Zusammenfassungsinformationen für den Build angezeigt.

   ![Output Window, Visual Basic Build Warnings](../ide/media/buildwalk-visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")

   Weitere Informationen finden Sie unter [Vorgehensweise: Unterdrücken von Compiler-Warnungen](../ide/how-to-suppress-compiler-warnings.md).

## <a name="BKMK_outputdetails"></a> Anzeigen zusätzlicher Builddetails im Ausgabefenster

Sie können die Menge der im Fenster **Ausgabe** angezeigten Informationen über den Buildprozess ändern. Buildausführlichkeit wird normalerweise auf „Minimal“ festgelegt. Das bedeutet, dass im Fenster **Ausgabe** nur eine Zusammenfassung des Buildprozesses zusammen mit allen Warnungen oder Fehlern mit hoher Priorität angezeigt wird. Sie können mithilfe von [Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) weitere Informationen zum Build anzeigen lassen.

> [!IMPORTANT]
> Wenn Sie weitere Informationen anzeigen, dauert der Abschluss des Builds länger.

#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>So ändern Sie die Informationsmenge im Ausgabefenster

1. Öffnen Sie das Dialogfeld **Optionen**.

    ![Befehl „Optionen“ im Menü „Tools“](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")

2. Wählen Sie die Kategorie **Projekte und Projektmappen**, und wählen Sie dann die Seite **Erstellen und Ausführen** aus.

3. Wählen Sie in der Liste **Ausführlichkeit der MSBuild-Projektbuildausgabe** die Option **Normal** und dann die Schaltfläche **OK** aus.

4. Wählen Sie in der Menüleiste **Build**, **Projektmappe bereinigen** aus.

5. Erstellen Sie die Projektmappe, und überprüfen Sie dann die Informationen im Fenster **Ausgabe**.

    Die Buildinformationen umfassen die Uhrzeit, zu der der Build gestartet ist (am Anfang), Reihenfolge, in der die Dateien verarbeitet wurden, und die zum Abschließen des Prozesses erforderliche Zeit (am Ende). Diese Informationen umfassen auch die von Visual Studio beim Build ausgeführt Compeliersyntax.

    Im Visual C#-Build führt die [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83)-Option z.B. den von Ihnen zuvor in diesem Thema angegebenen Warnungscode 1762 zusammen mit drei weiteren Warnungen auf.

    Im Visual Basic-Build umfasst [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) keine bestimmten auszuschließenden Warnungen, sodass keine Warnungen angezeigt werden.

   > [!TIP]
   > Sie können den Inhalt des Fensters **Ausgabe** durchsuchen, wenn Sie das Dialogfeld **Suchen** mithilfe der Tastenkombination STRG+F anzeigen.

   Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Erstellen eines Versionsbuilds

Sie können eine Version der Beispielanwendung erstellen, die für das Versenden optimiert wird. Beim Releasebuild geben Sie an, dass die ausführbare Datei auf eine Netzwerkfreigabe kopiert wird, bevor der Build gestartet wird.

Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Buildausgabeverzeichnisses](../ide/how-to-change-the-build-output-directory.md) und [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

#### <a name="to-specify-a-release-build-for-visual-basic"></a>So geben Sie einen Releasebuild für Visual Basic an

1. Öffnen Sie den **Projekt-Designer**.

     ![View menu, Property Pages command](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. Wählen Sie die Seite **Kompilieren** aus.

3. Wählen Sie in der Liste **Konfiguration** die Option **Release** aus.

4. Wählen Sie in der Liste **Plattform** die Option **x86** aus.

5. Geben Sie im Feld **Buildausgabepfad** einem Netzwerkpfad an.

     Sie können z.B. \\\myserver\builds angeben.

    > [!IMPORTANT]
    > Möglicherweise wird ein Meldungsfeld angezeigt, in dem davor gewarnt wird, dass die von Ihnen angegebene Netzwerkfreigabe eventuell kein vertrauenswürdiger Speicherort ist. Wenn Sie dem angegebenen Speicherort vertrauen, wählen Sie im Meldungsfeld die Schaltfläche **OK** aus.

6. Erstellen Sie die Anwendung.

     ![Befehl „Projektmappe erstellen“ im Menü „Erstellen“](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

#### <a name="to-specify-a-release-build-for-visual-c"></a>To specify a release build for Visual C\#

1. Öffnen Sie den **Projekt-Designer**.

    ![View menu, Property Pages command](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. Wählen Sie die Seite **Erstellen** aus.

3. Wählen Sie in der Liste **Konfiguration** die Option **Release** aus.

4. Wählen Sie in der Liste **Plattform** die Option **x86** aus.

5. Geben Sie im Feld **Ausgabepfad** einen Netzwerkpfad an.

    Sie könnten z.B. \\\myserver\builds angeben.

   > [!IMPORTANT]
   > Möglicherweise wird ein Meldungsfeld angezeigt, in dem davor gewarnt wird, dass die von Ihnen angegebene Netzwerkfreigabe eventuell kein vertrauenswürdiger Speicherort ist. Wenn Sie dem angegebenen Speicherort vertrauen, wählen Sie im Meldungsfeld die Schaltfläche **OK** aus.

6. Erstellen Sie die Anwendung.

    ![Befehl „Projektmappe erstellen“ im Menü „Erstellen“](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Die ausführbare Datei wird auf den von Ihnen angegebenen Netzwerkpfad kopiert. Der Pfad ist \\\myserver\builds\\*Dateiname*.exe.

   Herzlichen Glückwunsch: Sie haben diese exemplarische Vorgehensweise erfolgreich abgeschlossen.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Erstellen eines Projekts (C++)](https://msdn.microsoft.com/library/d459bc03-88ef-48d0-9f9a-82d17f0b6a4d)
- [Übersicht über die Vorkompilierung von ASP.NET-Webanwendungsprojekten](https://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)
- [Exemplarische Vorgehensweise: Verwenden von MSBuild](../msbuild/walkthrough-using-msbuild.md)
