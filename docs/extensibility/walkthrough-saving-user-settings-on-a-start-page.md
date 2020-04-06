---
title: 'Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8c791bb33d6c6a3952c14d5073857b0c3131cecf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697071"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite

Sie können die Benutzereinstellungen für Ihre Startseite beibehalten. Wenn Sie dieser exemplarischen Vorgehensweise folgen, können Sie ein Steuerelement erstellen, das eine Einstellung in der Registrierung speichert, wenn der Benutzer auf eine Schaltfläche klickt, und diese Einstellung dann jedes Mal abruft, wenn die Startseite geladen wird. Da die Projektvorlage Startseite ein anpassbares Benutzersteuerelement und die standardmäßigen XAML-Aufrufe der Startseite dieses Steuerelements enthält, müssen Sie die Startseite selbst nicht ändern.

Der Einstellungsspeicher, der in dieser exemplarischen Vorgehensweise <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> instanziiert wird, ist eine Instanz der Schnittstelle, die den folgenden Registrierungsspeicherort liest und schreibt, wenn er aufgerufen wird: **HKCU-Software-Microsoft-VisualStudio-14.0\\\<CollectionName>**

Wenn es in der experimentellen Instanz von Visual Studio ausgeführt wird, liest und schreibt der Einstellungsspeicher> in **HKCU-Software,Microsoft-VisualStudio-14.0Exp\\\<CollectionName.**

Weitere Informationen zum Beibehalten von Einstellungen finden Sie unter Erweitern von [Benutzereinstellungen und -optionen](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> Sie können die Projektvorlage Startseite mit **Extension Manager**herunterladen.

## <a name="set-up-the-project"></a>Einrichten des Projekts

1. Erstellen Sie ein Startseitenprojekt, wie unter [Erstellen einer benutzerdefinierten Startseite](creating-a-custom-start-page.md)beschrieben. Benennen Sie das Projekt **SaveMySettings**.

2. Fügen Sie im **Projektmappen-Explorer**die folgenden Assemblyverweise zum StartPageControl-Projekt hinzu:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Öffnen Sie *MyControl.xaml*.

4. Fügen Sie im XAML-Bereich <xref:System.Windows.Controls.UserControl> in der Elementdefinition der obersten Ebene die folgende Ereignisdeklaration nach den Namespacedeklarationen hinzu.

    ```xml
    Loaded="OnLoaded"
    ```

5. Klicken Sie im Entwurfsbereich auf den Hauptbereich des Steuerelements, und drücken Sie dann **Löschen**.

     In diesem Schritt <xref:System.Windows.Controls.Border> werden das Element und alles darin <xref:System.Windows.Controls.Grid> entfernt, und es bleibt nur das Element der obersten Ebene.

6. Ziehen **Toolbox**Sie aus <xref:System.Windows.Controls.StackPanel> der Toolbox ein Steuerelement in das Raster.

7. Ziehen Sie <xref:System.Windows.Controls.TextBlock>nun <xref:System.Windows.Controls.TextBox>a , a <xref:System.Windows.Controls.StackPanel>und eine Schaltfläche auf die .

8. Fügen Sie ein **x:Name-Attribut** für das <xref:System.Windows.Controls.TextBox>hinzu und ein `Click` Ereignis für die <xref:System.Windows.Controls.Button>, wie im folgenden Beispiel gezeigt.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementieren des Benutzersteuerelements

1. Klicken Sie im XAML-Bereich `Click` mit <xref:System.Windows.Controls.Button> der rechten Maustaste auf das Attribut des Elements, und klicken Sie dann auf **Navigieren zum Ereignishandler**.

     Dieser Schritt öffnet *MyControl.xaml.cs*und erstellt `Button_Click` einen Stubhandler für das Ereignis.

2. Fügen Sie `using` die folgenden Direktiven am oberen Rand der Datei hinzu.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Fügen Sie `SettingsStore` eine private Eigenschaft hinzu, wie im folgenden Beispiel gezeigt.

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

     Diese Eigenschaft ruft zuerst <xref:EnvDTE80.DTE2> einen Verweis auf die Schnittstelle ab, die das Automation-Objektmodell enthält, aus <xref:System.Windows.FrameworkElement.DataContext%2A> dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> Benutzersteuerelement und verwendet dann die DTE, um eine Instanz der Schnittstelle abzuverweisen. Anschließend wird diese Instanz verwendet, um die aktuellen Benutzereinstellungen zurückzugeben.

4. Füllen Sie `Button_Click` das Ereignis wie folgt aus.

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

     Dadurch wird der Inhalt des Textfelds in ein "MySetting"-Feld in einer "MySettings"-Auflistung in der Registrierung geschrieben. Wenn die Auflistung nicht vorhanden ist, wird sie erstellt.

5. Fügen Sie den `OnLoaded` folgenden Handler für das Ereignis des Benutzersteuerelements hinzu.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Dieser Code legt den Text des Textfeldes auf den aktuellen Wert von "MySetting" fest.

6. Erstellen Sie das Benutzersteuerelement.

7. Im **Projektmappen-Explorer**open *source.extension.vsixmanifest*.

8. Legen Sie im Manifest-Editor den **Produktnamen** auf **Startseite "Meine Einstellungen speichern"** fest.

     Diese Funktion legt den Namen der Startseite so fest, wie sie in der Liste **Startseite anpassen** im Dialogfeld **Optionen** angezeigt werden soll.

9. Erstellen Sie *StartPage.xaml*.

## <a name="test-the-control"></a>Testen des Steuerelements

1. Drücken Sie **F5**.

     Die experimentelle Instanz von Visual Studio wird geöffnet.

2. Klicken Sie in der experimentellen Instanz im Menü **Extras** auf **Optionen**.

3. Klicken Sie im **Umgebungsknoten** auf **Start**, und wählen Sie dann in der Liste **Startseite anpassen** **[Installierte Erweiterung] Startseite meine Einstellungen**speichern aus .

     Klicken Sie auf **OK**.

4. Schließen Sie die Startseite, wenn sie geöffnet ist, und klicken Sie dann im Menü **Ansicht** auf **Startseite**.

5. Klicken Sie auf der Startseite auf die Registerkarte **MyControl.**

6. Geben Sie im Textfeld **Cat**ein, und klicken Sie dann auf **Meine Einstellung speichern**.

7. Schließen Sie die Startseite, und öffnen Sie sie erneut.

     Das Wort "Katze" sollte im Textfeld angezeigt werden.

8. Ersetzen Sie das Wort "Katze" durch das Wort "Hund". Klicken Sie nicht auf die Schaltfläche.

9. Schließen Sie die Startseite, und öffnen Sie sie erneut.

     Das Wort "Hund" sollte im Textfeld angezeigt werden, auch wenn Sie die Einstellung nicht gespeichert haben, da Visual Studio Toolfenster im Arbeitsspeicher speichert, auch wenn sie geschlossen sind, bis Visual Studio selbst geschlossen wird.

10. Schließen Sie die experimentelle Instanz von Visual Studio.

11. Drücken Sie **F5,** um die experimentelle Instanz erneut zu öffnen.

12. Das Wort "Katze" sollte im Textfeld angezeigt werden.

## <a name="next-steps"></a>Nächste Schritte

Sie können dieses Benutzersteuerelement ändern, um eine beliebige Anzahl benutzerdefinierter Einstellungen zu speichern `SettingsStore` und abzurufen, indem Sie verschiedene Werte von verschiedenen Ereignishandlern verwenden, um die Eigenschaft abzurufen und festzulegen. Solange Sie für jeden `propertyName` Aufruf einen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>anderen Parameter verwenden, überschreiben sich die Werte in der Registrierung nicht gegenseitig.

## <a name="see-also"></a>Weitere Informationen

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Hinzufügen von Visual Studio-Befehlen zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
