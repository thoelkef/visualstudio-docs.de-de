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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110036"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Exemplarische Vorgehensweise: Erstellen eines SDK mit C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieser exemplarischen Vorgehensweise erstellen eine native C++ Mathematikbibliothek SDK Paket das SDK als ein Visual Studio-Erweiterung (VSIX), und klicken Sie dann zum Erstellen einer app verwenden. Die exemplarische Vorgehensweise ist in Schritte unterteilt:  
  
- [Zum Erstellen des systemeigenen und Windows-Runtime-Bibliotheken](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [Erstellen Sie das Erweiterungsprojekt NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [Zum Erstellen einer Beispielapp verwendet, die die Bibliothek.](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="createClassLibrary"></a> Zum Erstellen des systemeigenen und Windows-Runtime-Bibliotheken  
  
1. Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
2. Erweitern Sie in der Liste der Vorlagen, **Visual C++**, **Windows Store**, und wählen Sie dann die **DLL (Windows Store-apps)** Vorlage. In der **Namen** geben `NativeMath`, und wählen Sie dann die **OK** Schaltfläche.  
  
3. Aktualisieren Sie NativeMath.h entsprechend den folgenden Code ein.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. Aktualisieren Sie NativeMath.cpp, sodass dieser Code entspricht:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung "NativeMath"**, und wählen Sie dann **hinzufügen**, **neues Projekt**.  
  
6. Erweitern Sie in der Liste der Vorlagen, **Visual C++**, und wählen Sie dann die **Komponente für Windows-Runtime** Vorlage. In der **Namen** geben `NativeMathWRT`, und wählen Sie dann die **OK** Schaltfläche.  
  
7. Aktualisieren Sie "Class1.h", sodass dieser Code entspricht:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Aktualisieren Sie "Class1.cpp", sodass dieser Code entspricht:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
## <a name="createVSIX"></a> Erstellen Sie das Erweiterungsprojekt NativeMathVSIX  
  
1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung "NativeMath"**, und wählen Sie dann **hinzufügen**, **neues Projekt**.  
  
2. Erweitern Sie in der Liste der Vorlagen, **Visual C#-**, **Erweiterbarkeit**, und wählen Sie dann **VSIX-Paket**. In der **Namen** geben **NativeMathVSIX**, und wählen Sie dann die **OK** Schaltfläche.  
  
3. Wenn die VSIX-manifest-Designer angezeigt wird, schließen Sie es aus.  
  
4. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **"Source.Extension.vsixmanifest"**, und wählen Sie dann **Ansichtscode**.  
  
5. Verwenden Sie den folgenden XML-Code, um den vorhandenen XML-Code zu ersetzen.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathVSIX** Projekt, und wählen Sie dann **hinzufügen**, **neues Element**.  
  
7. In der Liste der **Visual c#-Elemente**, erweitern Sie **Daten**, und wählen Sie dann **XML-Datei**. In der **Namen** geben `SDKManifest.xml`, und wählen Sie dann die **OK** Schaltfläche.  
  
8. Verwenden Sie diesen XML-Code, um den Inhalt der Datei zu ersetzen:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. In **Projektmappen-Explorer**in die **NativeMathVSIX** Projekt, das diese Ordnerstruktur zu erstellen:  
  
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
  
10. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung "NativeMath"**, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.  
  
11. In **Datei-Explorer**, \NativeMath\NativeMath.h, kopieren und dann im **Projektmappen-Explorer**in die **NativeMathVSIX** Projekt, fügen Sie ihn in das \DesignTime\ CommonConfiguration\Neutral\Include\-Ordner.  
  
     Kopieren Sie \Debug\NativeMath\NativeMath.lib, und fügen Sie ihn im Ordner "\DesignTime\Debug\x86\".  
  
     Kopieren Sie \Debug\NativeMath\NativeMath.dll, und fügen Sie ihn im Ordner "\Redist\Debug\x86\".  
  
     Kopieren Sie DebugNativeMathWRTNativeMathWRT.dll, und fügen Sie ihn im Ordner "RedistDebugx86".  
  
     Kopieren Sie DebugNativeMathWRTNativeMathWRT.winmd, und fügen Sie ihn im Ordner "ReferencesCommonConfigurationNeutral".  
  
     Kopieren Sie DebugNativeMathWRTNativeMathWRT.pri, und fügen Sie ihn im Ordner "ReferencesCommonConfigurationNeutral".  
  
12. Klicken Sie im Ordner \DesignTime\Debug\x86\ erstellen Sie eine Textdatei mit dem Namen NativeMathSDK.props, und fügen Sie den folgenden Inhalt in ihr:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Wählen Sie auf der Menüleiste **Ansicht**, **Other Windows**, **Fenster "Eigenschaften"** (Tastatur: Drücken Sie F4).  
  
14. In **Projektmappen-Explorer**, wählen die **NativeMathWRT.winmd** Datei. In der **Eigenschaften** Ändern der **Buildvorgang** Eigenschaft **Content**, und ändern Sie dann die **Include in VSIX-Datei** Eigenschaft  **"True"**.  
  
     Wiederholen Sie diesen Vorgang für die **SimpleMath.pri** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMath.Lib** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMathSDK.props** Datei.  
  
15. In **Projektmappen-Explorer**, wählen die **NativeMath.h** Datei. In der **Eigenschaften** Ändern der **Include in VSIX-Datei** Eigenschaft **"true"**.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMath.dll** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMathWRT.dll** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **SDKManifest.xml** Datei.  
  
16. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
17. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathVSIX** Projekt, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.  
  
18. In **Datei-Explorer**, navigieren Sie zu dem Ordner "\bin\Debug\", und führen Sie NativeMathVSIX.vsix, um die Installation zu starten.  
  
19. Wählen Sie die **installieren** Schaltfläche warten, bis zum Abschluss der Installation, und klicken Sie dann Visual Studio neu starten.  
  
## <a name="createSample"></a> Zum Erstellen einer Beispielapp verwendet, die die Bibliothek.  
  
1. Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
2. Erweitern Sie in der Liste der Vorlagen, **Visual C++**, **Windows Store**, und wählen Sie dann **leere App**. In der **Namen** geben **NativeMathSDKSample**, und wählen Sie dann die **OK** Schaltfläche.  
  
3. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathSDKSample** Projekt, und wählen Sie dann **hinzufügen**, **Verweis**.  
  
4. Auf der **allgemeine Eigenschaften**, **Framework und Verweise** auf der Seite in der Liste der Verweistypen, erweitern Sie **Windows**, und wählen Sie dann **Erweiterungen** . Wählen Sie im Detailbereich die **Native mathematische SDK** -Erweiterung, und wählen Sie dann die **neuen Verweis hinzufügen** Schaltfläche.  
  
5. In der **Verweis hinzufügen** wählen Sie im Dialogfeld die **Native mathematische SDK** aus, und wählen Sie dann die **OK** Schaltfläche.  
  
6. Zeigen Sie die Projekteigenschaften für NativeMathSDKSample an.  
  
    Die Eigenschaften, die Sie in NativeMathSDK.props definiert wurden angewendet, wenn Sie den Verweis hinzugefügt. Sie können dies überprüfen, indem Sie untersuchen die **VC++-Verzeichnisse** -Eigenschaft des Projekts die **Konfigurationseigenschaften**.  
  
7. In **Projektmappen-Explorer**, öffnen Sie "MainPage.xaml" ein, und klicken Sie dann den folgenden XAML verwenden, um seinen Inhalt zu ersetzen:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Aktualisieren Sie "MainPage.Xaml.h", sodass dieser Code entspricht:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Aktualisieren Sie "MainPage.Xaml.cpp", sodass dieser Code entspricht:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Wählen Sie die F5-Taste, um die app auszuführen.  
  
11. Geben Sie in der app, die zwei Zahlen, wählen Sie einen Vorgang, und wählen Sie dann die **=** Schaltfläche.  
  
     Das richtige Ergebnis wird angezeigt.  
  
    In dieser exemplarischen Vorgehensweise wurde gezeigt, wie zum Erstellen und verwenden eine Erweiterungs-SDK für den Aufruf einer [!INCLUDE[wrt](../includes/wrt-md.md)] -Bibliothek und einem nicht-[!INCLUDE[wrt](../includes/wrt-md.md)] Bibliothek.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer SDK mit C# oder Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)
