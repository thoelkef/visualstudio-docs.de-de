---
title: 'Exemplarische Vorgehensweise: Erstellen eines C# SDK mithilfe von oder Visual Basic | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a604e3500c0ea438c987c4cf07ded98a5e03dd61
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558205"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Exemplarische Vorgehensweise: Erstellen eines SDK mit C# oder Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie ein einfaches Math Library SDK mithilfe von Visual C# erstellen und das SDK dann als Visual Studio-Erweiterung (VSIX) verpacken. Führen Sie die folgenden Schritte aus:  
  
- [So erstellen Sie die simplemath-Windows-Runtime Komponente](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [So erstellen Sie das simplemathvsix-Erweiterungsprojekt](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [So erstellen Sie eine Beispiel-APP, die die Klassenbibliothek verwendet](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="createClassLibrary"></a>So erstellen Sie die simplemath-Windows-Runtime Komponente  
  
1. Wählen Sie in der Menüleiste **Datei**, **neu**, **Neues Projekt**aus.  
  
2. Erweitern Sie in der Liste der Vorlagen die Option  **C# Visual** oder **Visual Basic**, wählen Sie den Knoten **Windows Store** aus, und wählen Sie dann die Vorlage **Windows-Runtime Komponenten** aus.  
  
3. Geben Sie im Feld **Name den Namen** **simplemath**an, und klicken Sie dann auf die Schaltfläche **OK** .  
  
4. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für den Projekt Knoten **simplemath** , und wählen Sie dann **Eigenschaften**aus.  
  
5. Benennen Sie **Class1.cs** in **Arithmetic.cs** um, und aktualisieren Sie ihn entsprechend dem folgenden Code:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für den Projektmappen-Knoten **"simplemath"** , und wählen Sie dann **Configuration Manager**aus.  
  
     Das Dialogfeld **Configuration Manager** wird geöffnet.  
  
7. Wählen Sie in der Liste **aktive Projektmappenkonfiguration** die Option **Release**aus.  
  
8. Überprüfen Sie in der Spalte **Konfiguration** , ob die Zeile **simplemath** auf **Release**festgelegt ist, und wählen Sie dann die Schaltfläche **Schließen** , um die Änderung zu übernehmen.  
  
    > [!IMPORTANT]
    > Das SDK für die simplemath-Komponente enthält nur eine Konfiguration. Diese Konfiguration muss der Releasebuild sein, oder apps, die die Komponente verwenden, erhalten keine Zertifizierung für die[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].  
  
9. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für den Projekt Knoten **simplemath** , und wählen Sie dann **Erstellen**aus.  
  
## <a name="createVSIX"></a>So erstellen Sie das simplemathvsix-Erweiterungsprojekt  
  
1. Wählen Sie im Kontextmenü für den Projektmappen-Knoten **"simplemath"** die Option **Hinzufügen**, **Neues Projekt**aus.  
  
2. Erweitern Sie in der Liste der Vorlagen die Option **Visual C#**  oder **Visual Basic**, wählen Sie den Knoten **Erweiterbarkeit** aus, und wählen Sie dann die Vorlage **VSIX-Projekt** aus.  
  
3. Geben Sie im Feld **Name den Namen** **simplemathvsix**an, und klicken Sie dann auf die Schaltfläche **OK** .  
  
4. Wählen Sie in **Projektmappen-Explorer**das Element **Source. Extension. vsixmanifest** aus.  
  
5. Wählen Sie in der Menüleiste **Ansicht**und **Code**aus.  
  
6. Ersetzen Sie den vorhandenen XML-Code durch den folgenden XML-Code:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. Wählen Sie in **Projektmappen-Explorer**das Projekt **simplemathvsix** aus.  
  
8. Wählen Sie in der Menüleiste **Projekt**, **Neues Element hinzufügen**aus.  
  
9. Erweitern Sie in der Liste der **allgemeinen Elemente**den Knoten **Daten**, und wählen Sie dann **XML-Datei**aus.  
  
10. Geben Sie im Feld **Name** `SDKManifest.xml`ein, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .  
  
11. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für `SDKManifest.xml`, wählen Sie **Eigenschaften**aus, und ändern Sie dann den Wert der Eigenschaft **in VSIX einschließen** in **true**.  
  
12. Ersetzen Sie den Inhalt der Datei durch folgendes XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für das Projekt **simplemathvsix** , wählen Sie **Hinzufügen**aus, und wählen Sie dann **neuer Ordner**aus.  
  
14. Benennen Sie den Ordner in `references`um.  
  
15. Öffnen Sie das Kontextmenü für den Ordner **Verweise** , wählen Sie **Hinzufügen**aus, und wählen Sie dann **neuer Ordner**aus.  
  
16. Benennen Sie den Unterordner in `commonconfiguration`um, erstellen Sie einen Unterordner darin, und benennen Sie den Unterordner `neutral`.  
  
17. Wiederholen Sie die vorherigen vier Schritte, und benennen Sie dabei den ersten Ordner in `redist`um.  
  
     Das Projekt enthält jetzt die folgende Ordnerstruktur:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für das Projekt **simplemath** , und wählen Sie dann **Ordner in Datei-Explorer öffnen**aus.  
  
19. Navigieren Sie im **Datei-Explorer**zum Ordner "Bin\Release", öffnen Sie das Kontextmenü für die Datei "simplemath. winmd", und wählen Sie dann **Kopieren**aus.  
  
20. Fügen Sie die Datei in **Projektmappen-Explorer**in den Ordner "references\commonconfiguration\neutral" im Projekt **simplemathvsix** ein.  
  
21. Wiederholen Sie den vorherigen Schritt, und legen Sie die Datei simplemath. pri in den Ordner redist\commonconfiguration\neutral des Projekts **simplemathvsix** ein.  
  
22. Wählen Sie in **Projektmappen-Explorer**die Option **simplemath. winmd**aus.  
  
23. Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaften** aus (Tastatur: Drücken Sie die F4-Taste).  
  
24. Ändern Sie im **Eigenschaften** Fenster die Eigenschaft **Buildaktion** in **Inhalt**, und ändern Sie dann die Eigenschaft **in VSIX einschließen** in **true**.  
  
25. Wiederholen Sie diesen Vorgang in **Projektmappen-Explorer**für **simplemath. pri**.  
  
26. Wählen Sie in **Projektmappen-Explorer**das Projekt **simplemathvsix** aus.  
  
27. Klicken Sie in der Menüleiste auf **Erstellen**, und **Erstellen Sie simplemathvsix**.  
  
28. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für das Projekt **simplemathvsix** , und wählen Sie dann **Ordner in Datei-Explorer öffnen**aus.  
  
29. Navigieren Sie im **Datei-Explorer**zu \bin\releaseordner, und führen Sie dann simplemathvsix. VSIX aus, um es zu installieren.  
  
30. Wählen Sie die Schaltfläche **Installieren** aus, warten Sie, bis die Installation abgeschlossen ist, und starten Sie Visual Studio neu.  
  
## <a name="createSample"></a>So erstellen Sie eine Beispiel-APP, die die Klassenbibliothek verwendet  
  
1. Wählen Sie in der Menüleiste **Datei**, **neu**, **Neues Projekt**aus.  
  
2. Erweitern Sie in der Liste der Vorlagen die Option **Visual C#**  oder **Visual Basic**, und wählen Sie dann den Knoten **Windows Store** aus.  
  
3. Wählen Sie die Vorlage **leere App** aus, benennen Sie das Projekt mit dem Namen **arithmeticui**, und wählen Sie dann die Schaltfläche **OK** .  
  
4. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für das **arithmeticui** -Projekt, und wählen Sie dann **Hinzufügen**, **Verweis**.  
  
5. Erweitern Sie in der Liste der Verweis Typen **Windows**, und klicken Sie dann auf **Erweiterungen**.  
  
6. Wählen Sie im Detailbereich die **simple math SDK** -Erweiterung aus.  
  
    Weitere Informationen zu Ihrem SDK werden angezeigt. Sie können den Link **Weitere Informationen** zum Öffnen von https://docs.microsoft.comauswählen, wie in der Datei "sdkmanifest. xml" weiter oben in dieser exemplarischen Vorgehensweise angegeben.  
  
7. Aktivieren Sie im Dialogfeld **Verweis-Manager** das Kontrollkästchen **simple math SDK** , und klicken Sie dann auf die Schaltfläche **OK** .  
  
8. Wählen Sie in der Menüleiste **Ansicht**, **Objektkatalog**aus.  
  
9. Wählen Sie in der Liste **Durchsuchen** die Option **simple math**aus.  
  
     Nun können Sie die Neuerungen im SDK untersuchen.  
  
10. Öffnen Sie in **Projektmappen-Explorer**die Datei "MainPage. XAML", und ersetzen Sie deren Inhalt durch den folgenden XAML-Code:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Aktualisieren Sie MainPage.XAML.cs entsprechend dem folgenden Code:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Drücken Sie die Taste F5, um die APP auszuführen.  
  
13. Geben Sie in der APP zwei Zahlen ein, wählen Sie einen Vorgang aus, und wählen Sie dann die Schaltfläche **=** aus.  
  
     Das richtige Ergebnis wird angezeigt.  
  
    Sie haben erfolgreich ein Erweiterungs-SDK erstellt und verwendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 Exemplarische Vorgehensweise [: Erstellen eines C++ SDK mithilfe](../extensibility/walkthrough-creating-an-sdk-using-cpp.md) von   
 Exemplarische Vorgehensweise [: Erstellen eines SDK mithilfe von JavaScript](walkthrough-creating-an-sdk-using-javascript.md)   
 [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)
