---
title: 'Exemplarische Vorgehensweise: Anzeigen von Signaturhilfe | Microsoft-Dokumentation'
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
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0642b798668e24e7ba1e6595ab3c8ea6dba6885e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247922"
---
# <a name="walkthrough-displaying-signature-help"></a>Exemplarische Vorgehensweise: Anzeigen der Signaturhilfe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Signaturhilfe (auch bekannt als *ParameterInfo*) die Signatur einer Methode in einer QuickInfo angezeigt, wenn ein Benutzer das Zeichen für den Parameter Liste (in der Regel eine öffnende Klammer) eingibt. Wie ein Parameter und das Parametertrennzeichen (in der Regel ein Komma) eingegeben werden, wird die QuickInfo aktualisiert, und den nächsten Parameter in Fettschrift angezeigt wird. Sie können die Signaturhilfe definieren, im Kontext von einem Sprachdienst, können Sie definieren Sie eine eigene Erweiterung und Inhalt Dateinamentyp und Anzeigen von Signaturhilfe für nur diesen Typ, oder Sie können die Signaturhilfe anzeigen, für die einem vorhandenen Inhaltstyp (z. B. "Text"). Dieser exemplarischen Vorgehensweise beim Anzeigen von Signaturhilfe für den Inhaltstyp "Text".  
  
 Signaturhilfe wird in der Regel ausgelöst werden, geben Sie ein bestimmtes Zeichen, z. B. "(" (Klammer), und geben Sie ein anderes Zeichen, z. B. geschlossen ")" (schließende Klammer). IntelliSense-Funktionen, die ausgelöst werden, durch Eingabe eines Zeichens können implementiert werden, indem ein Befehlshandler für die Tastatureingaben (die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle) und ein Handler für Anbieter, implementiert die <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Schnittstelle. Um die Quelle Signaturhilfe zu erstellen, die die Liste der Signaturen in der Signatur zu Hilfe nehmen, implementieren die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> Schnittstelle und eine Quellenanbieter, der implementiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> Schnittstelle. Die Anbieter sind Komponenten des Managed Extensibility Framework (MEF) und sind zuständig für die Quell- und Controller-Klassen exportieren und Importieren von Diensten und Makler, z. B. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, mit dem Sie im Textpuffer navigieren, und die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, die die Sitzung Signaturhilfe ausgelöst.  
  
 Diese exemplarische Vorgehensweise veranschaulicht das Implementieren von Signatur-Hilfe für einen hartcodierten Satz von Bezeichnern. In vollständige Implementierungen ist die Sprache für die Bereitstellung, dass der Inhalt verantwortlich.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `SignatureHelpTest`.  
  
2.  Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
4.  Fügen Sie die folgenden Verweise dem Projekt hinzu, und stellen Sie sicher, dass **CopyLocal** nastaven NA hodnotu `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementieren die Signatur Signaturen und Parameter-Hilfe  
 Die Signaturhilfe Quelle basiert darauf, dass Signaturen, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, von denen jede enthält Parameter, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. Klicken Sie in eine vollständige Implementierung würde diese Informationen erhalten Sie in der sprachdokumentation, aber in diesem Beispiel werden fest programmierte.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Zur Implementierung der Signaturhilfe Signaturen und Parameter  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `SignatureHelpSource`.  
  
2.  Fügen Sie die folgenden Importe hinzu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3.  Fügen Sie eine Klasse, die mit dem Namen `TestParameter` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4.  Fügen Sie einen Konstruktor, der alle Eigenschaften festlegt.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5.  Fügen Sie die Eigenschaften der <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6.  Fügen Sie eine Klasse, die mit dem Namen `TestSignature` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7.  Fügen Sie private Felder hinzu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8.  Fügen Sie einen Konstruktor, der die Felder festgelegt und abonniert das <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Deklarieren Sie eine `CurrentParameterChanged` Ereignis. Dieses Ereignis wird ausgelöst, wenn der Benutzer einer der Parameter in der Signatur ausfüllt.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Eigenschaft, sodass die It löst die `CurrentParameterChanged` Ereignis aus, wenn der Eigenschaftswert geändert wird.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Fügen Sie eine Methode, die löst die `CurrentParameterChanged` Ereignis.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Fügen Sie eine Methode, die den aktuellen Parameter berechnet anhand der Anzahl von Kommas in der <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> auf die Anzahl von Kommas in der Signatur.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Hinzufügen eines ereignishandlers für das <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> -Ereignis, das Aufrufen der `ComputeCurrentParameter()` Methode.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Implementiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>-Eigenschaft. Diese Eigenschaft enthält eine <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , entspricht der Textabschnitt im Puffer, der die Signatur angewendet wird.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Implementieren Sie die anderen Parameter an.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementieren die Quelle der Signatur-Hilfe  
 Die Signaturhilfe-Quelle ist der Satz von Signaturen für die Sie Informationen bereitstellen.  
  
#### <a name="to-implement-the-signature-help-source"></a>Um die Signaturhilfe Quelle zu implementieren.  
  
1.  Fügen Sie eine Klasse, die mit dem Namen `TestSignatureHelpSource` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2.  Fügen Sie einen Verweis auf den Textpuffer.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3.  Fügen Sie einen Konstruktor, der dem Textpuffer und der Quellenanbieter Signaturhilfe festlegt.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>-Methode. In diesem Beispiel werden fest programmierte, aber in eine vollständige Implementierung würden Sie erhalten diese Informationen in der sprachdokumentation.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5.  Die Hilfsmethode `CreateSignature()` wird nur zur Veranschaulichung bereitgestellt.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>-Methode. In diesem Beispiel sind nur zwei Signaturen, von die jede zwei Parameter verfügt. Diese Methode ist daher nicht erforderlich. In eine größere Implementierung, die in der Quelle mit mehr als eine Signatur-Hilfe verfügbar ist. wird diese Methode verwendet, zu entscheiden, ob die mit der höchsten Priorität Signaturhilfe Quelle eine übereinstimmende Signatur bereitgestellt werden kann. Wenn dies nicht möglich, die Methode gibt null zurück, und die Quelle weiter – mit der höchsten Priorität wird aufgefordert, eine Übereinstimmung anzugeben.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7.  Implementieren Sie die Dispose()-Methode:  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementieren die Quelle der Signaturhilfeanbieter  
 Der Quellenanbieter Signatur-Hilfe ist für den Export von der Komponente Managed Extensibility Framework (MEF) und für die Instanziierung der Signaturhilfe Quelle verantwortlich.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Zum Implementieren des Quellenanbieter Signaturhilfe  
  
1.  Fügen Sie eine Klasse, die mit dem Namen `TestSignatureHelpSourceProvider` , implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text", und ein <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von vor = "Default".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2.  Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> durch Instanziieren der `TestSignatureHelpSource`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Die Befehlshandler implementieren  
 Signaturhilfe wird in der Regel ausgelöst, indem eine (Zeichen und "verworfen" durch eine) Zeichen. Sie können diese Tastatureingaben behandeln, durch die Implementierung einer <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , damit sie eine Sitzung Signaturhilfe ausgelöst, empfängt eine (Zeichen vor dem Namen einer bekannten Methode und schließt die Sitzung, die beim Empfang einer) Zeichen.  
  
#### <a name="to-implement-the-command-handler"></a>Die Befehlshandler implementieren.  
  
1.  Fügen Sie eine Klasse, die mit dem Namen `TestSignatureHelpCommand` implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2.  Fügen Sie private Felder für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> -Adapter (mit der Sie die Kette der Befehlshandler die Befehlshandler hinzufügen zu können), die Textansicht, die Signaturhilfe Broker und die Sitzung eine <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, und die nächsten <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3.  Fügen Sie einen Konstruktor aus, um diese Felder zu initialisieren und die Befehlsketten-Filter der Befehlsfilter hinzu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode, um die Signaturhilfe Sitzung auslösen, wenn der Befehlsfilter empfängt, eine (Zeichen nach der die bekannte Methodennamen und die Sitzung zu schließen, empfängt eine) Zeichen, während die Sitzung noch aktiv ist. In jedem Fall wird der Befehl weitergeleitet.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, sodass die It immer den Befehl weiterleitet.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementieren der Signaturhilfeanbieter-Befehl  
 Sie können den Signatur-Hilfe-Befehl angeben, durch die Implementierung der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> die Befehlshandler instanziiert, wenn die Textansicht erstellt wird.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Den Anbieter für die Signaturhilfe Befehl implementiert  
  
1.  Fügen Sie eine Klasse, die mit dem Namen `TestSignatureHelpController` implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> und exportieren Sie sie mit der <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, und <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2.  Importieren der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (zum Abrufen der <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, bestimmte die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt), wird die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (verwendet das aktuelle Wort gefunden), und die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (um die Sitzung Signaturhilfe auszulösen).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Methode durch die Instanziierung der `TestSignatureCommandHandler`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe SignatureHelpTest, und führen Sie es in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Zum Erstellen und Testen der Lösung SignatureHelpTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei und geben Sie Text an, der das Wort "hinzufügen" sowie eine öffnende Klammer ein.  
  
4.  Nachdem Sie die öffnende Klammer eingeben, sollte eine QuickInfo, die zeigt eine Liste mit den zwei Signaturen für die `add()` Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

