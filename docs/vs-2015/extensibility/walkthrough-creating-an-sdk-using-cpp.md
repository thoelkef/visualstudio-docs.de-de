---
title: 'Exemplarische Vorgehensweise: Erstellen eines SDK mit C++ | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202077"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Exemplarische Vorgehensweise: Erstellen eines SDK mit C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein System eigenes C++ Math Library SDK erstellen, das SDK als Visual Studio-Erweiterung (VSIX) verpacken und dann zum Erstellen einer App verwenden. Die exemplarische Vorgehensweise ist in die folgenden Schritte unterteilt:  
  
- [So erstellen Sie Native und Windows-Runtime-Bibliotheken](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [So erstellen Sie das nativemathvsix-Erweiterungsprojekt](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [So erstellen Sie eine Beispiel-APP, die die Klassenbibliothek verwendet](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> So erstellen Sie Native und Windows-Runtime-Bibliotheken  
  
1. Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
2. Erweitern Sie in der Liste der Vorlagen **Visual C++**, **Windows Store**, und wählen Sie dann die Vorlage **dll (Windows Store-Apps)** aus. Geben Sie im Feld **Name den Namen** an `NativeMath` , und klicken Sie dann auf die Schaltfläche **OK** .  
  
3. Aktualisieren Sie nativemath. h entsprechend dem folgenden Code.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. Aktualisieren Sie nativemath. cpp entsprechend dem folgenden Code:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für die Projekt Mappe **"nativemath"**, und wählen Sie dann **Hinzufügen**, **Neues Projekt**aus.  
  
6. Erweitern Sie in der Liste der Vorlagen die **Visual C++**, und wählen Sie dann die Vorlage **Windows-Runtime Komponenten** aus. Geben Sie im Feld **Name den Namen** an `NativeMathWRT` , und klicken Sie dann auf die Schaltfläche **OK** .  
  
7. Aktualisieren Sie Class1. h entsprechend dem folgenden Code:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Aktualisieren Sie Class1. cpp entsprechend dem folgenden Code:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> So erstellen Sie das nativemathvsix-Erweiterungsprojekt  
  
1. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für die Projekt Mappe **"nativemath"**, und wählen Sie dann **Hinzufügen**, **Neues Projekt**aus.  
  
2. Erweitern Sie in der Liste der Vorlagen die Option **Visual c#**, **Erweiterbarkeit**, und wählen Sie dann **VSIX-Paket**aus. Geben Sie im Feld **Name den Namen** **nativemathvsix**an, und klicken Sie dann auf die Schaltfläche **OK** .  
  
3. Wenn der VSIX-Manifest-Designer angezeigt wird, schließen Sie ihn.  
  
4. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für " **Source. Extension. vsixmanifest**", und wählen Sie dann **Code anzeigen**aus.  
  
5. Verwenden Sie das folgende XML, um den vorhandenen XML-Code zu ersetzen.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für das Projekt **nativemathvsix** , und wählen Sie dann **Hinzufügen**, **Neues Element**aus.  
  
7. Erweitern Sie in der Liste der **Visual c#-Elemente den Knoten** **Daten**, und wählen Sie dann **XML-Datei**aus. Geben Sie im Feld **Name den Namen** an `SDKManifest.xml` , und klicken Sie dann auf die Schaltfläche **OK** .  
  
8. Verwenden Sie diese XML-Datei, um den Inhalt der Datei zu ersetzen:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. Erstellen Sie in **Projektmappen-Explorer**im Projekt **nativemathvsix** diese Ordnerstruktur:  
  
    ```  
  
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
  
10. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für die Projekt Mappe **"nativemath"**, und wählen Sie dann **Ordner in Datei-Explorer öffnen**aus.  
  
11. Kopieren Sie im **Datei-Explorer**\nativemath\nativemath.h, und fügen Sie ihn anschließend in **Projektmappen-Explorer**im Projekt **nativemathvsix** in den Ordner \designtime\commonconfiguration\neutral\include\ ein.  
  
     Kopieren Sie \Debug \ nativemath\nativemath.lib, und fügen Sie Sie dann in den Ordner \designtime\debug \ x86\ ein.  
  
     Kopieren Sie \Debug\NativeMath\NativeMath.dll, und fügen Sie ihn in den Ordner "\redist\debug \" ein.  
  
     Kopieren Sie DebugNativeMathWRTNativeMathWRT.dll, und fügen Sie ihn in den Ordner RedistDebugx86 ein.  
  
     Kopieren Sie debugnativemathwrtnativemathwrt. winmd, und fügen Sie Sie in den Ordner referencescommonconfigurationneutral ein.  
  
     Kopieren Sie debugnativemathwrtnativemathwrt. pri, und fügen Sie Sie in den Ordner referencescommonconfigurationneutral ein.  
  
12. Erstellen Sie im Ordner \designtime\debug\x86\ eine Textdatei mit dem Namen nativemathsdk.-Eigenschaften, und fügen Sie den folgenden Inhalt in die Datei ein:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Wählen Sie in der Menüleiste **Ansicht**, **Weitere Fenster**, **Eigenschaften Fenster** (Tastatur: Drücken Sie die F4-Taste).  
  
14. Wählen Sie in **Projektmappen-Explorer**die Datei **nativemathwrt. winmd** aus. Ändern Sie im **Eigenschaften** Fenster die Eigenschaft **Buildaktion** in **Inhalt**, und ändern Sie dann die Eigenschaft **in VSIX einschließen** in **true**.  
  
     Wiederholen Sie diesen Vorgang für die Datei **simplemath. pri** .  
  
     Wiederholen Sie diesen Vorgang für die Datei " **nativemath. lib** ".  
  
     Wiederholen Sie diesen Vorgang für die Datei **nativemathsdk.** -Eigenschaften.  
  
15. Wählen Sie in **Projektmappen-Explorer**die Datei **nativemath. h** aus. Ändern Sie im **Eigenschaften** Fenster die Eigenschaft **in VSIX einschließen** in **true**.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMath.dll** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMathWRT.dll** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **SDKManifest.xml** Datei.  
  
16. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
17. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für das Projekt **nativemathvsix** , und wählen Sie dann **Ordner in Datei-Explorer öffnen**aus.  
  
18. Navigieren Sie im **Datei-Explorer**zum Ordner \bin\debug\, und führen Sie dann nativemathvsix. VSIX aus, um mit der Installation zu beginnen.  
  
19. Wählen Sie die Schaltfläche **Installieren** aus, warten Sie, bis die Installation abgeschlossen ist, und starten Sie Visual Studio neu.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> So erstellen Sie eine Beispiel-APP, die die Klassenbibliothek verwendet  
  
1. Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
2. Erweitern Sie in der Liste der Vorlagen **Visual C++**, **Windows Store**, und wählen Sie dann **leere App**aus. Geben Sie im Feld **Name den Namen** **nativemathsdksample**ein, und klicken Sie dann auf die Schaltfläche **OK** .  
  
3. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für das Projekt **nativemathsdksample** , und wählen Sie dann **Hinzufügen**, **Verweis**.  
  
4. Erweitern Sie auf der **Eigenschaften Seite Allgemeine Eigenschaften**, **Framework und Verweise** in der Liste der Verweis Typen den Eintrag **Windows**, und klicken Sie dann auf **Erweiterungen**. Wählen Sie im Detailbereich die **native Math SDK** -Erweiterung aus, und wählen Sie dann die Schaltfläche **neuen Verweis hinzufügen** aus.  
  
5. Aktivieren Sie im Dialogfeld **Verweis hinzufügen** das Kontrollkästchen **native Math SDK** , und klicken Sie dann auf die Schaltfläche **OK** .  
  
6. Zeigen Sie die Projekteigenschaften für nativemathsdksample an.  
  
    Die Eigenschaften, die Sie in nativemathsdk. properties definiert haben, wurden beim Hinzufügen des Verweises angewendet. Sie können dies überprüfen, indem Sie die Eigenschaft **VC + +-Verzeichnisse** der **Konfigurations Eigenschaften**des Projekts überprüfen.  
  
7. Öffnen Sie in **Projektmappen-Explorer**die Datei "MainPage. XAML", und ersetzen Sie dann den Inhalt mit dem folgenden XAML-Code:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Aktualisieren Sie "MainPage. XAML. h" entsprechend dem folgenden Code:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Aktualisieren Sie "MainPage. XAML. cpp" entsprechend dem folgenden Code:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Drücken Sie die Taste F5, um die APP auszuführen.  
  
11. Geben Sie in der APP zwei Zahlen ein, wählen Sie einen Vorgang aus, und wählen Sie dann die **=** Schaltfläche aus.  
  
     Das richtige Ergebnis wird angezeigt.  
  
    In dieser exemplarischen Vorgehensweise wurde veranschaulicht, wie ein Erweiterungs-SDK erstellt und verwendet wird, um eine [!INCLUDE[wrt](../includes/wrt-md.md)] Bibliothek und eine nicht--Bibliothek aufzurufen [!INCLUDE[wrt](../includes/wrt-md.md)] .  
  
## <a name="next-steps"></a>Nächste Schritte  
  
## <a name="see-also"></a>Weitere Informationen  
 [Exemplarische Vorgehensweise: Erstellen eines SDK mit c# oder Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)
