---
title: 'Tutorial: „Hallo Welt“-App mit Windows Presentation Foundation (WPF) in C#'
description: Erstellen Sie eine einfache Windows Desktop.NET-App in C# mit Visual Studio mit dem Windows Presentation Foundation (WPF) UI-Framework.
ms.custom: seodec18, get-started
ms.date: 10/03/2017
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d59cb6a94259342b635df6632d54db825a427c63
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323853"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Tutorial: Erstellen einer einfachen Anwendung mit C\#

Wenn Sie diese exemplarische Vorgehensweise durcharbeiten, werden Sie mit vielen Tools, Dialogfeldern und Designern vertraut, die Sie für die Entwicklung von Anwendungen in Visual Studio verwenden können. Sie erstellen eine Anwendung „Hello, World“, entwerfen die Benutzeroberfläche, fügen Code hinzu und debuggen Fehler. Gleichzeitig erfahren Sie mehr über das Arbeiten in der integrierten Entwicklungsumgebung ([IDE](visual-studio-ide.md)).

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) kostenlos herunterladen.

## <a name="configure-the-ide"></a>Konfigurieren der IDE

Wenn Sie Visual Studio zum ersten Mal starten, werden Sie zur Anmeldung aufgefordert. Dieser Schritt ist für die exemplarische Vorgehensweise nicht unbedingt notwendig. Als Nächstes wird Ihnen möglicherweise ein Dialogfeld angezeigt, in dem Sie aufgefordert werden, Ihre Entwicklungseinstellungen und Farbdesigns festzulegen. Behalten Sie die Standardeinstellungen bei, und klicken Sie auf **Visual Studio starten**.

![Dialogfeld „Einstellungen auswählen“](../media/exploreide-settings.png)

::: moniker range="vs-2017"

Wenn sich Visual Studio öffnet, werden Toolfenster, die Menüs, Symbolleisten und der Hauptfensterbereich angezeigt. Mit **Schnellstart**werden Toolfenster auf der linken und rechten Seite des Anwendungsfensters und die Menüleiste und die Standardsymbolleiste oben angedockt. In der Mitte des Anwendungsfensters befindet sich die **Startseite**. Wenn Sie eine Projektmappe oder ein Projekt laden, werden Editoren und Designer dort angezeigt, wo sich die **Startseite** befindet. Wenn Sie eine Anwendung entwickeln, verbringen Sie die meiste Zeit in diesem zentralen Bereich.

![Visual Studio 2017 IDE mit übernommenen allgemeinen Einstellungen](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Wenn Sie Visual Studio starten, wird zunächst das Fenster **Start** geöffnet. Klicken Sie auf **Contine without code** (Ohne Code fortfahren), um die Entwicklungsumgebung zu öffnen. Ihnen werden Toolfenster, Menüs und Symbolleisten sowie das Hauptfenster angezeigt. Mit **Schnellstart**werden Toolfenster auf der linken und rechten Seite des Anwendungsfensters und die Menüleiste und die Standardsymbolleiste oben angedockt. Wenn Sie eine Projektmappe oder ein Projekt laden, werden Editoren und Designer im zentralen Bereich des Anwendungsfensters angezeigt. Wenn Sie eine Anwendung entwickeln, verbringen Sie die meiste Zeit in diesem zentralen Bereich.

::: moniker-end

## <a name="create-the-project"></a>Erstellen eines Projekts

Wenn Sie eine Anwendung in Visual Studio erstellen, erstellen Sie zunächst ein Projekt und eine Projektmappe. In diesem Beispiel erstellen Sie eine Windows Presentation Foundations-Projektmappe (WPF).

1. Erstellen Sie ein neues Projekt. Klicken Sie auf der Menüleiste auf **Datei** > **Neu** > **Projekt**.

     ![Wählen Sie auf der Menüleiste "Datei", "Neu", "Projekt" aus.](../media/exploreide-filenewproject.png)

1. Klicken Sie im Dialogfeld **Neues Projekt** auf **Installiert** > **Visual C#** > **Windows-Desktop**, und wählen Sie anschließend die Vorlage **WPF-App (.NET Framework)** aus. Nennen Sie das Projekt **HelloWPFApp**.

     ![Vorlage für eine WPF-App im Visual Studio-Dialogfeld „Neues Projekt“](media/exploreide-newprojectcsharp.png)

1. Klicken Sie auf **OK**.

   Visual Studio erstellt das „HelloWPFApp“-Projekt und die Projektmappe, woraufhin im **Projektmappen-Explorer** verschiedene Dateien angezeigt werden. Der **WPF-Designer** zeigt eine Entwurfsansicht und eine XAML-Ansicht der Datei *MainWindow.xaml* in einer geteilten Ansicht an. Ziehen Sie den Teiler, um mehr oder weniger der jeweiligen Ansichten anzuzeigen. Sie können auch nur die visuelle Ansicht oder nur die XAML-Ansicht anzeigen. Die folgenden Elemente werden in **Projektmappen-Explorer**angezeigt:

   ![Projektmappen-Explorer mit geladenen HelloWPFApp-Dateien](../media/exploreide-hellowpfappfiles.png)

   > [!NOTE]
   > Weitere Informationen zu XAML (eXtensible Application Markup Language) finden Sie auf der Seite [Übersicht über XAML für WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Nachdem Sie das Projekt erstellt haben, können Sie es anpassen. Im Fenster **Eigenschaften** (Menü **Ansicht** ) können Sie Optionen für Projektelemente, Steuerelemente und andere Elemente in einer Anwendung anzeigen und ändern.

### <a name="change-the-name-of-mainwindowxaml"></a>Ändern des Namens der Datei „MainWindow.xaml“

Geben Sie „MainWindow“ einen genaueren Namen.

1. Wählen Sie im **Projektmappen-Explorer** die Datei *MainWindow.xaml* aus. Das Fenster **Eigenschaften** sollte nun angezeigt werden. Wenn dies nicht der Fall ist, klicken Sie auf das Menü **Ansicht** und das **Eigenschaftenfenster**-Element.

1. Ändern Sie die Eigenschaft **Dateiname** in `Greetings.xaml`

     ![Eigenschaftenfenster mit hervorgehobenem Dateinamen](../media/exploreide-filenameinpropertieswindow.png)

     Im **Projektmappen-Explorer** wird angezeigt, dass der Name der Datei nun *Greetings.xaml* und der Name der geschachtelten Codedatei nun *Greetings.xaml.cs* lautet. Diese Codedatei ist unter dem *XAML*-Dateiknoten geschachtelt, um deren enge Verbindung untereinander darzustellen.

## <a name="design-the-user-interface-ui"></a>Entwerfen der Benutzeroberfläche (UI)

Nun fügen wir der Anwendung drei Arten von Steuerelementen hinzu: ein <xref:System.Windows.Controls.TextBlock>-Steuerelement, zwei <xref:System.Windows.Controls.RadioButton>-Steuerelemente und ein <xref:System.Windows.Controls.Button>-Steuerelement.

### <a name="add-a-textblock-control"></a>Hinzufügen eines TextBlock-Steuerelements

1. Öffnen Sie den **Werkzeugkasten** durch Auswählen des Menüs **Ansicht** und der Option **Werkzeugkasten** .

2. Erweitern Sie in der **Toolbox** den Knoten **Häufig verwendete WPF-Steuerelemente**, damit das TextBlock-Steuerelement angezeigt wird.

     ![Toolbox mit hervorgehobenem TextBlock-Steuerelement](../media/exploreide-textblocktoolbox.png)

3. Fügen Sie auf der Entwurfsoberfläche ein TextBlock-Steuerelement hinzu, indem Sie das **TextBlock**-Element auswählen und in das Fenster auf der Entwurfsoberfläche ziehen. Zentrieren Sie das Steuerelement im oberen Bereich des Fensters.

Das Fenster sollte der folgenden Abbildung entsprechen:

![TextBlock-Steuerelement im Formular "Greetings"](../media/exploreide-greetingswithtextblockonly.png)

Das XAML-Markup sollte in etwa dem folgenden Beispiel entsprechen:

```xaml
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Anpassen des Texts im Textblock

1. Suchen Sie in der XAML-Ansicht das Markup für TextBlock, und ändern Sie das Textattribut:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. Zentrieren Sie, wenn nötig, das TextBlock-Steuerelement erneut, und speichern Sie die Änderungen durch Drücken von **STRG**+**S** oder über das Menüelement **Datei**.

Anschließend fügen Sie dem Formular zwei [RadioButton](/dotnet/framework/wpf/controls/radiobutton)-Steuerelemente hinzu.

### <a name="add-radio-buttons"></a>Hinzufügen von Optionsfeldern

1. Suchen Sie in der **Toolbox** nach dem **Optionsfeld**-Steuerelement.

     ![Toolboxfenster mit aktiviertem RadioButton-Steuerelement](../media/exploreide-radiobuttontoolbox.png)

2. Fügen Sie auf der Entwurfsoberfläche zwei Optionsfeld-Steuerelemente hinzu, indem Sie auf das **Optionsfeld**-Element klicken und in das Fenster auf der Entwurfsoberfläche ziehen. Verschieben Sie die Schaltflächen (indem Sie darauf klicken und die Pfeiltasten drücken), sodass sie nebeneinander unter dem TextBlock-Steuerelement erscheinen.

     Das Fenster sieht wie folgt aus:

     ![Formular "Greetings" mit TextBlock und zwei RadioButtons](../media/exploreide-greetingswithradiobuttons.png)

3. Ändern Sie im Fenster **Eigenschaften** für das linke RadioButton-Steuerelement die Eigenschaft **Name** (die Eigenschaft oben im Fenster **Eigenschaften** ) in `HelloButton`.

     ![Eigenschaftenfenster „RadioButton“](../media/exploreide-buttonproperties.png)

4. Ändern Sie im Fenster **Eigenschaften** zum rechten RadioButton-Steuerelement die Eigenschaft **Name** in `GoodbyeButton`. Speichern Sie dann die Änderungen.

Sie können jetzt Anzeigetext für jedes RadioButton-Steuerelement hinzufügen. Die folgende Prozedur aktualisiert die Eigenschaft **Inhalt** für ein RadioButton-Steuerelement.

### <a name="add-display-text-for-each-radio-button"></a>Hinzufügen von Anzeigetext für jedes Optionsfeld

1. Öffnen Sie auf der Entwurfsoberfläche das Kontextmenü für „HelloButton“, indem Sie mit der rechten Maustaste auf „HelloButton“ klicken. Wählen Sie dann **Text bearbeiten** aus, und geben Sie anschließend `Hello` ein.

2. Öffnen Sie das Kontextmenü für „GoodbyeButton“, indem Sie mit der rechten Maustaste auf „GoodbyeButton“ klicken. Wählen Sie dann **Text bearbeiten** aus, und geben Sie anschließend `Goodbye` ein.

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Festlegen eines standardmäßig zu aktivierenden Optionsfelds

In diesem Schritt legen Sie fest, dass „HelloButton“ standardmäßig aktiviert wird, sodass eines der beiden Optionsfelder immer aktiviert ist.

Suchen Sie in der XAML-Ansicht das Markup für „HelloButton“ und fügen Sie ein **IsChecked**-Attribut hinzu:

```xaml
IsChecked="True"
```

Das letzte Benutzeroberflächenelement, das Sie hinzufügen, ist ein [Button](/dotnet/framework/wpf/controls/button)-Steuerelement.

### <a name="add-the-button-control"></a>Hinzufügen des Button-Steuerelements

1. Suchen Sie in der **Toolbox** nach dem **Schaltflächen**-Steuerelement, und fügen Sie es auf der Entwurfsoberfläche dem Optionsfeld-Steuerelement hinzu, indem Sie es in der Entwurfsansicht in das Formular ziehen.

2. Ändern Sie in der XAML-Ansicht den Wert von **Inhalt** für das Schaltflächen-Steuerelement von `Content="Button"` in `Content="Display"`. Speichern Sie dann die Änderungen.

     Das Markup sollte in etwa dem folgenden Beispiel entsprechen: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Das Fenster sollte der folgenden Abbildung entsprechen.

     ![Formular "Greetings" mit Steuerelementbezeichnungen](media/exploreide-greetingswithcontrollabels-cs.png)

### <a name="add-code-to-the-display-button"></a>Hinzufügen von Code zur Anzeigeschaltfläche

Wenn die Anwendung ausgeführt wird, wird ein Meldungsfeld angezeigt, nachdem ein Benutzer zunächst ein Optionsfeld aktiviert und anschließend die Schaltfläche **Anzeigen** ausgewählt hat. Ein Meldungsfeld wird für die Begrüßung ("Hello") und ein anderes für die Verabschiedung ("Goodbye") angezeigt. Um dieses Verhalten zu erstellen, fügen Sie Code zum `Button_Click`-Ereignis in *Greetings.xaml.cs* hinzu.

1. Doppelklicken Sie auf der Entwurfsoberfläche auf die Schaltfläche **Anzeigen** .

     *Greetings.xaml.cs* wird geöffnet, der Cursor steht im `Button_Click`-Ereignis.

    ```csharp
    private void Button_Click_1(object sender, RoutedEventArgs e)
    {

    }
    ```

2. Geben Sie den folgenden Code ein:

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

3. Speichern Sie die Anwendung.

## <a name="debug-and-test-the-application"></a>Debuggen und Testen der Anwendung

Als Nächstes debuggen Sie die Anwendung, um nach Fehlern zu suchen und zu testen, ob beide Meldungsfelder ordnungsgemäß angezeigt werden. Die folgenden Anweisungen beschreiben, wie Sie den Debugger erstellen und starten. Lesen Sie jedoch später für weitere Informationen [Erstellen einer WPF-Anwendung (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) und [Debuggen von WPF](../../debugger/debugging-wpf.md).

### <a name="find-and-fix-errors"></a>Suchen und Beheben von Fehlern

In diesem Schritt suchen Sie den Fehler, den Sie zuvor verursacht haben, indem Sie den Namen der Datei *MainWindow.xaml* geändert haben.

#### <a name="start-debugging-and-find-the-error"></a>Starten des Debuggings und Suchen des Fehlers

1. Starten Sie den Debugger, indem Sie **Debuggen**, dann **Debugging starten**auswählen.

     ![Befehl "Debugging starten" im Menü "Debuggen"](../media/exploreide-startdebugging.png)

     Ein **Haltemodus**-Fenster wird angezeigt, und das **Ausgabe**-Fenster gibt an, dass eine IOException-Klasse aufgetreten ist: Cannot locate resource 'mainwindow.xaml' (Die Ressource „mainwindow.xaml“ kann nicht gefunden werden).

2. Beenden Sie den Debugger, indem Sie **Debuggen** > **Debuggen beenden** auswählen.

     ![Befehl "Debugging beenden" im Menü "Debuggen"](../media/exploreide-stopdebugging.png)

Zu Beginn dieser exemplarischen Vorgehensweise wurde *Mainwindow.xaml* in *Greetings.xaml* umbenannt. Da der Code jedoch weiterhin auf *Mainwindow.xaml* als Start-URI für die Anwendung verweist, kann das Projekt nicht gestartet werden.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Angeben von „Greetings.xaml“ als Start-URI

1. Öffnen Sie im **Projektmappen-Explorer**die Datei *App.xaml*.

2. Ändern Sie `StartupUri="MainWindow.xaml"` zu `StartupUri="Greetings.xaml"`, und speichern Sie dann die Änderungen.

Starten Sie den Debugger erneut (drücken Sie auf **F5**). Sie sollten das **Greetings**-Fenster der Anwendung sehen. Schließen Sie nun das Anwendungsfenster, um das Debuggen zu beenden.

### <a name="debug-with-breakpoints"></a>Debuggen mit Haltepunkten

Wenn Sie einige Haltepunkte hinzufügen, können Sie den Code während des Debuggens testen. Sie können Haltepunkte durch Auswählen von **Debuggen** > **Haltepunkt umschalten** hinzufügen, indem Sie am linken Rand des Editors neben die Codezeile klicken, in der die Unterbrechung stattfinden soll, oder indem Sie **F9** drücken.

#### <a name="add-breakpoints"></a>Hinzufügen von Haltepunkten

1. Öffnen Sie *Greetings.xaml.cs*, und wählen Sie die folgende Zeile aus: `MessageBox.Show("Hello.")`

2. Fügen Sie einen Haltepunkt hinzu, indem Sie im Menü **Debuggen**und dann **Haltepunkt umschalten**auswählen.

     ![Befehl "Haltepunkt umschalten" im Menü "Debuggen"](../media/exploreide-togglebreakpoint.png)

     Am äußeren linken Rand des Editorfensters wird ein roter Kreis neben der Codezeile angezeigt.

3. Wählen Sie folgende Zeile aus: `MessageBox.Show("Goodbye.")`.

4. Drücken Sie die Taste **F9**, um einen Haltepunkt hinzuzufügen, und drücken Sie anschließend **F5**, um das Debuggen zu starten.

5. Aktivieren Sie im Fenster **Greetings** das Optionsfeld **Hello** , und wählen Sie dann die Schaltfläche **Anzeigen** aus.

     Die Zeile wird `MessageBox.Show("Hello.")` gelb hervorgehoben. Am unteren Rand der IDE werden die Fenster "Auto", "Lokal" und "Überwachen" auf der linken Seite zusammengedockt, und die Fenster "Aufrufliste", "Haltepunkte", "Befehl", "Direkt" und "Ausgabe" werden auf der rechten Seite zusammengedockt.

6. Wählen Sie in der Menüleiste **Debuggen** > **Rücksprung** aus.

     Die Anwendung wird weiter ausgeführt, und ein Meldungsfeld mit dem Wort „Hello“ wird angezeigt.

7. Wählen Sie die Schaltfläche **OK** im Meldungsfeld, um es zu schließen.

8. Aktivieren Sie im Fenster **Greetings** das Optionsfeld **Goodbye** , und wählen Sie dann die Schaltfläche **Anzeigen** aus.

     Die Zeile wird `MessageBox.Show("Goodbye.")` gelb hervorgehoben.

9. Drücken Sie die Taste **F5**, um das Debuggen fortzusetzen. Wenn das Meldungsfeld angezeigt wird, wählen Sie die Schaltfläche **OK** im Meldungsfeld, um es zu schließen.

10. Schließen Sie das Anwendungsfenster, um das Debuggen zu beenden.

11. Wählen Sie in der Menüleiste **Debuggen** > **Alle Haltepunkte deaktivieren** aus.

### <a name="build-a-release-version-of-the-application"></a>Version der Anwendung erstellen

Nachdem Sie überprüft haben, dass alles funktioniert, können Sie einen Releasebuild der Anwendung vorbereiten.

1. Wählen Sie im Hauptmenü **Erstellen** > **Projektmappe bereinigen** aus, um Zwischendateien und Ausgabedateien zu löschen, die bei vorherigen Builds erstellt wurden. Dies ist nicht erforderlich, bereinigt jedoch die Ausgaben des Builddebugvorgangs.

     ![Befehl "Projektmappe bereinigen" im Menü "Erstellen"](../media/exploreide-cleansolution.png)

2. Ändern Sie die Build-Konfiguration für HelloWPFApp über das Dropdown-Steuerelement in der Symbolleiste (derzeit „Debug“) von **Debug** in **Release**.

     ![Standardsymbolleiste mit ausgewählter Release](../media/exploreide-releaseversion.png)

3. Erstellen Sie die Projektmappe, indem Sie auf **Erstellen** > **Projektmappe erstellen** klicken.

     ![Befehl "Projektmappe erstellen" im Menü "Erstellen"](../media/exploreide-buildsolution.png)

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Sie finden die *EXE*-Datei, die Sie erstellt haben, in Ihrer Projektmappe und im Projektverzeichnis (*...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="see-also"></a>Siehe auch

- [Produktivitätstipps](../../ide/productivity-tips-for-visual-studio.md)