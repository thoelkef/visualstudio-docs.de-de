---
title: 'Exemplarische Vorgehensweise: Anzeigen von Quick Infos für QuickInfo | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b349f0293071dfa30677b7558ca93985d16d55e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841079"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Exemplarische Vorgehensweise: Anzeigen von QuickInfos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

QuickInfo ist eine IntelliSense-Funktion, die Methoden Signaturen und Beschreibungen anzeigt, wenn ein Benutzer den Zeiger auf einen Methodennamen verschiebt. Sie können sprachbasierte Funktionen wie QuickInfo implementieren, indem Sie die Bezeichner definieren, für die QuickInfo-Beschreibungen bereitgestellt werden sollen, und dann eine QuickInfo erstellen, in der der Inhalt angezeigt werden soll. Sie können QuickInfo im Kontext eines sprach Dienstanbieter definieren, oder Sie können eine eigene Dateinamenerweiterung und einen Inhaltstyp definieren und die QuickInfo nur für diesen Typ anzeigen, oder Sie können QuickInfo für einen vorhandenen Inhaltstyp (z. b. "Text") anzeigen. In dieser exemplarischen Vorgehensweise wird gezeigt, wie QuickInfo für den Inhaltstyp "Text" angezeigt wird.  
  
 Im QuickInfo-Beispiel in dieser exemplarischen Vorgehensweise werden die Quick Infos angezeigt, wenn ein Benutzer den Mauszeiger über einen Methodennamen verschiebt. Dieser Entwurf erfordert, dass Sie diese vier Schnittstellen implementieren:  
  
- Quell Schnittstelle  
  
- Quell Anbieter Schnittstelle  
  
- Controller Schnittstelle  
  
- Schnittstelle des Controller Anbieters  
  
  Der Quell-und der Controller Anbieter sind Managed Extensibility Framework Komponenten (MEF-Komponenten), die für den Export der Quell-und Controller Klassen und das Importieren von Diensten und Brokern wie der <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , der den QuickInfo-Text Puffer erstellt, und der <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> , der die QuickInfo-Sitzung auslöst, verantwortlich sind.  
  
  In diesem Beispiel verwendet die QuickInfo-Quelle eine hart codierte Liste von Methodennamen und Beschreibungen, aber in vollständigen Implementierungen sind der Sprachdienst und die Sprachdokumentation für die Bereitstellung dieses Inhalts verantwortlich.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit**und dann **VSIX-Projekt**aus.) Benennen Sie die Projekt Mappe `QuickInfoTest` .  
  
2. Fügen Sie dem Projekt eine Editor-Klassifizierungs Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementieren der QuickInfo-Quelle  
 Die QuickInfo-Quelle ist dafür verantwortlich, den Satz von bezeichern und deren Beschreibungen zu erfassen und den Inhalt dem QuickInfo-Text Puffer hinzuzufügen, wenn einer der Bezeichner gefunden wird. In diesem Beispiel werden die Bezeichner und ihre Beschreibungen soeben im quellkonstruktor hinzugefügt.  
  
#### <a name="to-implement-the-quickinfo-source"></a>So implementieren Sie die QuickInfo-Quelle  
  
1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestQuickInfoSource`.  
  
2. Fügen Sie einen Verweis auf Microsoft. VisualStudio. Language. IntelliSense hinzu.  
  
3. Fügen Sie die folgenden Importe hinzu.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4. Deklarieren Sie eine Klasse <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> , die implementiert, und benennen Sie Sie `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5. Fügen Sie Felder für den QuickInfo-Quell Anbieter, den Text Puffer und einen Satz von Methodennamen und Methoden Signaturen hinzu. In diesem Beispiel werden die Methodennamen und Signaturen im- `TestQuickInfoSource` Konstruktor initialisiert.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6. Fügen Sie einen Konstruktor hinzu, der den QuickInfo-Quell Anbieter und den Text Puffer festlegt und den Satz von Methodennamen und Methoden Signaturen und Beschreibungen auffüllt.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>-Methode. In diesem Beispiel findet die-Methode das aktuelle Wort oder das vorherige Wort, wenn sich der Cursor am Ende einer Zeile oder eines Text Puffers befindet. Wenn es sich bei dem Wort um einen der Methodennamen handelt, wird dem QuickInfo-Inhalt die Beschreibung für den Namen der Methode hinzugefügt.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8. Sie müssen auch eine verwerfen ()-Methode implementieren, da Folgendes <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementiert <xref:System.IDisposable> :  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementieren eines QuickInfo-Quell Anbieters  
 Der Anbieter der QuickInfo-Quelle dient in erster Linie dazu, sich selbst als MEF-Komponenten Teil zu exportieren und die QuickInfo-Quelle zu instanziieren. Da es sich um einen MEF-Komponenten Teil handelt, können andere MEF-Komponenten Teile importiert werden.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>So implementieren Sie einen QuickInfo-Quell Anbieter  
  
1. Deklarieren Sie einen QuickInfo-Quell Anbieter mit dem Namen, der `TestQuickInfoSourceProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> , und exportieren Sie ihn mit <xref:Microsoft.VisualStudio.Utilities.NameAttribute> der QuickInfo-Quelle "QuickInfo", einer <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von "Before =" Default "und <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> " Text ".  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2. Importieren Sie zwei Editor Dienste <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> und <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> als Eigenschaften von `TestQuickInfoSourceProvider` .  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> Sie, um einen neuen zurückzugeben `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementieren eines QuickInfo-Controllers  
 QuickInfo-Controller legen fest, wann QuickInfo angezeigt werden soll. In diesem Beispiel wird QuickInfo angezeigt, wenn sich der Zeiger über einem Wort befindet, das einem der Methodennamen entspricht. Der QuickInfo-Controller implementiert einen Mauszeiger-Ereignishandler, der eine QuickInfo-Sitzung auslöst.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>So implementieren Sie einen QuickInfo-Controller  
  
1. Deklarieren Sie eine Klasse <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> , die implementiert, und benennen Sie Sie `TestQuickInfoController` .  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2. Fügen Sie private Felder für die Textansicht, die in der Textansicht dargestellten Text Puffer, die QuickInfo-Sitzung und den QuickInfo-Controller Anbieter hinzu.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3. Fügen Sie einen Konstruktor hinzu, der die Felder festlegt und den Mauszeiger-Bewegungs Ereignishandler hinzufügt.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4. Fügen Sie den Mauszeiger-Ereignishandler hinzu, der die QuickInfo-Sitzung auslöst.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> Methode, sodass der Mauszeiger-Ereignishandler entfernt wird, wenn der Controller von der Textansicht getrennt wird.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> -Methode und die- <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> Methode als leere Methoden für dieses Beispiel.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementieren des QuickInfo-Controller Anbieters  
 Der Anbieter des QuickInfo-Controllers dient in erster Linie dazu, sich selbst als MEF-Komponenten Teil zu exportieren und den QuickInfo-Controller zu instanziieren. Da es sich um einen MEF-Komponenten Teil handelt, können andere MEF-Komponenten Teile importiert werden.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>So implementieren Sie den QuickInfo-Controller Anbieter  
  
1. Deklarieren Sie eine Klasse mit dem Namen, `TestQuickInfoControllerProvider` die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> , und exportieren Sie Sie mit einem <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "QuickInfo-Controller" und einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "Text":  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2. Importieren Sie <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> als Eigenschaft.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> Methode, indem Sie den QuickInfo-Controller instanziieren.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die quickinfotest-Projekt Mappe, und führen Sie Sie in der experimentellen Instanz aus.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>So erstellen und testen Sie die QuickInfo Test-Projekt Mappe  
  
1. Erstellen Sie die Projektmappe.  
  
2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der die Wörter "Add" und "Subtract" enthält.  
  
4. Bewegen Sie den Mauszeiger über eines der Vorkommen von "Add". Die Signatur und die Beschreibung der `add` Methode sollten angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
