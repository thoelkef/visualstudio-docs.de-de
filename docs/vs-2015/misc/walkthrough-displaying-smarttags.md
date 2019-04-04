---
title: 'Exemplarische Vorgehensweise: Anzeigen von SmartTags | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: jillfra
ms.openlocfilehash: e918c8e83909bb5a04d27f72cb07c7135b00daa9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959304"
---
# <a name="walkthrough-displaying-smarttags"></a>Exemplarische Vorgehensweise: Anzeigen von SmartTags
Smarttags sind veraltet und wurden gegen Glühbirnen ausgetauscht. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Smarttags sind Tags für Text, die erweitert werden können, um eine Reihe von Aktionen anzuzeigen. Beispielsweise wird in einem Visual Basic- oder Visual C#-Projekt eine rote Linie unter einem Wort angezeigt, wenn Sie einen Bezeichner (z. B. Variablenname) umbenennen. Wenn Sie den Mauszeiger über die Unterstreichung bewegen, wird eine Schaltfläche in der Nähe des Zeigers angezeigt. Wenn Sie auf die Schaltfläche klicken, wird eine empfohlene Aktion angezeigt, z. B. **IsRead in IsReady umbenennen**. Wenn Sie auf die Aktion klicken, werden alle Verweise auf **IsRead** im Projekt in **IsReady**umbenannt.  
  
 Obwohl Smarttags Bestandteil der IntelliSense-Implementierung im Editor sind, können Sie Smarttags implementieren, indem Sie eine Unterklasse für <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> erstellen und dann die Schnittstellen <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> und <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> implementieren.  
  
> [!NOTE]
>  Andere Arten von Tags können auf ähnliche Weise implementiert werden.  
  
 Die folgende exemplarische Vorgehensweise zeigt, wie Sie ein Smarttag erstellen, die für das aktuelle Wort angezeigt wird, und verfügt über zwei empfohlene Aktionen: **In Großschreibung konvertieren** und **in Kleinbuchstaben umwandeln**.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1.  Erstellen Sie ein Editorklassifiziererprojekt. Nennen Sie die Projektmappe `SmartTagTest`.  
  
2.  Öffnen Sie im VSIX-Manifest-Editor die Datei "source.extension.vsixmanifest".  
  
3.  Stellen Sie sicher, dass der Abschnitt **Objekte** einen `Microsoft.VisualStudio.MefComponent` -Typ enthält, die **Quelle** auf `A project in current solution`und das **Projekt** auf SmartTagTest.dll festgelegt ist.  
  
4.  Speichern und schließen Sie die Datei "source.extension.vsixmanifest".  
  
5.  Fügen Sie den folgenden Verweis auf das Projekt hinzu, und legen Sie **CopyLocal** auf `false`fest:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6.  Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Implementieren eines Taggers für Smarttags  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>So implementieren Sie einen Tagger für Smarttags  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestSmartTag`.  
  
2.  Fügen Sie die folgenden Importe hinzu:  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3.  Fügen Sie eine Klasse namens `TestSmartTag` hinzu, die von <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> erbt.  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4.  Fügen Sie einen Konstruktor für diese Klasse hinzu, der den Basiskonstruktor mit einem <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> von <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> aufruft, wodurch der erste Buchstabe eines Worts mit einer blauen Linie unterstrichen wird. (Bei Verwendung von <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> wird der letzte Buchstabe des Worts rot unterstrichen.)  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5.  Fügen Sie eine Klasse mit dem Namen `TestSmartTagger` hinzu, die von <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> vom Typ `TestSmartTag` erbt und <xref:System.IDisposable> implementiert.  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6.  Fügen Sie der Taggerklasse die folgenden privaten Felder hinzu:  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7.  Fügen Sie einen Konstruktor hinzu, der die privaten Felder festlegt und das <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>-Ereignis abonniert.  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8.  Implementieren Sie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>, damit das Tag für das aktuelle Wort erstellt wird. (Mit dieser Methode wird auch die private Methode `GetSmartTagActions` aufgerufen, die zu einem späteren Zeitpunkt erläutert wird.)  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. Fügen Sie eine `GetSmartTagActions` -Methode hinzu, um die Smarttag-Aktionen einzurichten. Die Aktionen selbst werden in späteren Schritten implementiert.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Deklarieren Sie das `SmartTagsChanged` -Ereignis.  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Implementieren Sie den `OnLayoutChanged`-Ereignishandler, um das `TagsChanged`-Ereignis auszulösen, wodurch <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> aufgerufen wird.  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. Implementieren Sie die <xref:System.IDisposable.Dispose%2A>-Methode, damit das Abonnement des <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>-Ereignisses aufgehoben wird.  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Implementieren des Anbieters des Smarttag-Taggers  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>So implementieren Sie den Anbieter des Smarttag-Taggers  
  
1.  Fügen Sie eine Klasse namens `TestSmartTagTaggerProvider` hinzu, die von <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> erbt. Exportieren Sie sie mit dem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text", dem <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "Default" und dem <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2.  Importieren Sie <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> als Eigenschaft.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3.  Implementieren Sie die <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>-Methode.  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Implementieren von Smarttag-Aktionen  
  
#### <a name="to-implement-smart-tag-actions"></a>So implementieren Sie Smarttag-Aktionen  
  
1. Erstellen Sie zwei Klassen, die erste mit dem Namen `UpperCaseSmartTagAction` und die zweite mit dem Namen `LowerCaseSmartTagAction`. Beide Klassen implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
    [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
    [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
    [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
    [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
   Beide Klassen sind bis auf eine Ausnahme identisch: Die eine ruft <xref:System.String.ToUpper%2A> und die andere <xref:System.String.ToLower%2A> auf. In den folgenden Schritten wird nur die Klasse für die Umwandlung in Großbuchstaben behandelt; Sie müssen aber beide Klassen implementieren. Verwenden Sie diese Schritte als Muster für die Implementierung der Aktion zur Umwandlung in Kleinbuchstaben.  
  
2. Deklarieren Sie einen Satz privater Felder.  
  
    [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
    [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
3. Fügen Sie einen Konstruktor hinzu, der die Felder festlegt.  
  
    [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
    [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
4. Implementieren Sie die Eigenschaften wie folgt:  
  
    [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
    [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
5. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A>-Methode, indem Sie den Text im Bereich durch entsprechende Großbuchstaben ersetzen.  
  
    [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
    [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe "SmartTagTest", und führen Sie sie in der experimentellen Instanz aus.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>So erstellen Sie die Projektmappe "SmartTagTest" und testen den Code  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei, und geben Sie Text ein.  
  
     Unter dem ersten Buchstaben des ersten Worts im Text sollte eine blaue Linie angezeigt werden.  
  
4.  Bewegen Sie den Zeiger über die blaue Linie.  
  
     Neben dem Zeiger sollte eine Schaltfläche angezeigt werden.  
  
5.  Wenn Sie die Schaltfläche klicken, sollten zwei empfohlene Aktionen angezeigt: **In Großschreibung konvertieren** und **in Kleinbuchstaben umwandeln**. Wenn Sie auf die erste Aktion klicken, sollte der gesamte Text im aktuellen Wort in Großbuchstaben umgewandelt werden. Wenn Sie auf die zweite Aktion klicken, sollte der gesamte Text im aktuellen Wort in Kleinbuchstaben umgewandelt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)