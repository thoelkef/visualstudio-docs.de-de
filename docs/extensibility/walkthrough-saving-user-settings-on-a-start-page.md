---
title: 'Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 18
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
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 1bf8a313898f9c12312beedb31238fb74e1a56a8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen einer Startseite
Sie können benutzereinstellungen für Ihre Startseite beibehalten. Anhand dieser exemplarischen Vorgehensweise können Sie ein Steuerelement erstellen, die eine Einstellung in der Registrierung gespeichert, wenn der Benutzer auf eine Schaltfläche klickt, und ruft dann ab, das jedes Mal, wenn die Seite lädt festlegen. Da die Startseite-Projektvorlage ein anpassbares Steuerelement enthält und der Standard-XAML-Starten von Seite, die steuern aufruft, müssen Sie nicht so ändern Sie die Seite selbst.  
  
 Die Einstellungen speichern, die in dieser exemplarischen Vorgehensweise instanziiert wird, ist eine Instanz der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>-Schnittstelle, die liest und schreibt in den folgenden Registrierungsschlüssel, wenn sie aufgerufen wird: HKCU\Software\Microsoft\VisualStudio\14.0\\*Auflistungsname* </xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>  
  
 Wenn sie in der experimentellen Instanz von Visual Studio ausgeführt wird, wird der einstellungsspeicher liest und schreibt in HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*Auflistungsname.*  
  
 Weitere Informationen dazu, wie Sie die Standardeinstellungen beibehalten werden, finden Sie unter [Benutzereinstellungen erweitern und Optionen](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
> [!NOTE]
>  Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
>   
>  Sie können mit die Projektvorlage Startseite herunterladen **Extension Manager**.  
  
## <a name="setting-up-the-project"></a>Einrichten des Projekts  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>So konfigurieren Sie das Projekt für diese exemplarische Vorgehensweise  
  
1.  Erstellen Sie ein Startseitenprojekt, wie unter beschrieben [erstellen eine benutzerdefinierte Startseite](creating-a-custom-start-page.md). Nennen Sie das Projekt **SaveMySettings**.  
  
2.  In **Projektmappen-Explorer**, fügen Sie dem StartPageControl-Projekt die folgenden Assemblyverweise hinzu:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  Öffnen Sie „MeinSteuerelement.xaml“.  
  
4.  In der obersten Ebene im Bereich von XAML- <xref:System.Windows.Controls.UserControl>Elementdefinition, fügen Sie die folgenden Ereignisdeklaration nach den Namespacedeklarationen.</xref:System.Windows.Controls.UserControl>  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  Klicken Sie im Entwurfsbereich auf den Hauptbereich des Steuerelements, und drücken Sie dann ENTF.  
  
     Dies entfernt das <xref:System.Windows.Controls.Border>-Element, und alles und bewirkt, dass nur der obersten Ebene <xref:System.Windows.Controls.Grid>Element.</xref:System.Windows.Controls.Grid> </xref:System.Windows.Controls.Border>  
  
6.  Aus der **Toolbox**, ziehen Sie ein <xref:System.Windows.Controls.StackPanel>Steuerelement zum Raster.</xref:System.Windows.Controls.StackPanel>  
  
7.  Ziehen Sie jetzt eine <xref:System.Windows.Controls.TextBlock>, ein <xref:System.Windows.Controls.TextBox>, und eine Schaltfläche mit dem <xref:System.Windows.Controls.StackPanel>.</xref:System.Windows.Controls.StackPanel> </xref:System.Windows.Controls.TextBox> </xref:System.Windows.Controls.TextBlock>  
  
8.  Hinzufügen einer **X: Name** -Attribut für die <xref:System.Windows.Controls.TextBox>, und ein `Click` -Ereignis für die <xref:System.Windows.Controls.Button>, wie im folgenden Beispiel gezeigt.</xref:System.Windows.Controls.Button> </xref:System.Windows.Controls.TextBox>  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Implementieren des Benutzersteuerelements  
  
#### <a name="to-implement-the-user-control"></a>Das Benutzersteuerelement implementiert.  
  
1.  Klicken Sie im XAML-Bereich mit der rechten Maustaste die `Click` -Attribut des der <xref:System.Windows.Controls.Button>-Element, und klicken Sie dann auf **zum Ereignishandler navigieren**.</xref:System.Windows.Controls.Button>  
  
     Dadurch wird die MyControl.xaml.cs geöffnet, und erstellt einen Stub-Ereignishandler für das `Button_Click` Ereignis.  
  
2.  Fügen Sie die folgenden `using` Anweisungen am Anfang der Datei.  
  
     [!code-cs[StartPageDTE&#11;](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  Fügen Sie einen privaten `SettingsStore` -Eigenschaft, wie im folgenden Beispiel gezeigt.  
  
    ```c#  
    private IVsWritableSettingsStore _settingsStore = null;  
    private IVsWritableSettingsStore SettingsStore  
    {  
        get  
        {  
            if (_settingsStore == null)  
            {  
                // Get a reference to the DTE from the DataContext.   
                var typeDescriptor = DataContext as ICustomTypeDescriptor;  
                var propertyCollection = typeDescriptor.GetProperties();  
                var dte = propertyCollection.Find("DTE", false).GetValue(  
                    DataContext) as DTE2;  
  
                // Get the settings manager from the DTE.   
                var serviceProvider = new ServiceProvider(  
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
                var settingsManager = serviceProvider.GetService(  
                    typeof(SVsSettingsManager)) as IVsSettingsManager;  
  
                // Write the user settings to _settingsStore.  
                settingsManager.GetWritableSettingsStore(  
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,  
                    out _settingsStore);  
            }  
            return _settingsStore;  
        }  
    }  
    ```  
  
     Diese Eigenschaft ruft zunächst einen Verweis auf die <xref:EnvDTE80.DTE2>-Schnittstelle, die das Automatisierungsobjektmodell von enthält die <xref:System.Windows.FrameworkElement.DataContext%2A>für das Benutzersteuerelement, und verwendet, um eine Instanz des DTE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>Schnittstelle.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> </xref:System.Windows.FrameworkElement.DataContext%2A> </xref:EnvDTE80.DTE2> Es verwendet dann diese Instanz die aktuellen benutzereinstellungen zurückgeben.  
  
4.  Füllen Sie die `Button_Click` Ereignis wie folgt.  
  
    ```c#  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        int exists = 0;  
        SettingsStore.CollectionExists("MySettings", out exists);  
        if (exists != 1)  
        {  
            SettingsStore.CreateCollection("MySettings");  
        }  
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);  
    }  
    ```  
  
     Schreibt den Inhalt des Textfelds an ein Feld "MySetting" in einer Auflistung "MySettings" in der Registrierung. Wenn die Auflistung nicht vorhanden ist, wird es erstellt.  
  
5.  Fügen Sie den folgenden Ereignishandler für das `OnLoaded` Ereignis des Benutzersteuerelements.  
  
    ```c#  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Dadurch wird den Text im Textfeld auf den aktuellen Wert des "MySetting".  
  
6.  Erstellen Sie das Benutzersteuerelement.  
  
7.  In **Projektmappen-Explorer**, "Source.Extension.vsixmanifest" zu öffnen.  
  
8.  Legen Sie im manifest-Editor **Produktname** auf **speichern Meine Einstellungen Startseite**.  
  
     Dadurch wird der Name der Startseite, wie er in angezeigt werden soll die **Startseite anpassen** Liste der **Optionen** Dialogfeld.  
  
9. Erstellen Sie StartPage.xaml.  
  
## <a name="testing-the-control"></a>Testen des Steuerelements  
  
#### <a name="to-test-the-user-control"></a>So testen Sie das Benutzersteuerelement  
  
1.  Drücken Sie F5.  
  
     Die experimentelle Instanz von Visual Studio wird geöffnet.  
  
2.  In der experimentellen Instanz auf die **Tools** Menü klicken Sie auf **Optionen**.  
  
3.  In der **Umgebung** Knoten, klicken Sie auf **Start**, und klicken Sie dann auf die **Startseite anpassen** wählen **[installierte Erweiterung] speichern Sie Meine Einstellungen Startseite**.  
  
     Klicken Sie auf **OK**.  
  
4.  Die Seite schließen, falls es geöffnet ist, und klicken Sie dann auf die **Ansicht** Menü klicken Sie auf **Startseite**.  
  
5.  Klicken Sie auf der Startseite auf die **MyControl** Registerkarte.  
  
6.  Geben Sie in das Textfeld **Cat**, und klicken Sie dann auf **eigene Einstellung speichern**.  
  
7.  Schließen Sie die Seite, und öffnen Sie es dann erneut.  
  
     Das Wort "Cat" im Textfeld angezeigt werden soll.  
  
8.  Ersetzen Sie das Wort "Cat" durch das Wort "Hund". Klicken Sie nicht auf die Schaltfläche.  
  
9. Schließen Sie die Seite, und öffnen Sie es dann erneut.  
  
     Auch wenn die Einstellung nicht gespeichert wurde, sollte das Wort "Dog" in das Textfeld angezeigt werden. Dies geschieht da Visual Studio-Fenster im Arbeitsspeicher bleibt, selbst wenn sie geschlossen werden, bis Visual Studio selbst geschlossen wird.  
  
10. Schließen Sie die experimentelle Instanz von Visual Studio.  
  
11. Drücken Sie F5, um die experimentelle Instanz erneut zu öffnen.  
  
12. Das Wort "Cat" im Textfeld angezeigt werden soll.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie können ändern, dieses Steuerelement zum Speichern und Abrufen von einer beliebigen Anzahl benutzerdefinierter Einstellungen mithilfe von verschiedenen Werten verschiedene Ereignishandler zum Abrufen und Festlegen der `SettingsStore` Eigenschaft. Solange die Verwendung eines anderen `propertyName` Parameter für jeden Aufruf von <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, die Werte überschreiben einander nicht in der Registrierung.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>  
  
## <a name="see-also"></a>Siehe auch  
 <xref:EnvDTE80.DTE2?displayProperty=fullName></xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [Hinzufügen von Visual Studio-Befehle zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
