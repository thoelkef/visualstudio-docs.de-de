---
title: 'Exemplarische Vorgehensweise: Erstellen eines SDK mit C++ | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2a0db4f34315f9e0eb4a5627cdc286a43a904a34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917604"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Exemplarische Vorgehensweise: Erstellen eines SDKS mit C++
Dieser exemplarischen Vorgehensweise erstellen eine native C++ Mathematikbibliothek SDK Paket das SDK als ein Visual Studio-Erweiterung (VSIX), und klicken Sie dann zum Erstellen einer app verwenden. Die exemplarische Vorgehensweise ist in Schritte unterteilt:  
  
-   [Zum Erstellen des systemeigenen und Windows-Runtime-Bibliotheken](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Erstellen Sie das Erweiterungsprojekt NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Zum Erstellen einer Beispielapp verwendet, die die Bibliothek.](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Zum Erstellen des systemeigenen und Windows-Runtime-Bibliotheken  
  
1.  Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C++** > **Windows Universal**, und wählen Sie dann die **DLL (Windows Universal-apps)** Vorlage. In der **Namen** geben `NativeMath`, und wählen Sie dann die **OK** Schaltfläche.  
  
3.  Update *NativeMath.h* entsprechend den folgenden Code.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Update *NativeMath.cpp* entsprechend diesen Code:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung "NativeMath"**, und wählen Sie dann **hinzufügen** > **neues Projekt**.  
  
6.  Erweitern Sie in der Liste der Vorlagen, **Visual C++**, und wählen Sie dann die **Komponente für Windows-Runtime** Vorlage. In der **Namen** geben `NativeMathWRT`, und wählen Sie dann die **OK** Schaltfläche.  
  
7.  Update *"Class1.h"* entsprechend diesen Code:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Update *"Class1.cpp"* entsprechend diesen Code:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.  
  
##  <a name="createVSIX"></a> Erstellen Sie das Erweiterungsprojekt NativeMathVSIX  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung "NativeMath"**, und wählen Sie dann **hinzufügen** > **neues Projekt**.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C#-** > **Erweiterbarkeit**, und wählen Sie dann **VSIX-Projekt**. In der **Namen** geben **NativeMathVSIX**, und wählen Sie dann die **OK** Schaltfläche.
  
3.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **"Source.Extension.vsixmanifest"**, und wählen Sie dann **Ansichtscode**.  
  
4.  Verwenden Sie den folgenden XML-Code, um den vorhandenen XML-Code zu ersetzen.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathVSIX** Projekt, und wählen Sie dann **hinzufügen** > **neues Element**.  
  
6.  In der Liste der **Visual c#-Elemente**, erweitern Sie **Daten**, und wählen Sie dann **XML-Datei**. In der **Namen** geben `SDKManifest.xml`, und wählen Sie dann die **OK** Schaltfläche.  
  
7.  Verwenden Sie diesen XML-Code, um den Inhalt der Datei zu ersetzen:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. In **Projektmappen-Explorer**unter der **NativeMathVSIX** Projekt, das diese Ordnerstruktur zu erstellen:  
  
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
  
9. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Lösung "NativeMath"**, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.  
  
10. In **Datei-Explorer**, Kopie *$SolutionRoot$\NativeMath\NativeMath.h*, und klicken Sie dann im **Projektmappen-Explorer**unter der **NativeMathVSIX**Projekt, fügen Sie ihn in das *$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\*  Ordner.  
  
     Kopie *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*, und fügen Sie ihn in das *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  Ordner.  
  
     Kopie *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* und fügen Sie ihn in das *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\\*  Ordner.  
  
     Kopie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* und fügen Sie ihn in das *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86* Ordner.  
     Kopie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* und fügen Sie ihn in das *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* Ordner.  
  
     Kopie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* und fügen Sie ihn in das *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* Ordner.  
  
11. In der *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  Ordner, erstellen Sie eine Textdatei mit dem Namen *NativeMathSDK.props*, und fügen Sie darin den folgenden Inhalt:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** > **Fenster "Eigenschaften"** (Tastatur: Wählen Sie die **F4** Schlüssel).  
  
13. In **Projektmappen-Explorer**, wählen die **NativeMathWRT.winmd** Datei. In der **Eigenschaften** Ändern der **Buildvorgang** Eigenschaft **Content**, und ändern Sie dann die **Include in VSIX-Datei** Eigenschaft  **"True"**.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMath.h** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMathWRT.pri** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMath.Lib** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMathSDK.props** Datei.  
  
14. In **Projektmappen-Explorer**, wählen die **NativeMath.h** Datei. In der **Eigenschaften** Ändern der **Include in VSIX-Datei** Eigenschaft **"true"**.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMath.dll** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **NativeMathWRT.dll** Datei.  
  
     Wiederholen Sie diesen Vorgang für die **SDKManifest.xml** Datei.  
  
15. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.  
  
16. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathVSIX** Projekt, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.  
  
17. In **Datei-Explorer**, navigieren Sie zu der *$SolutionRoot$ \NativeMathVSIX\bin\Debug* Ordner, und führen Sie *NativeMathVSIX.vsix* um die Installation zu beginnen.  
  
18. Wählen Sie die **installieren** Schaltfläche warten, bis die Installation abgeschlossen wurde, und starten Sie Visual Studio.  
  
##  <a name="createSample"></a> Zum Erstellen einer Beispielapp verwendet, die die Bibliothek.  
  
1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.  
  
2. Erweitern Sie in der Liste der Vorlagen, **Visual C++** > **Windows Universal** und wählen Sie dann **leere App**. In der **Namen** geben **NativeMathSDKSample**, und wählen Sie dann die **OK** Schaltfläche.  
  
3. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NativeMathSDKSample** Projekt, und wählen Sie dann **hinzufügen** > **Verweis**.  
  
4. In der **Verweis hinzufügen** erweitern Sie im Dialogfeld, in der Liste der Verweistypen **Universal Windows**, und wählen Sie dann **Erweiterungen**. Wählen Sie abschließend die **Native mathematische SDK** aus, und wählen Sie dann die **OK** Schaltfläche.
  
5. Zeigen Sie die Projekteigenschaften für NativeMathSDKSample an.  
  
    Die Eigenschaften, die Sie in definiert *NativeMathSDK.props* wurden angewendet, wenn Sie den Verweis hinzugefügt. Sie können überprüfen, ob die Eigenschaften angewendet wurden, anhand der **VC++-Verzeichnisse** -Eigenschaft des Projekts die **Konfigurationseigenschaften**.  
  
6. In **Projektmappen-Explorer**öffnen **"MainPage.xaml"**, und klicken Sie dann den folgenden XAML verwenden, um seinen Inhalt zu ersetzen:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7. Update *"MainPage.Xaml.h"* entsprechend diesen Code:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Update *"MainPage.Xaml.cpp"* entsprechend diesen Code:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Wählen Sie die **F5** Taste, um die app auszuführen.  
  
10. Geben Sie in der app, die zwei Zahlen, wählen Sie einen Vorgang, und wählen Sie dann die **=** Schaltfläche.  
  
     Das richtige Ergebnis wird angezeigt.  
  
    In dieser exemplarischen Vorgehensweise wurde gezeigt, wie zum Erstellen und verwenden eine Erweiterungs-SDK für den Aufruf einer [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] -Bibliothek und einem nicht-[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] Bibliothek.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen Sie eine SDK mit C# oder Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)
