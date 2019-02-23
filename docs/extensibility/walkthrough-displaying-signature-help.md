---
title: 'Exemplarische Vorgehensweise: Anzeigen von Signaturhilfe | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 884b054503ef94c84ef267d562897c93cded9948
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684220"
---
# <a name="walkthrough-display-signature-help"></a>Exemplarische Vorgehensweise: Signaturhilfe anzeigen
Signaturhilfe (auch bekannt als *ParameterInfo*) die Signatur einer Methode in einer QuickInfo angezeigt, wenn ein Benutzer das Zeichen für den Parameter Liste (in der Regel eine öffnende Klammer) eingibt. Wie ein Parameter und das Parametertrennzeichen (in der Regel ein Komma) eingegeben werden, wird die QuickInfo aktualisiert, und den nächsten Parameter in Fettschrift angezeigt wird. Sie können die Signaturhilfe definieren, es gibt folgende Möglichkeiten: im Kontext von einem Sprachdienst, definieren Sie Ihre eigenen Dateinamenerweiterung und Content-Type und Signatur-Hilfe für nur diesen Typ oder anzeigen Signaturhilfe für einem vorhandenen Inhaltstyp (z. B. "Text"). Dieser exemplarischen Vorgehensweise beim Anzeigen von Signaturhilfe für den Inhaltstyp "Text".

 Signaturhilfe wird in der Regel ausgelöst werden, geben Sie ein bestimmtes Zeichen, z. B. "(" (Klammer), und geben Sie ein anderes Zeichen, z. B. geschlossen ")" (schließende Klammer). IntelliSense-Funktionen, die ausgelöst werden, durch Eingabe eines Zeichens können implementiert werden, indem ein Befehlshandler für die Tastatureingaben (die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle) und ein Handler für Anbieter, implementiert die <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Schnittstelle. Um die Quelle Signaturhilfe zu erstellen, die die Liste der Signaturen in der Signatur zu Hilfe nehmen, implementieren die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> -Schnittstelle und eine Quellenanbieter, der ausgeführt wird die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> Schnittstelle. Die Anbieter sind Komponenten des Managed Extensibility Framework (MEF) und sind zuständig für die Quell- und Controller-Klassen exportieren und Importieren von Diensten und Makler, z. B. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, mit dem Sie im Textpuffer navigieren, und die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, die die Sitzung Signaturhilfe ausgelöst.

 Diese exemplarische Vorgehensweise veranschaulicht das Einrichten von Signatur-Hilfe für einen hartcodierten Satz von Bezeichnern. In vollständige Implementierungen ist die Sprache für die Bereitstellung, dass der Inhalt verantwortlich.

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015 können installieren nicht Sie das Visual Studio SDK aus dem Downloadcenter. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts

#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `SignatureHelpTest`.

2.  Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3.  Löschen Sie die vorhandenen Klassendateien.

4.  Fügen Sie die folgenden Verweise dem Projekt hinzu, und stellen Sie sicher, dass **CopyLocal** nastaven NA hodnotu `false`:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementieren der Signaturhilfe Signaturen und Parameter
 Die Signaturhilfe Quelle basiert darauf, dass Signaturen, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, von denen jede enthält Parameter, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. Klicken Sie in eine vollständige Implementierung würde diese Informationen erhalten Sie in der sprachdokumentation, aber in diesem Beispiel werden fest programmierte.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Zur Implementierung der Signaturhilfe Signaturen und Parameter

1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `SignatureHelpSource`.

2.  Fügen Sie die folgenden Importe hinzu.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3.  Fügen Sie eine Klasse, die mit dem Namen `TestParameter` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4.  Fügen Sie einen Konstruktor, der alle Eigenschaften festlegt.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5.  Fügen Sie die Eigenschaften der <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6.  Fügen Sie eine Klasse, die mit dem Namen `TestSignature` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7.  Fügen Sie private Felder hinzu.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8.  Fügen Sie einen Konstruktor, der die Felder festgelegt und abonniert das <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Deklarieren Sie eine `CurrentParameterChanged` Ereignis. Dieses Ereignis wird ausgelöst, wenn der Benutzer einer der Parameter in der Signatur ausfüllt.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Eigenschaft, sodass die It löst die `CurrentParameterChanged` Ereignis aus, wenn der Eigenschaftswert geändert wird.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Fügen Sie eine Methode, die löst die `CurrentParameterChanged` Ereignis.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Fügen Sie eine Methode, die den aktuellen Parameter berechnet anhand der Anzahl von Kommas in der <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> auf die Anzahl von Kommas in der Signatur.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Hinzufügen eines ereignishandlers für das <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> -Ereignis, das Aufrufen der `ComputeCurrentParameter()` Methode.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implementiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>-Eigenschaft. Diese Eigenschaft enthält eine <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , entspricht der Textabschnitt im Puffer, der die Signatur angewendet wird.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implementieren Sie die anderen Parameter an.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementieren der Signaturhilfe-Quelle
 Die Signaturhilfe-Quelle ist der Satz von Signaturen für die Sie Informationen bereitstellen.

#### <a name="to-implement-the-signature-help-source"></a>Um die Signaturhilfe Quelle zu implementieren.

1.  Fügen Sie eine Klasse, die mit dem Namen `TestSignatureHelpSource` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2.  Fügen Sie einen Verweis auf den Textpuffer.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3.  Fügen Sie einen Konstruktor, der dem Textpuffer und der Quellenanbieter Signaturhilfe festlegt.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>-Methode. In diesem Beispiel werden fest programmierte, aber in eine vollständige Implementierung würden Sie erhalten diese Informationen in der sprachdokumentation.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5.  Die Hilfsmethode `CreateSignature()` wird nur zur Veranschaulichung bereitgestellt.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>-Methode. In diesem Beispiel sind nur zwei Signaturen, von die jede zwei Parameter verfügt. Diese Methode ist daher nicht erforderlich. In eine größere Implementierung, die in der Quelle mit mehr als eine Signatur-Hilfe verfügbar ist. wird diese Methode verwendet, zu entscheiden, ob die mit der höchsten Priorität Signaturhilfe Quelle eine übereinstimmende Signatur bereitgestellt werden kann. Wenn dies nicht möglich, die Methode gibt null zurück, und die Quelle weiter – mit der höchsten Priorität wird aufgefordert, eine Übereinstimmung anzugeben.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7.  Implementieren der `Dispose()` Methode:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementieren der Quellenanbieter Signaturhilfe
 Der Quellenanbieter Signatur-Hilfe ist für den Export von der Komponente Managed Extensibility Framework (MEF) und für die Instanziierung der Signaturhilfe Quelle verantwortlich.

#### <a name="to-implement-the-signature-help-source-provider"></a>Zum Implementieren des Quellenanbieter Signaturhilfe

1.  Fügen Sie eine Klasse, die mit dem Namen `TestSignatureHelpSourceProvider` , implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text", und ein <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von vor = "Default".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2.  Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> durch Instanziieren der `TestSignatureHelpSource`.

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Die Befehlshandler implementieren
 Signaturhilfe wird in der Regel ausgelöst von einer öffnenden Klammer "(" Zeichen und "verworfen" durch eine schließende Klammer")"-Zeichen. Sie können diese Tastatureingaben behandeln, indem Sie Ausführung einer <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , damit sie eine Sitzung Signaturhilfe ausgelöst, ein öffnendes empfängt, Klammer einen bekannten Methodennamen vorangestellt, und schließt die Sitzung eine schließende empfängt Klammer.

#### <a name="to-implement-the-command-handler"></a>Die Befehlshandler implementieren.

1.  Fügen Sie eine Klasse, die mit dem Namen `TestSignatureHelpCommand` implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2.  Fügen Sie private Felder für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> -Adapter (mit der Sie die Kette der Befehlshandler die Befehlshandler hinzufügen zu können), die Textansicht, die Signaturhilfe Broker und die Sitzung eine <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, und die nächsten <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3.  Fügen Sie einen Konstruktor aus, um diese Felder zu initialisieren und die Befehlsketten-Filter der Befehlsfilter hinzu.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode, um die Signaturhilfe Sitzung auslösen, wenn der Befehlsfilter empfängt eine öffnende Klammer ein "("-Zeichen nach der die bekannte Methodennamen und um die Sitzung schließen empfängt eine schließende Klammer")"-Zeichen während die Sitzung noch aktiv ist. In jedem Fall wird der Befehl weitergeleitet.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, sodass die It immer den Befehl weiterleitet.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementieren der Signaturhilfe-Befehlsanbieter
 Sie können den Signatur-Hilfe-Befehl angeben, durch die Implementierung der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> die Befehlshandler instanziiert, wenn die Textansicht erstellt wird.

### <a name="to-implement-the-signature-help-command-provider"></a>Den Anbieter für die Signaturhilfe Befehl implementiert

1.  Fügen Sie eine Klasse, die mit dem Namen `TestSignatureHelpController` implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> und exportieren Sie sie mit der <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, und <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2.  Importieren der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (zum Abrufen der <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, bestimmte die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt), wird die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (verwendet das aktuelle Wort gefunden), und die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (um die Sitzung Signaturhilfe auszulösen).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3.  Implementieren der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Methode durch die Instanziierung der `TestSignatureCommandHandler`.

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die Projektmappe SignatureHelpTest, und führen Sie es in der experimentellen Instanz.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Zum Erstellen und Testen der Lösung SignatureHelpTest

1.  Erstellen Sie die Projektmappe.

2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3.  Erstellen Sie eine Textdatei und geben Sie Text an, der das Wort "hinzufügen" sowie eine öffnende Klammer ein.

4.  Nachdem Sie die öffnende Klammer eingeben, sollte eine QuickInfo, die zeigt eine Liste mit den zwei Signaturen für die `add()` Methode.

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Verknüpfen Sie einen Inhaltstyp mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)