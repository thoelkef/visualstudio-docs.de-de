---
title: 'Exemplarische Vorgehensweise: Implementieren von Codeausschnitten | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 377660b32f8edbb26e8a062d55ee152132f7f587
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707080"
---
# <a name="walkthrough-implement-code-snippets"></a>Exemplarische Vorgehensweise: Implementieren von Codeausschnitten
Sie können Codeausschnitte erstellen und in einer Editor-Erweiterung einschließen, damit Benutzer von der Erweiterung sie ihren eigenen Code hinzufügen können.

 Ein Codeausschnitt ist ein Fragment von Code oder Text, der in einer Datei eingebunden werden kann. Um alle Codeausschnitte anzuzeigen, die für bestimmte Programmiersprachen erfasst wurden, auf die **Tools** Menü klicken Sie auf **Codeausschnitt-Manager**. Klicken Sie zum Einfügen eines Ausschnitts in einer Datei mit der rechten Maustaste, Sie den Ausschnitt möchten, auf Ausschnitt einfügen oder **Umschließen mit**suchen den gewünschten Codeausschnitt, und doppelklicken Sie darauf. Drücken Sie die **Registerkarte** oder **UMSCHALT**+**Registerkarte** ändern die relevanten Teile des Ausschnitts ein, und drücken anschließend **EINGABETASTE** oder **Esc** annehmen. Weitere Informationen finden Sie unter [Codeausschnitte](../ide/code-snippets.md).

 Ein Codeausschnitt ist in einer XML-Datei enthalten, die die Dateierweiterung Snippet * verfügt. Ein Ausschnitt kann Felder enthalten, die hervorgehoben werden, nachdem der Ausschnitt eingefügt wird, sodass der Benutzer suchen und ändern kann. Eine Snippet-Datei enthält auch Informationen für die **Codeausschnitt-Manager** , damit sie den Namen des Ausschnitts in der richtigen Kategorie angezeigt werden kann. Weitere Informationen zu den Schemas des Codeausschnitts, finden Sie unter [Code Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md).

 In dieser exemplarischen Vorgehensweise erfahren, wie diese Aufgaben auszuführen:

1. Erstellen Sie und registrieren Sie Codeausschnitte für eine bestimmte Sprache.

2. Hinzufügen der **Ausschnitt einfügen** Befehl in einem Kontextmenü.

3. Implementieren Sie die ausschnitterweiterung.

   Diese exemplarische Vorgehensweise basiert auf [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015 können installieren nicht Sie das Visual Studio SDK aus dem Downloadcenter. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Erstellen und Registrieren von Codeausschnitten
 Codeausschnitte sind in der Regel eine registrierte Sprachdienst zugeordnet. Sie ist jedoch nicht erforderlich, implementieren ein <xref:Microsoft.VisualStudio.Package.LanguageService> Codeausschnitte registrieren. Stattdessen geben Sie einfach eine GUID in der Indexdatei, und verwenden Sie dann auf die gleiche GUID in der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , die Sie Ihrem Projekt hinzufügen.

 Die folgenden Schritte veranschaulichen das Erstellen von Codeausschnitten aus, und ordnen sie einen bestimmten GUID.

1. Erstellen Sie die folgende Verzeichnisstruktur:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    wo *% INSTALLDIR%* ist der Visual Studio-Installationsordner. (Obwohl dieser Pfad in der Regel verwendet wird, um Codeausschnitte zu installieren, können Sie einen Pfad angeben.)

2. Erstellen Sie in den Ordner \1033\ ein *XML* Datei und nennen Sie sie **TestSnippets.xml**. (Obwohl dieser Name in der Regel für die Datei einen Index verwendet wird, können Sie einen beliebigen Namen angeben, solange sie verfügt über eine *XML* Dateinamenerweiterung.) Fügen Sie den folgenden Text ein, und klicken Sie dann löschen Sie die Platzhalter-GUID und fügen Sie eine eigene hinzu.

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

3. Erstellen Sie eine Datei im Ordner "Ausschnitt", nennen Sie es **testen**`.snippet`, und fügen Sie dann den folgenden Text hinzu:

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

### <a name="to-register-code-snippets-for-a-specific-guid"></a>So registrieren Sie Codeausschnitte für einen bestimmten GUID

1.  Öffnen der **CompletionTest** Projekt. Weitere Informationen zum Erstellen des Projekts, finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md).

2.  Fügen Sie im Projekt Verweise auf die folgenden Assemblys hinzu:

    -   Microsoft.VisualStudio.TextManager.Interop

    -   Microsoft.VisualStudio.TextManager.Interop.8.0

    -   microsoft.msxml

3.  Öffnen Sie im Projekt, das **"Source.Extension.vsixmanifest"** Datei.

4.  Stellen Sie sicher, dass die **Assets** Registerkarte enthält eine **VsPackage** content-Type und, **Projekt** auf den Namen des Projekts festgelegt ist.

5.  Wählen Sie das CompletionTest-Projekt, und legen Sie im Eigenschaftenfenster **Pkgdef-Datei generieren** zu **"true"**. Speichern Sie das Projekt.

6.  Fügen Sie einen statischen `SnippetUtilities` Klasse, um das Projekt.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7.  Klicken Sie in der Klasse SnippetUtilities definieren eine GUID, und weisen Sie ihm den Wert, der in verwendet die *SnippetsIndex.xml* Datei.

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8.  Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> auf die `TestCompletionHandler` Klasse. Dieses Attribut kann einer beliebigen öffentlichen oder internen-Klasse im Projekt (nicht statisch) hinzugefügt werden. (Sie müssen möglicherweise Hinzufügen einer `using` -Anweisung für den Namespace Microsoft.VisualStudio.Shell.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Erstellen Sie das Projekt, und führen Sie es aus. In der experimentellen Instanz von Visual Studio, die gestartet wird, wenn das Projekt ausgeführt wird, der Ausschnitt, die Sie gerade registriert angezeigt werden soll, der **Codeausschnitt-Manager** unter der **TestSnippets** Sprache.

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Fügen Sie den Ausschnitt einfügen-Befehl, um das Kontextmenü
 Die **Ausschnitt einfügen** Befehl befindet sich nicht auf das Kontextmenü für eine Textdatei. Aus diesem Grund müssen Sie den Befehl aktivieren.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Um den Ausschnitt einfügen-Befehl im Kontextmenü den Befehl hinzufügen

1.  Öffnen der `TestCompletionCommandHandler` Klassendatei.

     Da diese Klasse implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, können Sie aktivieren die **Ausschnitt einfügen** -Befehl in der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode. Überprüfen Sie, dass diese Methode nicht in eine Automatisierungsfunktion da aufgerufen wird, bevor Sie den Befehl aktivieren, wenn die **Ausschnitt einfügen** Befehl geklickt wird, wird der Ausschnitt Picker-Benutzeroberfläche (UI) angezeigt.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2.  Erstellen Sie das Projekt, und führen Sie es aus. Öffnen Sie in der experimentellen Instanz, eine Datei mit den *.zzz* Dateinamenerweiterung ein, und klicken Sie dann mit der rechten Maustaste an einer beliebigen Stelle in ihr. Die **Ausschnitt einfügen** Befehl sollte auf das Kontextmenü angezeigt werden.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementieren Sie in der Benutzeroberfläche des Snippet Picker ausschnitterweiterung
 In diesem Abschnitt wird gezeigt, wie codeausschnitterweiterung implementieren, damit die Codeausschnittauswahl UI wird angezeigt, wenn **Ausschnitt einfügen** im Kontextmenü den Befehl geklickt wird. Ein Codeausschnitt ist ebenfalls erweitert, wenn ein Benutzer die Verknüpfung eines Codeausschnitts Typen und dann drückt **Registerkarte**.

 Verwenden Sie zum Anzeigen der Ausschnittauswahl Benutzeroberfläche und Navigation und nach der einfügungsausschnitt Akzeptanz zu ermöglichen, die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. Das Einfügen an sich selbst erfolgt durch die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> Methode.

 Die Implementierung der codeausschnitterweiterung verwendet Legacy <xref:Microsoft.VisualStudio.TextManager.Interop> Schnittstellen. Wenn Sie von den aktuellen Editor-Klassen für die legacy-Code übersetzen, denken Sie daran, dass die legacy-Schnittstellen eine Kombination von Zeilennummern und Spaltennummern zur Angabe der Speicherorte in einem Textpuffer verwenden, aber die aktuellen Klassen, einen Index verwenden. Aus diesem Grund hat ein Puffer, drei Zeilen, die jeweils 10 Zeichen aufweisen (sowie eine neue Zeile, die zählt als ein Zeichen), das vierte Zeichen in der dritten Zeile wird an der Position 27, in der aktuellen Implementierung, aber es ist in Zeile 2, positionieren Sie 3 in der alten-Implementierung.

#### <a name="to-implement-snippet-expansion"></a>Um ausschnitterweiterung zu implementieren.

1.  Um die Datei mit den `TestCompletionCommandHandler` Klasse, fügen Sie die folgenden `using` Anweisungen.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2.  Stellen Sie die `TestCompletionCommandHandler` implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Schnittstelle.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3.  In der `TestCompletionCommandHandlerProvider` Klasse, importieren Sie die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4.  Fügen Sie private Felder für die Schnittstellen der Code-Erweiterung hinzu, und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5.  Im Konstruktor der `TestCompletionCommandHandler` Klasse, legen Sie die folgenden Felder.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6.  Die Codeausschnittauswahl angezeigt, wenn der Benutzer klickt der **Ausschnitt einfügen** Befehl, fügen Sie den folgenden Code der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. (Damit diese Erklärung besser lesbar ist, wird die `Exec()`Code, der verwendet wird, für die Anweisungsvervollständigung wird nicht angezeigt, stattdessen die vorhandene Methode Codeblöcke hinzugefügt werden.) Fügen Sie den folgenden Codeblock nach dem Code, der prüft, ob ein Zeichen ein.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7.  Wenn ein Codeausschnitt Felder, zu dem navigiert werden kann verfügt, wird die erweiterungssitzung öffnen beibehalten, bis explizit die Erweiterung zulässig ist; Wenn der Codeausschnitt keine Felder enthält, wird die Sitzung wird geschlossen, und wird zurückgegeben, als `null` durch die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> Methode. In der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> -Methode, klicken Sie nach der Ausschnittauswahl UI-Code, die Sie im vorherigen Schritt hinzugefügt haben hinzufügen den folgenden Code zum Behandeln von Codeausschnitt Navigation (wenn der Benutzer drückt **Registerkarte** oder **UMSCHALT** + **Registerkarte** nach dem Einfügen von Codeausschnitten).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8.  Um den Codeausschnitt einzufügen, wenn der Benutzer die entsprechende Verknüpfung Typen und dann drückt **Registerkarte**, fügen Sie Code in die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. Die private Methode, mit der den Codeausschnitt eingefügt werden in einem späteren Schritt angezeigt. Fügen Sie den folgenden Code nach der Navigationscode, den Sie im vorherigen Schritt hinzugefügt haben.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implementieren Sie die Methoden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Schnittstelle. In dieser Implementierung wird nur die Methoden von Interesse sind <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Die anderen Methoden sollten nur zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>-Methode. Die Hilfsmethode, die tatsächlich die Erweiterungen eingefügt wird in einem späteren Schritt behandelt. Die <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> enthält Zeilen- und Informationen, die Sie erhalten können die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Die folgende private Methode fügt einen Codeausschnitt, basierend entweder auf die Verknüpfung oder auf den Titel und den Pfad ein. Es ruft dann die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> Methode durch den Codeausschnitt.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Erstellen und Testen von codeausschnitterweiterung
 Sie können testen, ob der Ausschnitt in Ihrem Projekt funktioniert.

1.  Erstellen Sie die Projektmappe. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

2.  Öffnen Sie eine Textdatei, und geben Sie Text.

3.  Mit der rechten Maustaste an einer beliebigen Stelle im Text, und klicken Sie dann auf **Ausschnitt einfügen**.

4.  Die Benutzeroberfläche sollte angezeigt werden, mit einem Popup, die besagt, Codeausschnittauswahl **testen Ersetzungsfelder**. Doppelklicken Sie auf das Popup-Fenster.

     Der folgende Codeausschnitt eingefügt werden soll.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Drücken Sie nicht **EINGABETASTE** oder **Esc**.

5.  Drücken Sie **Registerkarte** und **UMSCHALT**+**Registerkarte** zum Wechseln zwischen "first" und "Sekunde".

6.  Akzeptieren Sie die Einfügung, drücken Sie eine **EINGABETASTE** oder **Esc**.

7.  In einem anderen Teil des Texts, geben Sie "test" aus, und drücken Sie dann die **Registerkarte**. Da "Test" die Verknüpfung eines Codeausschnitts ist, sollte erneut der Ausschnitt eingefügt werden.

## <a name="next-steps"></a>Nächste Schritte