---
title: 'Exemplarische Vorgehensweise: Erstellen einer SDKS mit c# oder Visual Basic | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a8b0b8452fb20b9b6da4e8ad58c221010f23c9ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Exemplarische Vorgehensweise: Erstellen einer SDKS mit c# oder Visual Basic
In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie einen einfachen mathematischen Bibliothek SDK mit Visual c# erstellen und dann das SDK als eine Visual Studio-Erweiterung (VSIX) verpacken. Sie müssen die folgenden Verfahren ausführen:  
  
-   [So erstellen Sie die SimpleMath Windows-Runtime-Komponente](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [So erstellen das Erweiterungsprojekt SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [Eine Beispiel-app erstellen, die die Class-Bibliothek verwendet](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a>So erstellen Sie die SimpleMath Windows-Runtime-Komponente  
  
1.  Wählen Sie in der Menüleiste **Datei**, **neu**, **neues Projekt**.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C#-** oder **Visual Basic**, wählen Sie die **Windows Store** Knoten, und wählen Sie dann die **fürWindows-Runtime-Komponente** Vorlage.  
  
3.  In der **Namen** geben **SimpleMath**, und wählen Sie dann die **OK** Schaltfläche.  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMath** Projektknoten, und wählen Sie dann **Eigenschaften**.  
  
5.  Benennen Sie **"Class1.cs"** auf **Arithmetic.cs** und aktualisieren, damit Sie entsprechend folgendem Code:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]  
  
6.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Lösung "SimpleMath"** Knoten, und wählen Sie dann **Configuration Manager**.  
  
     Die **Configuration Manager** Dialogfeld wird geöffnet.  
  
7.  In der **aktive Projektmappenkonfiguration** wählen **Version**.  
  
8.  In der **Konfiguration** Spalte, überprüfen Sie, ob **SimpleMath** Zeile auf festgelegt ist **Release**, und wählen Sie dann die **schließen** Schaltfläche akzeptiert die ändern.  
  
    > [!IMPORTANT]
    >  Das SDK für die Komponente SimpleMath enthält nur eine Konfiguration. Diese Konfiguration muss der Releasebuild oder apps, die die Komponente wird nicht Zertifizierung übergeben, für die[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].  
  
9. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMath** Projektknoten, und wählen Sie dann **erstellen**.  
  
##  <a name="createVSIX"></a>So erstellen das Erweiterungsprojekt SimpleMathVSIX  
  
1.  Das Kontextmenü für die **Lösung "SimpleMath"** Knoten, wählen Sie **hinzufügen**, **neues Projekt**.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C#-** oder **Visual Basic**, wählen Sie die **Erweiterbarkeit** Knoten, und wählen Sie dann die **VSIX-Projekt** Vorlage.  
  
3.  In der **Namen** geben **SimpleMathVSIX**, und wählen Sie dann die **OK** Schaltfläche.  
  
4.  In **Projektmappen-Explorer**, wählen Sie die **"Source.Extension.vsixmanifest"** Element.  
  
5.  Wählen Sie in der Menüleiste **Ansicht**und **Code**aus.  
  
6.  Ersetzen Sie den vorhandenen XML-Code durch folgendes XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  In **Projektmappen-Explorer**, wählen Sie die **SimpleMathVSIX** Projekt.  
  
8.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
9. In der Liste der **gemeinsame Elemente**, erweitern Sie **Daten**, und wählen Sie dann **XML-Datei**.  
  
10. In der **Namen** geben `SDKManifest.xml`, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
11. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für `SDKManifest.xml`, wählen Sie **Eigenschaften**, und ändern Sie den Wert, der die **Include in VSIX** Eigenschaft **"True"**.  
  
12. Ersetzen Sie den Inhalt der Datei durch folgendes XML:  

    **C#**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
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
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```  
  
13. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMathVSIX** Projekts **hinzufügen**, und wählen Sie dann **neuer Ordner**.  
  
14. Benennen Sie den Ordner zu `references`.  
  
15. Öffnen Sie das Kontextmenü für die **Verweise** Ordner, wählen Sie **hinzufügen**, und wählen Sie dann **neuer Ordner**.  
  
16. Benennen Sie den Unterordner auf `commonconfiguration`, erstellen Sie einen Unterordner darin, und nennen Sie den Unterordner `neutral`.  
  
17. Wiederholen Sie die vorherigen vier Schritte, diesmal Umbenennen des ersten Ordners auf `redist`.  
  
     Das Projekt enthält jetzt die folgende Ordnerstruktur:  
  
    ```
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMath** Projekt, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.  
  
19. In **Datei-Explorer**, navigieren Sie zu dem Ordner "bin\Release", öffnen Sie das Kontextmenü für die SimpleMath.winmd-Datei, und wählen Sie dann **Kopie**.  
  
20. In **Projektmappen-Explorer**, fügen Sie die Datei in den Ordner "References\commonconfiguration\neutral" in der **SimpleMathVSIX** Projekt.  
  
21. Wiederholen Sie den vorherigen Schritt, Einfügen der SimpleMath.pri-Datei in den Ordner "Redist\commonconfiguration\neutral" in der **SimpleMathVSIX** Projekt.  
  
22. In **Projektmappen-Explorer**, wählen Sie **SimpleMath.winmd**.  
  
23. Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaften** (Tastatur: Drücken Sie die F4-Taste).  
  
24. In der **Eigenschaften** Ändern der **Buildvorgang** Eigenschaft **Content**, und ändern Sie dann die **Include in VSIX** Eigenschaft  **"True"**.  
  
25. In **Projektmappen-Explorer**, wiederholen Sie diesen Vorgang für **SimpleMath.pri**.  
  
26. In **Projektmappen-Explorer**, wählen Sie die **SimpleMathVSIX** Projekt.  
  
27. Wählen Sie in der Menüleiste **erstellen**, **SimpleMathVSIX erstellen**.  
  
28. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMathVSIX** Projekt, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.  
  
29. In **Datei-Explorer**, navigieren Sie zum Ordner \bin\Release, und führen Sie SimpleMathVSIX.vsix, um es zu installieren.  
  
30. Wählen Sie die **installieren** Schaltfläche, warten Sie, bis die Installation abgeschlossen wurde, und starten Sie Visual Studio.  
  
##  <a name="createSample"></a>Eine Beispiel-app erstellen, die die Class-Bibliothek verwendet  
  
1.  Wählen Sie in der Menüleiste **Datei**, **neu**, **neues Projekt**.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **Windows Store** Knoten.  
  
3.  Wählen Sie die **leere App** Vorlage, nennen Sie das Projekt **ArithmeticUI**, und wählen Sie dann die **OK** Schaltfläche.  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ArithmeticUI** Projekt, und wählen Sie dann **hinzufügen**, **Verweis**.  
  
5.  Erweitern Sie in der Liste von Verweistypen **Windows**, und wählen Sie dann **Erweiterungen**.  
  
6.  Wählen Sie im Detailbereich die **einfache mathematische SDK** Erweiterung.  
  
     Weitere Informationen zu Ihrem SDK wird angezeigt. Sie können die **mehr Informationen** Link zum Öffnen von http://www.msdn.microsoft.com, wie Sie in der Datei SDKManifest.xml weiter oben in dieser exemplarischen Vorgehensweise angegeben.  
  
7.  In der **Verweis-Manager** wählen Sie im Dialogfeld die **einfache mathematische SDK** Kontrollkästchen, und wählen Sie dann die **OK** Schaltfläche.  
  
8.  Wählen Sie in der Menüleiste **Ansicht**, **Objektkatalog**.  
  
9. In der **Durchsuchen** wählen **einfache mathematische**.  
  
     Sie können jetzt durchsuchen, was das SDK enthält.  
  
10. In **Projektmappen-Explorer**, öffnen Sie "MainPage.xaml" hinzu, und Ersetzen Sie den Inhalt durch Folgendes XAML:  

    **C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
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
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
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
  
11. Aktualisieren Sie die Datei "MainPage.Xaml.cs", um entsprechend folgendem Code:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]  
  
12. Drücken Sie die Taste F5, um die app auszuführen.  
  
13. Geben Sie in der app, die zwei Zahlen, wählen Sie einen Vorgang aus, und wählen Sie dann die  **=**  Schaltfläche.  
  
     Das richtige Ergebnis wird angezeigt.  
  
 Sie haben erfolgreich erstellt und verwendet eine Erweiterungs-SDK.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer SDKS mit C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Exemplarische Vorgehensweise: Erstellen einer SDKS mit JavaScript](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)