---
title: Überprüfen von XAML-Eigenschaften beim Debuggen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: c48e3623ba073d13a2b9ce2309b47a65ef45befb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="inspect-xaml-properties-while-debugging"></a>Überprüfen von XAML-Eigenschaften beim Debuggen
Sie erhalten eine Echtzeitansicht Ihres ausgeführten XAML-Codes mit dem **Live Visual Tree** und **Live Property Explorer**. Diese Tools bieten Ihnen eine Strukturansicht der Benutzeroberflächenelemente Ihrer ausgeführten XAML-Anwendung, und Sie zeigen Ihnen Runtime-Eigenschaften der von Ihnen ausgewählten Benutzeroberflächenelemente an.  
  
 Sie können diese Tools in den folgenden Konfigurationen verwenden:  
  
|App-Typ|Betriebssystem und Tools|  
|-----------------|--------------------------------|  
|Windows Presentation Foundation-Anwendungen (4.0 und höher)|Windows 7 und höher|  
|Universelle Windows-Apps|Windows 10 und höher, mit der [Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Elemente in Visuelle Echtzeitstruktur  
 Wir beginnen mit einer sehr einfachen WPF-Anwendung, die eine Listenansicht und eine Schaltfläche verfügt. Bei jedem Klick auf die Schaltfläche wird der Liste ein anderes Element hinzugefügt. Gerade nummerierte Elemente sind grau, und ungerade nummerierte Elemente sind gelb.  
  
 Erstellen einer neuen C#-WPF-Anwendung (Datei > Neu > Projekt, und klicken Sie dann select C#- und suchen Sie WPF-Anwendung). Nennen Sie sie **TestXAML**.  
  
 Ändern Sie „MainWindow.xaml“ wie folgt:  
  
```xaml  
<Window x:Class="TestXAML.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:TestXAML"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 Fügen Sie der Datei „MainWindow.xaml.cs“ den folgenden Befehlshandler hinzu:  
  
```csharp 
int count;

private void button_Click(object sender, RoutedEventArgs e)  
{  
    ListBoxItem item = new ListBoxItem();  
    item.Content = "Item" + ++count;  
    if (count % 2 == 0)  
    {  
        item.Background = Brushes.LightGray;  
    }  
    else  
    {  
        item.Background = Brushes.LightYellow;  
    }  
    listBox.Items.Add(item);  
}  
```  
  
 Erstellen Sie das Projekt, und starten Sie das Debugging. (Bei der Buildkonfiguration muss es sich um „Debug“ und nicht um „Release“ handeln. Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen zu Buildkonfigurationen](../ide/understanding-build-configurations.md).)  
  
 Wenn das Fenster wird angezeigt, klicken Sie auf die **Element hinzufügen** Schaltfläche ein paar Mal. Folgendes sollte angezeigt werden:  
  
 ![Im Hauptfenster der app](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")  
  
 Öffnen Sie jetzt die **Live Visual Tree** Fenster (**Debuggen > Windows > Live Visual Tree**, oder suchen Sie es auf der linken Seite der IDE). Weg von der verankerten Position ziehen, sodass dieses Fenster gesucht werden kann und die **Live Eigenschaften** Fenster nebeneinander angezeigt werden. In der **Live Visual Tree** Fenster, erweitern Sie die **ContentPresenter** Knoten. Es sollte Knoten für die Schaltfläche und das Listenfeld enthalten. Erweitern Sie das Listenfeld (und dann die **ScrollContentPresenter** und **ItemsPresenter**) um die Listenfeldelemente zu suchen. Das Fenster sieht wie folgt aus:  
  
 ![ListBoxItems in Live Visual Tree](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree ListBoxItems")  
  
 Kehren Sie zum Anwendungsfenster zurück, und fügen Sie ein paar weitere Elemente hinzu. Daraufhin sollten mehr Listenfeldelemente angezeigt werden die **Live Visual Tree**.  
  
 Jetzt sehen wir uns die Eigenschaften von einem der Listenfeldelemente. Wählen Sie das erste Listenfeldelement in der **Live Visual Tree** , und klicken Sie auf die **Eigenschaften anzeigen** auf der Symbolleiste auf das Symbol. Die **Live Property Explorer** sollte angezeigt werden. Beachten Sie, dass die **Content** Feld ist "Item1" handelt, und die **Hintergrund** Feld **#ffffffe0** (hellgelb). Wechseln Sie zurück zu den **Live Visual Tree** , und wählen Sie das zweite Listenfeldelement. Die **Live Property Explorer** sollte angezeigt werden, die **Content** Feld ist "Element2", und die **Hintergrund** Feld ist **#ffd3d3d3** (hellgrau ).  
  
 Die tatsächliche Struktur der XAML weist eine Menge von Elementen, denen Sie möglicherweise nicht direkt interessiert sind, und wenn Sie den Code nicht gut kennen müssen Sie möglicherweise Navigation in der Struktur zum Suchen, wonach Sie suchen. Damit die **Live Visual Tree** verfügt über mehrere Möglichkeiten, mit denen Sie Benutzeroberfläches der Anwendung verwenden, um Ihnen bei der Suche nach dem Element Sie untersuchen möchten.  
  
 **Aktivieren Sie die Auswahl in der laufenden Anwendung**. Sie können diesen Modus aktivieren, wenn Sie die Schaltfläche ganz links auf der **Live Visual Tree** Symbolleiste. Dieser Modus aktiviert ist, können Sie ein Benutzeroberflächenelement in der Anwendung auswählen und die **Live Visual Tree** (und die **Live Property Viewer**) automatisch aktualisiert, um den Knoten in der Struktur für dieses Element anzuzeigen. und seine Eigenschaften.  
  
 **Anzeigen der Layout-Adorner in der laufenden Anwendung**. Sie können diesen Modus aktivieren, wenn Sie die Schaltfläche auswählen, die sich direkt rechts neben der Schaltfläche „Auswahl aktivieren“ befindet. Wenn **Anzeigen der Layout-Adorner** ist, wird das Anwendungsfenster horizontale und vertikale Linien entlang der Grenzen des ausgewählten Objekts angezeigt, damit Sie sehen, was sie, sowie die Ränder Rechtecke entspricht. Aktivieren Sie z. B. sowohl **Auswahl aktivieren** und **Layout anzeigen** , und wählen die **Element hinzufügen** Textblock in der Anwendung. Daraufhin sollte den Block Textknoten in der **Live Visual Tree** und die Textblockeigenschaften der **Live Property Viewer**, sowie die horizontalen und vertikalen Linien auf den Grenzen des Textblocks.  
  
 ![LivePropertyViewer in DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **Vorschau für Auswahl**. Sie können diesen Modus aktivieren, indem Sie die dritte Schaltfläche von links auf der visuellen Echtzeitstruktur-Symbolleiste auswählen. Dieser Modus zeigt die XAML an, in der das Element deklariert wurde, wenn Sie über Zugriff auf den Quellcode der Anwendung verfügen. Wählen Sie **Auswahl aktivieren** und **Vorschau für Auswahl**, und wählen Sie dann die Schaltfläche mit den in der testanwendung. Die Datei „MainWindow.xaml“ wird in Visual Studio geöffnet, und der Cursor wird auf der Zeile platziert, auf der die Schaltfläche definiert ist.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Verwenden von XAML-Tools mit ausgeführten Anwendungen  
 Sie können diese XAML-Tools verwenden, selbst wenn Sie nicht über den Quellcode verfügen. Wenn Sie eine ausgeführte XAML-Anwendung anfügen, können Sie die **Live Visual Tree** auf den Benutzeroberflächenelementen der Anwendung zu. Hier ist ein Beispiel unter Verwendung der WPF-testanwendung an, der wir zuvor verwendet.  
  
1.  Starten Sie die **TestXaml** Anwendung in der Releasekonfiguration. Sie können nicht Anfügen an einen Prozess, der ausgeführt wird, in einem **Debuggen** Konfiguration.  
  
2.  Öffnen Sie eine zweite Instanz von Visual Studio, und klicken Sie auf **Debuggen > an den Prozess anhängen**. Suchen **TestXaml.exe** in der Liste der verfügbaren Prozesse, und klicken Sie auf **Anfügen**.  
  
3.  Die Anwendung wird ausgeführt.  
  
4.  Öffnen Sie in der zweiten Instanz von Visual Studio, die **Live Visual Tree** (**Debuggen > Windows > Live Visual Tree**). Daraufhin sollte die **TestXaml** Elemente der Benutzeroberfläche, und Sie sollten in der Lage, die sie bearbeiten können, während die Anwendung direkt Debuggen sein.