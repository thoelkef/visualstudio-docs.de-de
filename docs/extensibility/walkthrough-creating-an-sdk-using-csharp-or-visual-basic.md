---
title: 'Exemplarische Vorgehensweise: Erstellen eines SDK mit C- oder Visual Basic | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16eb20452601a65c498ff112ea996f2d93559940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697558"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Exemplarische Vorgehensweise: Erstellen eines SDK mit C- oder Visual Basic-Code
In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie ein einfaches Mathebibliotheks-SDK mithilfe von Visual C- erstellen und dann das SDK als Visual Studio-Erweiterung (VSIX) verpacken. Sie führen die folgenden Verfahren aus:

- [So erstellen Sie die SimpleMath Windows Runtime-Komponente](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [So erstellen Sie das Erweiterungsprojekt SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [So erstellen Sie eine Beispiel-App, die die Klassenbibliothek verwendet](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Voraussetzungen
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>So erstellen Sie die SimpleMath Windows Runtime-Komponente

1. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt**aus.

2. Erweitern Sie in der Liste der Vorlagen **Visual C oder** Visual **Basic**, wählen Sie den **Windows Store-Knoten** aus, und wählen Sie dann die **Vorlage windows-Runtime-Komponente** aus.

3. Geben Sie im Feld **Name** **SimpleMath**an, und wählen Sie dann die Schaltfläche **OK** aus.

4. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für den **SimpleMath-Projektknoten,** und wählen Sie dann **Eigenschaften**aus.

5. Benennen Sie **Class1.cs** in **Arithmetic.cs um,** und aktualisieren Sie sie entsprechend dem folgenden Code:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für den Knoten **"SimpleMath",** und wählen Sie dann **Configuration Manager**aus.

    Das Dialogfeld **Configuration Manager** wird geöffnet.

7. Wählen Sie in der **Konfigurationsliste Aktive Lösung** die Option **Freigeben**aus.

8. Überprüfen Sie in der Spalte **Konfiguration,** ob **simpleMath-Zeile** auf **Release**festgelegt ist, und wählen Sie dann die Schaltfläche **Schließen** aus, um die Änderung zu akzeptieren.

   > [!IMPORTANT]
   > Das SDK für die SimpleMath-Komponente enthält nur eine Konfiguration. Bei dieser Konfiguration muss es sich um den Releasebuild handelt, [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]oder Apps, die die Komponente verwenden, bestehen keine Zertifizierung für die .

9. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für den **SimpleMath-Projektknoten,** und wählen Sie dann **Build**aus.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>So erstellen Sie das Erweiterungsprojekt SimpleMathVSIX

1. Wählen Sie im Kontextmenü für den Knoten **"Lösung "SimpleMath"** die Option**Neues Projekt** **hinzufügen** > aus.

2. Erweitern Sie in der Liste der Vorlagen **Visual C oder** Visual **Basic**, wählen Sie den **Erweiterbarkeitsknoten** aus, und wählen Sie dann die **VSIX-Projektvorlage** aus.

3. Geben Sie im Feld **Name** **SimpleMathVSIX**an, und wählen Sie dann die Schaltfläche **OK** aus.

4. Wählen Sie im **Projektmappen-Explorer**das Element **source.extension.vsixmanifest** aus.

5. Wählen Sie in der Menüleiste**Code** **anzeigen** > .

6. Ersetzen Sie die vorhandene XML-Datei durch den folgenden XML-Code:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. Wählen Sie im **Projektmappen-Explorer**das **SimpleMathVSIX-Projekt** aus.

8. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen**aus.

9. Erweitern Sie in der Liste der **allgemeinen Elemente** **Daten**, und wählen Sie dann **XML-Datei**aus.

10. Geben **Name** Sie `SDKManifest.xml`im Feld Name an, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

11. Öffnen Sie im **Projektmappen-Explorer**das `SDKManifest.xml`Kontextmenü für , wählen Sie **Eigenschaften**aus, und ändern Sie dann den Wert der Eigenschaft **In VSIX einschließen** in **True**.

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

13. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das **SimpleMathVSIX-Projekt,** wählen **Sie Hinzufügen**aus, und wählen Sie dann **Neuer Ordner**aus.

14. Benennen Sie den `references`Ordner in um.

15. Öffnen Sie das Kontextmenü für den Ordner **Referenzen,** wählen Sie **Hinzufügen**aus, und wählen Sie dann **Neuer Ordner**aus.

16. Benennen Sie den `commonconfiguration`Unterordner in um , erstellen Sie `neutral`einen Unterordner darin, und benennen Sie den Unterordner .

17. Wiederholen Sie die vorherigen vier Schritte, indem `redist`Sie dieses Mal den ersten Ordner in umbenennen.

     Das Projekt enthält nun die folgende Ordnerstruktur:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das **SimpleMath-Projekt,** und wählen Sie dann **Ordner öffnen im Datei-Explorer**aus.

19. Navigieren Sie im **Datei-Explorer**zum Ordner *bin-Release,* öffnen Sie das Kontextmenü für die Datei **SimpleMath.winmd,** und wählen Sie dann **Kopieren**aus.

20. Fügen Sie im **Projektmappen-Explorer**die Datei in den Ordner *references-commonconfiguration-neutral* im **SimpleMathVSIX-Projekt** ein.

21. Wiederholen Sie den vorherigen Schritt, und fügen Sie die Datei **SimpleMath.pri** in den Ordner *redist-commonconfiguration-neutral* im **SimpleMathVSIX-Projekt** ein.

22. Wählen Sie im **Projektmappen-Explorer** **SimpleMath.winmd**.

23. Wählen Sie in der Menüleiste**Eigenschaften** **anzeigen** > (Tastatur: Wählen Sie die **Taste F4).**

24. Ändern Sie im **Fenster Eigenschaften** die **Build Aktionseigenschaft** in **Content**, und ändern Sie dann die Eigenschaft **In VSIX einschließen** in **True**.

25. Wiederholen Sie diesen Vorgang im **Projektmappen-Explorer**für **SimpleMath.pri**.

26. Wählen Sie im **Projektmappen-Explorer**das **SimpleMathVSIX-Projekt** aus.

27. Wählen Sie in der Menüleiste **Build** > **SimpleMathVSIX**erstellen.

28. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das **SimpleMathVSIX-Projekt,** und wählen Sie dann **Ordner öffnen im Datei-Explorer**aus.

29. Navigieren Sie im **Datei-Explorer**zum Ordner *,,bin'Release"* und führen Sie dann *SimpleMathVSIX.vsix* aus, um es zu installieren.

30. Wählen Sie die Schaltfläche **Installieren,** warten Sie, bis die Installation abgeschlossen ist, und starten Sie Visual Studio neu.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>So erstellen Sie eine Beispiel-App, die die Klassenbibliothek verwendet

1. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt**aus.

2. Erweitern Sie in der Liste der Vorlagen **Visual C oder** Visual **Basic**, und wählen Sie dann den **Windows Store-Knoten** aus.

3. Wählen Sie die **Vorlage Leere App** aus, benennen Sie das Projekt **ArithmeticUI**, und wählen Sie dann die Schaltfläche **OK** aus.

4. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das **ArithmeticUI-Projekt,** und wählen Sie dann**Referenz** **hinzufügen** > aus.

5. Erweitern Sie in der Liste der Referenztypen **Windows**, und wählen Sie dann **Erweiterungen**aus.

6. Wählen Sie im Detailbereich die Erweiterung **WinRT Math Library** aus.

    Zusätzliche Informationen zu Ihrem SDK werden angezeigt. Sie können den Link Weitere https://msdn.microsoft.com/ **Informationen** zum Öffnen auswählen, wie Sie zuvor in der Datei SDKManifest.xml in dieser exemplarischen Vorgehensweise angegeben haben.

7. Aktivieren Sie im Dialogfeld **Referenz-Manager** das Kontrollkästchen **WinRT-Mathematikbibliothek,** und wählen Sie dann die Schaltfläche **OK** aus.

8. Wählen Sie in der Menüleiste**Objektbrowser** **anzeigen** > aus.

9. Wählen Sie in der Liste **Durchsuchen** **einfache Mathematik**aus.

     Sie können nun untersuchen, was sich im SDK befindet.

10. Öffnen Sie im **Projektmappen-Explorer** **MainPage.xaml**, und ersetzen Sie dessen Inhalt durch das folgende XAML:

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

11. Aktualisieren **Sie MainPage.xaml.cs,** um dem folgenden Code zu entsprechen:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Wählen Sie die **F5-Taste** aus, um die App auszuführen.

13. Geben Sie in der App zwei beliebige Zahlen ein, wählen Sie einen Vorgang aus, und wählen Sie dann die **=** Schaltfläche aus.

     Das richtige Ergebnis wird angezeigt.

    Sie haben erfolgreich ein Erweiterungs-SDK erstellt und verwendet.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Erstellen eines SDK mit C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Exemplarische Vorgehensweise: Erstellen eines SDK mit JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)
