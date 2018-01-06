---
title: "Hinzufügen von Visual Studio-Befehle auf einer Startseite | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: efb332de822bd86cc95c4786dbca3472fd0984cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Hinzufügen von Visual Studio-Befehle auf einer Startseite
Wenn Sie eine benutzerdefinierte Startseite erstellen, können Sie Visual Studio-Befehle hinzufügen. Dieses Dokument beschreibt die verschiedenen Methoden zum Binden von Visual Studio-Befehle auf die Verwendung von XAML-Objekte auf einer Startseite.  
  
 Weitere Informationen zu XAML-Befehlen finden Sie unter [Befehle (Übersicht)](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="adding-commands-from-the-command-well"></a>Hinzufügen von Befehlen aus dem Befehl auch  
 In die Startseite erstellt [erstellen eine benutzerdefinierte Startseite](../extensibility/creating-a-custom-start-page.md) hinzugefügt der <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> und <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> Namespaces, wie folgt.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Fügen Sie einen anderen Namespace aus der Assembly Microsoft.VisualStudio.Shell.Immutable.11.0.dll für Microsoft.VisualStudio.Shell hinzu. (Möglicherweise müssen Sie einen Verweis auf diese Assembly in Ihrem Projekt hinzufügen.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Können Sie die `vscom:` Alias zum Binden von Visual Studio-Befehle in XAML-Steuerelemente auf der Seite durch Festlegen der <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Eigenschaft des Steuerelements `vscom:VSCommands.ExecuteCommand`. Legen Sie Sie dann die <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> -Eigenschaft auf den Namen des Befehls auszuführende wie im folgenden Beispiel gezeigt.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  Die `x:` Alias, der auf die Verwendung von XAML-Schema verweist, muss am Anfang aller Befehle.  
  
 Können Sie den Wert der Festlegen der `Command` Eigenschaft, um solche Befehle, die aus zugegriffen werden kann die **Befehl** Fenster. Eine Liste der verfügbaren Befehle, finden Sie unter [Visual Studio-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md).  
  
 Wenn der Befehl zum Hinzufügen zusätzlichen Parameter erfordert, können Sie es auf den Wert des Hinzufügen der `CommandParameter` Eigenschaft. Separate Parameter von Befehlen, die durch Leerzeichen, wie im folgenden Beispiel gezeigt.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Extensions aufrufen auch aus den Befehl  
 Sie können Befehle aus registrierten VSPackages aufrufen, mit der gleichen Syntax, die zum Aufrufen von anderen Visual Studio-Befehle verwendet wird. Z. B. ein installierten VSPackages Fügt eine **Startseite** -Befehls auf den **Ansicht** Menü können Sie diesen Befehl aufrufen, indem Sie festlegen `CommandParameter` zu `View.HomePage`.  
  
> [!NOTE]
>  Wenn Sie einen Befehl, der ein VSPackage zugeordnet ist aufrufen, muss das Paket geladen werden, wenn der Befehl aufgerufen wird.  
  
## <a name="adding-commands-from-assemblies"></a>Hinzufügen von Befehlen aus Assemblys  
 Zum Aufrufen eines Befehls an, aus einer Assembly oder den Zugriff von Code in einem VSPackage, die nicht mit einem Menübefehl verknüpft ist, müssen Sie erstellen Sie einen Alias für die Assembly und rufen dann den Alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Zum Aufrufen eines Befehls aus einer assembly  
  
1.  Fügen Sie einen Verweis auf die Assembly, in der Projektmappe.  
  
2.  Fügen Sie am Anfang der Datei "StartPage.xaml" eine Direktive für die Assembly hinzu, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Rufen Sie den Befehl durch Festlegen der `Command` Eigenschaft eines XAML-Objekts, wie im folgenden Beispiel gezeigt.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Sie müssen kopieren Sie die Assembly, und fügen Sie ihn in... \\ *Visual Studio-Installationsordner*\Common7\IDE\PrivateAssemblies\ um sicherzustellen, dass es geladen wird, bevor er aufgerufen wird.  
  
## <a name="adding-commands-with-the-dte-object"></a>Hinzufügen von Befehlen mit dem DTE-Objekt  
 Sie können das DTE-Objekt auf einer Startseite auf, sowohl in Markup und Code zugreifen.  
  
 Im Markup, Sie können darauf zugreifen, indem die [Markuperweiterung binden](/dotnet/framework/wpf/advanced/binding-markup-extension) Syntax zum Aufrufen der <xref:EnvDTE.DTE> Objekt. Verwenden Sie diesen Ansatz zum Binden an einfache Eigenschaften, z. B. solche, die Auflistungen zurückgeben, aber Sie können nicht gebunden werden, um Methoden oder Dienste. Das folgende Beispiel zeigt eine <xref:System.Windows.Controls.TextBlock> Steuerelement, das gebunden wird die <xref:EnvDTE._DTE.Name%2A> -Eigenschaft, und ein <xref:System.Windows.Controls.ListBox> Steuerelement, das Listet die <xref:EnvDTE.Window.Caption%2A> Eigenschaften der Auflistung, die von zurückgegeben wird die <xref:EnvDTE._DTE.Windows%2A> Eigenschaft.  
  
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
  
 Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen eines Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)