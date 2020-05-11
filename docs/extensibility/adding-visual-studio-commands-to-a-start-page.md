---
title: Hinzufügen von Visual Studio-Befehlen zu einer Startseite | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 13dd40006039209b06cc6a71760fdbaa240db4fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740114"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Hinzufügen von Visual Studio-Befehlen zu einer Startseite

Wenn Sie eine benutzerdefinierte Startseite erstellen, können Sie Visual Studio-Befehle hinzufügen. In diesem Dokument werden die verschiedenen Möglichkeiten zum Binden von Visual Studio-Befehlen an XAML-Objekte auf einer Startseite erläutert.

Weitere Informationen zu Befehlen in XAML finden Sie unter [Befehlsübersicht](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Hinzufügen von Befehlen aus dem Befehl sbrunnen

Die Startseite, die in Create a <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> custom [Start Page](../extensibility/creating-a-custom-start-page.md) erstellt wurde, hat die und die Namespaces wie folgt hinzugefügt.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Fügen Sie einen weiteren Namespace für Microsoft.VisualStudio.Shell aus der Assembly *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*hinzu. (Möglicherweise müssen Sie in Ihrem Projekt einen Verweis auf diese Assembly hinzufügen.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Sie können `vscom:` den Alias verwenden, um Visual Studio-Befehle an <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> XAML-Steuerelemente auf der Seite zu binden, indem Sie die Eigenschaft des Steuerelements auf `vscom:VSCommands.ExecuteCommand`festlegen. Sie können die <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> Eigenschaft dann auf den Namen des auszuführenden Befehls festlegen, wie im folgenden Beispiel gezeigt.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> Der `x:` Alias, der sich auf das XAML-Schema bezieht, ist am Anfang aller Befehle erforderlich.

 Sie können den Wert `Command` der Eigenschaft auf jeden Befehl festlegen, auf den über das **Befehlsfenster** zugegriffen werden kann. Eine Liste der verfügbaren Befehle finden Sie unter [Visual Studio-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md).

 Wenn der hinzuzufügende Befehl einen zusätzlichen Parameter erfordert, können `CommandParameter` Sie ihn dem Wert der Eigenschaft hinzufügen. Trennen Sie Parameter von Befehlen, indem Sie Leerzeichen verwenden, wie im folgenden Beispiel gezeigt.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Aufruferweiterungen aus dem Befehl swell
 Sie können Befehle aus registrierten VSPackages aufrufen, indem Sie dieselbe Syntax verwenden, die zum Aufrufen anderer Visual Studio-Befehle verwendet wird. Wenn z. B. ein installiertes VSPackage dem **Menü Ansicht** einen Befehl `CommandParameter` `View.HomePage` **"Startseite"** hinzufügt, können Sie diesen Befehl aufrufen, indem Sie auf .

> [!NOTE]
> Wenn Sie einen Befehl aufrufen, der einem VSPackage zugeordnet ist, muss das Paket geladen werden, wenn der Befehl aufgerufen wird.

## <a name="add-commands-from-assemblies"></a>Hinzufügen von Befehlen aus Assemblys
 Um einen Befehl aus einer Assembly aufzurufen oder auf Code in einem VSPackage zuzugreifen, der keinem Menübefehl zugeordnet ist, müssen Sie einen Alias für die Assembly erstellen und dann den Alias aufrufen.

### <a name="to-call-a-command-from-an-assembly"></a>So rufen Sie einen Befehl aus einer Assembly auf

1. Fügen Sie in der Projektmappe einen Verweis auf die Baugruppe hinzu.

2. Fügen Sie oben in der *Datei StartPage.xaml* eine Namespacedirektive für die Assembly hinzu, wie im folgenden Beispiel gezeigt.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Rufen Sie den `Command` Befehl auf, indem Sie die Eigenschaft eines XAML-Objekts festlegen, wie im folgenden Beispiel gezeigt.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Sie müssen die Baugruppe kopieren und dann in *. einfügen. \\"Visual Studio-Installationsordner" ,,Common7'IDE'PrivateAssemblies'\* , um sicherzustellen, dass er geladen wird, bevor er aufgerufen wird.

## <a name="add-commands-with-the-dte-object"></a>Hinzufügen von Befehlen mit dem DTE-Objekt
 Sie können sowohl im Markup als auch im Code von einer Startseite aus auf das DTE-Objekt zugreifen.

 In Markup können Sie darauf zugreifen, indem Sie die <xref:EnvDTE.DTE> [Syntax "Binding Markup Extension"](/dotnet/framework/wpf/advanced/binding-markup-extension) verwenden, um das Objekt aufzurufen. Sie können diesen Ansatz verwenden, um einfache Eigenschaften zu binden, z. B. solche, die Auflistungen zurückgeben, aber Sie können keine Bindung an Methoden oder Dienste. Das folgende Beispiel <xref:System.Windows.Controls.TextBlock> zeigt ein Steuerelement, das <xref:EnvDTE._DTE.Name%2A> <xref:System.Windows.Controls.ListBox> an die Eigenschaft gebunden <xref:EnvDTE.Window.Caption%2A> ist, und ein Steuerelement, das die Eigenschaften der Auflistung aufzählt, die von der <xref:EnvDTE._DTE.Windows%2A> Eigenschaft zurückgegeben wird.

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

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen von Benutzersteuerelementen zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)
