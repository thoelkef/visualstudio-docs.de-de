---
title: 'Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f26f37a945ce9ec665e924662d117f43e49ab77
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839335"
---
# <a name="walkthrough-displaying-statement-completion"></a>Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können-Sprache basierenden Anweisungsvervollständigung durch definieren die Bezeichner für die Sie die Vervollständigung bereitstellen möchten, und klicken Sie dann auszulösen eine vervollständigungssitzung implementieren. Anweisungsvervollständigung im Kontext von einem Sprachdienst zu definieren, definieren Sie Ihre eigenen Dateinamenerweiterung und Content-Type und -Vervollständigung für nur diesen Typ dann anzeigen, oder -Vervollständigung für einem vorhandenen Inhaltstyp auslösen, z. B. "nur-Text". In dieser exemplarischen Vorgehensweise zeigt, wie Anweisungsvervollständigung für den Inhaltstyp "nur-Text", den Inhaltstyp der Textdateien handelt, ausgelöst wird. Der Inhaltstyp "Text" ist der Vorgänger aller anderen Inhaltstypen, einschließlich Code und XML-Dateien.  
  
 Anweisungsvervollständigung in der Regel durch die Eingabe bestimmter Zeichen ausgelöst wird – z. B. durch den Anfang eines Bezeichners, z. B. "using" eingeben. Sie ist normalerweise geschlossen, durch Drücken der LEERTASTE, Tab oder EINGABETASTE-Taste, um eine Auswahl zu übernehmen. Können Sie die IntelliSense-Funktionen, die ausgelöst werden, geben Sie ein Zeichen mit einem Befehlshandler für die Tastatureingaben implementieren (die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle) und ein Handler für Anbieter, implementiert die <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Schnittstelle. Zum Erstellen der abschlussquelle, die die Liste der Bezeichner, die in der Anweisungsvervollständigung beteiligt sind ist, implementieren die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Schnittstelle und einen Vervollständigungsanbieter für die Quelle (die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> Schnittstelle). Die Anbieter sind Komponenten des Managed Extensibility Framework (MEF). Sie sind zuständig für das Exportieren von der Quell- und Controller-Klassen aus, und Importieren von Diensten und Brokern – z. B. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, dem ermöglicht die Navigation im Textpuffer, und die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, die löst der vervollständigungssitzung.  
  
 Diese exemplarische Vorgehensweise veranschaulicht das Implementieren der Anweisungsvervollständigung für einen hartcodierten Satz von Bezeichnern. In vollständige Implementierungen sind der Sprachdienst und in der sprachdokumentation für die Bereitstellung, dass der Inhalt verantwortlich.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `CompletionTest`.  
  
2.  Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
4.  Fügen Sie die folgenden Verweise dem Projekt hinzu, und stellen Sie sicher, dass **CopyLocal** nastaven NA hodnotu `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Implementieren der Abschlussquelle  
 Der abschlussquelle ist verantwortlich für das Sammeln der Satz von Bezeichnern, und das Fenster "Abschluss" den Inhalt hinzugefügt wird, wenn ein Benutzer, einen Trigger für buildabschluss, z. B. die ersten Buchstaben eines Bezeichners eingibt. In diesem Beispiel die IDs und Beschreibungen werden in hartcodiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Methode. In den meisten realen Fällen verwenden Sie die Sprache der Parser zum Abrufen von Token zum Auffüllen der Liste.  
  
#### <a name="to-implement-the-completion-source"></a>Zum Implementieren der abschlussquelle  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestCompletionSource`.  
  
2.  Fügen Sie diese Importe hinzu:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3.  Ändern Sie die Klassendeklaration für `TestCompletionSource` , damit er implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4.  Fügen Sie private Felder für den Quellenanbieter, das den Textpuffer und eine Liste der <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> Objekte (die entsprechen die Bezeichner, die in der Sitzung zur codevervollständigung einbezogen werden):  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5.  Fügen Sie einen Konstruktor, der dem Quellanbieter und Puffer festlegt. Die `TestCompletionSourceProvider` Klasse wird in späteren Schritten definiert:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Methode durch das Hinzufügen eines Vervollständigungssatzes, die die vervollständigungen enthält, die Sie in den Kontext angeben möchten. Jede Vervollständigungssatz enthält einen Satz von <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> vervollständigungen, und entspricht einer Registerkarte des Fensters Abschluss. (In Visual Basic-Projekten die Vervollständigung Registerkarten heißen **allgemeine** und **alle**.) Die FindTokenSpanAtPosition-Methode wird im nächsten Schritt definiert.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7.  Die folgende Methode wird verwendet, um das aktuelle Wort von der Position des Cursors zu finden:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8.  Implementieren der `Dispose()` Methode:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementieren den Quellenanbieter Abschluss  
 Der Abschluss-Source-Anbieter ist der MEF-Komponente, die der abschlussquelle instanziiert.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Zum Implementieren des Quellenanbieter Abschluss  
  
1.  Fügen Sie eine Klasse, die mit dem Namen `TestCompletionSourceProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exportieren Sie diese Klasse mit einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Klartext" und ein <xref:Microsoft.VisualStudio.Utilities.NameAttribute> Vollendungsgrad"Test".  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2.  Importieren einer <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, womit das aktuelle Wort in der abschlussquelle zu finden.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> Methode zum Instanziieren der abschlussquelle.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementieren den Abschluss Command-Handler-Provider  
 Handler die Vervollständigungsanbieter-Befehl ergibt sich aus einer <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, die Lauscht auf ein Erstellungsereignis für Text anzeigen, und konvertiert die Ansicht aus eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>– dadurch, dass das Hinzufügen des Befehls, der die Befehlskette der Visual Studio-Shell – zu einer <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Da diese Klasse einen MEF-Export ist, können Sie es auch verwenden, so importieren Sie die Dienste, die den Befehlshandler selbst erforderlich sind.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Den Abschluss Befehl Handler-Anbieter implementiert  
  
1.  Fügen Sie die Datei `TestCompletionCommandHandler`.  
  
2.  Fügen Sie die folgenden using-Anweisungen hinzu:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3.  Fügen Sie eine Klasse, die mit dem Namen `TestCompletionHandlerProvider` implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exportieren dieser Klasse mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> von "token Abschlusshandler", eine <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "nur-Text", und ein <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> von <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4.  Importieren der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, dem ermöglicht die Konvertierung von einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zu eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, eine <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, und ein <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> ermöglicht, die den Zugriff auf standardmäßige Visual Studio-Diensten.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> -Methode instanziieren, die den Befehlshandler.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementieren den Befehl Abschlusshandler  
 Da der Anweisungsvervollständigung von Tastatureingaben ausgelöst wird, müssen Sie implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle zum Empfangen und Verarbeiten von Tastenkombinationen, die auslösen, zu committen und Schließen der Sitzung zur codevervollständigung.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Um den Abschlusshandler-Befehl zu implementieren.  
  
1. Fügen Sie eine Klasse, die mit dem Namen `TestCompletionCommandHandler` implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Fügen Sie private Felder für den nächsten Befehlshandler (zu dem Sie den Befehl übergeben), die Textansicht, die Handler-Befehlsanbieter (wodurch der Zugriff auf verschiedene Dienste), und eine vervollständigungssitzung:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Fügen Sie einen Konstruktor, der festlegt, der Textansicht und die Anbieterfelder und die Befehlskette fügt den Befehl hinzu:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> -Methode und übergeben den Befehl an:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Implementieren Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>-Methode. Wenn diese Methode eine Tastatureingabe empfängt, müssen sie eine der folgenden Optionen:  
  
   - Ermöglichen Sie das Zeichen, das den Puffer geschrieben werden und lösen Sie dann oder Abschluss zu filtern. (Druckbaren Zeichen hierzu.)  
  
   - Committen Sie die Vervollständigung zu, aber lassen Sie nicht das Zeichen, das in den Puffer geschrieben werden. (Leerzeichen, Registerkarte und geben Sie dies eine vervollständigungssitzung angezeigt wird.)  
  
   - Ermöglichen Sie den Befehl aus, um an den nächsten Handler übergeben werden. (Alle anderen Befehle.)  
  
     Da diese Methode auf Benutzeroberfläche anzeigen kann, rufen <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> um sicherzustellen, dass sie nicht in einem Automation-Kontext aufgerufen wird:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Dieser Code ist eine private Methode, die die vervollständigungssitzung auslöst:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. Im nächste Beispiel wird eine private Methode, die von kündigt das Abonnement der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> Ereignis:  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe CompletionTest, und führen Sie es in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Zum Erstellen und Testen der Lösung CompletionTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei, und geben Sie Text, der das Wort "hinzufügen".  
  
4.  Wenn Sie zuerst "a", und klicken Sie dann "d" eingeben, sollte eine Liste mit "hinzufügen" und "Anpassung" angezeigt werden. Beachten Sie, dass Addition ausgewählt ist. Wenn Sie eine andere "d" eingeben, sollte die Liste enthalten, nur "hinzufügen", die jetzt ausgewählt wird. Sie können committen Sie "hinzufügen", indem Sie die LEERTASTE, Tab oder EINGABETASTE drücken, oder schließen die Liste durch Eingabe der ESC-Taste, oder eine beliebige Taste.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

