---
title: 'Exemplarische Vorgehensweise: Anzeigen der Signaturhilfe | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85d7eb3959064468e7583ec0c8a927f3e139daf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697423"
---
# <a name="walkthrough-display-signature-help"></a>Exemplarische Vorgehensweise: Signaturhilfe anzeigen
Die Signaturhilfe (auch als *Parameterinfo*bezeichnet ) zeigt die Signatur einer Methode in einer QuickInfo an, wenn ein Benutzer das Startzeichen der Parameterliste eingibt (in der Regel eine öffnende Klammer). Da ein Parameter und ein Parametertrennzeichen (in der Regel ein Komma) eingegeben werden, wird die QuickInfo aktualisiert, um den nächsten Parameter fett anzuzeigen. Sie können die Signaturhilfe wie folgt definieren: Definieren Sie im Kontext eines Sprachdienstes Ihre eigene Dateinamenerweiterung und Ihren eigenen Inhaltstyp, und zeigen Sie die Signaturhilfe für genau diesen Typ an, oder zeigen Sie die Signaturhilfe für einen vorhandenen Inhaltstyp an (z. B. "Text"). In dieser exemplarischen Vorgehensweise wird gezeigt, wie die Signaturhilfe für den Inhaltstyp "Text" angezeigt wird.

 Die Signaturhilfe wird in der Regel ausgelöst, indem ein bestimmtes Zeichen eingegeben wird, z. B. "(" (Öffnen der Klammer), und durch Eingabe eines anderen Zeichens, z. B. ")" (schließende Klammer), wird die Signaturhilfe ausgelöst. IntelliSense-Features, die durch Eingabe eines Zeichens ausgelöst werden, können mithilfe <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> eines Befehlshandlers für die <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Tastenanschläge (die Schnittstelle) und eines Handleranbieters, der die Schnittstelle implementiert, implementiert werden. Um die Signaturhilfequelle zu erstellen, d. h. die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> Liste der Signaturen, <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> die an der Signaturhilfe teilnehmen, implementieren Sie die Schnittstelle und einen Quellanbieter, der die Schnittstelle ausführt. Die Anbieter sind MEF-Komponenten (Managed Extensibility Framework) und sind für den Export der Quell- und <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>Controllerklassen und das Importieren von Diensten <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>und Brokern verantwortlich, z. B. die , mit der Sie im Textpuffer navigieren können, und die , die die Signaturhilfesitzung auslöst.

 In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die Signaturhilfe für einen hartcodierten Satz von Bezeichnern einrichten. Bei vollständigen Implementierungen ist die Sprache für die Bereitstellung dieser Inhalte verantwortlich.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts

#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen Sie ein Projekt von C-VSIX. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual C/ Erweiterbarkeit**aus, dann **VSIX-Projekt**.) Benennen Sie `SignatureHelpTest`die Lösung .

2. Fügen Sie dem Projekt eine Editor-Klassifierelementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

4. Fügen Sie die folgenden Verweise zum Projekt hinzu, `false`und stellen Sie sicher, dass **CopyLocal** auf :

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementieren von Signaturhilfesignaturen und -parametern
 Die Signaturhilfequelle basiert auf <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>Signaturen, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>, von denen jeder Parameter enthält, die implementieren. In einer vollständigen Implementierung würden diese Informationen aus der Sprachdokumentation abgerufen werden, aber in diesem Beispiel sind die Signaturen hartcodiert.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>So implementieren Sie die Signaturhilfesignaturen und -parameter

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `SignatureHelpSource`.

2. Fügen Sie die folgenden Importe hinzu.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Fügen Sie `TestParameter` eine Klasse <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>mit dem Namen hinzu, die implementiert.

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Fügen Sie einen Konstruktor hinzu, der alle Eigenschaften festlegt.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Fügen Sie <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>die Eigenschaften von hinzu.

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Fügen Sie `TestSignature` eine Klasse <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>mit dem Namen hinzu, die implementiert.

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Fügen Sie einige private Felder hinzu.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Fügen Sie einen Konstruktor hinzu, der <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> die Felder festlegt und das Ereignis abonniert.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Deklarieren Sie ein `CurrentParameterChanged` Ereignis. Dieses Ereignis wird ausgelöst, wenn der Benutzer einen der Parameter in der Signatur ausfüllt.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Sie die Eigenschaft `CurrentParameterChanged` so, dass sie das Ereignis auslöst, wenn der Eigenschaftswert geändert wird.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Fügen Sie eine `CurrentParameterChanged` Methode hinzu, die das Ereignis auslöst.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Fügen Sie eine Methode hinzu, die den aktuellen Parameter <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> berechnet, indem Sie die Anzahl der Kommas in der mit der Anzahl der Kommas in der Signatur vergleichen.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Fügen Sie einen <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignishandler für `ComputeCurrentParameter()` das Ereignis hinzu, das die Methode aufruft.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implementiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>-Eigenschaft. Diese Eigenschaft <xref:Microsoft.VisualStudio.Text.ITrackingSpan> enthält eine, die der Textspanne im Puffer entspricht, auf den die Signatur angewendet wird.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implementieren Sie die anderen Parameter.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementieren der Signaturhilfequelle
 Die Signaturhilfequelle ist der Satz von Signaturen, für die Sie Informationen bereitstellen.

#### <a name="to-implement-the-signature-help-source"></a>So implementieren Sie die Signaturhilfequelle

1. Fügen Sie `TestSignatureHelpSource` eine Klasse <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>mit dem Namen hinzu, die implementiert.

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Fügen Sie einen Verweis auf den Textpuffer hinzu.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Fügen Sie einen Konstruktor hinzu, der den Textpuffer und den Signaturhilfequellenanbieter festlegt.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>-Methode. In diesem Beispiel sind die Signaturen hartcodiert, aber in einer vollständigen Implementierung erhalten Sie diese Informationen aus der Sprachdokumentation.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Die Hilfsmethode `CreateSignature()` dient nur zur Veranschaulichung.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>-Methode. In diesem Beispiel gibt es nur zwei Signaturen, von denen jede zwei Parameter hat. Daher ist diese Methode nicht erforderlich. In einer umfassenderen Implementierung, in der mehr als eine Signaturhilfequelle verfügbar ist, wird diese Methode verwendet, um zu entscheiden, ob die Signaturhilfequelle mit der höchsten Priorität eine übereinstimmende Signatur bereitstellen kann. Wenn dies nicht möglich ist, gibt die Methode NULL zurück, und die Quelle mit der nächsthöheren Priorität wird aufgefordert, eine Übereinstimmung zu liefern.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Implementieren `Dispose()` Sie die Methode:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementieren des Signaturhilfequellenanbieters
 Der Signaturhilfe-Quellanbieter ist für den Export des MEF-Komponententeils (Managed Extensibility Framework) und für das Instanziieren der Signaturhilfequelle zuständig.

#### <a name="to-implement-the-signature-help-source-provider"></a>So implementieren Sie den Signaturhilfe-Quellanbieter

1. Fügen Sie `TestSignatureHelpSourceProvider` eine Klasse <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>mit dem Namen <xref:Microsoft.VisualStudio.Utilities.NameAttribute>hinzu, die implementiert, und exportieren Sie sie mit einem , a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "text" und einem <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von Before="default".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> Sie durch Instanziieren der `TestSignatureHelpSource`.

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implementieren des Befehlshandlers
 Die Signaturhilfe wird in der Regel durch eine öffnende Klammer "(" ausgelöst und durch ein schließendes Klammerzeichen ")" ausgelöst. Sie können diese Tastenanschläge verarbeiten, indem Sie eine <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ausführen, sodass sie eine Signaturhilfesitzung auslöst, wenn sie ein öffnendes Klammerzeichen empfängt, dem ein bekannter Methodenname vorangestellt ist, und die Sitzung beim Empfang eines schließenden Klammerzeichens ablehnt.

#### <a name="to-implement-the-command-handler"></a>So implementieren Sie den Befehlshandler

1. Fügen Sie `TestSignatureHelpCommand` eine Klasse <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>mit dem Namen hinzu, die implementiert.

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Fügen Sie private <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Felder für den Adapter (mit denen Sie den Befehlshandler zur Kette der Befehlshandler hinzufügen können), die Textansicht, den Signaturhilfebroker und die Sitzung, eine <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>und die nächste <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Fügen Sie einen Konstruktor hinzu, um diese Felder zu initialisieren und den Befehlsfilter der Kette der Befehlsfilter hinzuzufügen.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Sie die Methode, um die Signaturhilfesitzung auszulösen, wenn der Befehlsfilter ein öffnendes Klammerzeichen "(" nach einem der bekannten Methodennamen empfängt, und um die Sitzung zu beenden, wenn sie ein schließendes Klammerzeichen ")" empfängt, während die Sitzung noch aktiv ist. In jedem Fall wird der Befehl weitergeleitet.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Sie die Methode so, dass sie den Befehl immer weiterleitet.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementieren des Befehlsanbieters Signaturhilfe
 Sie können den Befehl Signaturhilfe <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> bereitstellen, indem Sie den implementieren, um den Befehlshandler zu instanziieren, wenn die Textansicht erstellt wird.

### <a name="to-implement-the-signature-help-command-provider"></a>So implementieren Sie den Befehlsanbieter Signaturhilfe

1. Fügen Sie `TestSignatureHelpController` eine Klasse <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> mit dem <xref:Microsoft.VisualStudio.Utilities.NameAttribute>Namen <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>hinzu, die sie implementiert und mit der <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>exportiert.

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importieren <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> Sie die (zum <xref:Microsoft.VisualStudio.Text.Editor.ITextView>Abrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> des <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , das Objekt), die (verwendet, um das aktuelle Wort zu finden) und die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (zum Auslösen der Signaturhilfesitzung).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implementieren <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Sie die Methode, `TestSignatureCommandHandler`indem Sie die instanziieren.

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die SignatureHelpTest-Lösung, und führen Sie sie in der experimentellen Instanz aus.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>So erstellen und testen Sie die SignatureHelpTest-Lösung

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der das Wort "hinzufügen" sowie eine öffnende Klammer enthält.

4. Nachdem Sie die öffnende Klammer eingegeben haben, sollte eine QuickInfo angezeigt werden, die eine Liste der beiden Signaturen für die `add()` Methode anzeigt.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
