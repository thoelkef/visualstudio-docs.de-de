---
title: 'Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a7d8649e0d8cf83650da58386901e638ec14a2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite
Sie können benutzereinstellungen für Ihre Startseite beibehalten. Anhand dieser exemplarischen Vorgehensweise können Sie ein Steuerelement erstellen, die eine Einstellung in der Registrierung gespeichert, wenn der Benutzer auf eine Schaltfläche klickt, und ruft dann ab, das jedes Mal, wenn die Startseite lädt festlegen. Da die Projektvorlage für Startseiten ein anpassbares Benutzersteuerelement umfasst, und die Standardeinstellung starten XAML-Code, die steuern aufruft, müssen Sie nicht die Startseite selbst ändern.  
  
 Der Einstellungen-Speicher, der in dieser exemplarischen Vorgehensweise instanziiert wird, ist eine Instanz von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> -Schnittstelle, die Lese- und Schreibvorgänge in folgendem Registrierungspfad, wenn sie aufgerufen wird: HKCU\Software\Microsoft\VisualStudio\14.0\\  *CollectionName*  
  
 Wenn es in der experimentellen Instanz von Visual Studio ausgeführt wird, der Informationsspeicher Einstellungen wird, liest und schreibt in HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*Auflistungsname.*  
  
 Weitere Informationen zum Beibehalten von Einstellungen finden Sie unter [Benutzereinstellungen erweitern und Optionen](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
> [!NOTE]
>  Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
>   
>  Sie können mithilfe der Projektvorlage für Startseiten herunterladen **Erweiterungs-Manager**.  
  
## <a name="setting-up-the-project"></a>Einrichten des Projekts  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>So konfigurieren Sie das Projekt für diese exemplarische Vorgehensweise  
  
1.  Erstellen Sie ein Startseitenprojekt wie beschrieben in [erstellen eine benutzerdefinierte Startseite](creating-a-custom-start-page.md). Nennen Sie das Projekt **SaveMySettings**.  
  
2.  In **Projektmappen-Explorer**, fügen Sie dem StartPageControl-Projekt die folgenden Assemblyverweise hinzu:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  Öffnen Sie „MeinSteuerelement.xaml“.  
  
4.  Aus dem XAML-Bereich, in der obersten Ebene <xref:System.Windows.Controls.UserControl> Elementdefinition, fügen Sie die folgenden Ereignisdeklaration nach befinden sich die Namespacedeklarationen hinzu.  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  Klicken Sie auf der wichtigste Bereich des Steuerelements in das Entwurfsfenster, und drücken Sie dann ENTF.  
  
     Dies entfernt das <xref:System.Windows.Controls.Border> Element und der gesamte, und bewirkt, dass nur der obersten Ebene <xref:System.Windows.Controls.Grid> Element.  
  
6.  Aus der **Toolbox**, ziehen Sie ein <xref:System.Windows.Controls.StackPanel> Steuerelement in den Entwurfsbereich.  
  
7.  Ziehen Sie jetzt eine <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>, und eine Schaltfläche, um die <xref:System.Windows.Controls.StackPanel>.  
  
8.  Hinzufügen einer **X: Name** -Attribut für die <xref:System.Windows.Controls.TextBox>, und ein `Click` -Ereignis für die <xref:System.Windows.Controls.Button>, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Implementieren des Benutzersteuerelements  
  
#### <a name="to-implement-the-user-control"></a>Um das Benutzersteuerelement zu implementieren.  
  
1.  Klicken Sie im XAML-mit der Maustaste die `Click` Attribut des der <xref:System.Windows.Controls.Button> -Element, und klicken Sie dann auf **zum Ereignishandler navigieren**.  
  
     Dadurch wird die MyControl.xaml.cs geöffnet, und erstellt einen Stub-Handler für das `Button_Click` Ereignis.  
  
2.  Fügen Sie die folgenden `using` -Anweisungen an den Anfang der Datei.  
  
     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  Hinzufügen eine privaten `SettingsStore` -Eigenschaft verwenden, wie im folgenden Beispiel gezeigt.  
  
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
  
     Diese Eigenschaft ruft zunächst einen Verweis auf die <xref:EnvDTE80.DTE2> -Schnittstelle, die das Automatisierungsobjektmodell von enthält die <xref:System.Windows.FrameworkElement.DataContext%2A> von des Benutzersteuerelements und verwendet zum Abrufen einer Instanz des DTE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> Schnittstelle. Er verwendet dann diese Instanz um die aktuellen benutzereinstellungen zurückzugeben.  
  
4.  Füllen Sie die `Button_Click` Ereignis wie folgt.  
  
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
  
     Schreibt den Inhalt des Textfelds, das auf ein Feld "MySetting" in einer Auflistung "MySettings" in der Registrierung. Wenn die Auflistung nicht vorhanden ist, wird er erstellt.  
  
5.  Fügen Sie den folgenden Ereignishandler für das `OnLoaded` -Ereignis für das Benutzersteuerelement.  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Dies legt den Text des Textfelds, das auf den aktuellen Wert von "MySetting" fest.  
  
6.  Erstellen Sie das Benutzersteuerelement.  
  
7.  In **Projektmappen-Explorer**, öffnen Sie die Datei "Source.Extension.vsixmanifest".  
  
8.  Legen Sie im manifest-Editor **Produktname** auf **speichern Meine Einstellungen Startseite**.  
  
     Dies legt den Namen der Startseite fest, wie er in angezeigt werden soll die **Startseite anpassen** in Liste der **Optionen** (Dialogfeld).  
  
9. Erstellen Sie "StartPage.xaml".  
  
## <a name="testing-the-control"></a>Testen des Steuerelements  
  
#### <a name="to-test-the-user-control"></a>So testen Sie das Benutzersteuerelement  
  
1.  Drücken Sie F5.  
  
     Die experimentelle Instanz von Visual Studio wird geöffnet.  
  
2.  In der experimentellen Instanz auf dem **Tools** Menü klicken Sie auf **Optionen**.  
  
3.  In der **Umgebung** Knoten, klicken Sie auf **Start**, und dann auf die **Startseite anpassen** Liste **[installierte Erweiterung] speichern Meine Einstellungen Startseite** .  
  
     Klicken Sie auf **OK**.  
  
4.  Schließen Sie die Seite starten, falls er geöffnet ist, klicken Sie dann auf die **Ansicht** Menü klicken Sie auf **Startseite**.  
  
5.  Klicken Sie auf der Startseite auf die **MyControl** Registerkarte.  
  
6.  Geben Sie in das Textfeld **Cat**, und klicken Sie dann auf **Meine Einstellung speichern**.  
  
7.  Schließen Sie die Startseite, und öffnen Sie es dann erneut.  
  
     Das Wort "Katze" sollte im Textfeld angezeigt werden.  
  
8.  Ersetzen Sie das Wort "Katze" mit dem Wort "Dog". Klicken Sie nicht auf die Schaltfläche "".  
  
9. Schließen Sie die Startseite, und öffnen Sie es dann erneut.  
  
     Das Wort "Dog" sollte in das Textfeld angezeigt werden, obwohl die Einstellung wurde nicht gespeichert. Dies geschieht da Visual Studio ein Toolfenster im Arbeitsspeicher bleibt, auch wenn sie geschlossen werden, bis Visual Studio selbst geschlossen wird.  
  
10. Schließen Sie die experimentelle Instanz von Visual Studio.  
  
11. Drücken Sie F5, um die experimentelle Instanz erneut zu öffnen.  
  
12. Das Wort "Katze" sollte im Textfeld angezeigt werden.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie können dieses Benutzersteuerelement zum Speichern und Abrufen von eine beliebige Anzahl von benutzerdefinierten Einstellungen mithilfe von verschiedenen Werten anderen Ereignishandler zum Abrufen und Festlegen der `SettingsStore` Eigenschaft. Solange Sie einen anderen verwenden `propertyName` Parameter für jeden Aufruf von <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, überschreiben die Werte werden nicht zueinander in der Registrierung.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [Hinzufügen von Visual Studio-Befehlen zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)