---
title: "Exemplarische Vorgehensweise: Anzeigen von Signaturhilfe | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] neue - Signatur Hilfe/ParameterInfo"
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Anzeigen von Signaturhilfe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Signaturhilfe \(auch bekannt als *ParameterInfo*\) die Signatur einer Methode in einer QuickInfo angezeigt, wenn ein Benutzer das Zeichen für den Parameter Liste \(in der Regel eine öffnende Klammer\) eingibt. Wie ein Parameter und Parametertrennzeichen \(normalerweise ein Komma\) eingegeben werden, wird die QuickInfo aktualisiert, und den nächsten Parameter in Fettdruck angezeigt. Signatur können Sie im Kontext eines Dienstes Sprache definieren können eigene Erweiterung und Inhalt Dateinamentyp definieren und Anzeigen von Signaturhilfe für nur diesen Typ oder Signatur können Sie für einen vorhandenen Inhaltstyp \(z. B. "Text"\) anzeigen. In dieser exemplarischen Vorgehensweise veranschaulicht die Signatur für den Inhaltstyp "Text" angezeigt.  
  
 Signaturhilfe wird in der Regel ausgelöst, durch Eingabe von einem bestimmten Zeichen, z. B. "\(" \(öffnenden Klammer\), und geben Sie ein anderes Zeichen, z. B. geschlossen "\)" \(schließende Klammer\). IntelliSense\-Funktionen, die ausgelöst werden, indem Sie ein Zeichen eingeben können mithilfe von einen Befehlshandler für die Tastatureingaben implementiert werden \(die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle\) und ein Handler\-Anbieter, implementiert die <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Schnittstelle. Implementieren Sie zum Erstellen der Signatur\-Datenquelle, die die Liste der Signaturen Signaturhilfe teilnehmen, die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> Schnittstelle und ein Quellenanbieter, implementiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> Schnittstelle. Die Anbieter sind Managed Extensibility Framework \(MEF\)\-Komponenten und verantwortlich für die Quell\- und Controller\-Klassen exportieren und Importieren von Services und Broker, z. B. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, können Sie in den Textpuffer navigieren und die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, dadurch wird die Sitzung Signaturhilfe ausgelöst.  
  
 In dieser exemplarischen Vorgehensweise wird die Signatur für einen hartcodierten Satz von Bezeichnern implementieren veranschaulicht. In vollständige Implementierungen ist die Sprache für die Bereitstellung dieses Inhalts verantwortlich.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines MEF\-Projekts  
  
#### So erstellen Sie ein MEF\-Projekt  
  
1.  Erstellen Sie ein C\#\-VSIX\-Projekt. \(In der **Neues Projekt** Dialogfeld **Visual c\# \/ Erweiterbarkeit**, dann **VSIX\-Projekt**.\) Nennen Sie die Projektmappe `SignatureHelpTest`.  
  
2.  Fügen Sie dem Projekt eine Classifier\-Editor\-Elementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einer Elementvorlage\-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
4.  Fügen Sie dem Projekt die folgenden Verweise hinzu, und stellen Sie sicher, dass **CopyLocal** Wert `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## Implementieren die Signatur Signaturen und Parameter\-Hilfe  
 Die Quelle Signaturhilfe basiert auf Signaturen, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, von denen jede enthält Parameter, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. Bei einer vollständigen Implementierung würde diese Informationen der Language\-Dokumentation entnommen werden, aber in diesem Beispiel werden fest programmierte.  
  
#### Implementieren Sie die Signatur Signaturen und Parameter  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie es `SignatureHelpSource`.  
  
2.  Fügen Sie die folgenden Importe hinzu.  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-cs[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Fügen Sie eine Klasse mit dem Namen `TestParameter` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-cs[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Fügen Sie einen Konstruktor, der alle Eigenschaften festgelegt.  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-cs[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Fügen Sie die Eigenschaften der <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-cs[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Fügen Sie eine Klasse mit dem Namen `TestSignature` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-cs[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Fügen Sie private Felder hinzu.  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-cs[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Fügen Sie einen Konstruktor, der die Felder festgelegt und abonniert das <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis.  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-cs[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Deklarieren Sie eine `CurrentParameterChanged` Ereignis. Dieses Ereignis wird ausgelöst, wenn der Benutzer einen der Parameter in der Signatur ausfüllt.  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-cs[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Eigenschaft so, dass die It\-löst das `CurrentParameterChanged` \-Ereignis, wenn der Eigenschaftswert geändert wird.  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-cs[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Fügen Sie eine Methode, die löst die `CurrentParameterChanged` Ereignis.  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-cs[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Fügen Sie eine Methode, die den aktuellen Parameter berechnet durch Vergleich der Anzahl von Kommas in der <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> auf die Anzahl von Kommas in der Signatur.  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-cs[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. Fügen Sie einen Ereignishandler für das <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> \-Ereignis, das Aufrufe der `ComputeCurrentParameter()` Methode.  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-cs[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Implementiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>\-Eigenschaft. Diese Eigenschaft enthält eine <xref:Microsoft.VisualStudio.Text.ITrackingSpan> entspricht der Textumfang in den Puffer, der die Signatur angewendet wird.  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-cs[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Implementieren Sie die anderen Parameter.  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-cs[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## Implementieren die Quelle der Signatur  
 Die Signatur\-Quelle ist der Satz von Signaturen für die Informationen bereitgestellt werden.  
  
#### Die Quelle Signaturhilfe implementieren  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestSignatureHelpSource` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-cs[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Fügen Sie einen Verweis auf den Textpuffer.  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-cs[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Fügen Sie einen Konstruktor, der Textpuffer und Quellenanbieter Signaturhilfe festlegt.  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-cs[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>\-Methode. In diesem Beispiel werden fest programmierte, aber in einer vollständigen Implementierung würde Sie erhalten diese Informationen aus der Language\-Dokumentation.  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-cs[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  Die Hilfsmethode `CreateSignature()` dient nur zur Veranschaulichung.  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-cs[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>\-Methode. In diesem Beispiel werden nur zwei Signaturen, von die jede über zwei Parameter verfügt. Diese Methode ist daher nicht erforderlich. In eine vollständige Implementierung, die in der Quelle für mehr als eine Signatur verfügbar ist wird diese Methode verwendet, zu entscheiden, ob die höchste Priorität Signaturhilfe Quelle eine übereinstimmende Signatur angeben kann. Ist es nicht möglich, die Methode gibt null zurück, und Quelle weiter höchste Priorität wird aufgefordert, eine Übereinstimmung anzugeben.  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-cs[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Implementieren Sie die Dispose\(\)\-Methode:  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-cs[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## Implementieren den Signatur Hilfe Quellenanbieter  
 Quellenanbieter Signaturhilfe ist verantwortlich für den Export von der Komponente Managed Extensibility Framework \(MEF\) und für die Instanziierung der Signatur\-Quelle.  
  
#### Implementieren den Signaturhilfe Quellenanbieter  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestSignatureHelpSourceProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute>,  <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text", und ein <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von vor \= "Default".  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-cs[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> durch Instanziieren der `TestSignatureHelpSource`.  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-cs[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## Implementieren den Befehlshandler  
 Signaturhilfe wird in der Regel ausgelöst, durch eine \(Zeichen\- und ausgeblendete durch eine\) Zeichen. Sie können diese Tastatureingaben behandeln, durch die Implementierung einer <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> damit er eine Sitzung Signaturhilfe löst empfängt eine \(Zeichen vorangestellt ist ein bekannter Methodenname und schließt die Sitzung empfängt eine\) Zeichen.  
  
#### Den Befehlshandler implementieren  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestSignatureHelpCommand` implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-cs[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  Fügen Sie private Felder für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> \-Adapter \(letztere Befehlshandler Befehlskette Handler hinzufügen\) der Textansicht, Signaturhilfe Broker und \-Sitzung eine <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, und der nächsten <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-cs[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Fügen Sie einen Konstruktor, um diese Felder zu initialisieren und die Befehlskette Filter den Befehlsfilter hinzu.  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-cs[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode, um die Sitzung Signaturhilfe Auslösen der Befehlsfilter erhält eine \(Zeichen, nach der die bekannten Methodennamen und die Sitzung zu schließen, empfängt eine\) Zeichen, während die Sitzung noch aktiv ist. In jedem Fall wird der Befehl weitergeleitet.  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-cs[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, sodass die It immer mit dem Befehl weitergeleitet.  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-cs[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## Implementieren des Signatur Help\-Befehl\-Anbieters  
 Sie können den Befehl Signaturhilfe bereitstellen, durch die Implementierung der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Befehlshandler instanziiert, wenn die Textansicht erstellt wird.  
  
#### Der Befehl Signaturhilfe Anbieter implementieren  
  
1.  Fügen Sie eine Klasse mit dem Namen `TestSignatureHelpController` implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> und exportieren Sie es mit der <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, und <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-cs[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  Importieren der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> \(zum Abrufen der <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, wenn die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt\), die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> \(verwendet die aktuelle Wort suchen\), und die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> \(für die Sitzung Signaturhilfe ausgelöst\).  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-cs[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Methode durch die Instanziierung der `TestSignatureCommandHandler`.  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-cs[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe SignatureHelpTest, und führen Sie es in der experimentellen Instanz.  
  
#### So erstellen und Testen der Lösung SignatureHelpTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei und geben Sie ein Text mit dem Wort "add" sowie eine öffnende Klammer ein.  
  
4.  Nachdem Sie die öffnende Klammer eingeben, sollte eine QuickInfo, die eine der zwei Signaturen für Liste die `add()` Methode.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit Erweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)