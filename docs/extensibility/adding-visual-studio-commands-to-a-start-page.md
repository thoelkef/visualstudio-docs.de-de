---
title: Hinzufügen von Visual Studio-Befehlen zu einer Startseite | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de713065b61df07a791fa81e89425481227676ea
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006710"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Hinzufügen von Visual Studio-Befehlen zu einer Startseite
Wenn Sie eine benutzerdefinierte Startseite erstellen, können Sie Visual Studio-Befehle, hinzufügen. Dieses Dokument erläutert die verschiedenen Methoden zum Binden von Visual Studio-Befehle an XAML-Objekte auf einer Startseite.  
  
 Weitere Informationen über Befehle in XAML finden Sie unter [Commanding-Übersicht](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="add-commands-from-the-command-well"></a>Hinzufügen von Befehlen aus dem Befehl auch  
 Die Startseite im erstellt [erstellen Sie eine benutzerdefinierte Startseite](../extensibility/creating-a-custom-start-page.md) hinzugefügt der <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> und <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> Namespaces wie folgt.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Fügen Sie einen anderen Namespace aus der Assembly für Microsoft.VisualStudio.Shell *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Möglicherweise müssen Sie einen Verweis auf diese Assembly in Ihrem Projekt hinzufügen.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Können Sie die `vscom:` Alias zum Binden von Visual Studio-Befehle an der XAML-Steuerelemente auf der Seite durch Festlegen der <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Eigenschaft des Steuerelements `vscom:VSCommands.ExecuteCommand`. Sie können dann Festlegen der <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> -Eigenschaft auf den Namen des Befehls zum Ausführen wie im folgenden Beispiel gezeigt.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  Die `x:` Alias, der dem XAML-Schema verweist, muss sich am Anfang aller Befehle.  
  
 Legen Sie den Wert von der `Command` Eigenschaft, um solche Befehle, die aus zugegriffen werden kann die **Befehl** Fenster. Eine Liste der verfügbaren Befehle, finden Sie unter [Visual Studio-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md).  
  
 Wenn Sie der Befehl zum Hinzufügen zusätzlichen Parameter erfordert, können Sie es hinzufügen, auf den Wert des der `CommandParameter` Eigenschaft. Separate Parameter von Befehlen mithilfe von Speicherplätzen, wie im folgenden Beispiel gezeigt.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="call-extensions-from-the-command-well"></a>Rufen Sie Erweiterungen auch aus dem Befehl  
 Sie können die Befehle von registrierte VSPackages aufrufen, indem Sie mit derselben Syntax, die verwendet wird, um andere Visual Studio-Befehle aufrufen. Wenn eine installierte VSPackage fügt z. B. eine **auf der Startseite** Befehl die **Ansicht** im Menü können Sie diesen Befehl aufrufen, indem Sie die Einstellung `CommandParameter` zu `View.HomePage`.  
  
> [!NOTE]
>  Wenn Sie einen Befehl, der ein VSPackage zugeordnet ist aufrufen, muss das Paket geladen werden, wenn der Befehl aufgerufen wird.  
  
## <a name="add-commands-from-assemblies"></a>Hinzufügen von Befehlen von Assemblys  
 Zum Aufrufen eines Befehls an, aus einer Assembly oder den Zugriff von Code in einem VSPackage, die nicht mit einem Menübefehl zugeordnet ist, müssen Sie erstellen Sie einen Alias für die Assembly und rufen Sie dann auf den Alias.  
  
### <a name="to-call-a-command-from-an-assembly"></a>Zum Aufrufen eines Befehls aus einer assembly  
  
1.  Fügen Sie einen Verweis auf die Assembly, in der Projektmappe.  
  
2.  Am oberen Rand der *"StartPage.xaml"* Datei, fügen Sie eine Direktive für die Assembly, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Rufen Sie den Befehl durch Festlegen der `Command` Eigenschaft eines XAML-Objekts, wie im folgenden Beispiel gezeigt.  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Sie müssen die Kopie der Assembly und fügen Sie ihn in *... \\{Visual Studio-Installationsordner} \Common7\IDE\PrivateAssemblies\* um sicherzustellen, dass es geladen wird, bevor sie aufgerufen wird.  
  
## <a name="add-commands-with-the-dte-object"></a>Hinzufügen von Befehlen mit dem DTE-Objekt  
 Sie können das DTE-Objekt auf einer Startseite auf, sowohl im Markup als auch im Code zugreifen.  
  
 Im Markup, Sie können darauf zugreifen, indem mithilfe der [Binding als Markuperweiterung](/dotnet/framework/wpf/advanced/binding-markup-extension) Syntax zum Aufrufen der <xref:EnvDTE.DTE> Objekt. Sie können diesen Ansatz verwenden, um an einfache Eigenschaften, z. B. die Bindung, die Auflistungen zurückgeben, aber Sie können nicht gebunden werden, um Methoden oder Dienste. Das folgende Beispiel zeigt eine <xref:System.Windows.Controls.TextBlock> -Steuerelement, das gebunden wird die <xref:EnvDTE._DTE.Name%2A> -Eigenschaft, und ein <xref:System.Windows.Controls.ListBox> -Steuerelement, das Listet die <xref:EnvDTE.Window.Caption%2A> Eigenschaften der Auflistung, die von zurückgegeben wird die <xref:EnvDTE._DTE.Windows%2A> Eigenschaft.  
  
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
  
 Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Speichern von benutzereinstellungen auf einer Startseite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen eines Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)