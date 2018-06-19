---
title: 'Exemplarische Vorgehensweise: Anzeigen von Signaturhilfe | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a714fdb268f44fd2a65d04184d899ced3de53bb9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148625"
---
# <a name="walkthrough-displaying-signature-help"></a>Exemplarische Vorgehensweise: Anzeigen von Signaturhilfe
Signaturhilfe (auch bekannt als *ParameterInfo*) die Signatur einer Methode in einer QuickInfo angezeigt, wenn ein Benutzer, das Zeichen für den Parameter Liste (in der Regel eine öffnende Klammer eingibt). Wie ein Parameter und Parametertrennzeichen (in der Regel ein Komma) eingegeben werden, wird die QuickInfo aktualisiert, um den nächsten Parameter in Fettdruck angezeigt. Signaturhilfe können Sie im Kontext eines Diensts Sprache definieren können Sie definieren Sie eine eigene Erweiterung und Inhalt Dateityp von Name und Signaturhilfe für nur dieses Typs angezeigt oder Signaturhilfe können Sie für einen vorhandenen Inhaltstyp (z. B. "Text") angezeigt. Diese exemplarischen Vorgehensweise beim Anzeigen von Signaturhilfe für den Inhaltstyp "Text".  
  
 Signaturhilfe wird in der Regel ausgelöst, indem Sie ein bestimmtes Zeichen eingeben "(" (öffnenden Klammer), und geschlossen werden, indem Sie ein anderes Zeichen, z. B. eingeben ")" (schließende Klammer). IntelliSense-Funktionen, die ausgelöst werden, indem Sie ein Zeichen eingeben können mithilfe der Befehlshandler für die Tastatureingaben implementiert werden (die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Interface) und ein Handler-Anbieter, implementiert die <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Schnittstelle. Implementieren, um die Quelle Signaturhilfe erstellen, das die Liste der Signaturen, Signaturhilfe teilnehmen, die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> Schnittstelle und eine Quellenanbieter, implementiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> Schnittstelle. Die Anbieter sind Komponenten des Managed Extensibility Framework (MEF) und sind verantwortlich für die Quell- und Controller-Klassen exportieren und Importieren von Diensten und Makler, z. B. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, und Sie können Sie in den Textpuffer navigieren und die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, der die Sitzung Signaturhilfe löst.  
  
 In dieser exemplarischen Vorgehensweise veranschaulicht, Signaturhilfe für ein fest programmiertes Satz von Bezeichnern zu implementieren. Vollständige Implementierung ist die Sprache für die Bereitstellung dieses Inhalts verantwortlich.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekts**.) Nennen Sie die Projektmappe `SignatureHelpTest`.  
  
2.  Dem Projekt eine Elementvorlage Editor Klassifizierer hinzugefügt. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
4.  Fügen Sie dem Projekt die folgenden Verweise hinzu, und stellen Sie sicher, dass **CopyLocal** festgelegt ist, um `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementieren die Signatur Signaturen und Parameter-Hilfe  
 Die Quelle Signaturhilfe basiert auf Signaturen, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, von denen jede enthält Parameter, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. Klicken Sie in keine vollständige Implementierung würde diese Informationen erhalten Sie in der sprachdokumentation, aber in diesem Beispiel wird die Signaturen hartcodiert sind.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Implementieren Sie die Signaturen Signaturhilfe und Parameter  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `SignatureHelpSource`.  
  
2.  Fügen Sie die folgenden Importe hinzu.  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Fügen Sie eine Klasse mit dem Namen `TestParameter` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Fügen Sie einen Konstruktor, der alle Eigenschaften festlegt.  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Fügen Sie die Eigenschaften des <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Fügen Sie eine Klasse mit dem Namen `TestSignature` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Fügen Sie einige private Felder hinzu.  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Fügen Sie einen Konstruktor, der die Felder festgelegt und abonniert die <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis.  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Deklarieren Sie eine `CurrentParameterChanged` Ereignis. Dieses Ereignis wird ausgelöst, wenn der Benutzer in einer der Parameter in der Signatur füllt.  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Eigenschaft, sodass die It löst die `CurrentParameterChanged` Ereignis aus, wenn der Eigenschaftswert geändert wird.  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Fügen Sie eine Methode, die löst die `CurrentParameterChanged` Ereignis.  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Fügen Sie eine Methode, die den aktuellen Parameter berechnet, indem Sie die Anzahl der Kommas in Vergleichen die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> auf die Anzahl von Kommas in der Signatur.  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. Fügen Sie einen Ereignishandler für das <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis, das Aufrufen der `ComputeCurrentParameter()` Methode.  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Implementiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>-Eigenschaft. Diese Eigenschaft enthält eine <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , die die Spanne des Texts in den Puffer, die Signatur gilt, entspricht.  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Implementieren Sie die anderen Parameter an.  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementieren die Quelle der Signatur-Hilfe  
 Die Quelle Signaturhilfe ist der Satz von Signaturen für die Sie Informationen bereitstellen.  
  
#### <a name="to-implement-the-signature-help-source"></a>Um die Quelle Signaturhilfe implementieren  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestSignatureHelpSource` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Fügen Sie einen Verweis auf den Textpuffer.  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Fügen Sie einen Konstruktor, der den Textpuffer und der Quellenanbieter Signaturhilfe festlegt.  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>-Methode. In diesem Beispiel wird die Signaturen hartcodiert sind, jedoch in eine vollständige Implementierung erhalten Sie diese Informationen in der sprachdokumentation.  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  Die Hilfsmethode `CreateSignature()` dient nur zur Veranschaulichung.  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>-Methode. In diesem Beispiel werden nur zwei Signaturen, von die jede zwei Parameter verfügt. Diese Methode ist daher nicht erforderlich. In eine größere-Implementierung, in der mehrere Signaturhilfe Quelle verfügbar ist. wird diese Methode verwendet, zu entscheiden, ob die höchste Priorität Signaturhilfe Quelle eine übereinstimmende Signatur bereitstellen kann. Wenn dies nicht möglich, die Methode gibt null zurück, und die Quelle weiter höchste Priorität wird gebeten, um eine Übereinstimmung anzugeben.  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Die Dispose()-Methode zu implementieren:  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementieren die Signatur Hilfe Quellenanbieter  
 Der Quellenanbieter Signaturhilfe ist verantwortlich für das Exportieren der Komponententeil Managed Extensibility Framework (MEF) und zum Instanziieren der Signaturhilfe Quelle.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Den Quellenanbieter Signaturhilfe implementieren  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestSignatureHelpSourceProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, und exportieren Sie sie mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, eine <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text", und ein <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> der Before = "Default".  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> durch Instanziierung der `TestSignatureHelpSource`.  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implementing-the-command-handler"></a>Implementieren der Befehlshandler  
 Signaturhilfe wird in der Regel ausgelöst, durch eine (Zeichen und "verworfen" durch einen) Zeichen. Sie können diese Tastatureingaben behandeln, durch die Implementierung einer <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , damit er eine Sitzung Signaturhilfe löst empfängt eine (Zeichen vorangestellt einen bekannten Methodennamen und schließt die Sitzung empfängt eine) Zeichen.  
  
#### <a name="to-implement-the-command-handler"></a>Der Befehlshandler implementieren  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestSignatureHelpCommand` implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  Fügen Sie private Felder für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Adapter (letztere Befehlshandler die Befehlskette Handler hinzufügen), Textansicht, Signaturhilfe Broker und die Sitzung eine <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, und der nächsten <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Fügen Sie einen Konstruktor, um diese Felder zu initialisieren und die Befehlskette Filter den Befehlsfilter hinzu.  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode, um die Sitzung Signaturhilfe auslösen, wenn der Befehlsfilter empfängt, eine (Zeichen, nach der die bekannten Methodennamen, und um die Sitzung zu schließen, empfängt eine) Zeichen, während die Sitzung noch aktiv ist. In jedem Fall wird der Befehl weitergeleitet.  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, sodass die It stets den Befehl weiterleitet.  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementieren des Anbieters des Signatur Help-Befehl  
 Sie können den Befehl Signaturhilfe bereitstellen, durch die Implementierung der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Befehlshandler zu instanziieren, wenn die Textansicht erstellt wird.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Um Signaturhilfe-Befehlsanbieter zu implementieren.  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestSignatureHelpController` implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> und exportieren Sie sie mit der <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, und <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  Importieren der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (zum Abrufen der <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, dessen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt), wird die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (verwendet das aktuelle Wort gefunden), und die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (um die Sitzung Signaturhilfe auszulösen).  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Methode durch die Instanziierung der `TestSignatureCommandHandler`.  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die SignatureHelpTest-Projektmappe, und führen Sie sie in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>So erstellen und Testen der Lösung SignatureHelpTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei und einigen Texten, die das Wort "hinzufügen" Typ sowie eine öffnende Klammer ein.  
  
4.  Nachdem Sie die öffnende Klammer eingeben, sehen Sie eine QuickInfo, die zeigt eine Liste der zwei Signaturen für die `add()` Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)