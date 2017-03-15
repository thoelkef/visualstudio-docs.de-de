---
title: "Erstellen ein WPF-Toolbox-Steuerelement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Toolbox-Steuerelement"
  - "Toolbox"
  - "WPF"
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Erstellen ein WPF-Toolbox-Steuerelement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Toolbox\-Steuerelement von WPF \(Windows Presentation Framework\) der Vorlage können Sie die WPF\-Steuerelemente erstellen, die automatisch hinzugefügt werden, die **Toolbox** Wenn die Erweiterung installiert wird. In diesem Thema veranschaulicht, wie die Vorlage zum Erstellen einer **Toolbox** Steuerelement, das Sie an andere Benutzer verteilen können.  
  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen ein WPF\-Toolbox\-Steuerelement  
  
#### Erstellen Sie eine Erweiterung mit einem WPF\-Toolbox\-Steuerelement  
  
1.  Erstellen Sie ein VSIX\-Projekt namens `MyToolboxControl`. Sie finden die VSIX\-Projektvorlage in die **Neues Projekt** Dialogfeld unter **Visual c\# \/ Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, eine **WPF\-Toolbox\-Steuerelement** Elementvorlage mit dem Namen `MyToolboxControl`. In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. In der **Neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c\# \/ Erweiterbarkeit** und wählen Sie **WPF\-Toolbox\-Steuerelement**. In den **Namen** Feld am unteren Rand des Fensters, das Ändern der Name der Befehlsdatei an `MyToolboxControl.cs`.  
  
     Die Projektmappe enthält jetzt ein Benutzersteuerelement, eine `ProvideToolboxControlAttribute`<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> die das Steuerelement fügt die **Toolbox**, und ein **Microsoft.VisualStudio.ToolboxControl** \-Ressourceneintrag im VSIX\-Manifest für die Bereitstellung.  
  
#### So erstellen Sie eine Steuerelement\-Benutzeroberfläche  
  
1.  Öffnen Sie MyToolboxControl.xaml im Designer.  
  
     Der Designer zeigt ein <xref:System.Windows.Controls.Grid>\-Steuerelement an, das ein <xref:System.Windows.Controls.Button>\-Steuerelement enthält.  
  
2.  Das Raster Layout. Bei der Auswahl der <xref:System.Windows.Controls.Grid> steuern, blauen Steuerleisten auf der oberen und linken Rands des Rasters angezeigt. Sie können Zeilen und Spalten zum Raster hinzufügen, durch Klicken auf den Balken.  
  
3.  Dem Raster untergeordnete Steuerelemente hinzuzufügen. Sie können ein untergeordnetes Steuerelement positionieren, ziehen Sie es aus der **Toolbox** auf einen Bereich des Rasters oder durch Festlegen seiner `Grid.Row` und `Grid.Column` Attribute im XAML. Das folgende Beispiel fügt zwei Bezeichnungen auf die oberste Zeile des Rasters und eine Schaltfläche in der zweiten Zeile.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## Umbenennen des Steuerelements  
 Standardmäßig wird das Steuerelement angezeigt, der **Toolbox** als **MyToolboxControl** in einer Gruppe namens **MyToolboxControl.MyToolboxControl**. Sie können diese Namen in der Datei MyToolboxControl.xaml.cs ändern.  
  
1.  Öffnen Sie die MyToolboxControl.xaml.cs in der Codeansicht.  
  
2.  Suchen Sie die MyToolboxControl\-Klasse, und benennen Sie sie in TestControl. \(Die schnellste Möglichkeit hierzu ist die Klasse umbenennen wählen **Umbenennen** aus dem Kontextmenü, und führen Sie die Schritte aus. \(Weitere Informationen zu den **Umbenennen** finden Sie unter [Umgestaltung durch Umbenennen \(C\#\)](../csharp-ide/rename-refactoring-csharp.md).\)  
  
3.  Wechseln Sie zu der `ProvideToolboxControl` Attribut, und ändern Sie den Wert des ersten Parameters **Test**. Dies ist der Name der Gruppe, die das Steuerelement in enthält die **Toolbox**.  
  
     Der resultierende Code sollte wie folgt aussehen:  
  
    ```c#  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## Erstellen, Tests und Bereitstellung  
 Wenn Sie das Projekt debuggen, finden Sie sollten das Steuerelement installiert, die der **Toolbox** der experimentellen Instanz von Visual Studio.  
  
#### So erstellen Sie das Steuerelement und testen es  
  
1.  Das Projekt neu, und starten Sie das Debuggen.  
  
2.  Erstellen Sie in der neuen Instanz von Visual Studio ein WPF\-Anwendungsprojekt. Stellen Sie sicher, dass die XAML\-Designer geöffnet ist.  
  
3.  Suchen Sie in der **Toolbox** nach dem Steuerelement, und ziehen Sie es dann auf die Entwurfsoberfläche.  
  
4.  Debuggen Sie die WPF\-Anwendung.  
  
5.  Stellen Sie sicher, dass das Steuerelement angezeigt wird.  
  
#### So stellen Sie das Steuerelement bereit  
  
1.  Nachdem Sie den getestete Projekt erstellen, finden Sie die VSIX\-Datei im Ordner "\\bin\\debug\\" des Projekts.  
  
2.  Sie können es auf einem lokalen Computer installieren, durch Doppelklicken auf die VSIX\-Datei, und folgen Sie den Installationsvorgang. Um das Steuerelement zu deinstallieren, wechseln Sie zu **Extras \/ Erweiterungen und Updates** suchen Sie nach der Erweiterung, und klicken Sie auf **Deinstallieren**.  
  
3.  Laden Sie die VSIX\-Datei in ein Netzwerk oder auf einer Website hoch.  
  
     Wenn Sie die Datei zum Hochladen der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) \-Website, andere Benutzer können **Tools \/ Erweiterungen und Updates** in Visual Studio online suchen und installieren es.