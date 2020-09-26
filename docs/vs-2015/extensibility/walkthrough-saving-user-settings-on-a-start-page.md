---
title: 'Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Start Seite | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8976d329f6303d60cc00609bc9ed9471456c1b63
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "91391700"
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Benutzereinstellungen für die Startseite persistent speichern. Mithilfe dieser exemplarischen Vorgehensweise können Sie ein Steuerelement erstellen, mit dem eine Einstellung in der Registrierung gespeichert wird, wenn der Benutzer auf eine Schaltfläche klickt, und diese Einstellung bei jedem Laden der Start Seite abruft. Da die Projektvorlage für Startseiten ein anpassbares Benutzer Steuerelement enthält und die standardmäßige XAML-Startseite dieses Steuerelement aufruft, müssen Sie die Startseite nicht ändern.  
  
 Der Einstellungs Speicher, der in dieser exemplarischen Vorgehensweise instanziiert wird, ist eine Instanz der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> -Schnittstelle, die den folgenden Registrierungs Speicherort liest und schreibt, wenn Sie aufgerufen wird: hkcu\software\microsoft\visualstudio\14,0 \\ *CollectionName*  
  
 Wenn Sie in der experimentellen Instanz von Visual Studio ausgeführt wird, werden die Einstellungen in hkcu\software\microsoft\visualstudio\14.0exp \\ *CollectionName* gelesen und geschrieben.  
  
 Weitere Informationen zum Beibehalten von Einstellungen finden Sie unter [Erweitern von Benutzereinstellungen und-Optionen](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
> [!NOTE]
> Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
>   
> Sie können die Projektvorlage für Start Seiten mit dem **Erweiterungs-Manager**herunterladen.  
  
## <a name="setting-up-the-project"></a>Einrichten des Projekts  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>So konfigurieren Sie das Projekt für diese exemplarische Vorgehensweise  
  
1. Erstellen Sie ein Startseiten Projekt mithilfe der Projektvorlage für Startseiten, wie unter [Erstellen einer eigenen Startseite](../misc/creating-your-own-start-page.md)beschrieben. Nennen Sie das Projekt **savemysettings**.  
  
2. Fügen Sie in **Projektmappen-Explorer**dem startpagecontrol-Projekt die folgenden Assemblyverweise hinzu:  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - Microsoft.VisualStudio.OLE.Interop  
  
    - Microsoft.VisualStudio.Shell.Interop.11.0  
  
3. Öffnen Sie „MeinSteuerelement.xaml“.  
  
4. Fügen Sie im XAML-Bereich in der Element Definition der obersten Ebene <xref:System.Windows.Controls.UserControl> nach den Namespace Deklarationen die folgende Ereignis Deklaration hinzu.  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5. Klicken Sie im Entwurfs Bereich auf den Hauptbereich des-Steuer Elements, und drücken Sie dann ENTF.  
  
     Dadurch wird das <xref:System.Windows.Controls.Border> -Element und alles darin entfernt, und es wird nur das Element der obersten Ebene beibehalten <xref:System.Windows.Controls.Grid> .  
  
6. Ziehen Sie aus der **Toolbox**ein- <xref:System.Windows.Controls.StackPanel> Steuerelement in das Raster.  
  
7. Ziehen Sie nun eine <xref:System.Windows.Controls.TextBlock> , eine <xref:System.Windows.Controls.TextBox> und eine Schaltfläche in den <xref:System.Windows.Controls.StackPanel> .  
  
8. Fügen Sie ein **x:Name** -Attribut für den <xref:System.Windows.Controls.TextBox> und ein- `Click` Ereignis für das hinzu <xref:System.Windows.Controls.Button> , wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Implementieren des Benutzer Steuer Elements  
  
#### <a name="to-implement-the-user-control"></a>So implementieren Sie das Benutzer Steuerelement  
  
1. Klicken Sie im XAML-Bereich mit der rechten Maustaste auf das- `Click` Attribut des- <xref:System.Windows.Controls.Button> Elements, und klicken Sie dann auf **zu Ereignis Handler navigieren**.  
  
     Dadurch wird myControl.XAML.CS geöffnet, und es wird ein Stub-Handler für das- `Button_Click` Ereignis erstellt.  
  
2. Fügen Sie am Anfang der Datei die folgenden `using`-Anweisungen hinzu.  
  
     [!code-csharp[StartPageDTE#11](../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs#11)]  
  
3. Fügen Sie eine private- `SettingsStore` Eigenschaft hinzu, wie im folgenden Beispiel gezeigt.  
  
    ```csharp  
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
  
     Diese Eigenschaft ruft zuerst einen Verweis auf die- <xref:EnvDTE80.DTE2> Schnittstelle ab, die das Automatisierungs Objektmodell aus dem <xref:System.Windows.FrameworkElement.DataContext%2A> des Benutzer Steuer Elements enthält, und verwendet dann den DTE, um eine Instanz der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> Schnittstelle zu erhalten. Anschließend wird diese Instanz verwendet, um die aktuellen Benutzereinstellungen zurückzugeben.  
  
4. Füllen Sie das `Button_Click` Ereignis wie folgt aus.  
  
    ```csharp  
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
  
     Dadurch wird der Inhalt des Textfelds in das Feld "MySetting" in der Sammlung "MySettings" in der Registrierung geschrieben. Wenn die Auflistung nicht vorhanden ist, wird Sie erstellt.  
  
5. Fügen Sie den folgenden Handler für das- `OnLoaded` Ereignis des Benutzer Steuer Elements hinzu.  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Dadurch wird der Text des Textfelds auf den aktuellen Wert von "MySetting" festgelegt.  
  
6. Erstellen Sie das Benutzer Steuerelement.  
  
7. Öffnen Sie in **Projektmappen-Explorer**die Datei Source. Extension. vsixmanifest.  
  
8. Legen Sie im Manifest-Editor den **Product Name** auf **Start Seite Meine Einstellungen speichern**fest.  
  
     Dadurch wird der Name der Startseite so festgelegt, dass Sie im Dialogfeld **Optionen** in der Liste **Startseite anpassen** angezeigt wird.  
  
9. Build StartPage. XAML.  
  
## <a name="testing-the-control"></a>Testen des Steuerelements  
  
#### <a name="to-test-the-user-control"></a>So testen Sie das Benutzer Steuerelement  
  
1. Drücken Sie F5.  
  
     Die experimentelle Instanz von Visual Studio wird geöffnet.  
  
2. Klicken Sie **in der experimentellen Instanz im Menü Extras** auf **Optionen**.  
  
3. Klicken Sie im Knoten **Umgebung** auf **Start**, und wählen Sie dann in der Liste **Startseite anpassen** die Option **[installierte Erweiterung] Startseite Einstellungen speichern**aus.  
  
     Klicken Sie auf **OK**.  
  
4. Schließen Sie die Startseite, wenn Sie geöffnet ist, und klicken Sie dann im Menü **Ansicht** auf **Start Seite**.  
  
5. Klicken Sie auf der Start Seite auf die Registerkarte **MyControl** .  
  
6. Geben Sie im Textfeld **Cat**ein, und klicken Sie dann auf **meine Einstellung speichern**.  
  
7. Schließen Sie die Start Seite, und öffnen Sie Sie erneut.  
  
     Das Wort "Cat" sollte im Textfeld angezeigt werden.  
  
8. Ersetzen Sie das Wort "Cat" durch das Wort "Dog". Klicken Sie nicht auf die Schaltfläche.  
  
9. Schließen Sie die Start Seite, und öffnen Sie Sie erneut.  
  
     Das Wort "Dog" sollte im Textfeld angezeigt werden, auch wenn die Einstellung nicht gespeichert wurde. Dies liegt daran, dass Visual Studio die Tool Fenster im Arbeitsspeicher beibehält, auch wenn Sie geschlossen sind, bis Visual Studio selbst geschlossen wird.  
  
10. Schließen Sie die experimentelle Instanz von Visual Studio.  
  
11. Drücken Sie F5, um die experimentelle Instanz erneut zu öffnen.  
  
12. Das Wort "Cat" sollte im Textfeld angezeigt werden.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie können dieses Benutzer Steuerelement ändern, um eine beliebige Anzahl benutzerdefinierter Einstellungen zu speichern und abzurufen, indem Sie unterschiedliche Werte aus unterschiedlichen Ereignis Handlern verwenden, um die Eigenschaft abzurufen und festzulegen `SettingsStore` . Solange Sie `propertyName` für jeden-Aufrufvorgang einen anderen Parameter verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> , überschreiben die Werte in der Registrierung nicht einander.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>   
 [Erstellen einer eigenen Start Seite](../misc/creating-your-own-start-page.md)   
 [Hinzufügen von Visual Studio-Befehlen zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
