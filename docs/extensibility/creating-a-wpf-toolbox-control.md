---
title: Erstellen eines WPF-Toolbox-Steuerelements | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c1a8338f0ebd964e5d039ffa8dff000a441523f8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="creating-a-wpf-toolbox-control"></a>Erstellen eines WPF-Toolbox-Steuerelements
Die Vorlage "WPF (Windows Presentation Framework)-Toolbox-Steuerelement" können Sie WPF-Steuerelemente erstellen, die automatisch hinzugefügt werden die **Toolbox** bei Installation der Erweiterung. In diesem Thema wird gezeigt, wie Sie die Vorlage verwenden, erstellen eine **Toolbox** Steuerelement, das Sie an andere Benutzer verteilen können.  
  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Erstellen eines WPF-Toolbox-Steuerelements  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Erstellen Sie eine Erweiterung mit einem WPF-Toolbox-Steuerelement  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `MyToolboxControl`. Sie finden die VSIX-Projektvorlage in die **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, fügen einen **WPF-Toolbox-Steuerelement** Elementvorlage, die mit dem Namen `MyToolboxControl`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **WPF-Toolbox-Steuerelement**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an `MyToolboxControl.cs`.  
  
     Die Projektmappe enthält jetzt ein Benutzersteuerelement, ein `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , die das Steuerelement addiert die **Toolbox**, und ein **Microsoft.VisualStudio.ToolboxControl** -Ressourceneintrag im VSIX-Manifest für  Bereitstellung.  
  
#### <a name="to-create-the-control-ui"></a>So erstellen Sie eine Steuerelement-Benutzeroberfläche  
  
1.  Öffnen Sie im Designer MyToolboxControl.xaml.  
  
     Der Designer zeigt eine <xref:System.Windows.Controls.Grid> -Steuerelement, enthält eine <xref:System.Windows.Controls.Button> Steuerelement.  
  
2.  Ordnen Sie Rasterlayout an. Bei Auswahl der <xref:System.Windows.Controls.Grid> zu steuern, Blau Steuerleisten auf den oberen und linken Rands des Rasters angezeigt werden. Sie können Zeilen und Spalten Raster hinzufügen, indem Sie auf die Balken.  
  
3.  Dem Raster untergeordnete Steuerelemente hinzuzufügen. Sie können ein untergeordnetes Steuerelement durch Ziehen von Positionieren der **Toolbox** zu einem Abschnitt des Rasters oder durch Festlegen seiner `Grid.Row` und `Grid.Column` Attribute im XAML. Im folgenden Beispiel werden zwei Bezeichnungen auf der obersten Zeile des Rasters und eine Schaltfläche auf der zweiten Zeile hinzugefügt.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Umbenennen des Steuerelements  
 Standardmäßig wird das Steuerelement angezeigt, der **Toolbox** als **MyToolboxControl** in einer Gruppe mit dem Namen **MyToolboxControl.MyToolboxControl**. Sie können diese Namen in der Datei MyToolboxControl.xaml.cs ändern.  
  
1.  MyToolboxControl.xaml.cs in der Codeansicht zu öffnen.  
  
2.  Suchen Sie die MyToolboxControl-Klasse, und benennen Sie sie in TestControl. (Die schnellste Möglichkeit hierzu ist, benennen Sie die Klasse, wählen Sie dann **umbenennen** aus dem Kontextmenü, und führen Sie die Schritte aus. (Weitere Informationen zu den **umbenennen** Befehl, finden Sie unter [Umgestaltung mit Umbenennung (c#)](../ide/reference/rename.md).)
  
3.  Wechseln Sie zu der `ProvideToolboxControl` Attribut, und ändern Sie den Wert des ersten Parameters **Test**. Dies ist der Name der Gruppe, die das Steuerelement in enthält die **Toolbox**.  
  
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
  
## <a name="building-testing-and-deployment"></a>Erstellen, Tests und Bereitstellung  
 Beim Debuggen des Projekts sollten Sie das Steuerelement installiert finden die **Toolbox** der experimentellen Instanz von Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>So erstellen Sie das Steuerelement und testen es  
  
1.  Das Projekt neu, und starten Sie das Debuggen.  
  
2.  Erstellen Sie in der neuen Instanz von Visual Studio ein WPF-Anwendungsprojekt. Stellen Sie sicher, dass die XAML-Designer geöffnet ist.  
  
3.  Suchen Sie in der **Toolbox** nach dem Steuerelement, und ziehen Sie es dann auf die Entwurfsoberfläche.  
  
4.  Debuggen Sie die WPF-Anwendung.  
  
5.  Stellen Sie sicher, dass das Steuerelement angezeigt wird.  
  
#### <a name="to-deploy-the-control"></a>So stellen Sie das Steuerelement bereit  
  
1.  Nachdem Sie das getestete Projekt erstellt haben, erhalten Sie die VSIX-Datei im Ordner "\bin\debug\" des Projekts.  
  
2.  Sie können es auf einem lokalen Computer installieren, durch Doppelklicken auf die VSIX-Datei, und befolgen die Installationsprozedur. Um das Steuerelement zu deinstallieren, wechseln Sie zu **Extras / Erweiterungen und Updates** die Control-Erweiterung gesucht, und klicken Sie auf **Deinstallieren**.  
  
3.  Laden Sie die VSIX-Datei in ein Netzwerk oder auf einer Website hoch.  
  
     Wenn Sie die Datei zum Hochladen der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) -Website, die andere Benutzer verwenden können **Extras / Erweiterungen und Updates** in Visual Studio online suchen und installieren Sie es.