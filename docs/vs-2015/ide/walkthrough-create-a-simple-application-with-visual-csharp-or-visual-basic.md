---
title: 'Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung mit Visual C# oder Visual Basic | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5e41dbf3422374add68e351da1e4b703772a3a4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296863"
---
# <a name="walkthrough-create-a-simple-application-with-visual-c-or-visual-basic"></a>Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung mit Visual C# oder Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie diese exemplarische Vorgehensweise durcharbeiten, werden Sie mit vielen Tools, Dialogfeldern und Designern vertraut, die Sie für die Entwicklung von Anwendungen in Visual Studio verwenden können. Sie erstellen die einfache Anwendung "Hello, World", entwerfen die Benutzeroberfläche, fügen Code hinzu und debuggen Fehler und erfahren gleichzeitig mehr über das Arbeiten in der integrierten Entwicklungsumgebung (IDE).

 Dieses Thema enthält folgende Abschnitte:

 [Konfigurieren der IDE](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_ConfigureIDE)

 [Erstellen einer einfachen Anwendung](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_CreateApp)

 [Debuggen und Testen der Anwendung](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_DebugTest)

> [!NOTE]
> Diese exemplarische Vorgehensweise basiert auf Visual Studio Professional, da diese Version die WPF-Anwendungsvorlage enthält, mit deren Hilfe Sie das Projekt für diese exemplarische Vorgehensweise erstellen. Visual Studio Express für Windows Desktop enthält diese Vorlage ebenfalls, nicht aber Visual Studio Express für Windows und Visual Studio Express für das Web. Einführende Informationen zur Verwendung von Visual Studio Express für Windows finden Sie unter [Developer Center für Windows Store-Apps](https://msdn.microsoft.com/windows/apps/br229519). Einführende Informationen zur Verwendung von Visual Studio Express für das Web finden Sie unter [Erste Schritte mit ASP.NET](https://dotnet.microsoft.com/learn/aspnet/hello-world-tutorial/intro). Außerdem bestimmen die Edition von Visual Studio und Einstellungen, die Sie verwenden, die Namen und Positionen einiger Elemente der Benutzeroberfläche. Siehe [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)

## <a name="BKMK_ConfigureIDE"></a> Konfigurieren der IDE
 Wenn Sie Visual Studio zum ersten Mal starten, werden Sie aufgefordert, sich mit einem Microsoft Dienstkonto (Microsoft Service Account; MSA) anzumelden, [Anmelden bei Visual Studio](https://devblogs.microsoft.com/visualstudio/welcome-sign-in-to-visual-studio/). Sie müssen sich nicht jetzt anmelden, sondern können dies auch später machen.

 Beim Start von Visual Studio müssen Sie als Nächstes eine Einstellungskombination auswählen, die einen Satz an vordefinierten Anpassungen auf die IDE anwendet. Jede Einstellungskombination wurde entwickelt, um Ihnen die Entwicklung von Anwendungen zu vereinfachen.

 Grundlage dieser exemplarischen Vorgehensweise sind die **Allgemeinen Entwicklungseinstellungen**, bei denen nur ein Mindestmaß an Anpassungen auf die IDE angewendet wird. Wenn Sie bereits C# oder Visual Basic (beides sind gute Optionen) ausgewählt haben, müssen Sie die Einstellungen nicht ändern.  Wenn Sie Ihre Einstellungen ändern möchten, können Sie den **Assistenten zum Importieren und Exportieren von Einstellungen**verwenden. Siehe [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)

 Wenn Sie Visual Studio geöffnet haben, können Sie die Toolfenster, die Menüs und Symbolleisten und den Hauptfensterbereich erkennen. Mit **Schnellstart**werden Toolfenster auf der linken und rechten Seite des Anwendungsfensters und die Menüleiste und die Standardsymbolleiste oben angedockt. In der Mitte des Anwendungsfensters befindet sich die **Startseite**. Wenn Sie eine Projektmappe oder ein Projekt laden, werden Editoren und Designer dort angezeigt, wo sich die **Startseite** befindet. Wenn Sie eine Anwendung entwickeln, verbringen Sie die meiste Zeit in diesem zentralen Bereich.

 Abbildung 2: Visual Studio-IDE

 ![IDE mit „Allgemeine Einstellungen“ übernommen](../ide/media/exploreide-idewithgeneralsettings.png "|::ref1::|")

 Sie können weitere Anpassungen an Visual Studio vornehmen. Sie können z. B. die Schriftart und Größe des Texts im Editor oder das Farbschema der IDE ändern, indem Sie das Dialogfeld **Optionen** verwenden. Je nach gültiger Einstellungskombination werden möglicherweise einige Elemente in diesem Dialogfeld nicht automatisch angezeigt. Sie können überprüfen, ob alle möglichen Optionen angezeigt werden, indem Sie das Kontrollkästchen **Alle Einstellungen anzeigen** aktivieren.

 Abbildung3: Dialogfeld "Optionen"

 ![Dialogfeld „Optionen“ mit Option „Alle Einstellungen anzeigen“](../ide/media/exploreide-optionsdialogbox.png "|::ref2::|")

 In diesem Beispiel ändern Sie das Farbschema der IDE von hell zu dunkel.  Erstellen Sie direkt ein Projekt, wenn Sie möchten.

#### <a name="to-change-the-color-theme-of-the-ide"></a>Ändern des Farbschemas der IDE

1. Öffnen Sie das Dialogfeld **Optionen** durch Auswählen des Menüs **Extras** am oberen Rand, und klicken Sie dann auf **Optionen...** .

    ![Befehl „Optionen“ im Menü „Tools“](../ide/media/exploreide-toolsoptionsmenu.png "|::ref3::|")

2. Ändern Sie das **Farbschema** zu **Dunkel**, und klicken Sie anschließend auf **OK**.

    ![Dunkles Farbschema ausgewählt](../ide/media/exploreide-darkthemeoptionsdlgbox.png "|::ref4::|")

   Die Farben in Visual Studio sollten mit dem folgenden Bild übereinstimmen:

   ![IDE mit „Dunkles Design“ übernommen](../ide/media/exploreide-darkthemeide.png "|::ref5::|")

   Das im weiteren Verlauf dieser exemplarischen Vorgehensweise für Bilder verwendete Farbschema ist das helle Design. Weitere Informationen zum Anpassen der IDE finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="BKMK_CreateApp"></a> Erstellen einer einfachen Anwendung

### <a name="create-the-project"></a>Erstellen eines Projekts
 Wenn Sie eine Anwendung in Visual Studio erstellen, erstellen Sie zunächst ein Projekt und eine Projektmappe. In diesem Beispiel erstellen Sie eine Windows Presentation Foundations (WPF)-Projektmappe.

##### <a name="to-create-the-wpf-project"></a>So erstellen Sie das WPF-Projekt

1. Erstellen Sie ein neues Projekt. Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.

    ![Wählen Sie in der Menüleiste „Datei > Neu > Projekt“ aus.](../ide/media/exploreide-filenewproject.png "|::ref6::|")

    Sie können auch **Neues Projekt** im Feld **Schnellstart** eingeben, um ein neues Projekt zu erstellen.

    ![Neues Projekt im Feld „Schnellstart“ angeben](../ide/media/exploreide-quicklaunchnewprojectsmall.png "|::ref7::|")

2. Wählen Sie die Visual Basic- oder Visual C# WPF-Anwendungsvorlage, in dem Sie z. B. im linken Bereich **Installiert**, **Vorlagen**, **Visual C#** , **Windows**auswählen und dann im mittleren Bereich "WPF-Anwendung" auswählen.  Geben Sie dem Projekt am unteren Rand des Dialogfelds "Neues Projekt" den Namen "HelloWPFApp".

    ![„Visual Basic WPF Project, HelloWPFApp“ erstellen](../ide/media/exploreide-newprojectvb.png "|::ref8::|")

    ODER

    ![Erstellen eines Visual C&#35; WPF-Projekts, hellowpfapp](../ide/media/exploreide-newprojectcsharp.png "|::ref9::|")

   Visual Studio erstellt das HelloWPFApp-Projekt und die Projektmappe, woraufhin im **Projektmappen-Explorer** verschiedene Dateien angezeigt werden. Der WPF-Designer zeigt eine Entwurfsansicht und eine XAML-Ansicht der Datei "MainWindow.xaml" in einer geteilten Ansicht an. Ziehen Sie den Teiler, um mehr oder weniger der jeweiligen Ansichten anzuzeigen.  Sie können auch nur die visuelle Ansicht oder nur die XAML-Ansicht anzeigen. Weitere Informationen finden Sie unter [WPF Designer für Windows Forms-Entwickler](https://msdn.microsoft.com/47ad0909-e89b-4996-b4ac-874d929f94ca). Die folgenden Elemente werden in **Projektmappen-Explorer**angezeigt:

   Abbildung 5: Projektelemente

   ![Projektmappen-Explorer mit geladenen HelloWPFApp-Dateien](../ide/media/exploreide-hellowpfappfiles.png "|::ref10::|")

   Nachdem Sie das Projekt erstellt haben, können Sie es anpassen. Im Fenster **Eigenschaften** (Menü **Ansicht** ) können Sie Optionen für Projektelemente, Steuerelemente und andere Elemente in einer Anwendung anzeigen und ändern. Auf den Projekteigenschafts- und die Eigenschaftsseiten können Sie Optionen für Projekte und Projektmappen anzeigen und ändern.

##### <a name="to-change-the-name-of-mainwindowxaml"></a>Ändern des Namens der Datei "MainWindow.xaml"

1. In der folgenden Prozedur geben Sie "MainWindow" einen genaueren Namen. Wählen Sie in **Projektmappen-Explorer**MainWindow.xaml aus. Es sollte das Fenster **Eigenschaften** angezeigt werden; wenn dies nicht der Fall ist, wählen Sie das Menü **Ansicht** und das **Eigenschaftenfenster** -Element aus. Ändern Sie die Eigenschaft **Dateiname** in `Greetings.xaml`

    ![Eigenschaftenfenster mit hervorgehobenem Dateinamen](../ide/media/exploreide-filenameinpropertieswindow.png "|::ref11::|")

    Im**Projektmappen-Explorer** wird jetzt als Name der Datei "Greetings.xaml" angezeigt, und wenn Sie den Knoten "MainWindow.xaml" erweitern (durch Aktivieren des Knotens und Drücken des Rechtspfeils) sehen Sie, dass der Name der Datei "MainWindow.xaml.vb" bzw. "MainWindow.xaml.cs" jetzt "Greetings.xaml.vb" bzw. "Greetings.xaml.cs" ist. Diese Codedatei ist unter dem XAML-Datei-Knoten geschachtelt, um deren enge Verbindung miteinander darzustellen.

   > [!WARNING]
   > Diese Änderung verursacht einen Fehler. In einem späteren Schritt werden Sie lernen, wie dieser Fehler erkannt und korrigiert wird.

2. Öffnen Sie im **Projektmappen-Explorer**die Datei "Greetings.xaml" in der Entwurfsansicht (durch Drücken der EINGABETASTE bei ausgewähltem Knoten), und wählen Sie die Titelleiste des Fensters mit der Maus aus.

3. Ändern Sie im Fenster **Eigenschaften** den Wert der **Titel** -Eigenschaft in `Greetings`.

   Die Titelleiste für MainWindow.xaml lautet jetzt Greetings.

### <a name="design-the-user-interface-ui"></a>Entwerfen der Benutzeroberfläche (UI)
 Nun fügen wir der Anwendung drei Arten von Steuerelementen hinzu: ein TextBlock-Steuerelement, zwei RadioButton-Steuerelemente und ein Button-Steuerelement.

##### <a name="to-add-a-textblock-control"></a>Hinzufügen eines TextBlock-Steuerelements

1. Öffnen Sie den **Werkzeugkasten** durch Auswählen des Menüs **Ansicht** und der Option **Werkzeugkasten** .

2. Suchen Sie im **Werkzeugkasten**nach dem TextBlock-Steuerelement.

    ![Toolbox mit hervorgehobenem TextBlock-Steuerelement](../ide/media/exploreide-textblocktoolbox.png "|::ref12::|")

3. Fügen Sie auf der Entwurfsoberfläche ein TextBlock-Steuerelement hinzu, indem Sie das TextBlock-Element auswählen und in das Fenster auf der Entwurfsoberfläche ziehen.  Zentrieren Sie das Steuerelement im oberen Bereich des Fensters.

   Das Fenster sollte der folgenden Abbildung entsprechen:

   Abbildung 7: Greetings-Fenster mit TextBlock-Steuerelement

   ![TextBlock-Steuerelement im Formular „Greetings“](../ide/media/exploreide-greetingswithtextblockonly.png "|::ref13::|")

   Das XAML-Markup sollte in etwa der folgenden Darstellung entsprechen:

```
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>
```

##### <a name="to-customize-the-text-in-the-text-block"></a>Anpassen des Texts im Textblock

1. Suchen Sie in der XAML-Ansicht das Markup für TextBlock, und ändern Sie das Textattribut: `Text=”Select a message option and then choose the Display button.”`

2. Wenn der Textblock nicht so erweitert wird, dass er in die Entwurfsansicht passt, vergrößern Sie das TextBlock-Steuerelement (mit den Handles an den Kanten), sodass es den gesamten Text anzeigt.

3. Speichern Sie die Änderungen durch Drücken von STRG + S oder mithilfe des Menüelements **Datei** .

   Anschließend fügen Sie dem Formular zwei [RadioButton](https://msdn.microsoft.com/library/6c9ba847-eab7-4bba-9c74-6b56ef72067b)-Steuerelemente hinzu.

##### <a name="to-add-radio-buttons"></a>Hinzufügen von Optionsfeldern

1. Suchen Sie im **Werkzeugkasten**nach dem RadioButton-Steuerelement.

    ![Toolboxfenster mit aktiviertem RadioButton-Steuerelement](../ide/media/exploreide-radiobuttontoolbox.png "|::ref14::|")

2. Fügen Sie der Entwurfsoberfläche zwei RadioButton-Steuerelemente hinzu, indem Sie das RadioButton-Element auswählen und es zweimal in das Fenster auf der Entwurfsoberfläche ziehen, und verschieben Sie die Schaltflächen (indem Sie sie auswählen und die Pfeiltasten drücken), damit die Schaltflächen unter dem TextBlock-Steuerelement nebeneinander angezeigt werden.

    Das Fenster sieht wie folgt aus:

    Abbildung 8: RadioButtons im Greetings-Fenster.

    ![Formular „Greetings“ mit TextBlock und zwei RadioButtons](../ide/media/exploreide-greetingswithradiobuttons.png "|::ref15::|")

3. Ändern Sie im Fenster **Eigenschaften** für das linke RadioButton-Steuerelement die Eigenschaft **Name** (die Eigenschaft oben im Fenster **Eigenschaften** ) in `RadioButton1`.  Stellen Sie sicher, dass Sie im Formular das Optionsfeld (RadioButton) und nicht das Hintergrundraster ausgewählt haben; im Feld "Typ" des Eigenschaftenfensters sollte unter dem Feld "Name" der Begriff "RadioButton" angezeigt werden.

4. Ändern Sie im Fenster **Eigenschaften** des rechten RadioButton-Steuerelements die Eigenschaft **Name** in `RadioButton2`. Speichern Sie dann die Änderungen durch Drücken von STRG + S oder über das Menü **Datei** .  Stellen Sie sicher, dass Sie "RadioButton" ausgewählt haben, bevor Sie Änderungen vornehmen und speichern.

   Sie können jetzt Anzeigetext für jedes RadioButton-Steuerelement hinzufügen. Die folgende Prozedur aktualisiert die Eigenschaft **Inhalt** für ein RadioButton-Steuerelement.

##### <a name="to-add-display-text-for-each-radio-button"></a>Hinzufügen von Anzeigetext für jedes Optionsfeld

1. Öffnen Sie auf der Entwurfsoberfläche das Kontextmenü für RadioButton1, indem Sie mit der rechten Maustaste bei ausgewähltem "RadioButton1" klicken, wählen Sie **Text bearbeiten**, und geben Sie dann `Hello`ein.

2. Öffnen Sie das Kontextmenü für RadioButton2, indem Sie mit der rechten Maustaste bei ausgewähltem RadioButton2 klicken, wählen Sie **Text bearbeiten**, und geben Sie dann `Goodbye`ein.

   Das letzte Benutzeroberflächenelement, das Sie hinzufügen, ist ein [Button](https://msdn.microsoft.com/library/a9d8f5a5-c98c-463e-808a-5a4e63173098)-Steuerelement.

##### <a name="to-add-the-button-control"></a>Hinzufügen eines Button-Steuerelements

1. Suchen Sie im **Werkzeugkasten**nach dem **Button** -Steuerelement, und fügen Sie es auf der Entwurfsoberfläche unter den RadioButton-Steuerelementen ein, indem Sie "Button" auswählen und es in der Entwurfsansicht in das Formular ziehen.

2. Ändern Sie in der XAML-Ansicht den Wert von **Inhalt** für das Button-Steuerelement von `Content=”Button”` in `Content=”Display”`. Speichern Sie dann die Änderungen (STRG + S oder Menü **Datei** ).

    Das Markup sollte in etwa dem folgenden Beispiel entsprechen: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

   Das Fenster sollte der folgenden Abbildung entsprechen.

   Abbildung 9: Abschließende Benutzeroberfläche von Greetings

   ![Formular „Greetings“ mit Steuerelementbezeichnungen](../ide/media/exploreide-greetingswithconrollabels.png "|::ref16::|")

### <a name="add-code-to-the-display-button"></a>Hinzufügen von Code zur Anzeigeschaltfläche
 Wenn die Anwendung ausgeführt wird, wird ein Meldungsfeld angezeigt, nachdem ein Benutzer zunächst ein Optionsfeld aktiviert und anschließend die Schaltfläche **Anzeigen** auswählt hat. Ein Meldungsfeld wird für die Begrüßung ("Hello") und ein anderes für die Verabschiedung ("Goodbye") angezeigt. Um dieses Verhalten zu erstellen, fügen Sie Code zum Button_Click-Ereignis in Greetings.xaml.vb oder in Greetings.xaml.cs hinzu.

##### <a name="add-code-to-display-message-boxes"></a>Hinzufügen von Code zu Anzeigenmeldungsfeldern

1. Doppelklicken Sie auf der Entwurfsoberfläche auf die Schaltfläche **Anzeigen** .

     Greetings.xaml.vb oder Greetings.xaml.cs wird geöffnet, der Cursor steht im Button_Click-Ereignis. Sie können auch einen Click-Ereignishandler wie folgt hinzufügen (wenn im eingefügten Code Namen rot unterstrichen sind, haben Sie wahrscheinlich nicht die RadioButton-Steuerelemente auf der Entwurfsoberfläche ausgewählt und umbenannt):

     Für Visual Basic sollte der Ereignishandler wie folgt aussehen:

    ```vb
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

     Für Visual C# sollte der Ereignishandler wie folgt aussehen:

    ```csharp
    private void Button_Click_1(object sender, RoutedEventArgs e)
    {

    }
    ```

2. Geben Sie für Visual Basic den folgenden Code ein:

    ```vb
    If RadioButton1.IsChecked = True Then
        MessageBox.Show("Hello.")
    Else RadioButton2.IsChecked = True
        MessageBox.Show("Goodbye.")
    End If

    ```

     Geben Sie für Visual C# den folgenden Code ein:

    ```
    if (RadioButton1.IsChecked == true)
    {
        MessageBox.Show("Hello.");
    }
    else
    {
        RadioButton2.IsChecked = true;
        MessageBox.Show("Goodbye.");
    }
    ```

3. Speichern Sie die Anwendung.

## <a name="BKMK_DebugTest"></a> Debuggen und Testen der Anwendung
 Als Nächstes debuggen Sie die Anwendung, um nach Fehlern zu suchen und zu testen, ob beide Meldungsfelder ordnungsgemäß angezeigt werden. Die folgenden Anweisungen beschreiben, wie Sie den Debugger erstellen und starten. Lesen Sie jedoch später für weitere Informationen [Erstellen einer WPF-Anwendung (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c) und [Debuggen von WPF](../debugger/debugging-wpf.md).

### <a name="find-and-fix-errors"></a>Suchen und Beheben von Fehlern
 In diesem Schritt suchen Sie den Fehler, den wir zuvor verursacht haben, indem wir den Namen der Hauptfensters der XAML-Datei geändert haben.

##### <a name="to-start-debugging-and-find-the-error"></a>Starten des Debugging und Suchen des Fehlers

1. Starten Sie den Debugger, indem Sie **Debuggen**, dann **Debugging starten**auswählen.

    ![Befehl „Debugging starten“ im Menü „Debuggen“](../ide/media/exploreide-startdebugging.png "|::ref17::|")

    Ein Dialogfeld wird angezeigt, das angibt, dass ein IOException aufgetreten ist: Ressource "mainwindow.xaml" kann nicht gefunden werden.

2. Wählen Sie die Schaltfläche **OK** aus, und beenden Sie anschließend den Debugger.

    ![Befehl „Debugging beenden“ im Menü „Debuggen“](../ide/media/exploreide-stopdebugging.png "|::ref18::|")

   Zu Beginn dieser exemplarischen Vorgehensweise haben wir "Mainwindow.xaml" in "Greetings.xaml" umbenannt. Da der Code jedoch weiterhin auf "Mainwindow.xaml" als Start-URI für die Anwendung verweist, kann das Projekt nicht gestartet werden.

##### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Angeben von Greetings.xaml als Start- URI

1. Öffnen Sie im **Projektmappen-Explorer**die Datei "App.xaml" (im C#-Projekt) oder die Datei "Application.xaml" (im Visual Basic-Projekt) in der XAML-Ansicht (sie kann nicht in der Entwurfsansicht geöffnet werden), indem Sie die Datei auswählen und die EINGABETASTE drücken oder indem Sie darauf doppelklicken.

2. Ändern Sie `StartupUri="MainWindow.xaml"` in `StartupUri="Greetings.xaml"`, und speichern Sie dann die Änderungen mit STRG + S.

   Starten Sie den Debugger erneut (Taste F5). Sie sollten das Greetings-Fenster der Anwendung sehen.

### <a name="to-debug-with-breakpoints"></a>Debuggen mit Haltepunkten
 Wenn Sie einige Haltepunkte hinzufügen, können Sie den Code während des Debuggens testen. Sie können Haltepunkte hinzufügen, indem Sie im Hauptmenü **Debuggen** und dann **Haltepunkt umschalten** auswählen oder indem Sie am linken Rand des Editors neben der Codezeile klicken, in der die Unterbrechung stattfinden soll.

##### <a name="to-add-breakpoints"></a>Hinzufügen von Haltepunkten

1. Öffnen Sie Greetings.xaml.vb oder Greetings.xaml.cs, und wählen Sie die folgende Zeile aus: `MessageBox.Show("Hello.")`

2. Fügen Sie einen Haltepunkt hinzu, indem Sie im Menü **Debuggen**und dann **Haltepunkt umschalten**auswählen.

     ![Befehl „Haltepunkt umschalten“ im Menü „Debuggen“](../ide/media/exploreide-togglebreakpoint.png "|::ref19::|")

     Am äußeren linken Rand des Editorfensters wird ein roter Kreis neben der Codezeile angezeigt.

3. Wählen Sie folgende Zeile aus: `MessageBox.Show("Goodbye.")`.

4. Drücken Sie die Taste F9, um einen Haltepunkt hinzuzufügen, und drücken Sie dann F5, um das Debuggen zu starten.

5. Aktivieren Sie im Fenster **Greetings** das Optionsfeld **Hello** , und wählen Sie dann die Schaltfläche **Anzeigen** aus.

     Die Zeile wird `MessageBox.Show("Hello.")` gelb hervorgehoben. Am unteren Rand der IDE werden die Fenster "Auto", "Lokal" und "Überwachen" auf der linken Seite zusammengedockt, und die Fenster "Aufrufliste", "Haltepunkte", "Befehl", "Direkt" und "Ausgabe" werden auf der rechten Seite zusammengedockt.

6. Wählen Sie in der Menüleiste **Debuggen**die Option **Rücksprung**aus.

     Die Anwendung wird weiter ausgeführt, und ein Meldungsfeld mit dem Wort "Hello" wird angezeigt.

7. Wählen Sie die Schaltfläche **OK** im Meldungsfeld, um es zu schließen.

8. Aktivieren Sie im Fenster **Greetings** das Optionsfeld **Goodbye** , und wählen Sie dann die Schaltfläche **Anzeigen** aus.

     Die Zeile wird `MessageBox.Show("Goodbye.")` gelb hervorgehoben.

9. Drücken Sie die F5-TASTE, um das Debuggen fortzusetzen. Wenn das Meldungsfeld angezeigt wird, wählen Sie die Schaltfläche **OK** im Meldungsfeld, um es zu schließen.

10. Drücken Sie UMSCHALT + F5 (drücken Sie zuerst die UMSCHALTTASTE, und halten Sie sie gedrückt, und drücken Sie dann F5), um den Debugvorgang zu beenden.

11. Klicken Sie in der Menüleiste **Debuggen**auf **Alle Haltepunkte deaktivieren**.

### <a name="build-a-release-version-of-the-application"></a>Version der Anwendung erstellen
 Nachdem Sie überprüft haben, dass alles funktioniert, können Sie einen Releasebuild der Anwendung vorbereiten.

##### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Bereinigen der Projektmappendateien und Erstellen einer Releaseversion

1. Wählen Sie im Hauptmenü **Erstellen**und dann **Projektmappe bereinigen** aus, um Zwischendateien und Ausgabedateien zu löschen, die bei vorherigen Durchläufen erstellt wurden.  Dies ist nicht erforderlich, bereinigt jedoch die Ausgaben des Builddebugvorgangs.

    ![Befehl „Projektmappe bereinigen“ im Menü „Erstellen“](../ide/media/exploreide-cleansolution.png "|::ref20::|")

2. Ändern Sie die Build-Konfiguration für HelloWPFApp über das Dropdown-Steuerelement in der Symbolleiste (derzeit "Debug") von **Debug** in **Release** .

    ![Standardsymbolleiste mit ausgewählter Release](../ide/media/exploreide-releaseversion.png "|::ref21::|")

3. Erstellen Sie die Projektmappe durch Auswahl von **Erstellen**und dann **Projektmappe erstellen** , oder drücken Sie die Taste F6.

    ![Befehl „Projektmappe erstellen“ im Menü „Erstellen“](../ide/media/exploreide-buildsolution.png "|::ref22::|")

   Herzlichen Glückwunsch, Sie haben diese exemplarischen Vorgehensweise abgeschlossen! Sie finden die EXE-Datei, die Sie erstellt haben, in Ihrer Projektmappe und im Projektverzeichnis (…\HelloWPFApp\HelloWPFApp\bin\Release\\). Weitere Beispiele zum Durcharbeiten finden Sie unter [Visual Studio-Beispiele](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Siehe auch
 [Neues in Visual Studio 2015 Einstieg in die](../what-s-new-in-visual-studio-2015.md) [Entwicklung mit Visual Studio](../ide/get-started-developing-with-visual-studio.md) [Produktivitäts Tipps](../ide/productivity-tips-for-visual-studio.md)
