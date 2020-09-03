---
title: 'Exemplarische Vorgehensweise: Anzeigen der Anweisungs Vervollständigung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db4e63beb1e3d4ff53e547492ae9eae7ee8001e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202009"
---
# <a name="walkthrough-displaying-statement-completion"></a>Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die sprachbasierte Anweisungs Vervollständigung implementieren, indem Sie die Bezeichner definieren, für die Sie den Abschluss bereitstellen möchten, und dann eine Beendigungs Sitzung auslösen. Sie können die Anweisungs Vervollständigung im Kontext eines sprach Dienes definieren, eine eigene Dateinamenerweiterung und einen Inhaltstyp definieren und dann den Abschluss nur für diesen Typ anzeigen, oder Sie können den Abschluss für einen vorhandenen Inhaltstyp, z. b. "Klartext", auslöst. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie die Anweisungs Vervollständigung für den Inhaltstyp "Klartext", der den Inhaltstyp von Textdateien darstellt, auslöst. Der Inhaltstyp "Text" ist der Vorgänger aller anderen Inhaltstypen, einschließlich Code-und XML-Dateien.  
  
 Die Anweisungs Vervollständigung wird in der Regel durch Eingabe bestimmter Zeichen ausgelöst, z. –. durch Eingabe des Anfangs eines Bezeichners, z. b. "using". Sie wird in der Regel durch Drücken der Leertaste, der Tab-Taste oder der EINGABETASTE, um eine Auswahl zu übernehmen. Sie können die IntelliSense-Funktionen implementieren, die ausgelöst werden, indem Sie mithilfe eines Befehls Handlers für die Tastatureingaben (die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle) und eines handleranbieters, der die-Schnittstelle implementiert, ein Zeichen eingeben <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Zum Erstellen der Vervollständigungs Quelle, bei der es sich um die Liste der Bezeichner handelt, die an der Vervollständigung beteiligt sind, implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> -Schnittstelle und einen Vervollständigungs Quellen Anbieter <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> Die Anbieter sind Managed Extensibility Framework Komponenten Teile (MEF). Sie sind dafür verantwortlich, die Quell-und Controller Klassen zu exportieren und Dienste und Broker zu importieren – z. b. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , die die Navigation im Text Puffer ermöglicht, und die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , die die Abschlusssitzung auslöst.  
  
 In dieser exemplarischen Vorgehensweise wird gezeigt, wie die Anweisungs Vervollständigung für einen hart codierten Satz von bezeichern implementiert wird. In vollständigen Implementierungen sind der Sprachdienst und die Sprachdokumentation für die Bereitstellung dieses Inhalts verantwortlich.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit**und dann **VSIX-Projekt**aus.) Benennen Sie die Projekt Mappe `CompletionTest` .  
  
2. Fügen Sie dem Projekt eine Editor-Klassifizierungs Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Löschen Sie die vorhandenen Klassendateien.  
  
4. Fügen Sie dem Projekt die folgenden Verweise hinzu, und stellen Sie sicher, dass **CopyLocal** auf festgelegt ist `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft. VisualStudio. Shell. 14,0  
  
     Microsoft. VisualStudio. Shell. immutable. 10.0  
  
     Microsoft. VisualStudio. Text Manager. Interop  
  
## <a name="implementing-the-completion-source"></a>Implementieren der Vervollständigungs Quelle  
 Die Vervollständigungs Quelle ist für das Erfassen der Gruppe von Bezeichnern und das Hinzufügen des Inhalts zum Vervollständigungs Fenster verantwortlich, wenn ein Benutzer einen Vervollständigungs-, z. b. die ersten Buchstaben eines Bezeichners, eingibt. In diesem Beispiel sind die Bezeichner und ihre Beschreibungen in der-Methode hart codiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> . In der Praxis verwenden Sie den Parser der Programmiersprache, um die Token zum Auffüllen der Vervollständigungsliste zu erhalten.  
  
#### <a name="to-implement-the-completion-source"></a>So implementieren Sie die Vervollständigungs Quelle  
  
1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestCompletionSource`.  
  
2. Fügen Sie diese Importe hinzu:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3. Ändern Sie die Klassen Deklaration für `TestCompletionSource` so, dass implementiert wird <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4. Fügen Sie private Felder für den Quell Anbieter, den Text Puffer und eine Liste von <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> Objekten (die den bezeichern entsprechen, die an der Abschlusssitzung beteiligt sind) hinzu:  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5. Fügen Sie einen Konstruktor hinzu, der den Quell Anbieter und-Puffer festlegt. Die- `TestCompletionSourceProvider` Klasse wird in späteren Schritten definiert:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> Methode, indem Sie einen Vervollständigungs Satz hinzufügen, der die Vervollständigungen enthält, die Sie im Kontext bereitstellen möchten. Jeder Vervollständigungs Satz enthält eine Reihe von <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> Vervollständigungen und entspricht einer Registerkarte im Vervollständigungs Fenster. (In Visual Basic-Projekten werden die Registerkarten für das Abschluss Fenster " **Common** " und " **all**" genannt.) Die finddekenspanatposition-Methode wird im nächsten Schritt definiert.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7. Die folgende Methode wird verwendet, um das aktuelle Wort von der Position des Cursors zu finden:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8. Implementieren Sie die- `Dispose()` Methode:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementieren des Vervollständigungs Quell Anbieters  
 Der Vervollständigungs Quellen Anbieter ist der MEF-Komponenten Teil, der die Vervollständigungs Quelle instanziiert.  
  
#### <a name="to-implement-the-completion-source-provider"></a>So implementieren Sie den Vervollständigungs Quellen Anbieter  
  
1. Fügen Sie eine Klasse mit dem Namen hinzu `TestCompletionSourceProvider` , die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Exportieren Sie diese Klasse mit <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Plaintext" und <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Test Vervollständigung".  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2. Importieren <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> Sie einen, der zum Suchen des aktuellen Worts in der Vervollständigungs Quelle verwendet wird.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> Methode, um die Vervollständigungs Quelle zu instanziieren.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementieren des Vervollständigungs Befehls Handler-Anbieters  
 Der Vervollständigungs Befehls Handler-Anbieter wird von einem abgeleitet <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , der auf ein Text Ansichts Erstellungs Ereignis lauscht und die Ansicht von einem –-Element konvertiert, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> das das Hinzufügen des Befehls zur Befehlskette der Visual Studio Shell – zu ermöglicht <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Da diese Klasse ein MEF-Export ist, können Sie Sie auch verwenden, um die Dienste zu importieren, die für den Befehls Handler selbst erforderlich sind.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>So implementieren Sie den Vervollständigungs Befehls Handler-Anbieter  
  
1. Fügen Sie eine Datei namens hinzu `TestCompletionCommandHandler` .  
  
2. Fügen Sie diese using-Anweisungen hinzu:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3. Fügen Sie eine Klasse mit dem Namen hinzu `TestCompletionHandlerProvider` , die implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Exportieren Sie diese Klasse mit <xref:Microsoft.VisualStudio.Utilities.NameAttribute> der "tokenvervollständigungs Handler", " <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Plaintext" und "" <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> von "" <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4. Importieren Sie den <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , der die Konvertierung von einem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> in einen <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , einen und einen ermöglicht, der den <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> Zugriff auf standardmäßige Visual Studio-Dienste ermöglicht.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5. Implementieren Sie die- <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Methode, um den Befehls Handler zu instanziieren.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementieren des Vervollständigungs Befehls Handlers  
 Da die Anweisungs Vervollständigung durch Tastatureingaben ausgelöst wird, müssen Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle implementieren, um die Tastatureingaben zu empfangen und zu verarbeiten, die die Abschlusssitzung auslösen, übertragen und verwerfen.  
  
#### <a name="to-implement-the-completion-command-handler"></a>So implementieren Sie den Vervollständigungs Befehls Handler  
  
1. Fügen Sie eine Klasse mit dem Namen hinzu `TestCompletionCommandHandler` , die implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Fügen Sie private Felder für den nächsten Befehls Handler (an den Sie den Befehl übergeben), die Textansicht, den Befehls Handler-Anbieter (der den Zugriff auf verschiedene Dienste ermöglicht) und eine Beendigungs Sitzung hinzu:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Fügen Sie einen Konstruktor hinzu, mit dem die Textansicht und die Anbieter Felder festgelegt werden, und fügen Sie der Befehlskette den Befehl hinzu:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Implementieren Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, indem Sie den Befehl übergeben:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Implementieren Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>-Methode. Wenn diese Methode eine Tastenkombination empfängt, muss Sie eine der folgenden Aktionen ausführen:  
  
   - Erlauben Sie, dass das Zeichen in den Puffer geschrieben wird, und starten Sie dann den Abschluss des-oder-Filters. (Dies wird von Druck Zeichen durchführen.)  
  
   - Commit für den Abschluss ausführen, lässt jedoch nicht zu, dass das Zeichen in den Puffer geschrieben wird. (Leerraum, Tab und Eingabe, wenn eine Vervollständigungs Sitzung angezeigt wird.)  
  
   - Ermöglicht das Weitergeben des Befehls an den nächsten Handler. (Alle anderen Befehle)  
  
     Da diese Methode möglicherweise die Benutzeroberfläche anzeigt, muss aufrufen, <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> um sicherzustellen, dass Sie nicht in einem Automatisierungs Kontext aufgerufen wird:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Dieser Code ist eine private Methode, die die Abschlusssitzung auslöst:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. Das nächste Beispiel ist eine private Methode, die das Abonnement des Ereignisses enthebt <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> :  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projekt Mappe completiontest, und führen Sie Sie in der experimentellen Instanz aus.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>So erstellen und testen Sie die completiontest-Projekt Mappe  
  
1. Erstellen Sie die Projektmappe.  
  
2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der das Wort "Add" enthält.  
  
4. Wenn Sie zuerst "a" und dann "d" eingeben, sollte eine Liste angezeigt werden, die "Addition" und "Anpassung" enthält. Beachten Sie, dass Addition ausgewählt ist. Wenn Sie ein anderes "d" eingeben, sollte die Liste nur "Addition" enthalten, das jetzt ausgewählt ist. Sie können einen Commit für "Addition" durchführen, indem Sie die Leertaste, die Tab-Taste oder die EINGABETASTE drücken oder die Liste durch Eingabe von ESC oder eines beliebigen anderen Schlüssels verwerfen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
