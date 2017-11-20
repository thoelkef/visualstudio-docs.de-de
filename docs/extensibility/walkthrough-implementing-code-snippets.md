---
title: 'Exemplarische Vorgehensweise: Implementieren von Codeausschnitten | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc6fbfee6ab64cb50c03c55604db969e8ffc2d9d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-implementing-code-snippets"></a>Exemplarische Vorgehensweise: Implementieren von Codeausschnitten
Sie können Codeausschnitte erstellen und sie in eine Editor-Erweiterung einfügen, sodass Benutzer die Erweiterung sie ihren eigenen Code hinzufügen können.  
  
 Ein Codeausschnitt ist ein Fragment von Code oder anderem Text, die in einer Datei eingebunden werden können. Alle Codeausschnitte anzeigen, die für bestimmte Programmiersprachen erfasst wurden, auf die **Tools** Menü klicken Sie auf **Codeausschnitt-Manager**. Klicken Sie zum Einfügen eines Codeausschnitts in einer Datei mit der rechten Maustaste, den Ausschnitt soll, auf **Ausschnitt einfügen** oder **Umschließen mit**, suchen Sie den Ausschnitt, Sie möchten, und doppelklicken Sie dann auf. Drücken Sie TAB oder UMSCHALT + TAB, ändern die relevanten Teile des Ausschnitts ein, und drücken dann die EINGABETASTE oder ESC, um es zu akzeptieren. Weitere Informationen finden Sie unter [Codeausschnitte](../ide/code-snippets.md).  
  
 Ein Codeausschnitt ist in einer XML-Datei enthalten, die die Snippet-Dateinamenerweiterung aufweist. Ein Ausschnitt kann Felder enthalten, die hervorgehoben werden, nachdem der Codeausschnitt eingefügt wird, damit der Benutzer suchen und diese ändern kann. Snippet-Datei enthält auch Informationen für die **Codeausschnitt-Manager** , damit sie den Namen des Ausschnitts in der richtigen Kategorie angezeigt werden kann. Informationen zum Schema Ausschnitt finden Sie unter [Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md).  
  
 In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie diese Aufgaben ausführen:  
  
1.  Erstellen Sie und registrieren Sie Codeausschnitte für eine bestimmte Sprache.  
  
2.  Hinzufügen der **Ausschnitt einfügen** Befehl um ein Kontextmenü aufrufen.  
  
3.  Implementieren Sie die Snippet-Erweiterung.  
  
 Diese exemplarische Vorgehensweise basiert auf [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Erstellen und registrieren Codeausschnitte  
 Codeausschnitte werden in der Regel einen registrierten Sprachdienst zugeordnet. Sie ist jedoch nicht erforderlich, implementieren ein <xref:Microsoft.VisualStudio.Package.LanguageService> Codeausschnitte zu registrieren. Stattdessen geben Sie einfach eine GUID in die Indexdatei Ausschnitt, und klicken Sie dann verwenden derselben GUID in der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , die Sie dem Projekt hinzufügen.  
  
 Die folgenden Schritte veranschaulichen, wie zum Erstellen von Codeausschnitten und einen bestimmten GUID zuordnen.  
  
1.  Erstellen Sie die folgende Verzeichnisstruktur an:  
  
     **%INSTALLDIR%\TestSnippets\Snippets\1033\\**  
  
     wobei *INSTALLDIR%* ist der Visual Studio-Installationsordner. (Obwohl dieser Pfad zum Installieren von Codeausschnitten in der Regel verwendet wird, können Sie beliebige Pfade angeben.)  
  
2.  Klicken Sie im Ordner "\1033\" erstellen eine XML-Datei, und nennen sie **TestSnippets.xml**. (Auch diesen Namen in der Regel für einen Index Ausschnittdatei verwendet wird, können Sie einen beliebigen Namen angeben, solange sie eine Dateinamenerweiterung hat.) Fügen Sie den folgenden Text, und löschen Sie die Platzhalter-GUID und fügen Sie eigene hinzu.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <SnippetCollection>  
        <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">  
            <SnippetDir>  
                <OnOff>On</OnOff>  
                <Installed>true</Installed>  
                <Locale>1033</Locale>  
                <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>  
                <LocalizedName>Snippets</LocalizedName>  
            </SnippetDir>  
        </Language>  
    </SnippetCollection>  
    ```  
  
3.  Erstellen Sie eine Datei im Ordner "Ausschnitt", benennen Sie sie **testen**`.snippet`, und fügen Sie dann den folgenden Text hinzu:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
        <CodeSnippet Format="1.0.0">  
            <Header>  
                <Title>Test replacement fields</Title>  
                <Shortcut>test</Shortcut>  
                <Description>Code snippet for testing replacement fields</Description>  
                <Author>MSIT</Author>  
                <SnippetTypes>  
                    <SnippetType>Expansion</SnippetType>  
                </SnippetTypes>  
            </Header>  
            <Snippet>  
                <Declarations>  
                    <Literal>  
                      <ID>param1</ID>  
                        <ToolTip>First field</ToolTip>  
                        <Default>first</Default>  
                    </Literal>  
                    <Literal>  
                        <ID>param2</ID>  
                        <ToolTip>Second field</ToolTip>  
                        <Default>second</Default>  
                    </Literal>  
                </Declarations>  
                <References>  
                   <Reference>  
                       <Assembly>System.Windows.Forms.dll</Assembly>  
                   </Reference>  
                </References>  
                <Code Language="TestSnippets">  
                    <![CDATA[MessageBox.Show("$param1$");  
         MessageBox.Show("$param2$");]]>  
                </Code>    
            </Snippet>  
        </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
 Die folgenden Schritte zeigen, wie Codeausschnitte zu registrieren.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>So registrieren Sie Codeausschnitte für einen bestimmten GUID  
  
1.  Öffnen der **CompletionTest** Projekt. Informationen zum Erstellen des Projekts, finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  Fügen Sie im Projekt Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  Öffnen Sie im Projekt die Datei "Source.Extension.vsixmanifest" ein.  
  
4.  Stellen Sie sicher, dass die **Bestand** Registerkarte enthält eine **VsPackage** content-Type und, **Projekt** auf den Namen des Projekts festgelegt ist.  
  
5.  Wählen Sie das CompletionTest-Projekt, und legen Sie im Eigenschaftenfenster **Pkgdef-Datei generieren** auf **"true"**. Speichern Sie das Projekt.  
  
6.  Fügen Sie einen statischen `SnippetUtilities` Klasse, um das Projekt.  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  Klicken Sie in der Klasse SnippetUtilities definieren Sie eine GUID, und geben sie den Wert, den in der Datei SnippetsIndex.xml verwendet.  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> auf die `TestCompletionHandler` Klasse. Dieses Attribut kann eine beliebige öffentliche oder eine interne-Klasse im Projekt (nicht statische) hinzugefügt werden. (Möglicherweise müssen Sie Sie Hinzufügen einer `using` -Anweisung für den Namespace Microsoft.VisualStudio.Shell.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Erstellen Sie das Projekt, und führen Sie es aus. In der experimentellen Instanz von Visual Studio, die beginnt, wenn das Projekt ausgeführt wird, der Ausschnitt, die Sie gerade registriert angezeigt werden soll, der **Codeausschnitt-Manager** unter der **TestSnippets** Sprache.  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Das Kontextmenü hinzugefügt den Insert-Befehl Ausschnitt  
 Die **Ausschnitt einfügen** Befehl befindet sich nicht auf das Kontextmenü für eine Textdatei. Aus diesem Grund müssen Sie den Befehl aktivieren.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Um den Ausschnitt einfügen-Befehl im Kontextmenü hinzufügen  
  
1.  Öffnen der `TestCompletionCommandHandler` Klassendatei.  
  
     Da diese Klasse implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, können Sie aktivieren die **Ausschnitt einfügen** -Befehl in der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode. Überprüfen Sie, dass diese Methode nicht innerhalb einer Automatisierungsfunktion da aufgerufen wird, bevor Sie den Befehl aktivieren, wenn die **Ausschnitt einfügen** Befehl geklickt wird, wird das Snippet Picker-Benutzeroberfläche (UI) angezeigt.  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Erstellen Sie das Projekt, und führen Sie es aus. In der experimentellen Instanz Öffnen einer Datei, die die .zzz-Dateinamenerweiterung aufweist, und klicken Sie dann mit der rechten Maustaste an einer beliebigen Stelle in diesem. Die **Ausschnitt einfügen** Befehl sollte im Kontextmenü angezeigt werden.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Snippet-Erweiterung in der Codeausschnittauswahl UI implementieren  
 In diesem Abschnitt wird gezeigt, wie Code Snippet-Erweiterung implementiert, damit die Codeausschnittauswahl UI wird angezeigt, wenn **Ausschnitt einfügen** im Kontextmenü geklickt wird. Ein Codeausschnitt ist ebenfalls erweitert, wenn ein Benutzer die Verknüpfung des Codeausschnitt Typen und dann die Registerkarte "drückt.  
  
 Die Codeausschnittauswahl UI anzeigen und Aktivieren der Navigation und nach der einfügungsausschnitt akzeptieren, verwenden die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. Einfügung erfolgt durch die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> Methode.  
  
 Die Implementierung der Code Snippet Erweiterung verwendet ältere <xref:Microsoft.VisualStudio.TextManager.Interop> Schnittstellen. Wenn Sie von den aktuellen Editor-Klassen für die legacy-Code übersetzen, denken Sie daran, dass die legacy-Schnittstellen eine Kombination von Zeilennummern und Spaltennummern verwenden an Speicherorte in einem Textpuffer, aber die aktuellen Klassen einen Index verwenden. Aus diesem Grund positionieren Sie ein Puffer verfügt über drei Zeilen, von die jede zehn Zeichen lang ist (plus ein Zeilenumbruch, das zählt als 1 Zeichen), das vierte Zeichen in der dritten Zeile wird an der Position 27 in der aktuellen Implementierung, aber es ist in Zeile 2, 3 in der alten-Implementierung.  
  
#### <a name="to-implement-snippet-expansion"></a>Snippet-Erweiterung implementiert.  
  
1.  Um die Datei mit den `TestCompletionCommandHandler` Klasse, fügen Sie die folgenden `using` Anweisungen.  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Stellen Sie die `TestCompletionCommandHandler` Klasse implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Schnittstelle.  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  In der `TestCompletionCommandHandlerProvider` Klasse, importieren Sie die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Fügen Sie einige private Felder für die Schnittstellen der Code-Erweiterung und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  Im Konstruktor der `TestCompletionCommandHandler` Klasse, legen Sie die folgenden Felder.  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Die Codeausschnittauswahl an, wenn der Benutzer klickt auf die **Ausschnitt einfügen** Befehl, den folgenden Code hinzu die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. (Um diese Erläuterung besser lesbar zu machen, die Exec()-Code für die Anweisungsvervollständigung verwendeten wird nicht angezeigt, stattdessen die vorhandene Methode Codeblöcke hinzugefügt werden.) Fügen Sie den folgenden Codeblock nach dem Code, der prüft, ob ein Zeichen ein.  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Weist ein Ausschnitt Felder, die navigiert werden kann, wird die Erweiterung Sitzung öffnen beibehalten, bis die Erweiterung explizit akzeptiert wird; verfügt der Ausschnitt keine Felder, die Sitzung geschlossen wird und wird zurückgegeben, als `null` durch die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> Methode. In der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> -Methode, nach der Codeausschnittauswahl Benutzeroberflächencode, die Sie im vorherigen Schritt hinzugefügt fügen Sie folgenden Code Snippet Navigation behandeln (wenn der Benutzer nach dem Einfügen des Codeausschnitts TAB oder UMSCHALT + TAB drückt).  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Fügen Sie Code hinzu, um den Codeausschnitt einfügen, wenn der Benutzer die entsprechende Verknüpfung Typen und drückt dann die Registerkarte, die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. Die private Methode, die von den Ausschnitt eingefügt werden in einem späteren Schritt angezeigt. Fügen Sie den folgenden Code nach dem Navigationsbereich-Code, den Sie im vorherigen Schritt hinzugefügt.  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Implementieren Sie die Methoden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Schnittstelle. In dieser Implementierung sind nur die Methoden von Interesse <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Die anderen Methoden zurückgeben sollte <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>-Methode. Die Hilfsmethode, die von den Erweiterungen tatsächlich eingefügt wird in einem späteren Schritt erläutert. Die <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> enthält Zeilen- und Spaltennummer Informationen aus der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. Die folgende private Methode fügt einen Codeausschnitt, basierend entweder auf die Verknüpfung oder auf den Titel und den Pfad ein. Er ruft dann die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> Methode mit den Ausschnitt.  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Erstellen und Testen von Code Snippet-Erweiterung  
 Sie können testen, ob der Ausschnitt-Erweiterung im Projekt funktioniert.  
  
1.  Erstellen Sie die Projektmappe. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
2.  Öffnen Sie eine Textdatei, und geben Sie etwas Text.  
  
3.  Mit der rechten Maustaste an einer beliebigen Stelle im Text, und klicken Sie dann auf **Ausschnitt einfügen**.  
  
4.  Die Codeausschnittauswahl UI sollte angezeigt werden, mit der ein Popupfenster angezeigt, die besagt, dass **testen Ersatz Felder**. Doppelklicken Sie auf das Popupfenster angezeigt.  
  
     Der folgende Codeausschnitt eingefügt werden soll.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     Drücken Sie EINGABETASTE oder ESC.  
  
5.  Drücken Sie TAB und UMSCHALT + TAB Wechseln zwischen "Erster" und "zweiter".  
  
6.  Akzeptieren Sie die Einfügemarke durch Drücken der EINGABETASTE oder ESC.  
  
7.  Geben Sie in einem anderen Teil des Texts "test", und drücken Sie dann die Registerkarte ". Da "Test" die Codeausschnitt Verknüpfung ist, sollte erneut der Ausschnitt eingefügt werden.  
  
## <a name="next-steps"></a>Nächste Schritte