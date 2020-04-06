---
title: 'Exemplarische Vorgehensweise: Erstellen eines SDK mit C++ | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65643e65490eacb79eea4d76aa49ff10d6cccf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697634"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Exemplarische Vorgehensweise: Erstellen eines SDK mit C++
In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein systemeigenes C++-Mathematikbibliotheks-SDK erstellen, das SDK als Visual Studio-Erweiterung (VSIX) verpacken und dann zum Erstellen einer App verwenden. Die exemplarische Vorgehensweise ist in folgende Schritte unterteilt:

- [So erstellen Sie die systemeigenen und Windows-Runtime-Bibliotheken](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [So erstellen Sie das NativeMathVSIX-Erweiterungsprojekt](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [So erstellen Sie eine Beispiel-App, die die Klassenbibliothek verwendet](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Voraussetzungen
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>So erstellen Sie die systemeigenen und Windows-Runtime-Bibliotheken

1. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt**aus.

2. Erweitern Sie in der Liste der Vorlagen **Visual C++** > **Windows Universal**, und wählen Sie dann die **DLL-Vorlage (Windows Universal Apps)** aus. Geben **Name** Sie `NativeMath`im Feld Name an, und wählen Sie dann die Schaltfläche **OK** aus.

3. Aktualisieren Sie *NativeMath.h,* um dem folgenden Code zu entsprechen.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Aktualisieren Sie *NativeMath.cpp,* um diesem Code zu entsprechen:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für **Die Projektmappe 'NativeMath'**, und wählen Sie dann**Neues Projekt** **hinzufügen** > aus.

6. Erweitern Sie in der Liste der Vorlagen **Visual C++**, und wählen Sie dann die **Vorlage windows-Runtime-Komponente** aus. Geben **Name** Sie `NativeMathWRT`im Feld Name an, und wählen Sie dann die Schaltfläche **OK** aus.

7. Aktualisieren Sie *Class1.h,* um diesen Code zu entsprechen:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Aktualisieren Sie *Class1.cpp,* um diesem Code zu entsprechen:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. Wählen Sie in der Menüleiste > **Buildlösung**erstellen aus. **Build**

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>So erstellen Sie das NativeMathVSIX-Erweiterungsprojekt

1. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für **Die Projektmappe 'NativeMath'**, und wählen Sie dann**Neues Projekt** **hinzufügen** > aus.

2. Erweitern Sie in der Liste der Vorlagen die Visual > **C-Extensibilität**, und wählen Sie dann **VSIX Project aus.** **Visual C#** Geben Sie im Feld **Name** **NativeMathVSIX**an, und wählen Sie dann die Schaltfläche **OK** aus.

3. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für **source.extension.vsixmanifest**, und wählen Sie dann **Code anzeigen**aus.

4. Verwenden Sie den folgenden XML-Code, um die vorhandene XML-Datei zu ersetzen.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das **NativeMathVSIX-Projekt,** und wählen Sie dann**Neues Element** **hinzufügen** > aus.

6. Erweitern Sie **Visual C# Items** **Daten**, und wählen Sie dann **XML-Datei**aus. Geben **Name** Sie `SDKManifest.xml`im Feld Name an, und wählen Sie dann die Schaltfläche **OK** aus.

7. Verwenden Sie diesen XML-Code, um den Inhalt der Datei zu ersetzen:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. Erstellen Sie im **Projektmappen-Explorer**unter dem **NativeMathVSIX-Projekt** diese Ordnerstruktur:

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für **die Projektmappe "NativeMath"**, und wählen Sie dann **Ordner öffnen im Datei-Explorer**aus.

10. Kopieren Sie im **Datei-Explorer** *$SolutionRoot, nativeMath,NativeMath.h*, und dann im **Projektmappen-Explorer**unter dem **NativeMathVSIX-Projekt** in den Ordner *\\ $SolutionRoot.,NativeMathVSIX-DesignTime-,CommonConfiguration-Neutral-Include-Ordner.*

     Kopieren Sie *$SolutionRoot,-Debug-,NativeMath-NativeMath.lib*, und fügen Sie sie dann in den Ordner *\\ $SolutionRoot-Datei-,NativeMathVSIX-DesignTime-Debug-X86-Ordner* ein.

     Kopieren Sie *$SolutionRoot-Debug-,NativeMath-NativeMath.dll,* und fügen Sie sie in den Ordner *$SolutionRoot-NativeMathVSIX-Redist-Debug-X86\\ * ein.

     Kopieren Sie *$SolutionRoot-Debug-,NativeMathWRT-NativeMathWRT.dll,* und fügen Sie sie in den Ordner *$SolutionRoot-NativeMathVSIX-Redist-Debug-X86-Ordner* ein.
     Kopieren Sie *$SolutionRoot-Debug-,NativeMathWRT-NativeMathWRT.winmd,* und fügen Sie sie in den Ordner *$SolutionRoot-NativeMathVSIX-Referenzen, CommonConfiguration-Neutral* ein.

     Kopieren Sie *$SolutionRoot-Debug-,NativeMathWRT-NativeMathWRT.pri-Ordner,* und fügen Sie sie in den Ordner *$SolutionRoot.,NativeMathVSIX-Referenzen, CommonConfiguration-Neutral-Ordner,* ein.

11. Erstellen Sie im Ordner $SolutionRoot Ordner *"NativeMathVSIX"\\ und "DesignTime" und "Debug"x86* eine Textdatei mit dem Namen *NativeMathSDK.props*, und fügen Sie dann den folgenden Inhalt ein:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. **Wählen** > Sie in der Menüleiste Andere**Windows-Eigenschaften** **Other Windows** > anzeigen (Tastatur: Wählen Sie die **F4-Taste).**

13. Wählen Sie im **Projektmappen-Explorer**die Datei **NativeMathWRT.winmd** aus. Ändern Sie im **Fenster Eigenschaften** die **Build Aktionseigenschaft** in **Content**, und ändern Sie dann die Eigenschaft **In VSIX einschließen** in **True**.

     Wiederholen Sie diesen Vorgang für die Datei **NativeMath.h.**

     Wiederholen Sie diesen Vorgang für die Datei **NativeMathWRT.pri.**

     Wiederholen Sie diesen Vorgang für die Datei **NativeMath.Lib.**

     Wiederholen Sie diesen Vorgang für die Datei **NativeMathSDK.props.**

14. Wählen Sie im **Projektmappen-Explorer**die Datei **NativeMath.h** aus. Ändern Sie im Fenster **Eigenschaften** die **Eigenschaft In VSIX einschließen** in **True**.

     Wiederholen Sie diesen Vorgang für die Datei **NativeMath.dll.**

     Wiederholen Sie diesen Vorgang für die Datei **NativeMathWRT.dll.**

     Wiederholen Sie diesen Vorgang für die Datei **SDKManifest.xml.**

15. Wählen Sie in der Menüleiste > **Buildlösung**erstellen aus. **Build**

16. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das **NativeMathVSIX-Projekt,** und wählen Sie dann **Ordner öffnen im Datei-Explorer**aus.

17. Navigieren Sie im **Datei-Explorer**zum Ordner *$SolutionRoot,-NativeMathVSIX-Bin-Debug-Ordner,* und führen Sie dann *NativeMathVSIX.vsix* aus, um mit der Installation zu beginnen.

18. Wählen Sie die Schaltfläche **Installieren** aus, warten Sie, bis die Installation abgeschlossen ist, und öffnen Sie dann Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>So erstellen Sie eine Beispiel-App, die die Klassenbibliothek verwendet

1. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt**aus.

2. Erweitern Sie in der Liste der Vorlagen **Visual C++** > **Windows Universal,** und wählen Sie dann **Leere App**aus. Geben Sie im Feld **Name** **NativeMathSDKSample**an, und wählen Sie dann die Schaltfläche **OK** aus.

3. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das **NativeMathSDKSample-Projekt,** und wählen Sie dann**Referenz** **hinzufügen** > aus.

4. Erweitern Sie im Dialogfeld **Referenz hinzufügen** in der Liste der **Referenztypen,** und wählen Sie dann **Erweiterungen**aus. Aktivieren Sie schließlich das Kontrollkästchen **Native Math SDK,** und wählen Sie dann die Schaltfläche **OK** aus.

5. Zeigen Sie die Projekteigenschaften für NativeMathSDKSample an.

    Die Eigenschaften, die Sie in *NativeMathSDK.props* definiert haben, wurden beim Hinzuladen des Verweises angewendet. Sie können überprüfen, ob die Eigenschaften angewendet wurden, indem Sie die **VC++-Verzeichnisse-Eigenschaft** der **Konfigurationseigenschaften**des Projekts untersuchen.

6. Öffnen Sie im **Projektmappen-Explorer** **MainPage.xaml**, und verwenden Sie dann das folgende XAML, um den Inhalt zu ersetzen:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Aktualisieren Sie *Mainpage.xaml.h,* um diesen Code zu entsprechen:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Aktualisieren Sie *MainPage.xaml.cpp,* um diesem Code zu entsprechen:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Wählen Sie die **F5-Taste** aus, um die App auszuführen.

10. Geben Sie in der App zwei beliebige Zahlen ein, wählen Sie einen Vorgang aus, und wählen Sie dann die **=** Schaltfläche aus.

     Das richtige Ergebnis wird angezeigt.

    In dieser exemplarischen Vorgehensweise wurde gezeigt, wie Sie [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] ein Extension[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] SDK erstellen und verwenden, um eine Bibliothek und eine Nichtbibliothek aufzurufen.

## <a name="next-steps"></a>Nächste Schritte

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Erstellen eines SDK mit C- oder Visual Basic-Code](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Erstellen eines Software-Entwicklungskits](../extensibility/creating-a-software-development-kit.md)
