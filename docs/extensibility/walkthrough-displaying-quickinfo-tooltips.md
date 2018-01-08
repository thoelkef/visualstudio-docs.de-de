---
title: 'Exemplarische Vorgehensweise: Anzeigen von QuickInfos | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9cd3e9d5e10e6946b4cae8ce02a5a39511e4baaf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Exemplarische Vorgehensweise: Anzeigen von QuickInfos
QuickInfo ist eine IntelliSense-Funktion, die Methodensignaturen anzeigt und Beschreibungen, wenn ein Benutzer den Mauszeiger über einen Methodennamen. Sie können die Sprache basierende Funktionen wie z. B. QuickInfo implementieren, indem definieren die Bezeichner für die Sie QuickInfo-Beschreibungen bereitstellen möchten, und klicken Sie dann Erstellen einer QuickInfo in dem den Inhalt angezeigt. Sie können die QuickInfo im Kontext eines Diensts Sprache definieren können Sie definieren Sie eine eigene Erweiterung und Inhalt Dateityp von Name und der QuickInfo für nur dieses Typs angezeigt oder können Sie die QuickInfo anzeigen, für einen vorhandenen Inhaltstyp (z. B. "Text"). Diese exemplarischen Vorgehensweise beim Anzeigen von QuickInfo für den Inhaltstyp "Text".  
  
 Das QuickInfo-Beispiel in dieser exemplarischen Vorgehensweise werden die QuickInfos angezeigt, wenn ein Benutzer den Zeiger über einen Methodennamen richtet. Dieser Entwurf erfordert, dass Sie diese vier Schnittstellen implementieren:  
  
-   Source-Schnittstelle  
  
-   Source-Provider-Schnittstelle  
  
-   Controller-Schnittstelle  
  
-   Controller-Provider-Schnittstelle  
  
 Die Quell- und Controller-Anbieter sind Komponenten des Managed Extensibility Framework (MEF) und sind verantwortlich für die Quell- und Controller-Klassen exportieren und importieren und handelt, z. B. die <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, der den QuickInfo-Text erstellt Puffer, und die <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, die Trigger der QuickInfo-Sitzungs.  
  
 In diesem Beispiel wird die QuickInfo-Quelle verwendet eine hartcodierten Liste der Methodennamen und Beschreibungen, aber vollständige Implementierungen der Sprachdienst und in der sprachdokumentation sind dafür verantwortlich, dass der Inhalt.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekts**.) Nennen Sie die Projektmappe `QuickInfoTest`.  
  
2.  Dem Projekt eine Elementvorlage Editor Klassifizierer hinzugefügt. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementieren die QuickInfo-Quelle  
 Die QuickInfo-Quelle ist verantwortlich für das Sammeln der Satz von IDs und Beschreibungen und den Inhalt in den QuickInfo-Text-Puffer hinzufügen, wenn einer der Bezeichner gefunden wird. In diesem Beispiel werden die Bezeichner und deren Beschreibungen nur in der Quelle Konstruktor hinzugefügt.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Implementieren Sie die QuickInfo-Quelle  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestQuickInfoSource`.  
  
2.  Fügen Sie einen Verweis auf Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Fügen Sie die folgenden Importe hinzu.  
  
     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Deklarieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>, und nennen Sie sie `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Hinzufügen von Feldern für die QuickInfo Quellenanbieter, Textpuffer und einen Satz von Methodennamen und Methodensignaturen. In diesem Beispiel im initialisiert den Methodennamen und Signaturen der `TestQuickInfoSource` Konstruktor.  
  
     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Fügen Sie einen Konstruktor, der der Quellenanbieter QuickInfo und den Textpuffer festlegt und füllt den Satz von Namen von Methoden und Methodensignaturen und Beschreibungen.  
  
     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>-Methode. In diesem Beispiel sucht die Methode das aktuelle Wort oder der vorherigen Wort, wenn der Cursor am Ende einer Zeile oder einen Textpuffer ist. Wenn das Wort eine der Methode handelt, wird die Beschreibung für dieses Methodennamens der QuickInfo-Inhalt hinzugefügt.  
  
     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  Sie müssen auch eine Dispose()-Methode implementieren, da <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementiert <xref:System.IDisposable>:  
  
     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementieren eines Anbieters für die QuickInfo-Quelle  
 Der Anbieter der QuickInfo Quelle dient in erster Linie zum Exportieren selbst als Teil der MEF-Komponente und die QuickInfo-Quelle zu instanziieren. Da es sich um eine MEF-Komponente handelt, können sie andere MEF-Komponententeilen importieren.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Implementieren Sie eine QuickInfo Quellenanbieter  
  
1.  Deklarieren Sie eine QuickInfo Quellenanbieter mit dem Namen `TestQuickInfoSourceProvider` , implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>, und exportieren Sie sie mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "QuickInfo QuickInfo Quelle" eine <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> der Before = "Default", und ein <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text".  
  
     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Importieren von zwei Editor Dienste <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> und <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, als Eigenschaften des `TestQuickInfoSourceProvider`.  
  
     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> zurückzugebenden ein neues `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementieren eine QuickInfo-Controller  
 QuickInfo-Controller ermitteln, wenn die QuickInfo angezeigt werden soll. In diesem Beispiel wird die QuickInfo angezeigt, wenn der Mauszeiger über ein Wort befindet, die die Methodennamen entspricht. Der QuickInfo-Controller implementiert einen Mausereignishandler gezeigt wird, der eine QuickInfo-Sitzung auslöst.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Implementieren Sie einen QuickInfo-controller  
  
1.  Deklarieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>, und nennen Sie sie `TestQuickInfoController`.  
  
     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Fügen Sie private Felder für Textansicht, die Textpuffer in der Textansicht, die QuickInfo-Sitzung und die QuickInfo-Controller-Anbieter dargestellt.  
  
     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Fügen Sie einen Konstruktor, der die Felder festgelegt und fügt der Maus gezeigt wird-Ereignishandler hinzu.  
  
     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Fügen Sie den Mausereignishandler gezeigt wird, der die QuickInfo-Sitzung auslöst.  
  
     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> Methode, sodass die It den Ereignishandler der Maus gezeigt wird entfernt, wenn der Controller von Textansicht getrennt wird.  
  
     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> Methode und die <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> Methode als leere Methoden für dieses Beispiel.  
  
     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementieren des Anbieters des QuickInfo-Controller  
 Der Anbieter des Controllers QuickInfo dient in erster Linie zum Exportieren selbst als Teil der MEF-Komponente und instanziieren Sie den QuickInfo-Controller. Da es sich um eine MEF-Komponente handelt, können sie andere MEF-Komponententeilen importieren.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Um die QuickInfo-Controller-Anbieter implementiert werden.  
  
1.  Deklarieren Sie eine Klasse mit dem Namen `TestQuickInfoControllerProvider` , implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>, und exportieren Sie sie mit einem <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "QuickInfo QuickInfo Controller" und eine <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text":  
  
     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Importieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> als Eigenschaft.  
  
     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> Methode durch Instanziierung des QuickInfo-Controllers.  
  
     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die QuickInfoTest-Projektmappe, und führen Sie sie in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>So erstellen und Testen der Lösung QuickInfoTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei und Typ Text, die die Wörter "hinzufügen" und "subtrahieren".  
  
4.  Bewegen Sie den Zeiger über einem Vorkommen von "hinzufügen". Die Signatur und die Beschreibung der `add` Methode sollte angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)