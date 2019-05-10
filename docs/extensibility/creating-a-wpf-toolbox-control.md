---
title: Erstellen eines WPF-Toolbox-Steuerelements | Microsoft-Dokumentation
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 811c87f73d1122b3e97ffdef9b4d3f6c044ce941
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926418"
---
# <a name="create-a-wpf-toolbox-control"></a>Erstellen Sie ein WPF-Toolbox-Steuerelement

Die Vorlage für Toolbox-Steuerelement für WPF (Windows Presentation Framework) können Sie die WPF-Steuerelemente erstellen, die automatisch hinzugefügt werden, die **Toolbox** beim Installieren der Erweiterung. In dieser exemplarischen Vorgehensweise zeigt, wie Sie die Vorlage zu verwenden, zum Erstellen einer **Toolbox** -Steuerelement, das Sie für andere Benutzer verteilen können.

Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Erstellen von Toolbox-Steuerelement

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Erstellen Sie eine Erweiterung mit einem WPF-Toolbox-Steuerelement

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `MyToolboxControl`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld, indem Sie nach "Vsix" suchen.

2. Wenn das Projekt geöffnet wird, eine **WPF-Toolbox-Steuerelement** Item-Vorlage, die mit dem Namen `MyToolboxControl`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen** > **neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual C#-** > **Erweiterbarkeit** , und wählen Sie **WPF-Toolbox-Steuerelement**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an *MyToolboxControl.cs*.

    Die Projektmappe enthält jetzt ein Benutzersteuerelement, ein `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , die das Steuerelement, fügt die **Toolbox**, und ein **Microsoft.VisualStudio.ToolboxControl** Ressourceneintrag im VSIX-Manifest für  die Bereitstellung.

#### <a name="to-create-the-control-ui"></a>So erstellen Sie eine Steuerelement-Benutzeroberfläche

1. Open *MyToolboxControl.xaml* im Designer.

    Der Designer zeigt ein <xref:System.Windows.Controls.Grid>-Steuerelement an, das ein <xref:System.Windows.Controls.Button>-Steuerelement enthält.

2. Ordnen Sie das Rasterlayout. Bei der Auswahl der <xref:System.Windows.Controls.Grid> zu steuern, Blau Schiebeleisten-Steuerelemente, die auf dem oberen und linken Rand des Rasters angezeigt werden. Sie können Zeilen und Spalten zum Raster hinzufügen, indem Sie auf die Balken.

3. Fügen Sie untergeordnete Steuerelemente in das Raster an. Sie können ein untergeordnetes Steuerelement positionieren, ziehen Sie es aus der **Toolbox** in einen Bereich des Rasters oder durch Festlegen seiner `Grid.Row` und `Grid.Column` Attribute in der XAML. Das folgende Beispiel fügt zwei Bezeichnungen auf der obersten Zeile des Rasters und eine Schaltfläche auf der zweiten Zeile.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Umbenennen des Steuerelements

 Standardmäßig wird das Steuerelement angezeigt, der **Toolbox** als **MyToolboxControl** in einer Gruppe namens **MyToolboxControl.MyToolboxControl**. Sie können diese Namen im Ändern der *MyToolboxControl.xaml.cs* Datei.

1. Open *MyToolboxControl.xaml.cs* in der Codeansicht.

2. Suchen der `MyToolboxControl` Klasse, und benennen Sie sie in TestControl. (Die schnellste Möglichkeit hierzu ist die-Klasse umbenennen wählen Sie dann **umbenennen** aus dem Kontextmenü, und führen Sie die Schritte aus. (Weitere Informationen zu den **umbenennen** Befehl, finden Sie unter [umbenennen refactoring (c#)](../ide/reference/rename.md).)

3. Wechseln Sie zu der `ProvideToolboxControl` Attribut, und ändern Sie den Wert des ersten Parameters, der **Test**. Dies ist der Name der Gruppe, die das Steuerelement in enthält die **Toolbox**.

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

## <a name="build-test-and-deployment"></a>Build, Test und Bereitstellung

 Wenn Sie das Projekt debuggen, finden Sie sollten das Steuerelement installiert, die der **Toolbox** der experimentellen Instanz von Visual Studio.

### <a name="to-build-and-test-the-control"></a>So erstellen Sie das Steuerelement und testen es

1. Das Projekt neu, und starten Sie das Debuggen.

2. Erstellen Sie in der neuen Instanz von Visual Studio ein WPF-Anwendungsprojekt. Stellen Sie sicher, dass der XAML-Designer geöffnet ist.

3. Suchen Sie in der **Toolbox** nach dem Steuerelement, und ziehen Sie es dann auf die Entwurfsoberfläche.

4. Debuggen Sie die WPF-Anwendung.

5. Stellen Sie sicher, dass das Steuerelement angezeigt wird.

### <a name="to-deploy-the-control"></a>So stellen Sie das Steuerelement bereit

1. Nachdem Sie das getestete Projekt erstellt haben, finden Sie die *VSIX* Datei der * \bin\debug\* -Ordner des Projekts.

2. Sie können es auf einem lokalen Computer installieren, durch Doppelklicken auf die *VSIX* -Datei, und folgen den Installationsvorgang zu starten. Um das Steuerelement zu deinstallieren, wechseln Sie zu **Tools** > **Erweiterungen und Updates** suchen Sie nach der Erweiterung, und klicken Sie auf **Deinstallieren**.

3. Hochladen der *VSIX* -Datei mit einem Netzwerk oder auf einer Website.

    Wenn Sie die Datei zum Hochladen der [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website, andere Benutzer können **Tools** > **Erweiterungen und Updates** in Visual Studio zum Suchen der online steuern Sie, und installieren Sie es aus.
