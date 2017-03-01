---
title: 'Exemplarische Vorgehensweise: Erstellen einer SDK mit C++ | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 32
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
ms.sourcegitcommit: d4458cb2cf0f3f198b2931beec15f8eead446ba6
ms.openlocfilehash: 3baf914755f0cdd4e0aa0a6c1405126faeec0364
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Exemplarische Vorgehensweise: Erstellen einer SDK mit C++
Dieser exemplarischen Vorgehensweise erstellen eine native C++ Mathematikbibliothek SDK Paket das SDK als eine Visual Studio-Erweiterung (VSIX), und verwenden Sie Sie dann zum Erstellen einer app. Die exemplarische Vorgehensweise ist in Schritte unterteilt:  
  
-   [Zum Erstellen des systemeigenen und Windows-Runtime-Bibliotheken](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Erstellen Sie das Erweiterungsprojekt NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Zum Erstellen einer Beispielapp verwendet, die die Bibliothek.](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="a-namecreateclasslibrarya-to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Zum Erstellen des systemeigenen und Windows-Runtime-Bibliotheken  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C++**, **Windows Store**, und wählen Sie dann die **DLL (Windows Store-apps)** Vorlage. In der **Namen** geben `NativeMath`, und wählen Sie dann die **OK** Schaltfläche.  
  
3.  Aktualisieren Sie die NativeMath.h entsprechend den folgenden Code.  
  
     [!code-cpp[CreatingAnSDKUsingCpp&#1;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Update NativeMath.cpp entsprechend diesem Code:  
  
     [!code-cpp[CreatingAnSDKUsingCpp&#2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung 'NativeMath'**, und wählen Sie dann **hinzufügen**, **neues Projekt**.  
  
6.  Erweitern Sie in der Liste der Vorlagen, **Visual C++**, und wählen Sie dann die **Windows-Runtime-Komponente** Vorlage. In der **Namen** geben `NativeMathWRT`, und wählen Sie dann die **OK** Schaltfläche.  
  
7.  Aktualisieren Sie "Class1.h", damit dieser Code entspricht:  
  
     [!code-cpp[CreatingAnSDKUsingCpp&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Update Class1.cpp entsprechend diesem Code:  
  
     [!code-cpp[CreatingAnSDKUsingCpp&4;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
##  <a name="a-namecreatevsixa-to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Erstellen Sie das Erweiterungsprojekt NativeMathVSIX  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung 'NativeMath'**, und wählen Sie dann **hinzufügen**, **neues Projekt**.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C#-**, **Erweiterbarkeit**, und wählen Sie dann **VSIX-Paket**. In der **Namen** geben **NativeMathVSIX**, und wählen Sie dann die **OK** Schaltfläche.  
  
3.  Wenn im VSIX-manifest-Designer angezeigt wird, schließen Sie es.  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **source.extension.vsixmanifest**, und wählen Sie dann **Anzeigecode**.  
  
5.  Verwenden Sie das folgende XML, um den vorhandenen XML-Code zu ersetzen.  
  
    [!code-xml[CreatingAnSDKUsingCpp&6;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

6.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathVSIX** Projekt, und wählen Sie dann **hinzufügen**, **neues Element**.  
  
7.  In der Liste der **Visual C#-Elemente**, erweitern Sie **Daten**, und wählen Sie dann **XML-Datei**. In der **Namen** geben `SDKManifest.xml`, und wählen Sie dann die **OK** Schaltfläche.  
  
8.  Verwenden Sie dieses XML den Inhalt der Datei ersetzt:  
  
     [!code-xml[CreatingAnSDKUsingCpp&5;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
9. In **Projektmappen-Explorer**in der **NativeMathVSIX** Projekt, erstellen Sie die folgende Ordnerstruktur:  
  
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
  
10. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung 'NativeMath'**, und wählen Sie dann **Ordner im Datei-Explorer öffnen**.  
  
11. In **Datei-Explorer**, \NativeMath\NativeMath.h, kopieren und dann im **Projektmappen-Explorer**in der **NativeMathVSIX** Projekt, fügen Sie ihn in den Ordner \DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Kopieren Sie \Debug\NativeMath\NativeMath.lib, und fügen Sie ihn in den Ordner \DesignTime\Debug\x86\.  
  
     Kopieren Sie \Debug\NativeMath\NativeMath.dll, und fügen Sie ihn in den Ordner \Redist\Debug\x86\.  
  
     Kopieren Sie DebugNativeMathWRTNativeMathWRT.dll, und fügen Sie ihn in den Ordner RedistDebugx86.  
  
     Kopieren Sie DebugNativeMathWRTNativeMathWRT.winmd, und fügen Sie ihn in den Ordner ReferencesCommonConfigurationNeutral.  
  
     Kopieren Sie DebugNativeMathWRTNativeMathWRT.pri, und fügen Sie ihn in den Ordner ReferencesCommonConfigurationNeutral.  
  
12. Erstellen Sie im Ordner \DesignTime\Debug\x86\ eine Textdatei mit dem Namen NativeMathSDK.props, und fügen Sie die folgenden Inhalte hinein:  
  
    [!code-xml[CreatingAnSDKUsingCpp&#7;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Wählen Sie auf der Menüleiste **Ansicht**, **Weitere Fenster**, **Eigenschaftenfenster** (Tastatur: Drücken Sie die Taste F4).  
  
14. In **Projektmappen-Explorer**, wählen die **NativeMathWRT.winmd** Datei. In der **Eigenschaften** Ändern der **Buildvorgang** -Eigenschaft **Content**, und ändern Sie dann die **Include in VSIX** -Eigenschaft **True**.  
  
     Wiederholen Sie diesen Vorgang für die **SimpleMath.pri** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMath.Lib** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMathSDK.props** Datei.  
  
15. In **Projektmappen-Explorer**, wählen die **NativeMath.h** Datei. In der **Eigenschaften** Ändern der **Include in VSIX** -Eigenschaft **True**.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMath.dll** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMathWRT.dll** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **SDKManifest.xml** Datei.  
  
16. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
17. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathVSIX** Projekt, und wählen Sie dann **Ordner im Datei-Explorer öffnen**.  
  
18. In **Datei-Explorer**, navigieren Sie zum Ordner "\bin\Debug\", und führen Sie NativeMathVSIX.vsix, um die Installation zu beginnen.  
  
19. Wählen Sie die **installieren** Schaltfläche warten, bis zum Abschluss der Installation, und starten Sie Visual Studio neu.  
  
##  <a name="a-namecreatesamplea-to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Zum Erstellen einer Beispielapp verwendet, die die Bibliothek.  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C++**, **Windows Store**, und wählen Sie dann **leere App**. In der **Namen** geben **NativeMathSDKSample**, und wählen Sie dann die **OK** Schaltfläche.  
  
3.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathSDKSample** Projekt, und wählen Sie dann **hinzufügen**, **Verweis**.  
  
4.  Auf der **allgemeine Eigenschaften**, **Framework und Verweise** erweitern Sie auf der Seite in der Liste der Verweistypen **Windows**, und wählen Sie dann **Extensions**. Wählen Sie im Detailbereich die **systemeigene mathematische SDK** -Erweiterung, und wählen Sie dann die **neuen Verweis hinzufügen** Schaltfläche.  
  
5.  In der **Verweis hinzufügen** wählen Sie im Dialogfeld die **systemeigene mathematische SDK** , und wählen Sie dann die **OK** Schaltfläche.  
  
6.  Zeigen Sie die Projekteigenschaften für NativeMathSDKSample.  
  
     Die Eigenschaften, die Sie in NativeMathSDK.props definiert wurden angewendet, wenn Sie den Verweis hinzugefügt. Sie können dies überprüfen, indem Sie untersuchen das **VC++-Verzeichnisse** die Projekteigenschaft **Konfigurationseigenschaften**.  
  
7.  In **Projektmappen-Explorer**, öffnen Sie "MainPage.xaml", und klicken Sie dann den folgenden XAML-Code verwenden, um seinen Inhalt zu ersetzen:  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp&#1;](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
8.  Aktualisieren Sie "MainPage.Xaml.h", damit dieser Code entspricht:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp&#2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
9. Aktualisieren Sie "MainPage.Xaml.cpp", damit dieser Code entspricht:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
10. Drücken Sie F5, um die app auszuführen.  
  
11. Geben Sie zwei Zahlen in der app, wählen Sie einen Vorgang, und wählen Sie dann die ** = ** Schaltfläche.  
  
     Das richtige Ergebnis wird angezeigt.  
  
 In dieser exemplarischen Vorgehensweise wurde gezeigt, wie zum Erstellen und Verwenden von SDK-Erweiterung zum Aufrufen einer [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] -Bibliothek und einem nicht-[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] Bibliothek.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer SDK mit c# oder Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)
