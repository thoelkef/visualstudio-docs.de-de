---
title: "Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ebdc87e1dccf2bde66ccfeebb6c2b4fba144c70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-statement-completion"></a>Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung
Sie können die Sprache basierende Anweisungsvervollständigung implementieren, durch Definieren der Bezeichner für die Sie die Beendigung bereitstellen möchten, und klicken Sie dann auszulösen einer Sitzungs abgeschlossen. Anweisungsvervollständigung im Rahmen einer Sprachdienst definieren, Definieren eigener Dateinamenerweiterung und des Inhaltstyps und zeigt dann Abschluss für nur dieses Typs, oder der Abschluss für einen vorhandenen Inhaltstyp auslösen – z. B. "Text". In dieser exemplarischen Vorgehensweise wird das Auslösen von Anweisungsvervollständigung für den Inhaltstyp "Text", also den Inhaltstyp der Textdateien veranschaulicht. Der Inhaltstyp "Text" ist der Vorgänger von allen anderen Inhaltstypen, einschließlich Code und XML-Dateien.  
  
 Anweisungsvervollständigung wird in der Regel ausgelöst, indem Sie bestimmte Zeichen eingeben, z. B. durch den Anfang eines Bezeichners, z. B. "using" eingeben. Es ist in der Regel verworfen, durch Drücken der Taste LEERTASTE, Tab oder die EINGABETASTE, um eine Auswahl zu übernehmen. Sie können die IntelliSense-Funktionen, die ausgelöst werden, durch ein Zeichen mithilfe der Befehlshandler für die Tastatureingaben eingeben implementieren (die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle) und ein Handler-Anbieter, implementiert die <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Schnittstelle. Implementieren, um die Quelle Abschluss erstellen, die die Liste der Bezeichner, die im Abschluss beteiligt sind ist, die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Schnittstelle und ein Abschluss Quellenanbieter (die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> Schnittstelle). Der Datenanbieter sind Komponenten des Managed Extensibility Framework (MEF). Sie sind verantwortlich für die Quell- und Controller-Klassen exportieren und Importieren von Services und Makler – z. B. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, dem ermöglicht die Navigation in den Textpuffer und die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, die Trigger der Sitzungs abgeschlossen.  
  
 Diese exemplarische Vorgehensweise zeigt, wie Anweisungsvervollständigung für ein fest programmiertes Satz von Bezeichnern zu implementieren. In vollständige Implementierungen sind Sprachdiensts und in der sprachdokumentation für die Bereitstellung dieses Inhalts verantwortlich.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekts**.) Nennen Sie die Projektmappe `CompletionTest`.  
  
2.  Dem Projekt eine Elementvorlage Editor Klassifizierer hinzugefügt. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
4.  Fügen Sie dem Projekt die folgenden Verweise hinzu, und stellen Sie sicher, dass **CopyLocal** festgelegt ist, um `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Implementieren der Abschluss-Quelle  
 Die Quelle für die Beendigung ist verantwortlich für das Sammeln der Satz von Bezeichnern und den Inhalt der Fenster zur tagvervollständigung hinzufügen, wenn ein Benutzer, einen Trigger ist abgeschlossen, z. B. die ersten Buchstaben eines Bezeichners eingibt. In diesem Beispiel wird die Bezeichner und deren Beschreibungen sind hartcodiert in die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Methode. Bei den meisten Verwendungen temporärer Tabellen realen würden Sie Ihre Sprache-Parser verwenden, um die Token zum Auffüllen der Vervollständigungsliste abzurufen.  
  
#### <a name="to-implement-the-completion-source"></a>Um die Quelle der Abschluss zu implementieren  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestCompletionSource`.  
  
2.  Fügen Sie diese Importe hinzu:  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Ändern Sie die Klassendeklaration für `TestCompletionSource` , damit er implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Fügen Sie private Felder für Quellenanbieter, die den Textpuffer und eine Liste der <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> Objekte (die alle Bezeichner, die in der Sitzung Abschluss einbezogen werden entsprechen):  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Fügen Sie einen Konstruktor, der der Quellenanbieter und Puffer festlegt. Die `TestCompletionSourceProvider` -Klasse ist in späteren Schritten definiert:  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Methode, indem eine Abschluss-Gruppe, die Abschlüsse enthält, hinzufügen, die Sie in den Kontext bereitstellen möchten. Jeder Satz Abschluss enthält eine Reihe von <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> Beendigungen, und entspricht einer Registerkarte des Fensters Abschluss. (In Visual Basic-Projekten, die Registerkarten Abschluss heißen **allgemeine** und **alle**.) Die FindTokenSpanAtPosition-Methode, die im nächsten Schritt definiert ist.  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  Die folgende Methode wird verwendet, um das aktuelle Wort von der Position des Cursors zu finden:  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implementieren der `Dispose()` Methode:  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementieren den Quellenanbieter Abschluss  
 Der Abschluss Quellenanbieter ist MEF-Komponente, die die Quelle der Abschluss instanziiert.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Zum Implementieren des Quellenanbieter Abschluss  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestCompletionSourceProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exportieren von dieser Klasse mit einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "nur-Text" und eine <xref:Microsoft.VisualStudio.Utilities.NameAttribute> Vollendungsgrad"Test".  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Importieren einer <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, dem wird verwendet, um das aktuelle Wort in der Quelle Abschluss zu suchen.  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> Methode, um die Quelle Abschluss zu instanziieren.  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementieren des Anbieters des Abschluss Befehl Handler  
 Der Abschluss Handler Befehlsanbieter abgeleitet wird eine <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, die Erstellung ein Text-sichtereignis überwacht und konvertiert die Ansicht aus ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>– die ermöglicht, dass das Hinzufügen der den Befehl aus, um die Befehlskette der Visual Studio-Shell – zu einer <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Da diese Klasse eine MEF-Export ist, können Sie es auch verwenden, die Dienste zu importieren, die der Befehlshandler selbst erforderlich sind.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Der Abschluss Befehl Handler-Anbieter implementiert  
  
1.  Fügen Sie eine Datei mit dem Namen `TestCompletionCommandHandler`.  
  
2.  Fügen Sie diese using-Anweisungen hinzu:  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Fügen Sie eine Klasse mit dem Namen `TestCompletionHandlerProvider` implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exportieren dieser Klasse mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> von "token Abschlusshandler", ein <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "nur-Text", und ein <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> von <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Importieren der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, dem ermöglicht die Konvertierung von einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> auf eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, eine <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, und ein <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , ermöglicht den Zugriff auf Visual Studio-Standarddienste.  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> -Methode Befehlshandler zu instanziieren.  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementieren den Abschlusshandler-Befehl  
 Da Anweisungsvervollständigung von Tastatureingaben ausgelöst wird, müssen Sie implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle zum Empfangen und Verarbeiten von Tastenkombinationen, die auslösen, commit und schließen die Sitzung abgeschlossen.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Um den Abschlusshandler-Befehl zu implementieren.  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestCompletionCommandHandler` implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Fügen Sie private Felder für nächsten Befehlshandler (zu dem Sie den Befehl übergeben), der Textansicht, die Handler-Befehlsanbieter (dadurch Zugriff auf verschiedene Dienste), und eine Sitzung abgeschlossen:  
  
     [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Fügen Sie einen Konstruktor, der festlegt, Textansicht und die Anbieterfelder und die Befehlskette fügt den Befehl hinzu:  
  
     [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> -Methode durch den Befehl entlang übergeben:  
  
     [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Implementieren Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>-Methode. Wenn diese Methode eine Tastatureingabe empfängt, müssen sie eine der folgenden Schritte:  
  
    -   Ermöglichen Sie das Zeichen in den Puffer geschrieben werden, und klicken Sie dann trigger, oder Filtern Abschluss. (Drucken Zeichen erledigen dies).  
  
    -   Commit der Abschluss allerdings lassen sich nicht auf das Zeichen in den Puffer geschrieben werden sollen. (Leerzeichen, Tab und EINGABETASTE dies geschieht, wenn eine Sitzung Abschluss angezeigt wird.)  
  
    -   Ermöglichen Sie den Befehl an den nächsten Handler übergeben werden. (Alle anderen Befehle.)  
  
     Da diese Methode Benutzeroberfläche anzeigen kann, rufen <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> um sicherzustellen, dass sie nicht in einem Automation-Kontext aufgerufen wird:  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Mit diesem Code wird eine private Methode, die die Abschluss Sitzung auslöst:  
  
     [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  Im nächste Beispiel wird eine private Methode, die von hebt das Abonnement der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> Ereignis:  
  
     [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die CompletionTest-Projektmappe, und führen Sie sie in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>So erstellen und Testen der Lösung CompletionTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei, und geben Sie Text an, der das Wort "hinzufügen".  
  
4.  Wenn Sie zuerst "a", und klicken Sie dann "d" eingeben, sollte eine Liste mit "hinzufügen" und "Anpassung" angezeigt werden. Beachten Sie, dass Addition ausgewählt ist. Wenn Sie eine andere "d" eingeben, sollte die Liste enthalten, nur "hinzufügen", die jetzt ausgewählt ist. Sie können einen commit "hinzufügen" die LEERTASTE, Tab oder die EINGABETASTE drücken oder schließen die Liste durch Eingabe der ESC-Taste, oder eine andere Taste.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)