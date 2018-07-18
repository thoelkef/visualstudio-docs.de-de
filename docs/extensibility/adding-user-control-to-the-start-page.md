---
title: Hinzufügen des Benutzersteuerelements an die Startseite | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2bec2b4ab834eb55bd34a80f9e6a30931e3cd325
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104094"
---
# <a name="adding-user-control-to-the-start-page"></a>Hinzufügen des Benutzersteuerelements an die Startseite
In dieser exemplarischen Vorgehensweise wird gezeigt, wie einen DLL-Verweis auf eine benutzerdefinierte Startseite hinzufügen. Im Beispiel wird ein Benutzersteuerelement der Lösung auf das Benutzersteuerelement erstellt und anschließend verweist auf die erstellte Assembly aus der Startseite auf XAML-Datei hinzugefügt. Eine neue Registerkarte hostet das Benutzersteuerelement, das Funktionen, wie eine grundlegende Webbrowser.  
  
 Dasselbe Verfahren können Sie eine beliebige Assembly hinzufügen, die von einem XAML-Datei aufgerufen werden kann.  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>Ein WPF-Benutzersteuerelement hinzufügen der Projektmappe  
 Fügen Sie zunächst ein Windows Presentation Foundation (WPF)-Benutzersteuerelement der Startseite-Projektmappe.  
  
1.  Erstellen Sie eine Startseite mithilfe von erstellten [erstellen eine benutzerdefinierte Startseite](../extensibility/creating-a-custom-start-page.md).  
  
2.  In **Projektmappen-Explorer**mit der rechten Maustaste auf die Projektmappe, klicken Sie auf **hinzufügen**, und klicken Sie dann auf **neues Projekt**.  
  
3.  Im linken Bereich des der **neues Projekt** Dialogfeld erweitern Sie entweder die **Visual Basic** oder **Visual C#-** Knoten, und klicken Sie auf **Windows**. Wählen Sie im mittleren Bereich **WPF-Benutzersteuerelementbibliothek**.  
  
4.  Benennen Sie das Steuerelement `WebUserControl` , und klicken Sie dann auf **OK**.  
  
## <a name="implementing-the-user-control"></a>Implementieren des Benutzersteuerelements  
 Um ein WPF-Benutzersteuerelement zu implementieren, erstellen Sie die Benutzeroberfläche (UI) in XAML und Schreiben Sie dann die CodeBehind-Ereignisse in c# oder einer anderen .NET-Sprache.  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>Den XAML-Code für das Benutzersteuerelement schreiben  
  
1.  Öffnen Sie die Verwendung von XAML-Datei für das Benutzersteuerelement. In der \<Raster >-Element, das Steuerelement die folgenden Zeilendefinitionen hinzugefügt.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  Im Hauptfenster `Grid` Element, fügen Sie die folgenden neuen `Grid` -Element, das ein Textfeld zum Eingeben von Webadressen und eine Schaltfläche zum Festlegen der neuen Adresse enthält.  
  
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
  
3.  Fügen Sie den folgenden Frame auf der obersten Ebene `Grid` Element direkt nach der `Grid` Element, das die Schaltfläche und ein Textfeld enthält.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  Das folgende Beispiel zeigt den abgeschlossene XAML für das Benutzersteuerelement.  
  
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
  
#### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Der Code-Behind-Ereignisse für das Benutzersteuerelement schreiben  
  
1.  Doppelklicken Sie in der XAML-Designer auf die **Adresse festlegen** Schaltfläche, die Sie dem Steuerelement hinzugefügt.  
  
     Die Datei "UserControl1.cs" wird im Code-Editor geöffnet.  
  
2.  Füllen Sie den SetButton_Click-Ereignishandler wie folgt aus.  
  
    ```csharp  
    private void SetButton_Click(object sender, RoutedEventArgs e)  
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
  
     Dieser Code legt die Webadresse an, die als Ziel für den Webbrowser in das Textfeld eingegeben wird. Wenn die Adresse ungültig ist, löst der Code einen Fehler aus.  
  
3.  Sie müssen auch das WebFrame_Navigated Ereignis behandeln:  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  Erstellen Sie die Projektmappe.  
  
## <a name="adding-the-user-control-to-the-start-page"></a>Hinzufügen des Benutzersteuerelements an die Startseite  
 Fügen Sie einen Verweis auf die neue Steuerelementbibliothek hinzu, um dieses Steuerelement in der Projektdatei Startseite für das Startseitenprojekt verfügbar zu machen. Sie können dann starten Seite XAML-Markup des Steuerelements hinzufügen.  
  
1.  In **Projektmappen-Explorer**, das Startseitenprojekt Maustaste **Verweise** , und klicken Sie dann auf **Verweis hinzufügen**.  
  
2.  Auf der **Projekte** Registerkarte **WebUserControl** , und klicken Sie dann auf **OK**.  
  
3.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Beim Erstellen der Projektmappe stellt das Benutzersteuerelement zur Verfügung IntelliSense für andere Dateien in der Projektmappe.  
  
 Zum Starten des Seite XAML-Markup des Steuerelements hinzugefügt haben, fügen Sie einen Namespaceverweis auf die Assembly, platzieren Sie das Steuerelement auf der Seite.  
  
#### <a name="to-add-the-control-to-the-markup"></a>Das Markup das Steuerelement hinzu  
  
1.  In **Projektmappen-Explorer**, öffnen Sie die Startseite XAML-Datei.  
  
2.  In der **XAML** Bereich, fügen Sie die folgende Namespacedeklaration hinzu, auf der obersten Ebene <xref:System.Windows.Controls.Grid> Element.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  In der **XAML** Bereich einen Bildlauf zu der \<Raster > Abschnitt.  
  
     Der Abschnitt enthält eine <xref:System.Windows.Controls.TabControl> Element in einem <xref:System.Windows.Controls.Grid> Element.  
  
4.  Hinzufügen einer \<TabControl > mit einer \<TabItem >, der einen Verweis auf das Benutzersteuerelement enthält.  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 Jetzt können Sie das Steuerelement testen.  
  
## <a name="testing-a-manually-created-custom-start-page"></a>Testen einer manuell erstellten benutzerdefinierten Startseite  
  
1.  Kopieren der XAML-Datei, und alle unterstützenden Textdateien oder Markup, zu der **%USERPROFILE%\My Dateien\Visual Studio 2015\StartPages\\**  Ordner.  
  
2.  Wenn Ihre Startseite verweist auf keine Steuerelemente oder die Typen in Assemblys, die von Visual Studio nicht installiert sind, kopieren Sie die Assemblys, und fügen Sie sie in * Visual Studio-Installation Ordner ***\Common7\IDE\PrivateAssemblies\\** .  
  
3.  Geben Sie an einer Visual Studio-Eingabeaufforderung **Devenv /rootsuffix Exp** eine experimentelle Instanz von Visual Studio zu öffnen.  
  
4.  Wechseln Sie in der experimentellen Instanz zu den **Extras / Optionen / Umgebung / Start** Seite und wählen Sie die XAML-Datei aus der **Startseite anpassen** Dropdownliste.  
  
5.  Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
     Ihre benutzerdefinierte Startseite angezeigt werden sollen. Wenn Sie Dateien ändern möchten, müssen Sie die experimentelle Instanz schließen, nehmen Änderungen vor kopieren und fügen Sie die geänderten Dateien und öffnen Sie dann erneut die experimentelle Instanz um die Änderungen anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [WPF-Containersteuerelemente](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)