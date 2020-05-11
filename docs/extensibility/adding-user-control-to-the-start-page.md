---
title: Hinzufügen von Benutzersteuerelementen zur Startseite | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b426cfbbfca2e301797644a1fc73f188054d0cfa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740129"
---
# <a name="add-user-control-to-the-start-page"></a>Hinzufügen von Benutzersteuerelementen zur Startseite

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie einer benutzerdefinierten Startseite einen DLL-Verweis hinzufügen. Im Beispiel wird der Projektmappe ein Benutzersteuerelement hinzugefügt, das Benutzersteuerelement erstellt und dann auf die erstellte Assembly aus der *.xaml-Datei* Startseite verwiesen. Eine neue Registerkarte hostet das Benutzersteuerelement, das als einfacher Webbrowser fungiert.

Sie können denselben Prozess verwenden, um eine assembly hinzuzufügen, die aus einer *.xaml-Datei* aufgerufen werden kann.

## <a name="add-a-wpf-user-control-to-the-solution"></a>Hinzufügen eines WPF-Benutzersteuerelements zur Lösung

Fügen Sie zunächst der Lösung "Startseite" ein Windows Presentation Foundation (WPF)-Benutzersteuerelement hinzu.

1. Erstellen Sie eine Startseite, indem Sie sie verwenden, indem Sie unter [Erstellen einer benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md)erstellt haben.

2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf die Projektmappe, klicken Sie auf **Hinzufügen**, und dann auf **Neues Projekt**.

3. Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** entweder den Knoten **Visual Basic** oder **Visual C,** und klicken Sie auf **Windows**. Wählen Sie im mittleren Bereich **die WPF-Benutzersteuerungsbibliothek**aus.

4. Benennen Sie `WebUserControl` das Steuerelement, und klicken Sie dann auf **OK**.

## <a name="implement-the-user-control"></a>Implementieren des Benutzersteuerelements

Um ein WPF-Benutzersteuerelement zu implementieren, erstellen Sie die Benutzeroberfläche (UI) in XAML, und schreiben Sie dann die CodeBehind-Ereignisse in C- oder einer anderen .NET-Sprache.

### <a name="to-write-the-xaml-for-the-user-control"></a>So schreiben Sie das XAML für das Benutzersteuerelement

1. Öffnen Sie die XAML-Datei für das Benutzersteuerelement. Fügen `<Grid>` Sie im Element dem Steuerelement die folgenden Zeilendefinitionen hinzu.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. Fügen Sie `<Grid>` im Hauptelement `<Grid>` das folgende neue Element hinzu, das ein Textfeld zum Eingeben von Webadressen und eine Schaltfläche zum Festlegen der neuen Adresse enthält.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. Fügen Sie den folgenden Frame `<Grid>` dem Element `<Grid>` der obersten Ebene direkt nach dem Element hinzu, das die Schaltfläche und das Textfeld enthält.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Das folgende Beispiel zeigt das abgeschlossene XAML für das Benutzersteuerelement.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>So schreiben Sie die CodeBehind-Ereignisse für das Benutzersteuerelement

1. Doppelklicken Sie im XAML-Designer auf die Schaltfläche **Adresse festlegen,** die Sie dem Steuerelement hinzugefügt haben.

    Die *UserControl1.cs* Datei wird im Code-Editor geöffnet.

2. Füllen Sie den SetButton_Click Ereignishandler wie folgt aus.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    Dieser Code legt die Webadresse, die im Textfeld eingegeben wird, als Ziel für den Webbrowser fest. Wenn die Adresse ungültig ist, löst der Code einen Fehler aus.

3. Sie müssen auch das WebFrame_Navigated-Ereignis behandeln:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Erstellen Sie die Projektmappe.

## <a name="add-the-user-control-to-the-start-page"></a>Hinzufügen des Benutzersteuerelements zur Startseite

Um dieses Steuerelement für das Projekt Startseite verfügbar zu machen, fügen Sie in der Projektdatei Startseite einen Verweis auf die neue Steuerelementbibliothek hinzu. Anschließend können Sie das Steuerelement dem XAML-Markup Startseite hinzufügen.

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Referenzen,** und klicken Sie dann auf **Referenz hinzufügen**.

2. Wählen Sie auf der Registerkarte **Projekte** **WebUserControl** aus, und klicken Sie dann auf **OK**.

3. Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

    Durch das Erstellen der Lösung wird das Benutzersteuerelement für IntelliSense für andere Dateien in der Lösung verfügbar.

    Um das Steuerelement zum XAML-Markup Startseite hinzuzufügen, fügen Sie der Assembly einen Namespaceverweis hinzu, und fügen Sie das Steuerelement dann auf der Seite ab.

### <a name="to-add-the-control-to-the-markup"></a>So fügen Sie das Steuerelement zum Markup hinzu

1. Öffnen Sie im **Projektmappen-Explorer**die Startseite *.xaml-Datei.*

2. Fügen Sie im **XAML-Bereich** dem Element der <xref:System.Windows.Controls.Grid> obersten Ebene die folgende Namespacedeklaration hinzu.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. Scrollen Sie im **XAML-Bereich** zum \<Abschnitt Grid>.

    Der Abschnitt <xref:System.Windows.Controls.TabControl> enthält ein <xref:System.Windows.Controls.Grid> Element in einem Element.

4. Fügen \<Sie ein TabControl->-Element hinzu, das einen \<TabItem-> enthält, der einen Verweis auf das Benutzersteuerelement enthält.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Jetzt können Sie das Steuerelement testen.

## <a name="test-a-manually-created-custom-start-page"></a>Testen einer manuell erstellten benutzerdefinierten Startseite

1. Kopieren Sie Ihre XAML-Datei und alle unterstützenden Textdateien oder Markupdateien in den Ordner *%USERPROFILE%-Meine Dokumente, Visual Studio 2015, StartPages.\\ *

2. Wenn Ihre Startseite auf Steuerelemente oder Typen in Assemblys verweist, die nicht von Visual Studio installiert sind, kopieren Sie die Assemblys, und fügen Sie sie dann in den _Visual Studio-Installationsordner_**"Common7" und "PrivateAssemblies"\\**ein.

3. Geben Sie an einer Visual Studio-Eingabeaufforderung **devenv /rootsuffix Exp** ein, um eine experimentelle Instanz von Visual Studio zu öffnen.

4. Wechseln Sie in der **Tools** > experimentellen Instanz zur Seite "Tools**Options** > **Environment** > **Startup"** und wählen Sie Ihre XAML-Datei aus der Dropdown-Liste Startseite **anpassen** aus.

5. Klicken Sie im Menü **Ansicht** auf **Startseite**.

    Ihre benutzerdefinierte Startseite sollte angezeigt werden. Wenn Sie Dateien ändern möchten, müssen Sie die experimentelle Instanz schließen, die Änderungen vornehmen, die geänderten Dateien kopieren und einfügen und dann die experimentelle Instanz erneut öffnen, um die Änderungen anzuzeigen.

## <a name="see-also"></a>Weitere Informationen

- [WPF-Containersteuerelemente](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
