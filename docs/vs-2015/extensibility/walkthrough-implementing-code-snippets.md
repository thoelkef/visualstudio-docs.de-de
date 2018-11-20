---
title: 'Exemplarische Vorgehensweise: Implementieren von Codeausschnitten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6fe91fd4e80c14e9b4cf59136fa6d3e0e003f554
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752060"
---
# <a name="walkthrough-implementing-code-snippets"></a>Exemplarische Vorgehensweise: Implementieren von Codeausschnitten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Codeausschnitte erstellen und in einer Editor-Erweiterung einschließen, damit Benutzer von der Erweiterung sie ihren eigenen Code hinzufügen können.  
  
 Ein Codeausschnitt ist ein Fragment von Code oder Text, der in einer Datei eingebunden werden kann. Um alle Codeausschnitte anzuzeigen, die für bestimmte Programmiersprachen erfasst wurden, auf die **Tools** Menü klicken Sie auf **Codeausschnitt-Manager**. Klicken Sie zum Einfügen eines Ausschnitts in einer Datei mit der rechten Maustaste, Sie den Ausschnitt möchten, auf **Ausschnitt einfügen** oder **Umschließen mit**suchen den gewünschten Codeausschnitt, und doppelklicken Sie darauf. Drücken Sie die Registerkarte oder UMSCHALT + TAB, ändern die relevanten Teile des Ausschnitts ein, und drücken dann die EINGABETASTE oder ESC, um es zu akzeptieren. Weitere Informationen finden Sie unter [Codeausschnitte](../ide/code-snippets.md).  
  
 Ein Codeausschnitt ist eine XML-Datei enthalten, die die Snippet-Dateinamenerweiterung aufweist. Ein Ausschnitt kann Felder enthalten, die hervorgehoben werden, nachdem der Ausschnitt eingefügt wird, sodass der Benutzer suchen und ändern kann. Eine Snippet-Datei enthält auch Informationen für die **Codeausschnitt-Manager** , damit sie den Namen des Ausschnitts in der richtigen Kategorie angezeigt werden kann. Weitere Informationen zu den Schemas des Codeausschnitts, finden Sie unter [Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md).  
  
 In dieser exemplarischen Vorgehensweise erfahren, wie diese Aufgaben auszuführen:  
  
1. Erstellen Sie und registrieren Sie Codeausschnitte für eine bestimmte Sprache.  
  
2. Hinzufügen der **Ausschnitt einfügen** Befehl in einem Kontextmenü.  
  
3. Implementieren Sie die ausschnitterweiterung.  
  
   Diese exemplarische Vorgehensweise basiert auf [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Erstellen und Registrieren von Codeausschnitten  
 Codeausschnitte sind in der Regel eine registrierte Sprachdienst zugeordnet. Sie ist jedoch nicht erforderlich, implementieren ein <xref:Microsoft.VisualStudio.Package.LanguageService> Codeausschnitte registrieren. Stattdessen geben Sie einfach eine GUID in der Indexdatei, und verwenden Sie dann auf die gleiche GUID in der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , die Sie Ihrem Projekt hinzufügen.  
  
 Die folgenden Schritte veranschaulichen das Erstellen von Codeausschnitten aus, und ordnen sie einen bestimmten GUID.  
  
1. Erstellen Sie die folgende Verzeichnisstruktur:  
  
    **%INSTALLDIR%\TestSnippets\Snippets\1033\\**  
  
    wo *% INSTALLDIR%* ist der Visual Studio-Installationsordner. (Obwohl dieser Pfad in der Regel verwendet wird, um Codeausschnitte zu installieren, können Sie einen Pfad angeben.)  
  
2. Klicken Sie im Ordner "\1033\", erstellen Sie eine XML-Datei, und nennen Sie sie **TestSnippets.xml**. (Auch diesen Namen in der Regel für die Datei einen Index verwendet wird, können Sie einen beliebigen Namen angeben, solange sie eine Dateinamenerweiterung hat.) Fügen Sie den folgenden Text ein, und klicken Sie dann löschen Sie die Platzhalter-GUID und fügen Sie eine eigene hinzu.  
  
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
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>So registrieren Sie Codeausschnitte für einen bestimmten GUID  
  
1.  Öffnen der **CompletionTest** Projekt. Weitere Informationen zum Erstellen des Projekts, finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  Fügen Sie im Projekt Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  Öffnen Sie im Projekt die Datei "Source.Extension.vsixmanifest" ein.  
  
4.  Stellen Sie sicher, dass die **Assets** Registerkarte enthält eine **VsPackage** content-Type und, **Projekt** auf den Namen des Projekts festgelegt ist.  
  
5.  Wählen Sie das CompletionTest-Projekt, und legen Sie im Eigenschaftenfenster **Pkgdef-Datei generieren** zu **"true"**. Speichern Sie das Projekt.  
  
6.  Fügen Sie einen statischen `SnippetUtilities` Klasse, um das Projekt.  
  
     [!code-csharp[VSSDKCompletionTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#22)]
     [!code-vb[VSSDKCompletionTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#22)]  
  
7.  Klicken Sie in der Klasse SnippetUtilities definieren Sie eine GUID, und geben sie den Wert, den Sie in der Datei SnippetsIndex.xml verwendet.  
  
     [!code-csharp[VSSDKCompletionTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#23)]
     [!code-vb[VSSDKCompletionTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#23)]  
  
8.  Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> auf die `TestCompletionHandler` Klasse. Dieses Attribut kann einer beliebigen öffentlichen oder internen-Klasse im Projekt (nicht statisch) hinzugefügt werden. (Sie müssen möglicherweise Hinzufügen einer `using` -Anweisung für den Namespace Microsoft.VisualStudio.Shell.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#24)]
     [!code-vb[VSSDKCompletionTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#24)]  
  
9. Erstellen Sie das Projekt, und führen Sie es aus. In der experimentellen Instanz von Visual Studio, die gestartet wird, wenn das Projekt ausgeführt wird, der Ausschnitt, die Sie gerade registriert angezeigt werden soll, der **Codeausschnitt-Manager** unter der **TestSnippets** Sprache.  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Das Kontextmenü hinzugefügt den Insert-Befehl Codeausschnitt  
 Die **Ausschnitt einfügen** Befehl befindet sich nicht auf das Kontextmenü für eine Textdatei. Aus diesem Grund müssen Sie den Befehl aktivieren.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Um den Ausschnitt einfügen-Befehl im Kontextmenü den Befehl hinzufügen  
  
1.  Öffnen der `TestCompletionCommandHandler` Klassendatei.  
  
     Da diese Klasse implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, können Sie aktivieren die **Ausschnitt einfügen** -Befehl in der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode. Überprüfen Sie, dass diese Methode nicht in eine Automatisierungsfunktion da aufgerufen wird, bevor Sie den Befehl aktivieren, wenn die **Ausschnitt einfügen** Befehl geklickt wird, wird der Ausschnitt Picker-Benutzeroberfläche (UI) angezeigt.  
  
     [!code-csharp[VSSDKCompletionTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#25)]
     [!code-vb[VSSDKCompletionTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#25)]  
  
2.  Erstellen Sie das Projekt, und führen Sie es aus. Öffnen Sie eine Datei mit der Erweiterung .zzz, und klicken Sie dann mit der rechten Maustaste an einer beliebigen Stelle in ihr, in der experimentellen Instanz. Die **Ausschnitt einfügen** Befehl sollte auf das Kontextmenü angezeigt werden.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Implementieren in der Codeausschnittauswahl UI Ausschnitterweiterung  
 In diesem Abschnitt wird gezeigt, wie codeausschnitterweiterung implementieren, damit die Codeausschnittauswahl UI wird angezeigt, wenn **Ausschnitt einfügen** im Kontextmenü den Befehl geklickt wird. Ein Codeausschnitt ist ebenfalls erweitert, wenn ein Benutzer die Verknüpfung eines Codeausschnitts Typen und drückt dann die Registerkarte.  
  
 Verwenden Sie zum Anzeigen der Ausschnittauswahl Benutzeroberfläche und Navigation und nach der einfügungsausschnitt Akzeptanz zu ermöglichen, die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. Das Einfügen an sich selbst erfolgt durch die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> Methode.  
  
 Die Implementierung der codeausschnitterweiterung verwendet Legacy <xref:Microsoft.VisualStudio.TextManager.Interop> Schnittstellen. Wenn Sie von den aktuellen Editor-Klassen für die legacy-Code übersetzen, denken Sie daran, dass die legacy-Schnittstellen eine Kombination von Zeilennummern und Spaltennummern zur Angabe der Speicherorte in einem Textpuffer verwenden, aber die aktuellen Klassen, einen Index verwenden. Aus diesem Grund hat ein Puffer, drei Zeilen, die jeweils 10 Zeichen umfasst (plus eine neue Zeile, die zählt als 1 Zeichen), das vierte Zeichen in der dritten Zeile wird an der Position 27, in der aktuellen Implementierung, aber es ist in Zeile 2, positionieren Sie 3 in der alten-Implementierung.  
  
#### <a name="to-implement-snippet-expansion"></a>Um ausschnitterweiterung zu implementieren.  
  
1.  Um die Datei mit den `TestCompletionCommandHandler` Klasse, fügen Sie die folgenden `using` Anweisungen.  
  
     [!code-csharp[VSSDKCompletionTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#26)]
     [!code-vb[VSSDKCompletionTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#26)]  
  
2.  Stellen Sie die `TestCompletionCommandHandler` implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Schnittstelle.  
  
     [!code-csharp[VSSDKCompletionTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#27)]
     [!code-vb[VSSDKCompletionTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#27)]  
  
3.  In der `TestCompletionCommandHandlerProvider` Klasse, importieren Sie die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-csharp[VSSDKCompletionTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#28)]
     [!code-vb[VSSDKCompletionTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#28)]  
  
4.  Fügen Sie private Felder für die Schnittstellen der Code-Erweiterung hinzu, und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#29)]
     [!code-vb[VSSDKCompletionTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#29)]  
  
5.  Im Konstruktor der `TestCompletionCommandHandler` Klasse, legen Sie die folgenden Felder.  
  
     [!code-csharp[VSSDKCompletionTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#30)]
     [!code-vb[VSSDKCompletionTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#30)]  
  
6.  Die Codeausschnittauswahl angezeigt, wenn der Benutzer klickt der **Ausschnitt einfügen** Befehl, fügen Sie den folgenden Code der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. (Um diese Erklärung besser lesbar zu machen, der der Exec()-Code, der verwendet wird, für die Anweisungsvervollständigung wird nicht angezeigt, stattdessen die vorhandene Methode Codeblöcke hinzugefügt werden.) Fügen Sie den folgenden Codeblock nach dem Code, der prüft, ob ein Zeichen ein.  
  
     [!code-csharp[VSSDKCompletionTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#31)]
     [!code-vb[VSSDKCompletionTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#31)]  
  
7.  Wenn ein Codeausschnitt Felder, zu dem navigiert werden kann verfügt, wird die erweiterungssitzung öffnen beibehalten, bis explizit die Erweiterung zulässig ist; Wenn der Codeausschnitt keine Felder enthält, wird die Sitzung wird geschlossen, und wird zurückgegeben, als `null` durch die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> Methode. In der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> -Methode, nach der Ausschnittauswahl UI-Code, die Sie im vorherigen Schritt hinzugefügt haben fügen Sie folgenden Code Ausschnitt Navigation verarbeiten (wenn der Benutzer nach dem Einfügen von Codeausschnitten TAB oder UMSCHALT + TAB drückt).  
  
     [!code-csharp[VSSDKCompletionTest#32](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#32)]
     [!code-vb[VSSDKCompletionTest#32](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#32)]  
  
8.  Fügen Sie Code zum Einfügen des Codeausschnitts, wenn der Benutzer die entsprechende Verknüpfung Typen und drückt dann die Registerkarte, die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode. Die private Methode, mit der den Codeausschnitt eingefügt werden in einem späteren Schritt angezeigt. Fügen Sie den folgenden Code nach der Navigationscode, den Sie im vorherigen Schritt hinzugefügt haben.  
  
     [!code-csharp[VSSDKCompletionTest#33](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#33)]
     [!code-vb[VSSDKCompletionTest#33](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#33)]  
  
9. Implementieren Sie die Methoden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> Schnittstelle. In dieser Implementierung wird nur die Methoden von Interesse sind <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Die anderen Methoden sollten nur zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-csharp[VSSDKCompletionTest#34](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#34)]
     [!code-vb[VSSDKCompletionTest#34](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#34)]  
  
10. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>-Methode. Die Hilfsmethode, die tatsächlich die Erweiterungen eingefügt wird in einem späteren Schritt erläutert. Die <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> enthält Zeilen- und Informationen, die Sie erhalten können die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#35)]
     [!code-vb[VSSDKCompletionTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#35)]  
  
11. Die folgende private Methode fügt einen Codeausschnitt, basierend entweder auf die Verknüpfung oder auf den Titel und den Pfad ein. Es ruft dann die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> Methode durch den Codeausschnitt.  
  
     [!code-csharp[VSSDKCompletionTest#36](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#36)]
     [!code-vb[VSSDKCompletionTest#36](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#36)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Erstellen und Testen von Codeausschnitterweiterung  
 Sie können testen, ob der Ausschnitt in Ihrem Projekt funktioniert.  
  
1.  Erstellen Sie die Projektmappe. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
2.  Öffnen Sie eine Textdatei, und geben Sie Text.  
  
3.  Mit der rechten Maustaste an einer beliebigen Stelle im Text, und klicken Sie dann auf **Ausschnitt einfügen**.  
  
4.  Die Benutzeroberfläche sollte angezeigt werden, mit einem Popup, die besagt, Codeausschnittauswahl **testen Ersetzungsfelder**. Doppelklicken Sie auf das Popup-Fenster.  
  
     Der folgende Codeausschnitt eingefügt werden soll.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     Drücken Sie nicht die EINGABETASTE oder ESC-Taste.  
  
5.  Drücken Sie TAB und UMSCHALT + TAB zum Umschalten zwischen "first" und "Sekunde".  
  
6.  Akzeptieren Sie durch Drücken von EINGABETASTE oder ESC entweder das Einfügen.  
  
7.  Klicken Sie in einem anderen Teil des Texts Geben Sie "test", und drücken Sie dann die Registerkarte. Da "Test" die Verknüpfung eines Codeausschnitts ist, sollte erneut der Ausschnitt eingefügt werden.  
  
## <a name="next-steps"></a>Nächste Schritte

