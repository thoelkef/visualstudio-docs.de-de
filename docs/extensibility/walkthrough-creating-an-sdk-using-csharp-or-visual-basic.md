---
title: 'Exemplarische Vorgehensweise: Erstellen einer SDK mit C# oder Visual Basic | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 6bb9ae53dfb2e849c35c05fe5187cddcf301622c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312641"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Exemplarische Vorgehensweise: Erstellen Sie eine SDK mit C# oder Visual Basic
In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie mit Visual C#-Erstellen eines einfachen Math-Bibliothek-SDK und klicken Sie dann das SDK als ein Visual Studio-Erweiterung (VSIX)-Paket. Sie müssen die folgenden Schritte auszuführen:

- [So erstellen Sie die SimpleMath Windows Runtime-Komponente](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Erstellen Sie das Erweiterungsprojekt SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Zum Erstellen einer Beispielapp verwendet, die die Bibliothek.](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Vorraussetzungen
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="createClassLibrary"></a> So erstellen Sie die SimpleMath Windows Runtime-Komponente

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. Erweitern Sie in der Liste der Vorlagen, **Visual C#-** oder **Visual Basic**, wählen Sie die **Windows Store** Knoten, und wählen Sie dann die **Komponente für Windows-Runtime** Vorlage.

3. In der **Namen** geben **SimpleMath**, und wählen Sie dann die **OK** Schaltfläche.

4. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMath** Projektknoten, und wählen Sie dann **Eigenschaften**.

5. Benennen Sie **"Class1.cs"** zu **Arithmetic.cs** und aktualisieren, um entsprechend folgendem Code:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Lösung "SimpleMath"** Knoten, und wählen Sie dann **Configuration Manager**.

    Die **Configuration Manager** Dialogfeld wird geöffnet.

7. In der **aktive Projektmappenkonfiguration** wählen **Version**.

8. In der **Konfiguration** Spalte überprüfen Sie, ob **SimpleMath** Zeile nastaven NA hodnotu **Version**, und wählen Sie dann die **schließen** Schaltfläche zum Akzeptieren der Ändern Sie.

   > [!IMPORTANT]
   > Das SDK für die Komponente SimpleMath enthält nur eine Konfiguration. Diese Konfiguration muss die endgültige Produktversion sein, oder apps, die die Komponente wird nicht Zertifizierung übergeben, für die [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].

9. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMath** Projektknoten, und wählen Sie dann **erstellen**.

## <a name="createVSIX"></a> Erstellen Sie das Erweiterungsprojekt SimpleMathVSIX

1. Auf der rechten Maustaste auf die **Lösung "SimpleMath"** Knoten, wählen Sie **hinzufügen** > **neues Projekt**.

2. Erweitern Sie in der Liste der Vorlagen, **Visual C#-** oder **Visual Basic**, wählen Sie die **Erweiterbarkeit** Knoten, und wählen Sie dann die **VSIX-Projekt** Vorlage.

3. In der **Namen** geben **SimpleMathVSIX**, und wählen Sie dann die **OK** Schaltfläche.

4. In **Projektmappen-Explorer**, wählen Sie die **"Source.Extension.vsixmanifest"** Element.

5. Wählen Sie in der Menüleiste **Ansicht** > **Code** aus.

6. Ersetzen Sie den vorhandenen XML-Code durch folgendes XML:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. In **Projektmappen-Explorer**, wählen Sie die **SimpleMathVSIX** Projekt.

8. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

9. In der Liste der **gemeinsame Elemente**, erweitern Sie **Daten**, und wählen Sie dann **XML-Datei**.

10. In der **Namen** geben `SDKManifest.xml`, und wählen Sie dann die **hinzufügen** Schaltfläche.

11. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für `SDKManifest.xml`, wählen Sie **Eigenschaften**, und ändern Sie den Wert, der die **Include in VSIX-Datei** Eigenschaft **"True"** .

12. Ersetzen Sie den Inhalt der Datei durch folgendes XML:

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMathVSIX** Projekts **hinzufügen**, und wählen Sie dann **neuer Ordner**.

14. Benennen Sie den Ordner zu `references`.

15. Öffnen Sie das Kontextmenü für die **Verweise** Ordner wählen **hinzufügen**, und wählen Sie dann **neuer Ordner**.

16. Benennen Sie den Unterordner zu `commonconfiguration`, erstellen Sie einen Unterordner darin, und nennen Sie den Unterordner `neutral`.

17. Wiederholen Sie die vorhergehenden vier Schritte, die dieses Mal den ersten Ordner umbenennen `redist`.

     Das Projekt enthält nun die folgende Ordnerstruktur:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMath** Projekt, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.

19. In **Datei-Explorer**, navigieren Sie zu der *"bin\Release"* Ordner, öffnen Sie das Kontextmenü für die **SimpleMath.winmd** Datei, und wählen Sie dann **kopieren**.

20. In **Projektmappen-Explorer**, fügen Sie die Datei in die *References\commonconfiguration\neutral* Ordner in der **SimpleMathVSIX** Projekt.

21. Wiederholen Sie den vorherigen Schritt einfügen der **SimpleMath.pri** Eingabedatei in die *Redist\commonconfiguration\neutral* Ordner in der **SimpleMathVSIX** Projekt.

22. In **Projektmappen-Explorer**, wählen Sie **SimpleMath.winmd**.

23. Wählen Sie auf der Menüleiste **Ansicht** > **Eigenschaften** (Tastatur: Wählen Sie die **F4** Schlüssel).

24. In der **Eigenschaften** Ändern der **Buildvorgang** Eigenschaft **Content**, und ändern Sie dann die **Include in VSIX-Datei** Eigenschaft  **"True"** .

25. In **Projektmappen-Explorer**, wiederholen Sie diesen Vorgang für **SimpleMath.pri**.

26. In **Projektmappen-Explorer**, wählen Sie die **SimpleMathVSIX** Projekt.

27. Wählen Sie auf der Menüleiste **erstellen** > **erstellen SimpleMathVSIX**.

28. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMathVSIX** Projekt, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.

29. In **Datei-Explorer**, navigieren Sie zu *\bin\Release* Ordner, und führen Sie *SimpleMathVSIX.vsix* installieren.

30. Wählen Sie die **installieren** Schaltfläche warten, bis zum Abschluss der Installation, und klicken Sie dann Visual Studio neu starten.

## <a name="createSample"></a> Zum Erstellen einer Beispielapp verwendet, die die Bibliothek.

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. Erweitern Sie in der Liste der Vorlagen, **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **Windows Store** Knoten.

3. Wählen Sie die **leere App** Vorlage, nennen Sie das Projekt **ArithmeticUI**, und wählen Sie dann die **OK** Schaltfläche.

4. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ArithmeticUI** Projekt, und wählen Sie dann **hinzufügen** > **Verweis**.

5. Erweitern Sie in der Liste der Verweistypen, **Windows**, und wählen Sie dann **Erweiterungen**.

6. Wählen Sie im Detailbereich die **WinRT-Math-Bibliothek** Erweiterung.

    Weitere Informationen zu Ihrem SDK wird angezeigt. Sie können die **mehr Informationen** Link zum Öffnen https://msdn.microsoft.com/, wie Sie in der SDKManifest.xml-Datei weiter oben in dieser exemplarischen Vorgehensweise angegeben.

7. In der **Verweis-Manager** wählen Sie im Dialogfeld die **WinRT-Math-Bibliothek** aus, und wählen Sie dann die **OK** Schaltfläche.

8. Wählen Sie auf der Menüleiste **Ansicht** > **Objektkatalog**.

9. In der **Durchsuchen** wählen **einfache mathematische**.

     Sie können nun untersuchen, was im SDK ist.

10. In **Projektmappen-Explorer**öffnen **"MainPage.xaml"** , und Ersetzen Sie den Inhalt mit den folgenden XAML:

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. Update **"MainPage.Xaml.cs"** entsprechend den folgenden Code:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Wählen Sie die **F5** Taste, um die app auszuführen.

13. Geben Sie in der app, die zwei Zahlen, wählen Sie einen Vorgang aus, und wählen Sie dann die **=** Schaltfläche.

     Das richtige Ergebnis wird angezeigt.

    Sie haben erfolgreich erstellt und verwendet eine Erweiterungs-SDK.

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Erstellen eines SDKS mit C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Exemplarische Vorgehensweise: Erstellen eines SDKS mit JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)
