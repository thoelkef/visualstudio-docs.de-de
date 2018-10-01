---
title: 'Exemplarische Vorgehensweise: Erstellen eines SDKS mit c# oder Visual Basic | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d870be666efd0457ed472fb065642db456459b97
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511367"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Exemplarische Vorgehensweise: Erstellen eines SDK mit C# oder Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines SDK mit c# oder Visual Basic](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic).  
  
In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie mit Visual C#-Erstellen eines einfachen Math-Bibliothek-SDK und klicken Sie dann das SDK als ein Visual Studio-Erweiterung (VSIX)-Paket. Sie müssen die folgenden Schritte auszuführen:  
  
-   [So erstellen Sie die SimpleMath Windows Runtime-Komponente](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [Erstellen Sie das Erweiterungsprojekt SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [Zum Erstellen einer Beispielapp verwendet, die die Bibliothek.](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> So erstellen Sie die SimpleMath Windows Runtime-Komponente  
  
1.  Wählen Sie auf der Menüleiste **Datei**, **neu**, **neues Projekt**.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C#-** oder **Visual Basic**, wählen Sie die **Windows Store** Knoten, und wählen Sie dann die **Komponente für Windows-Runtime** Vorlage.  
  
3.  In der **Namen** geben **SimpleMath**, und wählen Sie dann die **OK** Schaltfläche.  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMath** Projektknoten, und wählen Sie dann **Eigenschaften**.  
  
5.  Benennen Sie **"Class1.cs"** zu **Arithmetic.cs** und aktualisieren, um entsprechend folgendem Code:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Lösung "SimpleMath"** Knoten, und wählen Sie dann **Configuration Manager**.  
  
     Die **Configuration Manager** Dialogfeld wird geöffnet.  
  
7.  In der **aktive Projektmappenkonfiguration** wählen **Version**.  
  
8.  In der **Konfiguration** Spalte überprüfen Sie, ob **SimpleMath** Zeile nastaven NA hodnotu **Version**, und wählen Sie dann die **schließen** Schaltfläche zum Akzeptieren der Ändern Sie.  
  
    > [!IMPORTANT]
    >  Das SDK für die Komponente SimpleMath enthält nur eine Konfiguration. Diese Konfiguration muss die endgültige Produktversion sein, oder apps, die die Komponente wird nicht Zertifizierung übergeben, für die[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].  
  
9. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMath** Projektknoten, und wählen Sie dann **erstellen**.  
  
##  <a name="createVSIX"></a> Erstellen Sie das Erweiterungsprojekt SimpleMathVSIX  
  
1.  Auf der rechten Maustaste auf die **Lösung "SimpleMath"** Knoten, wählen Sie **hinzufügen**, **neues Projekt**.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C#-** oder **Visual Basic**, wählen Sie die **Erweiterbarkeit** Knoten, und wählen Sie dann die **VSIX-Projekt** Vorlage.  
  
3.  In der **Namen** geben **SimpleMathVSIX**, und wählen Sie dann die **OK** Schaltfläche.  
  
4.  In **Projektmappen-Explorer**, wählen Sie die **"Source.Extension.vsixmanifest"** Element.  
  
5.  Wählen Sie in der Menüleiste **Ansicht**und **Code**aus.  
  
6.  Ersetzen Sie den vorhandenen XML-Code durch folgendes XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  In **Projektmappen-Explorer**, wählen Sie die **SimpleMathVSIX** Projekt.  
  
8.  Wählen Sie auf der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
9. In der Liste der **gemeinsame Elemente**, erweitern Sie **Daten**, und wählen Sie dann **XML-Datei**.  
  
10. In der **Namen** geben `SDKManifest.xml`, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
11. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für `SDKManifest.xml`, wählen Sie **Eigenschaften**, und ändern Sie den Wert, der die **Include in VSIX-Datei** Eigenschaft **"True"**.  
  
12. Ersetzen Sie den Inhalt der Datei durch folgendes XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMathVSIX** Projekts **hinzufügen**, und wählen Sie dann **neuer Ordner**.  
  
14. Benennen Sie den Ordner zu `references`.  
  
15. Öffnen Sie das Kontextmenü für die **Verweise** Ordner wählen **hinzufügen**, und wählen Sie dann **neuer Ordner**.  
  
16. Benennen Sie den Unterordner zu `commonconfiguration`, erstellen Sie einen Unterordner darin, und nennen Sie den Unterordner `neutral`.  
  
17. Wiederholen Sie die vorhergehenden vier Schritte, die dieses Mal den ersten Ordner umbenennen `redist`.  
  
     Das Projekt enthält nun die folgende Ordnerstruktur:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMath** Projekt, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.  
  
19. In **Datei-Explorer**, navigieren Sie zum Ordner "bin\Release", öffnen das Kontextmenü für die SimpleMath.winmd-Datei, und wählen Sie dann **Kopie**.  
  
20. In **Projektmappen-Explorer**, fügen Sie die Datei in den Ordner References\commonconfiguration\neutral in die **SimpleMathVSIX** Projekt.  
  
21. Wiederholen Sie die im vorherigen Schritt einfügen der SimpleMath.pri-Datei in den Ordner Redist\commonconfiguration\neutral in die **SimpleMathVSIX** Projekt.  
  
22. In **Projektmappen-Explorer**, wählen Sie **SimpleMath.winmd**.  
  
23. Wählen Sie auf der Menüleiste **Ansicht**, **Eigenschaften** (Tastatur: Drücken Sie die F4-Taste).  
  
24. In der **Eigenschaften** Ändern der **Buildvorgang** Eigenschaft **Content**, und ändern Sie dann die **Include in VSIX-Datei** Eigenschaft  **"True"**.  
  
25. In **Projektmappen-Explorer**, wiederholen Sie diesen Vorgang für **SimpleMath.pri**.  
  
26. In **Projektmappen-Explorer**, wählen Sie die **SimpleMathVSIX** Projekt.  
  
27. Wählen Sie auf der Menüleiste **erstellen**, **erstellen SimpleMathVSIX**.  
  
28. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SimpleMathVSIX** Projekt, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.  
  
29. In **Datei-Explorer**, navigieren Sie zum Ordner \bin\Release, und führen Sie SimpleMathVSIX.vsix, um es zu installieren.  
  
30. Wählen Sie die **installieren** Schaltfläche warten, bis zum Abschluss der Installation, und klicken Sie dann Visual Studio neu starten.  
  
##  <a name="createSample"></a> Zum Erstellen einer Beispielapp verwendet, die die Bibliothek.  
  
1.  Wählen Sie auf der Menüleiste **Datei**, **neu**, **neues Projekt**.  
  
2.  Erweitern Sie in der Liste der Vorlagen, **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **Windows Store** Knoten.  
  
3.  Wählen Sie die **leere App** Vorlage, nennen Sie das Projekt **ArithmeticUI**, und wählen Sie dann die **OK** Schaltfläche.  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ArithmeticUI** Projekt, und wählen Sie dann **hinzufügen**, **Verweis**.  
  
5.  Erweitern Sie in der Liste der Verweistypen, **Windows**, und wählen Sie dann **Erweiterungen**.  
  
6.  Wählen Sie im Detailbereich die **einfache mathematische SDK** Erweiterung.  
  
     Weitere Informationen zu Ihrem SDK wird angezeigt. Sie können die **mehr Informationen** Link zum Öffnen http://www.msdn.microsoft.com, wie Sie in der SDKManifest.xml-Datei weiter oben in dieser exemplarischen Vorgehensweise angegeben.  
  
7.  In der **Verweis-Manager** wählen Sie im Dialogfeld die **einfache mathematische SDK** aus, und wählen Sie dann die **OK** Schaltfläche.  
  
8.  Wählen Sie auf der Menüleiste **Ansicht**, **Objektkatalog**.  
  
9. In der **Durchsuchen** wählen **einfache mathematische**.  
  
     Sie können nun untersuchen, was im SDK ist.  
  
10. In **Projektmappen-Explorer**, öffnen Sie "MainPage.xaml" ein, und Ersetzen Sie den Inhalt mit den folgenden XAML:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Aktualisieren Sie die Datei "MainPage.Xaml.cs" entsprechend den folgenden Code:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Wählen Sie die F5-Taste, um die app auszuführen.  
  
13. Geben Sie in der app, die zwei Zahlen, wählen Sie einen Vorgang aus, und wählen Sie dann die **=** Schaltfläche.  
  
     Das richtige Ergebnis wird angezeigt.  
  
 Sie haben erfolgreich erstellt und verwendet eine Erweiterungs-SDK.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines SDKS mit C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Exemplarische Vorgehensweise: Erstellen eines SDKS mit JavaScript](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)

