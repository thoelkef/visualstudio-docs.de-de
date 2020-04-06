---
title: Erstellen eines WPF Toolbox-Steuerelements | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1400efb0095760bf1cee302dd33dcf6ebb90152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739567"
---
# <a name="create-a-wpf-toolbox-control"></a>Erstellen eines WPF Toolbox-Steuerelements

Mit der Toolboxcontrol-Vorlage WPF (Windows Presentation Framework) können Sie WPF-Steuerelemente erstellen, die automatisch zur **Toolbox** hinzugefügt werden, wenn die Erweiterung installiert wird. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die Vorlage verwenden, um ein **Toolbox-Steuerelement** zu erstellen, das Sie an andere Benutzer verteilen können.

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Erstellen des Toolbox-Steuerelements

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Erstellen einer Erweiterung mit einem WPF Toolbox Control

1. Erstellen Sie ein `MyToolboxControl`VSIX-Projekt mit dem Namen . Die VSIX-Projektvorlage finden Sie im Dialogfeld **Neues Projekt,** indem Sie nach "vsix" suchen.

2. Wenn das Projekt geöffnet wird, fügen Sie `MyToolboxControl`eine **WPF Toolbox** Control-Elementvorlage mit dem Namen hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu Visual **C-Extensibility,** > **Extensibility** und wählen Sie **WPF Toolbox Control**aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Befehlsdateinamen in *MyToolboxControl.cs*.

    Die Lösung enthält jetzt ein `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> Benutzersteuerelement, ein Steuerelement zur **Toolbox**und einen **Microsoft.VisualStudio.ToolboxControl** Asset-Eintrag im VSIX-Manifest für die Bereitstellung.

#### <a name="to-create-the-control-ui"></a>So erstellen Sie eine Steuerelement-Benutzeroberfläche

1. Öffnen Sie *MyToolboxControl.xaml* im Designer.

    Der Designer zeigt ein <xref:System.Windows.Controls.Grid>-Steuerelement an, das ein <xref:System.Windows.Controls.Button>-Steuerelement enthält.

2. Ordnen Sie das Rasterlayout an. Wenn Sie <xref:System.Windows.Controls.Grid> das Steuerelement auswählen, werden oben und links blaue Steuerleisten am oberen und linken Rand des Rasters angezeigt. Sie können dem Raster Zeilen und Spalten hinzufügen, indem Sie auf die Balken klicken.

3. Fügen Sie dem Raster untergeordnete Steuerelemente hinzu. Sie können ein untergeordnetes Steuerelement positionieren, indem Sie es aus der `Grid.Row` `Grid.Column` **Toolbox** in einen Abschnitt des Rasters ziehen oder indem Sie seine und Attribute im XAML festlegen. Im folgenden Beispiel werden zwei Beschriftungen in der obersten Zeile des Rasters und eine Schaltfläche in der zweiten Zeile hinzugefügt.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Umbenennen des Steuerelements

 Standardmäßig wird Ihr Steuerelement in der **Toolbox** als **MyToolboxControl** in einer Gruppe mit dem Namen **MyToolboxControl.MyToolboxControl**angezeigt. Sie können diese Namen in der *MyToolboxControl.xaml.cs-Datei* ändern.

1. Öffnen Sie *MyToolboxControl.xaml.cs* in der Codeansicht.

2. Suchen `MyToolboxControl` Sie die Klasse, und benennen Sie sie in TestControl um. (Der schnellste Weg, dies zu tun, besteht darin, die Klasse umzubenennen, dann im Kontextmenü **umbenennen** auszuwählen und die Schritte abzuschließen. (Weitere Informationen zum Befehl **Umbenennen** finden Sie unter [Umbenennen von Umgestaltungs-Umgestaltungen (C)](../ide/reference/rename.md).)

3. Wechseln Sie `ProvideToolboxControl` zum Attribut, und ändern Sie den Wert des ersten Parameters in **Test**. Dies ist der Name der Gruppe, die das Steuerelement in der **Toolbox**enthält.

    Der resultierende Code sollte wie folgt aussehen:

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>Erstellen, Testen und Bereitstellen

 Wenn Sie das Projekt debuggen, sollten Sie das Steuerelement finden, das in der **Toolbox** der experimentellen Instanz von Visual Studio installiert ist.

### <a name="to-build-and-test-the-control"></a>So erstellen Sie das Steuerelement und testen es

1. Erstellen Sie das Projekt neu, und starten Sie das Debuggen.

2. Erstellen Sie in der neuen Instanz von Visual Studio ein WPF-Anwendungsprojekt. Stellen Sie sicher, dass der XAML-Designer geöffnet ist.

3. Suchen Sie in der **Toolbox** nach dem Steuerelement, und ziehen Sie es dann auf die Entwurfsoberfläche.

4. Beginnen Sie mit dem Debuggen der WPF-Anwendung.

5. Stellen Sie sicher, dass das Steuerelement angezeigt wird.

### <a name="to-deploy-the-control"></a>So stellen Sie das Steuerelement bereit

1. Nachdem Sie das getestete Projekt erstellt haben, finden Sie die\* *.vsix-Datei* im Ordner *-bin-debug des Projekts.

2. Sie können es auf einem lokalen Computer installieren, indem Sie auf die *.vsix-Datei* doppelklicken und den Installationsvorgang befolgen. Um das Steuerelement zu deinstallieren, gehen Sie zu > **Tools-Erweiterungen und Updates,** suchen Sie nach der Steuerelementerweiterung, und klicken Sie dann auf **Deinstallieren**. **Tools**

3. Laden Sie die *.vsix-Datei* in ein Netzwerk oder eine Website hoch.

    Wenn Sie die Datei auf die [Visual Studio Marketplace-Website](https://marketplace.visualstudio.com/) hochladen, können andere Benutzer **Tools** > **Extensions and Updates** in Visual Studio verwenden, um das Steuerelement online zu suchen und zu installieren.
