---
title: "Hinzuf&#252;gen des Benutzersteuerelements zur Startseite | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Starten Sie die Seite dll"
  - "benutzerdefinierte Startseite"
  - "Seitenassembly beginnen"
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Hinzuf&#252;gen des Benutzersteuerelements zur Startseite
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht, wie einen DLL\-Verweis auf eine benutzerdefinierte Startseite hinzufügen. Das Beispiel fügt ein Benutzersteuerelement der Lösung auf das Benutzersteuerelement erstellt und die erstellte Assembly von der Startseite XAML\-Datei verweist. Eine neue Registerkarte hostet das Benutzersteuerelement, das als grundlegender Webbrowser funktioniert.  
  
 Den gleichen Prozess können Sie eine beliebige Assembly hinzufügen, die aus einer XAML\-Datei aufgerufen werden können.  
  
## Die Projektmappe hinzufügen ein WPF\-Benutzersteuerelement  
 Der Lösung "Startseite" zuerst ein Windows Presentation Foundation \(WPF\)\-Benutzersteuerelement hinzugefügt.  
  
1.  Erstellen Sie eine Startseite mit in erstellten [Erstellen einer benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md).  
  
2.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Projektmappe, klicken Sie auf **Hinzufügen** und dann auf **Neues Projekt**.  
  
3.  Im linken Bereich von der **Neues Projekt** Dialogfeld erweitern Sie entweder die **Visual Basic** oder **Visual C\#\-** Knoten, und klicken Sie auf **Windows**. Wählen Sie im mittleren Bereich **WPF\-Benutzersteuerelementbibliothek**.  
  
4.  Name des Steuerelements `WebUserControl` und klicken Sie dann auf **OK**.  
  
## Implementieren des Benutzersteuerelements  
 Um ein WPF\-Benutzersteuerelement zu implementieren, erstellen Sie die Benutzeroberfläche \(UI\) in XAML, und Schreiben Sie dann die CodeBehind\-Ereignisse in c\# oder einer anderen.  
  
#### Das XAML für das Benutzersteuerelement schreiben.  
  
1.  Öffnen Sie die XAML\-Datei für das Benutzersteuerelement. Fügen Sie die folgenden Zeilendefinitionen in das \< Grid \>\-Element auf das Steuerelement.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  Im Hauptfenster `Grid` Element hinzufügen die folgenden neuen `Grid` \-Element, das ein Textfeld zum Eingeben von Webadressen und eine Schaltfläche zum Festlegen der neuen Adresse enthält.  
  
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
  
3.  Fügen Sie den folgenden Frame auf der obersten Ebene `Grid` Element direkt nach dem `Grid` \-Element, das die Schaltfläche und das Textfeld enthält.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  Das folgende Beispiel zeigt das abgeschlossene XAML für das Benutzersteuerelement.  
  
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
  
#### Die CodeBehind\-Ereignisse für das Benutzersteuerelement schreiben  
  
1.  Doppelklicken Sie in der XAML\-Designer auf die **Adresse festlegen** Schaltfläche, die Sie dem Steuerelement hinzugefügt.  
  
     Die Datei "UserControl1.cs" wird im Code\-Editor geöffnet.  
  
2.  Füllen Sie den SetButton\_Click\-Ereignishandler wie folgt aus.  
  
    ```c#  
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
  
     Dieser Code legt die Webadresse, die als Ziel für den Webbrowser in das Textfeld eingegeben wird. Wenn die Adresse nicht gültig ist, löst der Code einen Fehler.  
  
3.  Sie müssen auch das WebFrame\_Navigated\-Ereignis behandeln:  
  
    ```c#  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  Erstellen Sie die Projektmappe.  
  
## Hinzufügen des Benutzersteuerelements zur Startseite  
 Um dieses Steuerelement in der Projektdatei für die Startseite des Projekts Startseite verfügbar zu machen, fügen Sie einen Verweis auf die neue Steuerelementbibliothek hinzu. Anschließend können Sie das Steuerelement starten Seite XAML\-Markup hinzufügen.  
  
1.  In **Projektmappen\-Explorer**, Startseite im Projekt mit der rechten Maustaste **Verweise** und klicken Sie dann auf **Verweis hinzufügen**.  
  
2.  Auf der **Projekte** Registerkarte **WebUserControl** und klicken Sie dann auf **OK**.  
  
3.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Erstellen der Projektmappe wird das Benutzersteuerelement verfügbar für IntelliSense für andere Dateien in der Projektmappe.  
  
 Zum Hinzufügen des Steuerelements zum Starten des Seite XAML\-Markup einen Namespaceverweis auf die Assembly hinzufügen, bevor Sie das Steuerelement auf der Seite.  
  
#### Das Markup des Steuerelements hinzu  
  
1.  In **Projektmappen\-Explorer**, öffnen Sie die Startseite XAML\-Datei.  
  
2.  In der **XAML** Bereich, fügen Sie die folgende Namespacedeklaration auf der obersten Ebene <xref:System.Windows.Controls.Grid> Element.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  In der **XAML** Bereich einen Bildlauf zum Abschnitt \< Grid \>.  
  
     Der Abschnitt enthält ein <xref:System.Windows.Controls.TabControl> Element in einer <xref:System.Windows.Controls.Grid> Element.  
  
4.  Fügen Sie ein \< TabControl \>\-Element, das ein \< TabItem \> enthält, die einen Verweis auf das Benutzersteuerelement enthält.  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 Jetzt können Sie das Steuerelement testen.  
  
## Testen eine manuell erstellte benutzerdefinierte Startseite  
  
1.  Kopieren Sie die XAML\-Datei, und alle unterstützenden Textdateien oder Markup\-Dateien, zu der **%USERPROFILE%\\My Documents\\Visual Studio 2015\\StartPages\\** Ordner.  
  
2.  Wenn Ihre Startseite verweist keine Steuerelemente oder Typen in Assemblys, die von Visual Studio nicht installiert sind, kopieren Sie die Assemblys, und fügen Sie sie in *Visual Studio\-Installationsordner***\\Common7\\IDE\\PrivateAssemblies\\**.  
  
3.  Geben Sie an einer Visual Studio\-Eingabeaufforderungsfenster **Devenv\/rootsuffix Exp** um eine experimentelle Instanz von Visual Studio zu öffnen.  
  
4.  Wechseln Sie in der experimentellen Instanz, zu der **Extras \/ Optionen \/ Umgebung \/ Start** Seite und wählen Sie die XAML\-Datei aus der **Startseite anpassen** Dropdown\-Liste.  
  
5.  Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
     Eine benutzerdefinierte Startseite angezeigt werden sollen. Wenn Sie Dateien ändern möchten, müssen Sie schließen Sie die experimentelle Instanz ändern, kopieren und fügen Sie die geänderten Dateien und öffnen Sie dann erneut die experimentelle Instanz um die Änderungen anzuzeigen.  
  
## Siehe auch  
 [WPF\-Containersteuerelemente](http://msdn.microsoft.com/de-de/a0177167-d7db-4205-9607-8ae316952566)   
 [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)