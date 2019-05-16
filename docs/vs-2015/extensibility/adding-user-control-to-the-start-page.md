---
title: Hinzufügen eines Benutzersteuerelements zur Startseite | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1171197ba55c2fe3fa59ccc9ca918fa0c8f9e727
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699129"
---
# <a name="adding-user-control-to-the-start-page"></a>Hinzufügen eines Benutzersteuerelements zur Startseite
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht das Hinzufügen eines DLL-Verweises auf eine benutzerdefinierte Startseite. Im Beispiel wird ein Benutzersteuerelement mit der Lösung, das Benutzersteuerelement erstellt, und klicken Sie dann verweist auf die erstellte Assembly, die von der Startseite XAML-Datei hinzugefügt. Eine neue Registerkarte hostet das Benutzersteuerelement, das Funktionen als einfachen Webbrowser.  
  
 Sie können den gleichen Prozess verwenden, eine beliebige Assembly hinzufügen, die von einer XAML-Datei aufgerufen werden kann.  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>Ein WPF-Benutzersteuerelement hinzufügen zur Projektmappe  
 Fügen Sie zunächst ein Windows Presentation Foundation (WPF)-Benutzersteuerelement an die Startseite-Lösung.  
  
1. Erstellen Sie eine Startseite verwenden wir erstellt, [erstellen eine benutzerdefinierte Startseite](../extensibility/creating-a-custom-start-page.md).  
  
2. In **Projektmappen-Explorer**mit der rechten Maustaste auf die Projektmappe, klicken Sie auf **hinzufügen**, und klicken Sie dann auf **neues Projekt**.  
  
3. Im linken Bereich die **neues Projekt** Dialogfeld erweitern Sie entweder die **Visual Basic** oder **Visual C#-** Knoten, und klicken Sie auf **Windows**. Wählen Sie im mittleren Bereich **WPF-Benutzersteuerelementbibliothek**.  
  
4. Benennen Sie das Steuerelement `WebUserControl` , und klicken Sie dann auf **OK**.  
  
## <a name="implementing-the-user-control"></a>Das Benutzersteuerelement implementiert  
 Um ein WPF-Benutzersteuerelement zu implementieren, erstellen Sie die Benutzeroberfläche (UI) in XAML, und klicken Sie dann schreiben Sie die CodeBehind-Ereignisse in c# oder einer anderen .NET-Sprache zu.  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>Der XAML für das Benutzersteuerelement schreiben  
  
1. Öffnen Sie die XAML-Datei für das Benutzersteuerelement. In der \<Raster >-Element, das Steuerelement die folgenden Zeilendefinitionen hinzugefügt.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2. Auf dem hauptblatt `Grid` -Element, fügen Sie die folgenden neuen `Grid` -Element, das ein Textfeld zum Eingeben von Webadressen und eine Schaltfläche zum Festlegen der neuen Adresse enthält.  
  
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
  
3. Fügen Sie den folgenden Frames der obersten Ebene `Grid` Elements direkt hinter der `Grid` Element, das die Schaltfläche und ein Textfeld enthält.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4. Das folgende Beispiel zeigt die abgeschlossene XAML für das Benutzersteuerelement.  
  
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
  
#### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Die Code-Behind-Ereignisse für das Benutzersteuerelement schreiben  
  
1. Doppelklicken Sie im XAML-Designer auf die **Adresse festlegen** Schaltfläche, die Sie hinzugefügt, auf das Steuerelement haben.  
  
     Die Datei "UserControl1.cs" wird im Code-Editor geöffnet.  
  
2. Füllen Sie den SetButton_Click-Ereignishandler wie folgt aus.  
  
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
  
     Dieser Code legt fest, die Adresse der Webserver, die als Ziel für den Webbrowser in das Textfeld eingegeben wird. Wenn die Adresse nicht gültig ist, löst der Code einen Fehler aus.  
  
3. Sie müssen auch das Ereignis WebFrame_Navigated behandeln:  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4. Erstellen Sie die Projektmappe.  
  
## <a name="adding-the-user-control-to-the-start-page"></a>Hinzufügen des Benutzersteuerelements zur Startseite  
 Fügen Sie einen Verweis auf die neue Steuerelementbibliothek hinzu, um dieses Steuerelement in der Projektdatei der Startseite auf die Startseitenprojekt verfügbar zu machen. Anschließend können Sie das Steuerelement an das Starten der Seite "-XAML-Markup hinzufügen.  
  
1. In **Projektmappen-Explorer**, in dem Projekt Startseite mit der Maustaste **Verweise** , und klicken Sie dann auf **Verweis hinzufügen**.  
  
2. Auf der **Projekte** Registerkarte **WebUserControl** , und klicken Sie dann auf **OK**.  
  
3. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
    Erstellen der Projektmappe stellt das Benutzersteuerelement zur Verfügung IntelliSense für andere Dateien in der Projektmappe.  
  
   Um das Starten der Seite "-XAML-Markup des Steuerelements hinzuzufügen, fügen Sie einen Namespaceverweis auf die Assembly, und fügen Sie das Steuerelement auf der Seite.  
  
#### <a name="to-add-the-control-to-the-markup"></a>Das Markup des Steuerelements hinzu  
  
1. In **Projektmappen-Explorer**, öffnen Sie die Startseite XAML-Datei.  
  
2. In der **XAML** Bereich fügen Sie die folgende Namespacedeklaration hinzu, auf der obersten Ebene <xref:System.Windows.Controls.Grid> Element.  
  
   ```xml  
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
   ```  
  
3. In der **XAML** einen Bildlauf zum Bereich der \<Raster > Abschnitt.  
  
    Der Abschnitt enthält eine <xref:System.Windows.Controls.TabControl> Element in einem <xref:System.Windows.Controls.Grid> Element.  
  
4. Hinzufügen einer \<TabControl > mit einer \<TabItem >, der einen Verweis auf das Benutzersteuerelement enthält.  
  
   ```xml  
  
   <TabItem Header="Web" Height="Auto">  
       <vsc:UserControl1 />  
   </TabItem>  
  
   ```  
  
   Jetzt können Sie das Steuerelement testen.  
  
## <a name="testing-a-manually-created-custom-start-page"></a>Testen einer manuell erstellten benutzerdefinierten Startseite  
  
1. Kopieren der XAML-Datei und alle unterstützenden Textdateien oder Markup-Dateien, zu der **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\**  Ordner.  
  
2. Wenn Ihre Startseite verweist keine Steuerelemente oder Typen in Assemblys, die von Visual Studio nicht installiert sind, kopieren Sie die Assemblys, und fügen Sie sie in _Visual Studio-Installationsordner_**\Common7\IDE\ "Privateassemblies"\\**.  
  
3. Geben Sie an einer Visual Studio-Eingabeaufforderung **Devenv/rootsuffix Exp** um eine experimentelle Instanz von Visual Studio zu öffnen.  
  
4. Wechseln Sie in der experimentellen Instanz zu den **Extras / Optionen / Umgebung / Start** Seite, und wählen Sie die XAML-Datei aus der **Customize Start Page** Dropdownliste.  
  
5. Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
     Der benutzerdefinierten Startseite sollte angezeigt werden. Wenn Sie Dateien ändern möchten, müssen Sie die experimentelle Instanz schließen, nehmen Sie die Änderungen, kopieren und fügen Sie die geänderten Dateien und öffnen Sie erneut die experimentelle Instanz um die Änderungen anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [WPF-Container-Steuerelemente](https://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)   
 [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
