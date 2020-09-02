---
title: Hinzufügen von Visual Studio-Befehlen zu einer Start Seite | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a2042ef9a96eed99636ea0a2f5f09d99cd35ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699150"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Hinzufügen von Visual Studio-Befehlen zu einer Startseite
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine benutzerdefinierte Startseite erstellen, können Sie Ihr Visual Studio-Befehle hinzufügen. In diesem Dokument werden die verschiedenen Möglichkeiten erläutert, Visual Studio-Befehle auf einer Startseite an XAML-Objekte zu binden.  
  
 Weitere Informationen zu Befehlen in XAML finden Sie unter [Befehls Übersicht](https://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81) .  
  
## <a name="adding-commands-from-the-command-well"></a>Hinzufügen von Befehlen aus der Befehlszeile  
 Auf der Startseite, die beim [Erstellen einer benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md) erstellt wurde <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> , wurden die Namespaces und wie folgt hinzugefügt.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Fügen Sie aus dem AssemblyMicrosoft.VisualStudio.Shell.Immutable.11.0.dll einen weiteren Namespace für Microsoft. VisualStudio. Shell hinzu. (Möglicherweise müssen Sie im Projekt einen Verweis auf diese Assembly hinzufügen.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Sie können den- `vscom:` Alias verwenden, um Visual Studio-Befehle an XAML-Steuerelemente auf der Seite zu binden, indem Sie die- <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Eigenschaft des Steuer Elements auf festlegen `vscom:VSCommands.ExecuteCommand` . Anschließend können Sie die- <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> Eigenschaft auf den Namen des auszuführenden Befehls festlegen, wie im folgenden Beispiel gezeigt.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
> Der `x:` Alias, der sich auf das XAML-Schema bezieht, ist am Anfang aller Befehle erforderlich.  
  
 Sie können den Wert der- `Command` Eigenschaft auf einen beliebigen Befehl festlegen, auf den über das **Befehls** Fenster zugegriffen werden kann. Eine Liste der verfügbaren Befehle finden Sie unter [Visual Studio-Befehls Aliase](../ide/reference/visual-studio-command-aliases.md).  
  
 Wenn für den hinzu zufügenden Befehl ein zusätzlicher Parameter erforderlich ist, können Sie ihn dem Wert der-Eigenschaft hinzufügen `CommandParameter` . Trennen Sie Parameter von Befehlen mithilfe von Leerzeichen, wie im folgenden Beispiel gezeigt.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Aufrufen von Erweiterungen aus der Befehlszeile  
 Sie können Befehle aus registrierten VSPackages mithilfe derselben Syntax, die zum Abrufen anderer Visual Studio-Befehle verwendet wird, abrufen. Wenn beispielsweise ein installiertes VSPackage dem Menü **Ansicht** einen **Startseiten** Befehl hinzufügt, können Sie diesen Befehl durch Festlegen von `CommandParameter` auf Abrufen `View.HomePage` .  
  
> [!NOTE]
> Wenn Sie einen Befehl aufrufen, der einem VSPackage zugeordnet ist, muss das Paket geladen werden, wenn der Befehl aufgerufen wird.  
  
## <a name="adding-commands-from-assemblies"></a>Fügen von Befehlen aus Assemblys  
 Zum Aufrufen eines Befehls aus einer Assembly oder zum Zugreifen auf Code in einem VSPackage, das keinem Menübefehl zugeordnet ist, müssen Sie einen Alias für die Assembly erstellen und dann den Alias aufrufen.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>So greifen Sie einen Befehl aus einer Assembly an  
  
1. Fügen Sie in der Projekt Mappe einen Verweis auf die Assembly hinzu.  
  
2. Fügen Sie am Anfang der Datei "StartPage. XAML" eine Namespace-Direktive für die Assembly hinzu, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3. Rufen Sie den Befehl auf, indem Sie die- `Command` Eigenschaft eines XAML-Objekts festlegen, wie im folgenden Beispiel gezeigt.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
> Sie müssen die Assembly kopieren und anschließend in einfügen. \\ *Visual Studio-Installationsordner*\common7\ide\privateassemblies\, um sicherzustellen, dass er geladen wird, bevor er aufgerufen wird.  
  
## <a name="adding-commands-with-the-dte-object"></a>Hinzufügen von Befehlen mit dem DTE-Objekt  
 Sie können auf das DTE-Objekt von einer Start Seite aus zugreifen, sowohl in Markup als auch im Code.  
  
 In Markup können Sie darauf zugreifen, indem Sie die Syntax der [Bindungs Markup Erweiterung](https://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) zum Aufrufen des- <xref:EnvDTE.DTE> Objekts verwenden. Sie können diesen Ansatz verwenden, um eine Bindung an einfache Eigenschaften wie z. b. die zurückgegebenen Auflistungen herzustellen Das folgende Beispiel zeigt ein <xref:System.Windows.Controls.TextBlock> Steuerelement, das an die-Eigenschaft gebunden wird <xref:EnvDTE._DTE.Name%2A> , und ein-Steuerelement, <xref:System.Windows.Controls.ListBox> das die Eigenschaften der Auflistung auflistet, die <xref:EnvDTE.Window.Caption%2A> von der-Eigenschaft zurückgegeben wird <xref:EnvDTE._DTE.Windows%2A> .  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 Ein Beispiel finden Sie unter Exemplarische Vorgehensweise [: Speichern von Benutzereinstellungen auf einer Start Seite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen eines Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)
