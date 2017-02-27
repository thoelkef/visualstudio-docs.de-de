---
title: "Exemplarische Vorgehensweise: Anzeigen von Anweisungsabschluss | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] neue - Anweisungsabschluss"
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# Exemplarische Vorgehensweise: Anzeigen von Anweisungsabschluss
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können\-basierter Anweisungsabschluss implementieren, indem Sie definieren die Bezeichner für die Sie die Beendigung bereitstellen möchten, und klicken Sie dann Auslösen einer Sitzungs abgeschlossen. Sie definieren Anweisungsabschluss im Kontext eines Sprachdiensts, Erweiterung und Inhaltstyp definieren und Abschluss für nur diesen Typ anzeigen können, oder Abschluss für einen vorhandenen Inhaltstyp auslösen, z. B. "Text". In dieser exemplarischen Vorgehensweise veranschaulicht, wie zum Auslösen von Anweisungsvervollständigung für den Inhaltstyp "nur\-Text", wird der Inhaltstyp von Textdateien. Der Inhaltstyp "Text" ist der Vorgänger aller anderen Inhaltstypen, einschließlich Code und XML\-Dateien.  
  
 Anweisungsabschluss wird in der Regel ausgelöst, durch bestimmte Zeichen eingeben, z. B. durch den Anfang eines Bezeichners, z. B. "using" eingeben. Es ist normalerweise geschlossen, Drücken der LEERTASTE, Tab oder die EINGABETASTE, um eine Auswahl zu übernehmen. Sie können die IntelliSense\-Funktionen, die ausgelöst werden, geben Sie ein Zeichen mit einen Befehlshandler für die Tastatureingaben implementieren \(die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle\) und ein Handler\-Anbieter, implementiert die <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Schnittstelle. Zum Erstellen der Abschluss\-Datenquelle, die die Liste der Bezeichner, die beim Abschluss von beteiligt sind ist, implementieren die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Schnittstelle und ein Abschluss Quellenanbieter \(die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> Schnittstelle\). Managed Extensibility Framework \(MEF\)\-Komponenten sind. Sie sind verantwortlich für die Quell\- und Controller\-Klassen exportieren und Importieren von Services und Brokern – z. B. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, die ermöglicht die Navigation in den Textpuffer und <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, dadurch wird die Abschluss Sitzung ausgelöst.  
  
 In dieser exemplarischen Vorgehensweise veranschaulicht, wie Anweisungsvervollständigung für einen hartcodierten Satz von Bezeichnern zu implementieren. Vollständige Implementierungen sind Sprachdiensts und die Dokumentation zur dafür verantwortlich, dass der Inhalt.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines MEF\-Projekts  
  
#### So erstellen Sie ein MEF\-Projekt  
  
1.  Erstellen Sie ein C\#\-VSIX\-Projekt. \(In der **Neues Projekt** Dialogfeld **Visual c\# \/ Erweiterbarkeit**, dann **VSIX\-Projekt**.\) Nennen Sie die Projektmappe `CompletionTest`.  
  
2.  Fügen Sie dem Projekt eine Classifier\-Editor\-Elementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einer Elementvorlage\-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
4.  Fügen Sie dem Projekt die folgenden Verweise hinzu, und stellen Sie sicher, dass **CopyLocal** Wert `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## Implementieren der Abschluss\-Quelle  
 Die Abschluss\-Quelle ist verantwortlich für das Sammeln der Satz von Bezeichnern und den Inhalt zum Abschluss\-Fenster hinzufügen, wenn ein Benutzer einen Abschluss\-Triggers, z. B. die ersten Buchstaben eines Bezeichners eingibt. In diesem Beispiel die Bezeichner und Beschreibungen sind hartcodiert in die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Methode. In den meisten realen verwendet verwenden Sie Ihre Sprache Parser zum Abrufen der Tokens, um die Vervollständigungsliste aufzufüllen.  
  
#### Implementieren die Abschluss\-Quelle  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie es `TestCompletionSource`.  
  
2.  Fügen Sie diese Importe hinzu:  
  
     [!code-cs[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Ändern Sie die Klassendeklaration für `TestCompletionSource` damit er implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-cs[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Fügen Sie private Felder für den Quellenanbieter Textpuffer und eine Liste der <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> Objekte \(die entsprechen die Bezeichner, die in der Sitzung Abschluss einbezogen werden\):  
  
     [!code-cs[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Fügen Sie einen Konstruktor, der dem Anbieter und dem Puffer festlegt. Die `TestCompletionSourceProvider` \-Klasse in späteren Schritten definiert:  
  
     [!code-cs[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Methode, indem eine Abschluss\-Gruppe, die Abschlüsse enthält, hinzufügen, die Sie im Kontext bereitstellen möchten. Jeder Satz Abschluss enthält eine Reihe von <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> Abschlüsse, und entspricht einer Registerkarte des Fensters Abschluss. \(In Visual Basic\-Projekten die Fertigstellung Registerkarten heißen **Allgemeine** und **alle**.\) Im nächsten Schritt wird die FindTokenSpanAtPosition\-Methode definiert.  
  
     [!code-cs[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  Die folgende Methode wird verwendet, um das aktuelle Wort von der Position des Cursors zu suchen:  
  
     [!code-cs[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implementieren der `Dispose()` Methode:  
  
     [!code-cs[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## Implementieren den Abschluss Quellenanbieter  
 Der Abschluss Quellenanbieter ist MEF\-Komponente, die die Quelle der Abschluss instanziiert.  
  
#### Den Abschluss Quellenanbieter implementiert  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestCompletionSourceProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exportieren Sie diese Klasse mit einer <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "nur\-Text" und einem <xref:Microsoft.VisualStudio.Utilities.NameAttribute> Vollendungsgrad"Test".  
  
     [!code-cs[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Importieren einer <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, die wird verwendet, um das aktuelle Wort im Quell\-Abschluss zu suchen.  
  
     [!code-cs[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> \-Methode instanziieren, die Quelle der Abschluss des Vorgangs.  
  
     [!code-cs[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## Implementieren den Abschluss Command\-Handler\-Provider  
 Der Abschluss Command\-Handler Provider abgeleitet ist eine <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, die für ein Textfeld Ansicht Erstellung\-Ereignis überwacht und konvertiert die Ansicht aus ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>– die ermöglicht des Hinzufügen des Befehls den Befehl Kette von der Visual Studio\-Shell – auf ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Da diese Klasse einen MEF\-Export ist, auch können diese Sie um die Dienste zu importieren, die den Befehlshandler selbst erforderlich sind.  
  
#### Den Abschluss Befehl Handler\-Anbieter implementiert  
  
1.  Fügen Sie eine Datei namens `TestCompletionCommandHandler`.  
  
2.  Fügen Sie diese using\-Anweisungen hinzu:  
  
     [!code-cs[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Fügen Sie eine Klasse mit dem Namen `TestCompletionHandlerProvider` implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exportieren dieser Klasse mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> von "token Abschlusshandler", eine <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "nur\-Text", und ein <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> von <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-cs[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Importieren der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, die ermöglicht die Konvertierung von ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, ein <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, und ein <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> ermöglicht den Zugriff auf Visual Studio\-Standarddienste.  
  
     [!code-cs[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> \-Methode Befehlshandler instanziieren.  
  
     [!code-cs[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## Implementieren den Befehl Abschlusshandler  
 Da Anweisungsabschluss Tastatureingaben ausgelöst wird, müssen Sie implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle zum Empfangen und Verarbeiten von Tastenkombinationen, die auslösen, commit und schließen die Sitzung abgeschlossen.  
  
#### Implementieren Sie den Befehl Abschlusshandler  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestCompletionCommandHandler` implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-cs[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Fügen Sie private Felder für den nächsten Befehlshandler \(zu dem Sie den Befehl übergeben\), der Textansicht, den Command\-Handler\-Provider \(wodurch Zugriff auf verschiedene Dienste\), und eine Sitzung Abschluss:  
  
     [!code-cs[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Fügen Sie einen Konstruktor, der festlegt, die Textansicht und die Anbieterfelder und fügt der Befehl an die Befehlskette ein:  
  
     [!code-cs[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \-Methode übergeben den Befehl auf:  
  
     [!code-cs[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Implementieren Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>\-Methode. Wenn diese Methode eine Tastatureingabe empfängt, muss er Folgendes tun:  
  
    -   Ermöglichen Sie das Zeichen in den Puffer geschrieben werden, und klicken Sie dann trigger oder Abschluss zu filtern. \(Drucken Zeichen dafür.\)  
  
    -   Commit abgeschlossen, aber lassen sich nicht auf das Zeichen, das in den Puffer geschrieben werden. \(Leerzeichen, Tab und EINGABETASTE dies eine Sitzung abgeschlossen angezeigt wird.\)  
  
    -   Ermöglicht es dem Befehl an den nächsten Ereignishandler übergeben werden. \(Alle anderen Befehle.\)  
  
     Da diese Methode die Benutzeroberfläche anzeigen kann, rufen Sie <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> um sicherzustellen, dass sie nicht in einem Benutzeroberflächenautomatisierungs\-Kontext aufgerufen wird:  
  
     [!code-cs[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Dieser Code ist eine private Methode, die die Sitzung Abschluss auslöst:  
  
     [!code-cs[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  Im nächste Beispiel wird eine private Methode, die von hebt die <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> Ereignis:  
  
     [!code-cs[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe CompletionTest, und führen Sie es in der experimentellen Instanz.  
  
#### So erstellen und Testen der Lösung CompletionTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei, und geben Sie einen Text mit dem Wort "hinzufügen".  
  
4.  Wenn Sie zuerst "a" und dann "d" eingeben, sollte eine Liste mit "hinzufügen" und "Anpassung" angezeigt werden. Beachten Sie, dass zusätzlich ausgewählt ist. Bei der Eingabe von einem anderen "d" sollte die Liste enthalten, nur "hinzufügen", das jetzt aktiviert ist. Sie können einen commit "hinzufügen" die LEERTASTE, Tab oder die EINGABETASTE drücken, oder schließen die Liste durch Drücken der ESC\-Taste oder eine beliebige Taste.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit Erweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)