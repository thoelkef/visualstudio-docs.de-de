---
title: 'Exemplarische Vorgehensweise: Implementieren von Codeausschnitten | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: ba1b6e0852c1ec1b306938b791eed78e79d211ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697102"
---
# <a name="walkthrough-implement-code-snippets"></a>Exemplarische Vorgehensweise: Implementieren von Codeausschnitten
Sie können Codeausschnitte erstellen und in eine Editorerweiterung einschließen, damit Benutzer der Erweiterung sie ihrem eigenen Code hinzufügen können.

 Ein Codeausschnitt ist ein Codefragment oder ein anderer Text, der in eine Datei integriert werden kann. Um alle Snippets anzuzeigen, die für bestimmte Programmiersprachen registriert wurden, klicken Sie im Menü **Extras** auf **Code Snippet Manager**. Um einen Ausschnitt in eine Datei einzufügen, klicken Sie mit der rechten Maustaste auf die Stelle, an der Sie den Ausschnitt verwenden möchten, klicken Sie auf Ausschnitt einfügen oder **mit umgeben ,** suchen Sie den gewünschten Ausschnitt, und doppelklicken Sie dann darauf. Drücken Sie **die Tabulator-** oder **Umschalttaste,**+**Tab** um die relevanten Teile des Ausschnitts zu ändern, und drücken Sie dann **Enter** oder **Esc,** um ihn zu akzeptieren. Weitere Informationen finden Sie unter [Codeausschnitte](../ide/code-snippets.md).

 Ein Codeausschnitt ist in einer XML-Datei mit der Dateinamenerweiterung .snippet* enthalten. Ein Ausschnitt kann Felder enthalten, die nach dem Einfügen des Ausschnitts hervorgehoben werden, damit der Benutzer sie finden und ändern kann. Eine Codeausschnittdatei enthält auch Informationen für den **Code-Snippet-Manager,** sodass der Codeausschnittname in der richtigen Kategorie angezeigt werden kann. Informationen zum Snippet-Schema finden Sie unter [Schemareferenz code snippets](../ide/code-snippets-schema-reference.md).

 In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie diese Aufgaben ausführen:

1. Erstellen und registrieren Sie Codeausschnitte für eine bestimmte Sprache.

2. Fügen Sie den Befehl **Snippet einfügen** zu einem Kontextmenü hinzu.

3. Implementieren Sie die Snippet-Erweiterung.

   Diese exemplarische Vorgehensweise basiert auf [Walkthrough: Display statement completion](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Erstellen und Registrieren von Codeausschnitten
 In der Regel sind Codeausschnitte einem registrierten Sprachdienst zugeordnet. Sie müssen jedoch keine <xref:Microsoft.VisualStudio.Package.LanguageService> zum Registrieren von Codeausschnitten implementieren. Geben Sie stattdessen einfach eine GUID in der Snippet-Indexdatei <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> an, und verwenden Sie dann dieselbe GUID in der, die Sie Ihrem Projekt hinzufügen.

 Die folgenden Schritte veranschaulichen, wie Codeausschnitte erstellt und einer bestimmten GUID zugeordnet werden.

1. Erstellen Sie die folgende Verzeichnisstruktur:

    **%InstallDir %'TestSnippets'Snippets'1033\\**

    wobei *%InstallDir%* der Visual Studio-Installationsordner ist. (Obwohl dieser Pfad in der Regel zum Installieren von Codeausschnitten verwendet wird, können Sie einen beliebigen Pfad angeben.)

2. Erstellen Sie im Ordner .1033 eine *.xml-Datei,* und nennen Sie sie **TestSnippets.xml**. (Obwohl dieser Name in der Regel für eine Codeausschnittindexdatei verwendet wird, können Sie einen beliebigen Namen angeben, solange er über eine *Dateinamenerweiterung von XML* verfügt.) Fügen Sie den folgenden Text hinzu, und löschen Sie dann die Platzhalter-GUID, und fügen Sie Eine eigene hinzu.

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

3. Erstellen Sie eine Datei im Snippet-Ordner, benennen Sie sie **als test**`.snippet`, und fügen Sie dann den folgenden Text hinzu:

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

   Die folgenden Schritte zeigen, wie Sie die Codeausschnitte registrieren.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>So registrieren Sie Codeausschnitte für eine bestimmte GUID

1. Öffnen Sie das **CompletionTest-Projekt.** Informationen zum Erstellen dieses Projekts finden Sie unter [Exemplarische Vorgehensweise: Anweisungsvervollständigung anzeigen](../extensibility/walkthrough-displaying-statement-completion.md).

2. Fügen Sie im Projekt Verweise auf die folgenden Assemblys hinzu:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - microsoft.msxml

3. Öffnen Sie im Projekt die Datei **source.extension.vsixmanifest.**

4. Stellen Sie sicher, dass die Registerkarte **Assets** einen **VsPackage-Inhaltstyp** enthält und dass **Project** auf den Namen des Projekts festgelegt ist.

5. Wählen Sie das CompletionTest-Projekt aus, und legen Sie im Eigenschaftenfenster **Pkgdef-Datei** **auf true generieren**fest. Speichern Sie das Projekt.

6. Fügen Sie `SnippetUtilities` dem Projekt eine statische Klasse hinzu.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. Definieren Sie in der SnippetUtilities-Klasse eine GUID, und geben Sie ihr den Wert an, den Sie in der Datei *SnippetsIndex.xml* verwendet haben.

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Fügen <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> Sie `TestCompletionHandler` die der Klasse hinzu. Dieses Attribut kann jeder öffentlichen oder internen (nicht statischen) Klasse im Projekt hinzugefügt werden. (Möglicherweise müssen Sie `using` eine Direktive für den Microsoft.VisualStudio.Shell-Namespace hinzufügen.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Erstellen Sie das Projekt, und führen Sie es aus. In der experimentellen Instanz von Visual Studio, die beim Ausführen des Projekts gestartet wird, sollte der soeben registrierte Ausschnitt im **Codesnippets Manager** unter der Sprache **TestSnippets** angezeigt werden.

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Hinzufügen des Befehls Snippet einfügen zum Kontextmenü
 Der Befehl **Snippet einfügen** ist nicht im Kontextmenü für eine Textdatei enthalten. Daher müssen Sie den Befehl aktivieren.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>So fügen Sie den Befehl Snippet einfügen zum Kontextmenü hinzu

1. Öffnen `TestCompletionCommandHandler` Sie die Klassendatei.

     Da diese Klasse <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>implementiert, können Sie den Befehl **Snippet einfügen** in der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode aktivieren. Bevor Sie den Befehl aktivieren, überprüfen Sie, ob diese Methode nicht innerhalb einer Automatisierungsfunktion aufgerufen wird, da beim Klicken auf den Befehl **Snippet** einfügen die Benutzeroberfläche der Snippet-Auswahl (UI) angezeigt wird.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Erstellen Sie das Projekt, und führen Sie es aus. Öffnen Sie in der experimentellen Instanz eine Datei mit der *Dateinamenerweiterung .zzz,* und klicken Sie dann mit der rechten Maustaste auf eine beliebige Stelle. Der Befehl **Snippet einfügen** sollte im Kontextmenü angezeigt werden.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementieren der Snippet-Erweiterung in der Snippet-Picker-Benutzeroberfläche
 In diesem Abschnitt wird gezeigt, wie Die Codeausschnitterweiterung implementiert wird, sodass die Benutzeroberfläche der Auswahl auswahl für Ausschnitte angezeigt wird, wenn im Kontextmenü auf **"Snippet** einfügen" geklickt wird. Ein Codeausschnitt wird auch erweitert, wenn ein Benutzer die Codeausschnittverknüpfung eingibt und dann **Tab**drückt.

 Verwenden Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode, um die Benutzeroberfläche der Auswahl für Ausschnitte aus der Auswahl des Ausschnitts anzuzeigen und die Navigation und die Annahme von Ausschnitts nach dem Einfügen zu aktivieren. Die Einfügung selbst <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> wird von der Methode behandelt.

 Die Implementierung der Codeausschnitterweiterung verwendet <xref:Microsoft.VisualStudio.TextManager.Interop> ältere Schnittstellen. Wenn Sie von den aktuellen Editorklassen in den Legacycode übersetzen, denken Sie daran, dass die älteren Schnittstellen eine Kombination aus Zeilennummern und Spaltennummern verwenden, um Positionen in einem Textpuffer anzugeben, die aktuellen Klassen jedoch einen Index verwenden. Wenn ein Puffer also drei Zeilen hat, von denen jede 10 Zeichen hat (plus eine Zeilenzeile, die als ein Zeichen zählt), befindet sich das vierte Zeichen in der dritten Zeile an Position 27 in der aktuellen Implementierung, aber es befindet sich in Zeile 2, Position 3 in der alten Implementierung.

#### <a name="to-implement-snippet-expansion"></a>So implementieren Sie die Snippet-Erweiterung

1. Fügen Sie der `TestCompletionCommandHandler` Datei, die `using` die Klasse enthält, die folgenden Direktiven hinzu.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Machen `TestCompletionCommandHandler` Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Klasse die Schnittstelle implementieren.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. Importieren `TestCompletionCommandHandlerProvider` Sie in <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>der Klasse die .

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Fügen Sie einige private Felder für <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>die Codeerweiterungsschnittstellen und die hinzu.

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. Legen Sie im `TestCompletionCommandHandler` Konstruktor der Klasse die folgenden Felder fest.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Um die Auswahlauswahl für Ausschnitte anzuzeigen, wenn der Benutzer auf den Befehl **Snippet** einfügen klickt, fügen Sie der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode den folgenden Code hinzu. (Um diese Erklärung lesbarer `Exec()`zu machen, wird der Code, der für die Anweisungsvervollständigung verwendet wird, nicht angezeigt; stattdessen werden Codeblöcke zur vorhandenen Methode hinzugefügt.) Fügen Sie den folgenden Codeblock nach dem Code hinzu, der nach einem Zeichen sucht.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Wenn ein Ausschnitt Felder enthält, die navigiert werden können, bleibt die Erweiterungssitzung offen, bis die Erweiterung explizit akzeptiert wird. Wenn der Ausschnitt keine Felder enthält, wird die Sitzung `null` geschlossen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> und wie von der Methode zurückgegeben. Fügen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Sie in der Methode nach dem Code der Auswahlauswahl aus, den Sie im vorherigen Schritt hinzugefügt haben, den folgenden Code zum Behandeln der Snippet-Navigation hinzu (wenn der Benutzer **die Registerkarte** oder **Umschalttaste**+**Tab** nach dem Einfügen von Ausschnitten drückt).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Um den Codeausschnitt einzufügen, wenn der Benutzer die **Tab**entsprechende Verknüpfung eingibt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> und dann Tab drückt, fügen Sie der Methode Code hinzu. Die private Methode, die den Ausschnitt einfügt, wird in einem späteren Schritt angezeigt. Fügen Sie den folgenden Code nach dem Navigationscode hinzu, den Sie im vorherigen Schritt hinzugefügt haben.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Methoden der Schnittstelle. Bei dieser Implementierung sind <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> die einzigen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>Methoden von Interesse und . Die anderen Methoden <xref:Microsoft.VisualStudio.VSConstants.S_OK>sollten einfach zurückgegeben werden.

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>-Methode. Die Hilfsmethode, die die Erweiterungen tatsächlich einfügt, wird in einem späteren Schritt behandelt. Die <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> enthält Zeilen- und Spalteninformationen, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>die Sie aus der erhalten können.

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Die folgende private Methode fügt einen Codeausschnitt ein, der entweder auf der Verknüpfung oder auf dem Titel und Pfad basiert. Anschließend wird <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> die Methode mit dem Ausschnitt aufruft.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Erstellen und Testen der Codeausschnittserweiterung
 Sie können testen, ob die Snippet-Erweiterung in Ihrem Projekt funktioniert.

1. Erstellen Sie die Projektmappe. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

2. Öffnen Sie eine Textdatei, und geben Sie Text ein.

3. Klicken Sie mit der rechten Maustaste auf eine andere Stelle im Text, und klicken Sie dann auf **Snippet einfügen**.

4. Die Benutzeroberfläche für die Auswahl von Ausschnitten sollte mit einem Pop-up angezeigt werden, das **Testersatzfelder**angibt. Doppelklicken Sie auf das Pop-up.

     Der folgende Ausschnitt sollte eingefügt werden.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Drücken Sie nicht **enter** oder **Esc**.

5. Drücken Sie **Tab** und **Shift**+**Tab,** um zwischen "first" und "second" umzuschalten.

6. Akzeptieren Sie die Einfügung, indem Sie entweder **Enter** oder **Esc drücken.**

7. Geben Sie in einem anderen Teil des Textes "test" ein, und **drücken**Sie dann tab . Da "test" die Code-Snippet-Verknüpfung ist, sollte der Ausschnitt erneut eingefügt werden.

## <a name="next-steps"></a>Nächste Schritte
