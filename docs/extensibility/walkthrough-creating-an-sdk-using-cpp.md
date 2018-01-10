---
title: 'Exemplarische Vorgehensweise: Erstellen einer SDKS mit C++ | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7a4091506bcd16222ff02600bd924d3526d57c38
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Exemplarische Vorgehensweise: Erstellen einer SDKS mit C++
In dieser exemplarischen Vorgehensweise wird gezeigt, wie eine systemeigene C++ Mathematikbibliothek SDK Paket das SDK als Visual Studio Extension (VSIX) zu erstellen und verwenden dieses dann zum Erstellen einer app. Die exemplarische Vorgehensweise ist in Schritte unterteilt:  
  
-   [So erstellen den einheitlichen und Windows-Runtime-Bibliotheken](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [So erstellen das Erweiterungsprojekt NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Eine Beispiel-app erstellen, die die Class-Bibliothek verwendet](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a>So erstellen den einheitlichen und Windows-Runtime-Bibliotheken  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C++**, **universellen Windows-**, und wählen Sie dann die **DLL (Windows Universal-apps)** Vorlage. In der **Namen** geben `NativeMath`, und wählen Sie dann die **OK** Schaltfläche.  
  
3.  Aktualisieren Sie NativeMath.h entsprechend den folgenden Code ein.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Update NativeMath.cpp entsprechend diesem Code:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung "NativeMath"**, und wählen Sie dann **hinzufügen**, **neues Projekt**.  
  
6.  Erweitern Sie in der Liste der Vorlagen, **Visual C++**, und wählen Sie dann die **Windows Runtime-Komponente** Vorlage. In der **Namen** geben `NativeMathWRT`, und wählen Sie dann die **OK** Schaltfläche.  
  
7.  Aktualisieren Sie die Datei "Class1.h", um diesen Code entsprechen:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Update Class1.cpp entsprechend diesem Code:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
##  <a name="createVSIX"></a>So erstellen das Erweiterungsprojekt NativeMathVSIX  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung "NativeMath"**, und wählen Sie dann **hinzufügen**, **neues Projekt**.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C#-**, **Erweiterbarkeit**, und wählen Sie dann **VSIX-Projekt**. In der **Namen** geben **NativeMathVSIX**, und wählen Sie dann die **OK** Schaltfläche.
  
3.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **"Source.Extension.vsixmanifest"**, und wählen Sie dann **Code anzeigen**.  
  
4.  Verwenden Sie das folgende XML, um den vorhandenen XML-Code zu ersetzen.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathVSIX** Projekt, und wählen Sie dann **hinzufügen**, **neues Element**.  
  
6.  In der Liste der **Visual C#-Elemente**, erweitern Sie **Daten**, und wählen Sie dann **XML-Datei**. In der **Namen** geben `SDKManifest.xml`, und wählen Sie dann die **OK** Schaltfläche.  
  
7.  Verwenden Sie diese XML-Daten um den Inhalt der Datei zu ersetzen:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. In **Projektmappen-Explorer**in der **NativeMathVSIX** Projekt, erstellen Sie die folgende Ordnerstruktur:  
  
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
  
9. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung "NativeMath"**, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.  
  
10. In **Datei-Explorer**, $SolutionRoot$\NativeMath\NativeMath.h, kopieren und dann im **Projektmappen-Explorer**in der **NativeMathVSIX** Projekt, fügen Sie ihn in die $SolutionRoot$ \ NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\-Ordner.  
  
     Kopieren Sie $SolutionRoot$\Debug\NativeMath\NativeMath.lib, und fügen Sie ihn im Ordner "$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\".  
  
     Kopieren Sie $SolutionRoot$\Debug\NativeMath\NativeMath.dll, und fügen Sie ihn im Ordner "$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\".  
  
     Kopieren Sie $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll, und fügen Sie ihn im Ordner "$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86".  
  
     Kopieren Sie $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd, und fügen Sie ihn im Ordner "$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral".  
  
     Kopieren Sie $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri, und fügen Sie ihn im Ordner "$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral".  
  
11. Erstellen Sie eine Textdatei mit dem Namen NativeMathSDK.props, und fügen Sie den folgenden Inhalt darin, im Ordner \NativeMathVSIX\DesignTime\Debug\x86\ $SolutionRoot$:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. Wählen Sie in der Menüleiste **Ansicht**, **Weitere Fenster**, **Fenster "Eigenschaften"** (Tastatur: Drücken Sie die F4-Taste).  
  
13. In **Projektmappen-Explorer**, wählen die **NativeMathWRT.winmd** Datei. In der **Eigenschaften** Ändern der **Buildvorgang** Eigenschaft **Content**, und ändern Sie dann die **Include in VSIX** Eigenschaft  **"True"**.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMath.h** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMathWRT.pri** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMath.Lib** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMathSDK.props** Datei.  
  
14. In **Projektmappen-Explorer**, wählen die **NativeMath.h** Datei. In der **Eigenschaften** Ändern der **Include in VSIX** Eigenschaft **"true"**.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMath.dll** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMathWRT.dll** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **SDKManifest.xml** Datei.  
  
15. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
16. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathVSIX** Projekt, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.  
  
17. In **Datei-Explorer**, navigieren Sie zum Ordner "$SolutionRoot$ \NativeMathVSIX\bin\Debug\", und führen Sie NativeMathVSIX.vsix, um die Installation zu starten.  
  
18. Wählen Sie die **installieren** Schaltfläche, warten Sie, bis die Installation abgeschlossen wurde, und starten Sie Visual Studio.  
  
##  <a name="createSample"></a>Eine Beispiel-app erstellen, die die Class-Bibliothek verwendet  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C++**, **universellen Windows-**, und wählen Sie dann **leere App**. In der **Namen** geben **NativeMathSDKSample**, und wählen Sie dann die **OK** Schaltfläche.  
  
3.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathSDKSample** Projekt, und wählen Sie dann **hinzufügen**, **Verweis**.  
  
4.  In der **Verweis hinzufügen** (Dialogfeld), in der Liste der Verweistypen, erweitern Sie **universelle Windows**, und wählen Sie dann **Erweiterungen**. Wählen Sie abschließend die **Native mathematische SDK** Kontrollkästchen, und wählen Sie dann die **OK** Schaltfläche.
  
5.  Zeigen Sie die Projekteigenschaften für NativeMathSDKSample.  
  
     Die Eigenschaften, die Sie in NativeMathSDK.props definiert wurden angewendet, wenn Sie den Verweis hinzugefügt. Sie können dies überprüfen, indem Sie untersuchen die **VC++-Verzeichnisse** Eigenschaft des Projekts **Konfigurationseigenschaften**.  
  
6.  In **Projektmappen-Explorer**, öffnen Sie "MainPage.xaml" hinzu, und klicken Sie dann den folgenden XAML-Code verwenden, um seinen Inhalt zu ersetzen:  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7.  Aktualisieren Sie "MainPage.Xaml.h", um diesen Code entsprechen:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Aktualisieren Sie "MainPage.Xaml.cpp", um diesen Code entsprechen:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Drücken Sie die Taste F5, um die app auszuführen.  
  
10. Geben Sie in der app, die zwei Zahlen, wählen Sie einen Vorgang, und wählen Sie dann die  **=**  Schaltfläche.  
  
     Das richtige Ergebnis wird angezeigt.  
  
 In dieser exemplarischen Vorgehensweise wurde gezeigt, wie zum Erstellen und verwenden eine Erweiterungs-SDK zum Aufrufen einer [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] -Bibliothek und einem nicht-[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] Bibliothek.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer SDKS mit c# oder Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)