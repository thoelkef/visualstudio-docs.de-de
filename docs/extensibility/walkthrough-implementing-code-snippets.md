---
title: "Exemplarische Vorgehensweise: Implementieren von Codeausschnitten | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 17
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Implementieren von Codeausschnitten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Codeausschnitte erstellen und Einbinden in eine Editor\-Erweiterung, damit Benutzer die Erweiterung diese ihren eigenen Code hinzufügen können.  
  
 Ein Codeausschnitt ist ein Fragment von Code oder Text, der in einer Datei eingebunden werden kann. Alle Codeausschnitte anzeigen, die für bestimmte Programmiersprachen erfasst wurden, auf die **Tools** Menü klicken Sie auf **Codeausschnitt\-Manager**. Um einen Ausschnitt einzufügen, den Ausschnitt angezeigt werden soll, in einer Datei mit der rechten Maustaste klicken Sie auf **Ausschnitt einfügen** oder **Umschließen mit**, suchen Sie den gewünschten Ausschnitt, und doppelklicken Sie darauf. Drücken Sie TAB oder UMSCHALT \+ TAB, zu ändern, die relevanten Teile des Ausschnitts ein, und drücken dann die EINGABETASTE oder ESC, um es zu akzeptieren. Weitere Informationen finden Sie unter [Codeausschnitte](../ide/code-snippets.md).  
  
 Ein Codeausschnitt ist in eine XML\-Datei enthalten, die die Erweiterung Snippet verfügt. Ein Ausschnitt kann Felder enthalten, die hervorgehoben werden, nachdem der Codeausschnitt eingefügt wird, damit der Benutzer suchen und diese ändern kann. Eine Snippet\-Datei enthält auch Informationen für die **Codeausschnitt\-Manager** damit sie den Namen des Ausschnitts in der richtigen Kategorie angezeigt werden kann. Informationen über den Codeausschnitt\-Schema finden Sie unter [Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md).  
  
 Diese exemplarische Vorgehensweise zeigt, wie Sie diese Aufgaben ausführen:  
  
1.  Erstellen Sie und registrieren Sie Codeausschnitte für eine bestimmte Sprache.  
  
2.  Hinzufügen der **Ausschnitt einfügen** Befehl zu einem Kontextmenü.  
  
3.  Codeausschnitt\-Erweiterung zu implementieren.  
  
 Diese exemplarische Vorgehensweise basiert auf [Exemplarische Vorgehensweise: Anzeigen von Anweisungsabschluss](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise ausführen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Erstellen und Registrieren von Codeausschnitten  
 In der Regel sind Codeausschnitte mit einem Dienst registrierten Sprache verknüpft. Sie ist jedoch nicht erforderlich, Implementieren einer <xref:Microsoft.VisualStudio.Package.LanguageService> Codeausschnitte zu registrieren. Stattdessen geben Sie einfach eine GUID in der Indexdatei Codeausschnitt, und verwenden Sie die gleiche GUID in die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> die Sie dem Projekt hinzufügen.  
  
 Die folgenden Schritte veranschaulichen, wie Codeausschnitte erstellen und diese mit einer bestimmten GUID zuzuordnen.  
  
1.  Erstellen Sie die folgende Verzeichnisstruktur:  
  
     **%INSTALLDIR%\\TestSnippets\\Snippets\\1033\\**  
  
     wobei *% INSTALLDIR%* ist der Visual Studio\-Installationsordner. \(Obwohl dieser Pfad zum Installieren von Codeausschnitten in der Regel verwendet wird, können Sie einen Pfad angeben.\)  
  
2.  Klicken Sie im Ordner \\1033\\ erstellen Sie eine XML\-Datei, und nennen sie **TestSnippets.xml**. \(Obwohl dieser Name in der Regel für einen Index Ausschnittdatei verwendet wird, können Sie einen beliebigen Namen geben solange sie die Erweiterung .xml hat.\) Fügen Sie den folgenden Text, und löschen Sie die Platzhalter\-GUID und fügen Sie eine eigene hinzu.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <SnippetCollection> <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}"> <SnippetDir> <OnOff>On</OnOff> <Installed>true</Installed> <Locale>1033</Locale> <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath> <LocalizedName>Snippets</LocalizedName> </SnippetDir> </Language> </SnippetCollection>  
    ```  
  
3.  Erstellen Sie eine Datei im Ordner "Ausschnitt", nennen Sie sie **Testen**`.snippet`, und fügen Sie den folgenden Text hinzu:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet"> <CodeSnippet Format="1.0.0"> <Header> <Title>Test replacement fields</Title> <Shortcut>test</Shortcut> <Description>Code snippet for testing replacement fields</Description> <Author>MSIT</Author> <SnippetTypes> <SnippetType>Expansion</SnippetType> </SnippetTypes> </Header> <Snippet> <Declarations> <Literal> <ID>param1</ID> <ToolTip>First field</ToolTip> <Default>first</Default> </Literal> <Literal> <ID>param2</ID> <ToolTip>Second field</ToolTip> <Default>second</Default> </Literal> </Declarations> <References> <Reference> <Assembly>System.Windows.Forms.dll</Assembly> </Reference> </References> <Code Language="TestSnippets"> <![CDATA[MessageBox.Show("$param1$"); MessageBox.Show("$param2$");]]> </Code> </Snippet> </CodeSnippet> </CodeSnippets>  
    ```  
  
 Die folgenden Schritte zeigen, wie Sie die Codeausschnitte zu registrieren.  
  
#### So registrieren Sie Codeausschnitte für einen bestimmten GUID  
  
1.  Öffnen Sie die **CompletionTest** Projekt. Informationen zum Erstellen dieses Projekts finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Anweisungsabschluss](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  Fügen Sie im Projekt Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  Öffnen Sie im Projekt die Datei "Source.Extension.vsixmanifest" ein.  
  
4.  Stellen Sie sicher, dass die **Bestand** Registerkarte enthält eine **VsPackage** content\-Typ und **Projekt** auf den Namen des Projekts festgelegt ist.  
  
5.  Wählen Sie das Projekt CompletionTest, und legen Sie im Fenster Eigenschaften **Pkgdef\-Datei erstellen** auf **true**. Speichern Sie das Projekt.  
  
6.  Fügen Sie eine statische `SnippetUtilities` Klasse zum Projekt.  
  
     [!code-cs[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  Klicken Sie in der SnippetUtilities\-Klasse definieren Sie eine GUID, und geben sie den Wert, den Sie in der Datei SnippetsIndex.xml verwendet.  
  
     [!code-cs[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> an die `TestCompletionHandler` Klasse. Dieses Attribut kann für jede öffentliche und interne\-Klasse im Projekt \(nicht statisch\) hinzugefügt werden. \(Möglicherweise müssen Sie hinzufügen eine `using` \-Anweisung für den Namespace Microsoft.VisualStudio.Shell.\)  
  
     [!code-cs[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Erstellen Sie das Projekt, und führen Sie es aus. In der experimentellen Instanz von Visual Studio, die beginnt, wenn das Projekt ausgeführt wird, der Ausschnitt, das Sie gerade registriert angezeigt werden soll, der **Codeausschnitt\-Manager** unter der **TestSnippets** Sprache.  
  
## Ausschnitt einfügen\-Befehl hinzufügen im Kontextmenü  
 Die **Ausschnitt einfügen** Befehl befindet sich nicht auf das Kontextmenü für eine Textdatei. Aus diesem Grund müssen Sie den Befehl aktivieren.  
  
#### Im Kontextmenü den Befehl Ausschnitt einfügen hinzu  
  
1.  Öffnen Sie die `TestCompletionCommandHandler` Klassendatei.  
  
     Da diese Klasse implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, können Sie aktivieren die **Ausschnitt einfügen** in den Befehl die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode. Bevor Sie den Befehl aktivieren, überprüfen Sie, dass diese Methode nicht in einer Automatisierungsfunktion da aufgerufen wird bei der **Ausschnitt einfügen** Befehl geklickt wird, wird die Snippet Picker\-Benutzeroberfläche \(UI\) angezeigt.  
  
     [!code-cs[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Erstellen Sie das Projekt, und führen Sie es aus. Öffnen Sie in der experimentellen Instanz eine Datei mit der Erweiterung .zzz, und klicken Sie dann mit der rechten Maustaste an einer beliebigen Stelle in diesem. Die **Ausschnitt einfügen** Befehl im Kontextmenü angezeigt werden sollte.  
  
## Codeausschnitt\-Erweiterung in der Codeausschnittauswahl Benutzeroberfläche implementieren  
 Dieser Abschnitt zeigt, wie Code Snippet\-Erweiterung zu implementieren, sodass die Codeausschnittauswahl UI wird angezeigt, wenn **Ausschnitt einfügen** im Kontextmenü geklickt wird. Ein Codeausschnitt wird auch erweitert werden, wenn ein Benutzer die Verknüpfung des Codeausschnitt Typen und drückt dann die Registerkarte.  
  
 Verwenden Sie zum Anzeigen der Codeausschnittauswahl Benutzeroberfläche und Navigation und einfügungsausschnitt nach der Annahme zu ermöglichen, die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. Die Einfügung erfolgt durch die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> Methode.  
  
 Die Implementierung von Code Snippet Erweiterung verwendet ältere <xref:Microsoft.VisualStudio.TextManager.Interop> Schnittstellen. Wenn Sie die aktuellen Editor\-Klassen für die legacy\-Code übersetzen, beachten Sie, dass die legacy\-Schnittstellen mithilfe einer Kombination von Zeilennummern und Spaltennummern Speicherorte in einem Textpuffer angeben, aber die aktuellen Klassen einen Index verwenden. Aus diesem Grund positionieren Sie ein Puffer verfügt über drei Zeilen, von die jedes über zehn Zeichen hat \(plus einem Zeilenumbruch, die zählt als 1 Zeichen\), das vierte Zeichen in der dritten Zeile an Position 27 in der aktuellen Implementierung ist, aber es ist in Zeile 2, 3 in der alten\-Implementierung.  
  
#### Codeausschnitt\-Erweiterung implementiert.  
  
1.  Um die Datei mit der `TestCompletionCommandHandler` \-Klasse verwenden, fügen Sie die folgenden `using` Anweisungen.  
  
     [!code-cs[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Stellen Sie die `TestCompletionCommandHandler` Klasse implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Schnittstelle.  
  
     [!code-cs[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  In der `TestCompletionCommandHandlerProvider` Klasse, importieren Sie die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-cs[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Fügen Sie private Felder für die Schnittstellen des Code\-Erweiterung hinzu, und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-cs[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  Im Konstruktor der `TestCompletionCommandHandler` Klasse, legen Sie die folgenden Felder.  
  
     [!code-cs[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Die Codeausschnittauswahl angezeigt, wenn der Benutzer klickt der **Ausschnitt einfügen** Befehl, fügen Sie den folgenden Code der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. \(Um diese Erläuterung besser lesbar zu machen, der Exec\(\)\-Code, der für den Abschluss der Anweisung verwendet wird nicht angezeigt, stattdessen die vorhandene Methode Codeblöcke hinzugefügt werden.\) Fügen Sie den folgenden Codeblock nach dem Code, der ein Zeichen überprüft.  
  
     [!code-cs[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Weist ein Ausschnitt Felder, die navigiert werden kann, wird die Erweiterung\-Sitzung geöffnet bleiben, bis die Erweiterung explizit akzeptiert wird; Wenn der Ausschnitt keine Felder enthält, wird die Sitzung geschlossen wird und als zurückgegeben `null` durch die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> Methode. In der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> \-Methode, nach der Codeausschnittauswahl UI\-Code, den Sie im vorherigen Schritt hinzugefügt fügen Sie folgenden Code Snippet Navigation behandeln \(wenn der Benutzer nach dem Einfügen von Codeausschnitten TAB oder UMSCHALT \+ TAB drückt\).  
  
     [!code-cs[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Fügen Sie Code, um den Codeausschnitt einfügen, wenn der Benutzer die zugehörige Verknüpfung Typen und drückt dann die Registerkarte, die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. Die private Methode, die den Codeausschnitt einfügt werden in einem späteren Schritt angezeigt. Fügen Sie den folgenden Code nach dem Navigationsbereich\-Code, den Sie im vorherigen Schritt hinzugefügt.  
  
     [!code-cs[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Implementieren Sie die Methoden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Schnittstelle. In dieser Implementierung werden nur die Methoden von Interesse <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Die anderen Methoden sollten nur zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-cs[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>\-Methode. Die Hilfsmethode, mit der die Erweiterungen tatsächlich eingefügt werden in einem späteren Schritt behandelt. Die <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> enthält Zeilen\- und Informationen, das Sie aus der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-cs[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. Die folgende private Methode fügt einen Codeausschnitt, basierend auf die Verknüpfung oder auf den Titel und den Pfad. Es ruft dann die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> Methode durch den Codeausschnitt.  
  
     [!code-cs[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## Erstellen und Testen von Code Snippet\-Erweiterung  
 Sie können testen, ob der Ausschnitt Erweiterung in Ihrem Projekt funktioniert.  
  
1.  Erstellen Sie die Projektmappe. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
2.  Öffnen Sie eine Textdatei, und geben Sie einen Text.  
  
3.  Mit der rechten Maustaste an einer beliebigen Stelle im Text, und klicken Sie dann auf **Ausschnitt einfügen**.  
  
4.  Die Codeausschnittauswahl Benutzeroberfläche sollte angezeigt werden, mit einem Popup\-Fenster mit der Meldung **Testen Ersetzungsfelder**. Doppelklicken Sie auf das Popup\-Fenster.  
  
     Der folgende Codeausschnitt eingefügt werden soll.  
  
    ```  
    MessageBox.Show("first"); MessageBox.Show("second");  
    ```  
  
     Drücken Sie EINGABETASTE oder ESC.  
  
5.  Drücken Sie TAB und UMSCHALT \+ TAB Wechseln zwischen "first" und "second".  
  
6.  Akzeptieren Sie die Einfügemarke durch Drücken der EINGABETASTE oder ESC\-Taste.  
  
7.  Geben Sie in einem anderen Teil des Texts "test", und drücken Sie dann die Registerkarte. Da "Test" die Codeausschnitt Verknüpfung ist, sollte der Ausschnitt erneut eingefügt werden.  
  
## Nächste Schritte