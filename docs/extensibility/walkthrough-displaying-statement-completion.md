---
title: 'Exemplarische Vorgehensweise: Anzeigen der Anweisungsvervollständigung | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 1d2f5499511c9dc0bbb6711d0da630315384f8e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697416"
---
# <a name="walkthrough-display-statement-completion"></a>Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung
Sie können die sprachbasierte Anweisungsvervollständigung implementieren, indem Sie die Bezeichner definieren, für die Sie den Abschluss bereitstellen möchten, und dann eine Abschlusssitzung auslösen. Sie können die Anweisungsvervollständigung im Kontext eines Sprachdienstes definieren, Ihre eigene Dateinamenerweiterung und Ihren eigenen Inhaltstyp definieren und dann die Vervollständigung nur für diesen Typ anzeigen. Sie können auch die Fertigstellung für einen vorhandenen Inhaltstyp auslösen, z. B. "Klartext". In dieser exemplarischen Vorgehensweise wird gezeigt, wie die Anweisungsvervollständigung für den Inhaltstyp "Klartext" ausgelöst wird, d. h. der Inhaltstyp von Textdateien. Der Inhaltstyp "Text" ist der Vorgänger aller anderen Inhaltstypen, einschließlich Code- und XML-Dateien.

 Die Anweisungsvervollständigung wird in der Regel durch Eingabe bestimmter Zeichen ausgelöst, z. B. durch Eingabe des Anfangs eines Bezeichners wie "verwenden". Es wird in der Regel durch Drücken der **Leertaste**, **Tab**oder **Enter-Taste,** um eine Auswahl zu übertragen. Sie können die IntelliSense-Features implementieren, die beim Eingeben eines Zeichens ausgelöst <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> werden, indem Sie einen <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Befehlshandler für die Tastenanschläge (die Schnittstelle) und einen Handleranbieter verwenden, der die Schnittstelle implementiert. Um die Abschlussquelle zu erstellen, d. h. die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Liste der Bezeichner, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> die an der Fertigstellung beteiligt sind, implementieren Sie die Schnittstelle und einen Abschlussquellanbieter (die Schnittstelle). Die Anbieter sind MEF-Komponenten (Managed Extensibility Framework). Sie sind für den Export der Quell- und Controllerklassen und das <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>Importieren von Diensten und Brokern <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>verantwortlich, z. B. die , die die Navigation im Textpuffer ermöglicht, und die , die die Abschlusssitzung auslöst.

 In dieser exemplarischen Vorgehensweise wird gezeigt, wie die Anweisungsvervollständigung für einen hartcodierten Satz von Bezeichnern implementiert wird. Bei vollständigen Implementierungen sind der Sprachdienst und die Sprachdokumentation für die Bereitstellung dieser Inhalte verantwortlich.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen Sie ein Projekt von C-VSIX. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual C/ Erweiterbarkeit**aus, dann **VSIX-Projekt**.) Benennen Sie `CompletionTest`die Lösung .

2. Fügen Sie dem Projekt eine Editor-Klassifierelementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

4. Fügen Sie die folgenden Verweise zum Projekt hinzu, `false`und stellen Sie sicher, dass **CopyLocal** auf :

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.15.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Implementieren der Abschlussquelle
 Die Abschlussquelle ist für das Sammeln der Bezeichner und das Hinzufügen des Inhalts zum Vervollständigungsfenster verantwortlich, wenn ein Benutzer einen Abschlusstrigger eingibt, z. B. die ersten Buchstaben eines Bezeichners. In diesem Beispiel sind die Bezeichner und ihre <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Beschreibungen in der Methode hartcodiert. In den meisten realen Anwendungen würden Sie den Parser Ihrer Sprache verwenden, um die Token zum Auffüllen der Vervollständigungsliste zu erhalten.

### <a name="to-implement-the-completion-source"></a>So implementieren Sie die Abschlussquelle

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestCompletionSource`.

2. Addieren Sie diese Importe:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Ändern Sie die `TestCompletionSource` Klassendeklaration <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>so, dass sie implementiert:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Fügen Sie private Felder für den Quellanbieter, <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> den Textpuffer und eine Liste von Objekten hinzu (die den Bezeichnern entsprechen, die an der Abschlusssitzung teilnehmen):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Fügen Sie einen Konstruktor hinzu, der den Quellanbieter und den Puffer festlegt. Die `TestCompletionSourceProvider` Klasse wird in späteren Schritten definiert:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Sie die Methode, indem Sie einen Abschlusssatz hinzufügen, der die Abgeschlossenen enthält, die Sie im Kontext bereitstellen möchten. Jeder Abschlusssatz enthält <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> einen Satz von Vervollständigungen und entspricht einer Registerkarte des Abschlussfensters. (In Visual Basic-Projekten werden die Registerkarten für das Abschlussfenster **common** und **All**genannt.) Die `FindTokenSpanAtPosition` Methode wird im nächsten Schritt definiert.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Die folgende Methode wird verwendet, um das aktuelle Wort aus der Position des Cursors zu finden:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Implementieren `Dispose()` Sie die Methode:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementieren des Abschlussquellanbieters
 Der Abschlussquellanbieter ist das MEF-Komponententeil, das die Abschlussquelle instanziiert.

### <a name="to-implement-the-completion-source-provider"></a>So implementieren Sie den Abschlussquellanbieter

1. Fügen Sie `TestCompletionSourceProvider` eine Klasse <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>mit dem Namen hinzu, die implementiert. Exportieren Sie diese <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Klasse mit einem <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Klartext" und einem "Testabschluss".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importieren <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>Sie eine , die das aktuelle Wort in der Abschlussquelle findet.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> Sie die Methode, um die Abschlussquelle zu instanziieren.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementieren des Vervollständigungsbefehlshandlers
 Der Befehlshandler für die <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>Vervollständigung wird von einem abgeleitet, der auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>ein Textansichtserstellungsereignis wartet und die Ansicht von einem <xref:Microsoft.VisualStudio.Text.Editor.ITextView>konvertiert, der das Hinzufügen des Befehls zur Befehlskette der Visual Studio-Shell ermöglicht, in eine . Da es sich bei dieser Klasse um einen MEF-Export handelt, können Sie sie auch zum Importieren der Dienste verwenden, die vom Befehlshandler selbst benötigt werden.

#### <a name="to-implement-the-completion-command-handler-provider"></a>So implementieren Sie den Vervollständigungsbefehlshandleranbieter

1. Fügen Sie `TestCompletionCommandHandler`eine Datei mit dem Namen hinzu.

2. Fügen Sie diese mithilfe von Direktiven hinzu:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Fügen Sie `TestCompletionHandlerProvider` eine Klasse <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>mit dem Namen hinzu, die implementiert. Exportieren Sie diese <xref:Microsoft.VisualStudio.Utilities.NameAttribute> Klasse mit einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Token-Vervollständigungshandler", einem "Klartext" und einem <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> von <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importieren <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>Sie die , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> die <xref:Microsoft.VisualStudio.Text.Editor.ITextView>die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>Konvertierung von <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> a in ermöglicht, a , und eine, die den Zugriff auf Standardmäßige Visual Studio-Dienste ermöglicht.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implementieren <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Sie die Methode zum Instanziieren des Befehlshandlers.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementieren des Befehlshandlers für den Abschluss
 Da die Anweisungsvervollständigung durch Tastenanschläge <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ausgelöst wird, müssen Sie die Schnittstelle implementieren, um die Tastenanschläge zu empfangen und zu verarbeiten, die die Abschlusssitzung auslösen, übertragen und ablehnen.

#### <a name="to-implement-the-completion-command-handler"></a>So implementieren Sie den Vervollständigungsbefehlshandler

1. Fügen Sie `TestCompletionCommandHandler` eine Klasse <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>mit dem Namen hinzu, die implementiert:

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Fügen Sie private Felder für den nächsten Befehlshandler (an den Sie den Befehl übergeben), die Textansicht, den Befehlshandler (der den Zugriff auf verschiedene Dienste ermöglicht) und eine Abschlusssitzung hinzu:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Fügen Sie einen Konstruktor hinzu, der die Textansicht und die Anbieterfelder festlegt und den Befehl zur Befehlskette hinzufügt:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Sie die Methode, indem Sie den Befehl entlang übergeben:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implementieren Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>-Methode. Wenn diese Methode einen Tastenanschlag erhält, muss sie eines der folgenden Schritte tun:

   - Lassen Sie zu, dass das Zeichen in den Puffer geschrieben wird, und lösen Sie dann den Abschluss aus oder filtern. (Drucken von Zeichen tun dies.)

   - Geben Sie die Vervollständigung fest, lassen Sie jedoch nicht zu, dass das Zeichen in den Puffer geschrieben wird. (Whitespace, **Tab**und **Enter** tun dies, wenn eine Abschlusssitzung angezeigt wird.)

   - Lassen Sie zu, dass der Befehl an den nächsten Handler übergeben wird. (Alle anderen Befehle.)

     Da diese Methode möglicherweise <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> die Benutzeroberfläche anzeigt, rufen Sie auf, um sicherzustellen, dass sie nicht in einem Automatisierungskontext aufgerufen wird:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Dieser Code ist eine private Methode, die die Abschlusssitzung auslöst:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. Das nächste Beispiel ist eine private Methode, die <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> sich vom Ereignis abmeldet:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die CompletionTest-Lösung, und führen Sie sie in der experimentellen Instanz aus.

#### <a name="to-build-and-test-the-completiontest-solution"></a>So erstellen und testen Sie die CompletionTest-Lösung

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der das Wort "hinzufügen" enthält.

4. Wenn Sie zuerst "a" und dann "d" eingeben, sollte eine Liste mit "Addition" und "Anpassung" angezeigt werden. Beachten Sie, dass der Zusatz ausgewählt ist. Wenn Sie ein anderes "d" eingeben, sollte die Liste nur "Addition" enthalten, das jetzt ausgewählt ist. Sie können "Addition" festschreiben, indem Sie die **Taste Leertaste**, **Tabulator**oder **Eingabedrücken** drücken oder die Liste schließen, indem Sie Esc oder einen anderen Schlüssel eingeben.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
