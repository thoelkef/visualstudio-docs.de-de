---
title: 'Exemplarische Vorgehensweise: Anzeigen der Signatur Hilfe | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 280b5b517089ad9e5b38cb00dc9b14c68253d1e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202045"
---
# <a name="walkthrough-displaying-signature-help"></a>Exemplarische Vorgehensweise: Anzeigen der Signaturhilfe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit der Signatur Hilfe (auch als *Parameter Info*bezeichnet) wird die Signatur einer Methode in einer QuickInfo angezeigt, wenn ein Benutzer das Parameter Listen-Startzeichen (in der Regel eine öffnende Klammer) eingibt. Wenn ein Parameter und Parameter Trennzeichen (in der Regel ein Komma) eingegeben werden, wird die QuickInfo aktualisiert, um den nächsten Parameter fett anzuzeigen. Sie können die Signatur Hilfe im Kontext eines sprach Dienstanbieter definieren, oder Sie können eine eigene Dateinamenerweiterung und einen Inhaltstyp definieren und die Signatur Hilfe für diesen Typ anzeigen, oder Sie können die Signatur Hilfe für einen vorhandenen Inhaltstyp anzeigen (z. b. "Text"). In dieser exemplarischen Vorgehensweise wird gezeigt, wie die Signatur Hilfe für den Inhaltstyp "Text" angezeigt wird.  
  
 Die Signatur Hilfe wird in der Regel durch Eingabe eines bestimmten Zeichens ausgelöst, z. b. "(" (öffnende Klammer), und durch Eingabe eines anderen Zeichens, z. b. ")" (schließende Klammer). IntelliSense-Funktionen, die durch Eingabe eines Zeichens ausgelöst werden, können mithilfe eines Befehls Handlers für die Tastatureingaben (die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle) und eines handleranbieters implementiert werden, der die- <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Schnittstelle implementiert. Um die Signatur Hilfe Quelle zu erstellen, die die Liste der Signaturen ist, die an der Signatur Hilfe beteiligt sind, implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> -Schnittstelle und einen Quell Anbieter, der die- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> Schnittstelle implementiert. Die Anbieter sind Managed Extensibility Framework Komponenten Komponenten (MEF), die für den Export der Quell-und Controller Klassen und das Importieren von Diensten und Brokern zuständig sind, z. b. das-Element, mit dem <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> Sie im Text Puffer navigieren können, und das-Element <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> , das die Signatur Hilfe Sitzung auslöst.  
  
 In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die Signatur Hilfe für einen hart codierten Satz von bezeichern implementieren. Bei vollständigen Implementierungen ist die Sprache für die Bereitstellung dieses Inhalts verantwortlich.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit**und dann **VSIX-Projekt**aus.) Benennen Sie die Projekt Mappe `SignatureHelpTest` .  
  
2. Fügen Sie dem Projekt eine Editor-Klassifizierungs Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Löschen Sie die vorhandenen Klassendateien.  
  
4. Fügen Sie dem Projekt die folgenden Verweise hinzu, und stellen Sie sicher, dass **CopyLocal** auf festgelegt ist `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft. VisualStudio. Shell. 14,0  
  
     Microsoft. VisualStudio. Text Manager. Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementieren von Signaturen und Parametern der Signatur Hilfe  
 Die Signatur Hilfe Quelle basiert auf Signaturen, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , die jeweils Parameter enthalten, die implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . In einer vollständigen Implementierung werden diese Informationen aus der Sprachdokumentation abgerufen, aber in diesem Beispiel sind die Signaturen hart codiert.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>So implementieren Sie Signaturen und Parameter der Signatur Hilfe  
  
1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `SignatureHelpSource`.  
  
2. Fügen Sie die folgenden Importe hinzu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3. Fügen Sie eine Klasse mit dem Namen hinzu `TestParameter` , die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4. Fügen Sie einen Konstruktor hinzu, der alle Eigenschaften festlegt.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5. Fügen Sie die Eigenschaften von hinzu <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6. Fügen Sie eine Klasse mit dem Namen hinzu `TestSignature` , die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7. Fügen Sie einige private Felder hinzu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8. Fügen Sie einen Konstruktor hinzu, der die Felder festlegt und das-Ereignis abonniert <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Deklarieren Sie ein- `CurrentParameterChanged` Ereignis. Dieses Ereignis wird ausgelöst, wenn der Benutzer einen der Parameter in der Signatur ausfüllt.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Eigenschaft, sodass das- `CurrentParameterChanged` Ereignis ausgelöst wird, wenn der-Eigenschafts Wert geändert wird.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Fügen Sie eine Methode hinzu, die das- `CurrentParameterChanged` Ereignis auslöst.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Fügen Sie eine Methode hinzu, die den aktuellen Parameter berechnet, indem Sie die Anzahl von Kommas in der <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> mit der Anzahl von Kommas in der Signatur vergleichen.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Fügen Sie einen Ereignishandler für das- <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis hinzu, das die- `ComputeCurrentParameter()` Methode aufruft.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Implementiert die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>-Eigenschaft. Diese Eigenschaft enthält ein-Objekt <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , das dem Textabschnitt im Puffer entspricht, für den die Signatur gilt.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Implementieren Sie die anderen Parameter.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementieren der Signatur Hilfe Quelle  
 Die Signatur Hilfe Quelle ist der Satz von Signaturen, für den Sie Informationen bereitstellen.  
  
#### <a name="to-implement-the-signature-help-source"></a>So implementieren Sie die Signatur Hilfe Quelle  
  
1. Fügen Sie eine Klasse mit dem Namen hinzu `TestSignatureHelpSource` , die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2. Fügen Sie einen Verweis auf den Text Puffer hinzu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3. Fügen Sie einen Konstruktor hinzu, mit dem der Text Puffer und der Signatur Hilfe Quellen-Anbieter festgelegt werden.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>-Methode. In diesem Beispiel sind die Signaturen hart codiert, aber in einer vollständigen Implementierung würden Sie diese Informationen aus der Sprachdokumentation erhalten.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5. Die-Hilfsmethode `CreateSignature()` wird nur zur Veranschaulichung bereitgestellt.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>-Methode. In diesem Beispiel gibt es nur zwei Signaturen, von denen jede über zwei Parameter verfügt. Daher ist diese Methode nicht erforderlich. Bei einer umfassenderen Implementierung, bei der mehr als eine Signatur Hilfe Quelle verfügbar ist, wird diese Methode verwendet, um zu entscheiden, ob die Signatur Hilfe Quelle mit der höchsten Priorität eine passende Signatur bereitstellen kann. Wenn dies nicht möglich ist, gibt die Methode NULL zurück, und die Quelle mit der höchsten Priorität wird aufgefordert, eine Entsprechung bereitzustellen.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7. Implementieren Sie die Methode "verwerfen ()":  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementieren des Signatur Hilfe Quellen-Anbieters  
 Der Signatur Hilfe Quellen-Anbieter ist für den Export des Komponenten Teils der Managed Extensibility Framework (MEF) und zum Instanziieren der Signatur Hilfe Quelle verantwortlich.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>So implementieren Sie den Signatur Hilfe Quellen-Anbieter  
  
1. Fügen Sie eine Klasse mit dem Namen hinzu, `TestSignatureHelpSourceProvider` die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> , und exportieren Sie Sie mit <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "Text" und einem <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von vor = "Default".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2. Implementieren Sie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> durch Instanziieren von `TestSignatureHelpSource` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Implementieren des Befehls Handlers  
 Die Signatur Hilfe wird in der Regel durch ein-Zeichen (Zeichen und verwerfen durch) ausgelöst. Sie können diese Tastatureingaben behandeln, indem Sie einen implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , sodass er eine Signatur Hilfe Sitzung auslöst, wenn er ein-Zeichen empfängt (gefolgt von einem bekannten Methodennamen), und die Sitzung beim Empfang eines-Zeichens verschließt.  
  
#### <a name="to-implement-the-command-handler"></a>So implementieren Sie den Befehls Handler  
  
1. Fügen Sie eine Klasse mit dem Namen hinzu `TestSignatureHelpCommand` , die implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2. Fügen Sie private Felder für den Adapter hinzu (mit dem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Sie den Befehls Handler der Kette von Befehls Handlern hinzufügen können), die Textansicht, die Signatur Hilfe Broker und die Sitzung, eine <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> und die nächste <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3. Fügen Sie einen Konstruktor hinzu, um diese Felder zu initialisieren und der Kette von Befehls Filtern den Befehls Filter hinzuzufügen.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4. Implementieren Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode, um die Signatur Hilfe Sitzung aufzurufende, wenn der Befehls Filter ein (Zeichen nach einem der bekannten Methodennamen empfängt und die Sitzung beim Empfang eines Zeichens), während die Sitzung noch aktiv ist. In jedem Fall wird der Befehl weitergeleitet.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5. Implementieren Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, sodass Sie den Befehl immer weiterleitet.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementieren des Signatur Hilfe-Befehls Anbieters  
 Sie können den Signatur Hilfe Befehl bereitstellen, indem Sie implementieren <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , um den Befehls Handler zu instanziieren, wenn die Textansicht erstellt wird.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>So implementieren Sie den Signatur Hilfe-Befehls Anbieter  
  
1. Fügen Sie eine Klasse `TestSignatureHelpController` mit dem Namen hinzu, die implementiert, <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> und exportieren Sie Sie mit <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> und <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2. Importieren Sie das (zum Abrufen des- <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> Objekts mit dem angegebenen- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt), das <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> -Objekt (das zum Suchen nach dem aktuellen Wort verwendet wird) und das-Objekt <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (zum auslöst der Signatur Hilfe Sitzung).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3. Implementieren Sie die- <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Methode, indem Sie die instanziieren `TestSignatureCommandHandler` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projekt Mappe signaturehelptest, und führen Sie Sie in der experimentellen Instanz aus.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>So erstellen und testen Sie die Projekt Mappe signaturehelptest  
  
1. Erstellen Sie die Projektmappe.  
  
2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der das Wort "Add" sowie eine öffnende Klammer enthält.  
  
4. Nachdem Sie die öffnende Klammer eingefügt haben, sollte eine QuickInfo angezeigt werden, in der eine Liste der beiden Signaturen für die Methode angezeigt wird `add()` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
