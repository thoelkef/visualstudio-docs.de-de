---
title: Überprüfen von XAML-Eigenschaften beim Debuggen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 282b93ac9f04f5e547567e8380e65826f433ba2d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282255"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Überprüfen von XAML-Eigenschaften beim Debuggen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie erhalten eine Echtzeitansicht Ihres ausgeführten XAML-Codes mit dem **Live Visual Tree** und **Live Property Explorer**. Diese Tools bieten Ihnen eine Strukturansicht der Benutzeroberflächenelemente Ihrer ausgeführten XAML-Anwendung, und Sie zeigen Ihnen Runtime-Eigenschaften der von Ihnen ausgewählten Benutzeroberflächenelemente an.  
  
 Sie können diese Tools in den folgenden Konfigurationen verwenden:  
  
|App-Typ|Betriebssystem und Tools|  
|-----------------|--------------------------------|  
|Windows Presentation Foundation-Anwendungen (4.0 und höher)|Windows 7 und höher|  
|Windows Store- und Windows Phone 8.1-Apps|Windows 10 und höher, mit der [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
|Universelle Windows-Apps|Windows 10 und höher, mit der [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Elemente in Visuelle Echtzeitstruktur  
 Wir beginnen mit einer sehr einfachen WPF-Anwendung, die über eine Listenansicht und eine Schaltfläche verfügt. Bei jedem Klick auf die Schaltfläche wird der Liste ein anderes Element hinzugefügt. Gerade nummerierte Elemente sind grau, und ungerade nummerierte Elemente sind gelb.  
  
 Erstellen Sie eine neue C#-WPF-Anwendung (wählen Sie „Datei“, „Neu“, „Projekt“ aus, und wählen Sie dann C# aus, und suchen Sie nach der WPF-Anwendung). Nennen Sie sie **TestXAML**.  
  
 Ändern Sie „MainWindow.xaml“ wie folgt:  
  
```xaml  
<Window x:Class="WpfApplication1.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:WpfApplication1"  
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
  
 Erstellen Sie das Projekt, und starten Sie das Debugging. (Bei der Buildkonfiguration muss es sich um „Debug“ und nicht um „Release“ handeln. Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md).)  
  
 Wenn das Fenster angezeigt wird, klicken Sie auf die **Element hinzufügen** Schaltfläche ein paar Mal. Folgendes sollte angezeigt werden:  
  
 ![Hauptfenster der app](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")  
  
 Öffnen Sie nun die **Live Visual Tree** Fenster (**Debuggen / Windows / visuelle Echtzeitstruktur**, oder suchen sie auf der linken Seite der IDE). Ziehen Sie ihn von der verankerten Position dieses Fenster gesucht werden kann und die **Live-Eigenschaften** Fenster nebeneinander. In der **Live Visual Tree** Fenster, erweitern Sie die **ContentPresenter** Knoten. Es sollte Knoten für die Schaltfläche und das Listenfeld enthalten. Erweitern Sie im Listenfeld (und klicken Sie dann die **ScrollContentPresenter** und **ItemsPresenter**) auf der Liste Listenfeldelemente zu suchen. Das Fenster sieht wie folgt aus:  
  
 ![ListBoxItems in der visuellen Echtzeitstruktur](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")  
  
 Kehren Sie zum Anwendungsfenster zurück, und fügen Sie ein paar weitere Elemente hinzu. Daraufhin sollten mehr Listenfeldelemente angezeigt werden die **Live Visual Tree**.  
  
 Nun schauen wir uns die Eigenschaften von einem der Listenfeldelemente an. Wählen Sie das erste Listenfeldelement in die **Live Visual Tree** , und klicken Sie auf die **Eigenschaften anzeigen** auf der Symbolleiste auf das Symbol. Die **Live Property Explorer** sollte angezeigt werden. Beachten Sie, dass die **Content** Feld ist "Item1", und die **Hintergrund** Feld **#ffffffe0** (hellgelb). Wechseln Sie zurück zu den **Live Visual Tree** , und wählen Sie das zweite Listenfeldelement. Die **Live Property Explorer** sollte angezeigt werden, die die **Content** Feld ist "Item2" lautet, und die **Hintergrund** Feld **#ffd3d3d3** (hellgrau ).  
  
 Die tatsächliche Struktur der XAML weist eine Menge Elemente auf, an denen Sie möglicherweise nicht direkt interessiert sind. Wenn Sie sich darüber hinaus nicht gut mit dem Code auskennen, ist die Navigation in der Struktur zum Suchen des gewünschten Elements möglicherweise kompliziert. Daher **Live Visual Tree** verfügt über mehrere Möglichkeiten, mit denen Sie Benutzeroberfläches der Anwendung verwenden, um das Element zu finden, Sie untersuchen möchten.  
  
 **Aktivieren Sie die Auswahl in der ausgeführten Anwendung**. Sie können diesen Modus aktivieren, wenn Sie die Schaltfläche ganz links auf die **Live Visual Tree** Symbolleiste. Dieser Modus aktiviert, können Sie ein Element der Benutzeroberfläche auswählen, in der Anwendung und die **Live Visual Tree** (und die **Live Property Viewer**) automatisch aktualisiert, um den Knoten in der Struktur entspricht, die zu diesem Element anzuzeigen und dessen Eigenschaften.  
  
 **Anzeigen von Layout-Adorner in der ausgeführten Anwendung**. Sie können diesen Modus aktivieren, wenn Sie die Schaltfläche auswählen, die sich direkt rechts neben der Schaltfläche „Auswahl aktivieren“ befindet. Wenn **Anzeigen der Layout-Adorner** aktiviert ist, wird das Anwendungsfenster horizontale und vertikale Linien entlang der Grenzen des ausgewählten Objekts angezeigt, damit Sie sehen, was sie sowie Rechtecke, die die Ränder, entspricht. Aktivieren Sie z. B. sowohl **Auswahl aktivieren** und **Layout anzeigen** , und wählen die **Element hinzufügen** Textblock in der Anwendung. Daraufhin sollte die Block-Textknoten in die **Live Visual Tree** und die Textblockeigenschaften die **Live Property Viewer**, sowie die horizontalen und vertikalen Linien auf den Grenzen des Textblocks.  
  
 ![LivePropertyViewer in DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")  
  
 **Vorschau für Auswahl**. Sie können diesen Modus aktivieren, indem Sie die dritte Schaltfläche von links auf der visuellen Echtzeitstruktur-Symbolleiste auswählen. Dieser Modus zeigt die XAML an, in der das Element deklariert wurde, wenn Sie über Zugriff auf den Quellcode der Anwendung verfügen. Wählen Sie **Auswahl aktivieren** und **Vorschau für Auswahl**, und wählen Sie dann die Schaltfläche mit den in der testanwendung. Die Datei „MainWindow.xaml“ wird in Visual Studio geöffnet, und der Cursor wird auf der Zeile platziert, auf der die Schaltfläche definiert ist.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Verwenden von XAML-Tools mit ausgeführten Anwendungen  
 Sie können diese XAML-Tools sogar dann verwenden, wenn Sie nicht über den Quellcode verfügen. Wenn eine Anfügung an eine ausgeführte XAML-Anwendung können Sie die **Live Visual Tree** auf die Elemente der Benutzeroberfläche der Anwendung zu. Im Folgenden finden Sie ein Beispiel unter Verwendung derselben WPF-Testanwendung, die wir zuvor verwendet haben.  
  
1.  Starten Sie den **TestXaml** Anwendung in der Releasekonfiguration. Sie können nicht angefügt werden an einen Prozess, der ausgeführt wird, in einem **Debuggen** Konfiguration.  
  
2.  Öffnen Sie eine zweite Instanz von Visual Studio, und klicken Sie auf **Debuggen / an den Prozess anhängen**. Suchen **TestXaml.exe** in der Liste der verfügbaren Prozesse, und klicken Sie auf **Anfügen**.  
  
3.  Die Anwendung wird ausgeführt.  
  
4.  In der zweiten Instanz von Visual Studio, öffnen Sie die **Live Visual Tree** (**Debuggen / Windows / visuelle Echtzeitstruktur**). Daraufhin sollte die **TestXaml** UI-Elemente, und Sie sollten in der Lage, die sie bearbeiten, wie die Anwendung direkt Debuggen dabei sein.



