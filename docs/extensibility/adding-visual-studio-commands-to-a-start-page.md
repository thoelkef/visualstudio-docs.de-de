---
title: "Hinzufügen von Visual Studio-Befehle zu einer Startseite | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c75d9b41d0e51d6db2e78d0afa0e1ddf37e87b8a
ms.lasthandoff: 02/22/2017

---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Hinzufügen von Visual Studio-Befehle zu einer Startseite
Wenn Sie eine benutzerdefinierte Startseite erstellen, können Sie Visual Studio-Befehle hinzufügen. Dieses Dokument beschreibt die verschiedenen Methoden zum Binden von Visual Studio-Befehle an XAML-Objekte auf einer Startseite.  
  
 Weitere Informationen zu Befehlen in XAML finden Sie unter [Befehle (Übersicht)](http://msdn.microsoft.com/Library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Hinzufügen von Befehlen auch über den Befehl  
 Die Startseite erstellt [erstellen eine benutzerdefinierte Startseite](../extensibility/creating-a-custom-start-page.md) hinzugefügt der <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>und <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>Namespaces wie folgt.</xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> </xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Fügen Sie einen anderen Namespace für Microsoft.VisualStudio.Shell aus der Assembly Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Möglicherweise müssen einen Verweis auf diese Assembly in Ihrem Projekt hinzufügen.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Können Sie die `vscom:` Alias zum Binden von Visual Studio-Befehle an XAML-Steuerelemente auf der Seite durch Festlegen der <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>Eigenschaft des Steuerelements `vscom:VSCommands.ExecuteCommand`.</xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Sie können festlegen, die <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>-Eigenschaft auf den Namen des Befehls ausführen, wie im folgenden Beispiel gezeigt,.</xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  Die `x:` Alias, der auf das XAML-Schema verweist, ist am Anfang aller Befehle erforderlich.  
  
 Können Sie den Wert der Festlegen der `Command` -Eigenschaft jeder Befehl, der aus zugegriffen werden kann die **Befehl** Fenster. Eine Liste der verfügbaren Befehle finden Sie unter [Visual Studio-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md).  
  
 Wenn der Befehl zum Hinzufügen zusätzlichen Parameter erfordert, können Sie es auf den Wert des Hinzufügen der `CommandParameter` Eigenschaft. Separate Parameter von Befehlen, die durch Leerzeichen, wie im folgenden Beispiel gezeigt.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Aufrufen von Erweiterungen auch über den Befehl  
 Sie können Befehle von registrierten VSPackages aufrufen, indem Sie mit der gleichen Syntax, die zum Aufrufen der anderen Visual Studio-Befehle verwendet wird. Beispielsweise, wenn eine installierte VSPackage Fügt eine **Startseite** Befehl die **Ansicht** Menü können Sie den Befehl aufrufen, indem Sie festlegen `CommandParameter` auf `View.HomePage`.  
  
> [!NOTE]
>  Wenn Sie einen Befehl, der ein VSPackage zugeordnet ist aufrufen, muss das Paket geladen werden, wenn der Befehl aufgerufen wird.  
  
## <a name="adding-commands-from-assemblies"></a>Hinzufügen von Befehlen von Assemblys  
 Zum Aufrufen eines Befehls aus einer Assembly oder Datenzugriffscode in ein VSPackage, das einen Menübefehl zugeordnet ist müssen Sie einen Alias für die Assembly erstellen und rufen dann den Alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Aufrufen ein Befehls aus einer assembly  
  
1.  Fügen Sie einen Verweis auf die Assembly, in der Projektmappe.  
  
2.  Fügen Sie am Anfang der Datei StartPage.xaml Namespace eine Direktive für die Assembly hinzu, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Rufen Sie den Befehl durch Festlegen der `Command` Eigenschaft eines XAML-Objekts, wie im folgenden Beispiel gezeigt.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Sie müssen kopieren Sie die Assembly, und fügen Sie ihn in... \\ *Visual Studio-Installationsordner*\Common7\IDE\PrivateAssemblies\ um sicherzustellen, dass es geladen wird, bevor sie aufgerufen wird.  
  
## <a name="adding-commands-with-the-dte-object"></a>Hinzufügen von Befehlen mit dem DTE-Objekt  
 Sie können eine Startseite, sowohl im Markup als auch im Code das DTE-Objekt zugreifen.  
  
 Im Markup, Sie können darauf zugreifen, indem mithilfe der [Binding-Markuperweiterung](http://msdn.microsoft.com/Library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) Syntax zum Aufrufen der <xref:EnvDTE.DTE>Objekt.</xref:EnvDTE.DTE> Sie können diesen Ansatz verwenden, zum Binden an einfache Eigenschaften wie z. B. diejenigen, die Auflistungen zurückgeben, aber Sie können keine Bindung an Methoden oder Dienste. Das folgende Beispiel zeigt eine <xref:System.Windows.Controls.TextBlock>-Steuerelement, das gebunden wird die <xref:EnvDTE._DTE.Name%2A>-Eigenschaft, und ein <xref:System.Windows.Controls.ListBox>-Steuerelement, das Listet die <xref:EnvDTE.Window.Caption%2A>Eigenschaften der Auflistung, die von zurückgegeben wird die <xref:EnvDTE._DTE.Windows%2A>Eigenschaft.</xref:EnvDTE._DTE.Windows%2A> </xref:EnvDTE.Window.Caption%2A> </xref:System.Windows.Controls.ListBox> </xref:EnvDTE._DTE.Name%2A> </xref:System.Windows.Controls.TextBlock>  
  
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
  
 Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf eine Startseite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen des Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)
