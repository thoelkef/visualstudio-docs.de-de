---
title: 'Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdd96c124dafabf5584dfa13547cdea1e2b843b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879323"
---
# <a name="walkthrough-display-statement-completion"></a>Exemplarische Vorgehensweise: Anzeigen Anweisungsvervollständigung
Sie können-Sprache basierenden Anweisungsvervollständigung durch definieren die Bezeichner für die Sie die Vervollständigung bereitstellen möchten, und klicken Sie dann auszulösen eine vervollständigungssitzung implementieren. Sie können Anweisungsvervollständigung im Kontext von einem Sprachdienst zu definieren, Definieren eigener Dateinamenerweiterung und Content-Type und -Vervollständigung für nur diesen Typ dann anzeigen. Oder Sie können die Vervollständigung für einem vorhandenen Inhaltstyp auslösen, z. B. "nur-Text". In dieser exemplarischen Vorgehensweise zeigt, wie Anweisungsvervollständigung für den Inhaltstyp "nur-Text", den Inhaltstyp der Textdateien handelt, ausgelöst wird. Der Inhaltstyp "Text" ist der Vorgänger aller anderen Inhaltstypen, einschließlich Code und XML-Dateien.  
  
 Anweisungsvervollständigung in der Regel durch die Eingabe bestimmter Zeichen ausgelöst wird – z. B. durch den Anfang eines Bezeichners, z. B. "using" eingeben. Es ist in der Regel durch Drücken von geschlossen der **LEERTASTE**, **Registerkarte**, oder **EINGABETASTE** Schlüssel, um eine Auswahl zu übernehmen. Können Sie die IntelliSense-Funktionen, die ausgelöst wird, wenn ein Zeichen eingeben, mit einem Befehlshandler für die Tastatureingaben implementieren (die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle) und ein Handler für Anbieter, implementiert die <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Schnittstelle. Zum Erstellen der abschlussquelle, die die Liste der Bezeichner, die in der Anweisungsvervollständigung beteiligt sind ist, implementieren die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Schnittstelle und einen Vervollständigungsanbieter für die Quelle (die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> Schnittstelle). Die Anbieter sind Komponenten des Managed Extensibility Framework (MEF). Sie sind verantwortlich für die Quell- und Controller-Klassen und-importieren Dienste und Brokern – z. B. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, dem ermöglicht die Navigation im Textpuffer, und die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, die löst der vervollständigungssitzung.  
  
 Diese exemplarische Vorgehensweise veranschaulicht das Implementieren der Anweisungsvervollständigung für einen hartcodierten Satz von Bezeichnern. In vollständige Implementierungen sind der Sprachdienst und in der sprachdokumentation für die Bereitstellung, dass der Inhalt verantwortlich.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015 können installieren nicht Sie das Visual Studio SDK aus dem Downloadcenter. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `CompletionTest`.  
  
2.  Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
4.  Fügen Sie die folgenden Verweise dem Projekt hinzu, und stellen Sie sicher, dass **CopyLocal** nastaven NA hodnotu `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implement-the-completion-source"></a>Implementieren der abschlussquelle  
 Der abschlussquelle ist verantwortlich für das Sammeln der Satz von Bezeichnern, und das Fenster "Abschluss" den Inhalt hinzugefügt wird, wenn ein Benutzer, einen Trigger für buildabschluss, z. B. die ersten Buchstaben eines Bezeichners eingibt. In diesem Beispiel die IDs und Beschreibungen werden in hartcodiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Methode. In den meisten realen Fällen verwenden Sie die Sprache der Parser zum Abrufen von Token zum Auffüllen der Liste.  
  
### <a name="to-implement-the-completion-source"></a>Zum Implementieren der abschlussquelle  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestCompletionSource`.  
  
2.  Fügen Sie diese Importe hinzu:  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Ändern Sie die Klassendeklaration für `TestCompletionSource` , damit er implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Fügen Sie private Felder für den Quellenanbieter, das den Textpuffer und eine Liste der <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> Objekte (die entsprechen die Bezeichner, die in der Sitzung zur codevervollständigung einbezogen werden):  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Fügen Sie einen Konstruktor, der dem Quellanbieter und Puffer festlegt. Die `TestCompletionSourceProvider` Klasse wird in späteren Schritten definiert:  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Methode durch das Hinzufügen eines Vervollständigungssatzes, die die vervollständigungen enthält, die Sie in den Kontext angeben möchten. Jede Vervollständigungssatz enthält einen Satz von <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> vervollständigungen, und entspricht einer Registerkarte des Fensters Abschluss. (In Visual Basic-Projekten die Vervollständigung Registerkarten heißen **allgemeine** und **alle**.) Die `FindTokenSpanAtPosition`-Methode wird im nächsten Schritt definiert.  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  Die folgende Methode wird verwendet, um das aktuelle Wort von der Position des Cursors zu finden:  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implementieren der `Dispose()` Methode:  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implement-the-completion-source-provider"></a>Implementieren der Quellenanbieter Abschluss  
 Der Abschluss-Source-Anbieter ist der MEF-Komponente, die der abschlussquelle instanziiert.  
  
### <a name="to-implement-the-completion-source-provider"></a>Zum Implementieren des Quellenanbieter Abschluss  
  
1.  Fügen Sie eine Klasse, die mit dem Namen `TestCompletionSourceProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exportieren Sie diese Klasse mit einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Klartext" und ein <xref:Microsoft.VisualStudio.Utilities.NameAttribute> Vollendungsgrad"Test".  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Importieren einer <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, die das aktuelle Wort findet, in der abschlussquelle.  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> Methode zum Instanziieren der abschlussquelle.  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implement-the-completion-command-handler-provider"></a>Implementieren Sie den Abschluss Command-Handler-provider  
 Handler die Vervollständigungsanbieter-Befehl ergibt sich aus einer <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, die Lauscht auf ein Erstellungsereignis für Text anzeigen, und konvertiert die Ansicht aus eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>– dadurch, dass das Hinzufügen des Befehls, der die Befehlskette der Visual Studio-Shell – zu einer <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Da diese Klasse einen MEF-Export ist, können Sie es auch verwenden, so importieren Sie die Dienste, die den Befehlshandler selbst erforderlich sind.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Den Abschluss Befehl Handler-Anbieter implementiert  
  
1.  Fügen Sie die Datei `TestCompletionCommandHandler`.  
  
2.  Fügen Sie die folgenden using-Anweisungen hinzu:  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Fügen Sie eine Klasse, die mit dem Namen `TestCompletionHandlerProvider` implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exportieren dieser Klasse mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> von "token Abschlusshandler", eine <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "nur-Text", und ein <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> von <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Importieren der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, dem ermöglicht die Konvertierung von einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zu eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, eine <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, und ein <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> ermöglicht, die den Zugriff auf standardmäßige Visual Studio-Diensten.  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> -Methode instanziieren, die den Befehlshandler.  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implement-the-completion-command-handler"></a>Implementieren Sie den Befehl Abschlusshandler  
 Da der Anweisungsvervollständigung von Tastatureingaben ausgelöst wird, müssen Sie implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle zum Empfangen und Verarbeiten von Tastenkombinationen, die auslösen, zu committen und Schließen der Sitzung zur codevervollständigung.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Um den Abschlusshandler-Befehl zu implementieren.  
  
1. Fügen Sie eine Klasse, die mit dem Namen `TestCompletionCommandHandler` implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2. Fügen Sie private Felder für den nächsten Befehlshandler (zu dem Sie den Befehl übergeben), die Textansicht, die Handler-Befehlsanbieter (wodurch der Zugriff auf verschiedene Dienste), und eine vervollständigungssitzung:  
  
    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3. Fügen Sie einen Konstruktor, der festlegt, der Textansicht und die Anbieterfelder und die Befehlskette fügt den Befehl hinzu:  
  
    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4. Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> -Methode und übergeben den Befehl an:  
  
    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5. Implementieren Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>-Methode. Wenn diese Methode eine Tastatureingabe empfängt, müssen sie eine der folgenden Optionen:  
  
   - Ermöglichen Sie das Zeichen, das den Puffer geschrieben werden und lösen Sie dann oder Abschluss zu filtern. (Druckbaren Zeichen hierzu.)  
  
   - Committen Sie die Vervollständigung zu, aber lassen Sie nicht das Zeichen, das in den Puffer geschrieben werden. (Leerzeichen, **Registerkarte**, und **EINGABETASTE** dies geschieht, wenn eine vervollständigungssitzung angezeigt wird.)  
  
   - Ermöglichen Sie den Befehl aus, um an den nächsten Handler übergeben werden. (Alle anderen Befehle.)  
  
     Da diese Methode auf Benutzeroberfläche anzeigen kann, rufen <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> um sicherzustellen, dass sie nicht in einem Automation-Kontext aufgerufen wird:  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6. Dieser Code ist eine private Methode, die die vervollständigungssitzung auslöst:  
  
    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7. Im nächste Beispiel wird eine private Methode, die von kündigt das Abonnement der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> Ereignis:  
  
    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe CompletionTest, und führen Sie es in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Zum Erstellen und Testen der Lösung CompletionTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.  
  
3.  Erstellen Sie eine Textdatei, und geben Sie Text, der das Wort "hinzufügen".  
  
4.  Wenn Sie zuerst "a", und klicken Sie dann "d" eingeben, wird eine Liste mit "hinzufügen" und "Anpassung" sollte angezeigt werden. Beachten Sie, dass Addition ausgewählt ist. Wenn Sie eine andere "d" eingeben, sollte die Liste enthalten, nur "hinzufügen", die jetzt ausgewählt wird. Sie können "hinzufügen" einen Commit ausführen, durch Drücken der **LEERTASTE**, **Registerkarte**, oder **EINGABETASTE** Schlüssel, oder schließen Sie die Liste, indem Sie die ESC-Taste, oder jeder andere Schlüssel eingeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)