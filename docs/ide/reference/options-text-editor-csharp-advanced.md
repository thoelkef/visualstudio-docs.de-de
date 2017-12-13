---
title: Optionen, Text-Editor, C#, Erweitert | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb1c757ed5c266c74ca14e0b990528844bad0fb2
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2017
---
# <a name="options-text-editor-c-advanced"></a>Optionen, Text-Editor, C#, Erweitert
Mithilfe dieses Dialogfelds können Sie die Einstellungen für Formatierungen mithilfe des Editors, Coderefactoring und XML-Dokumentationskommentaren verändern. Klicken Sie zum Öffnen dieses Dialogfelds im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Text-Editor**, erweitern Sie **C#**, und klicken Sie dann auf **Erweitert**.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="outlining"></a>Gliedern  
 Beim Öffnen von Dateien in Gliederungsmodus wechseln  
 Wenn diese Option aktiviert ist, wird die Codedatei automatisch gegliedert. Hierdurch werden reduzierbare Codeblöcke erstellt. Beim ersten Öffnen einer Datei werden #Region-Blöcke und inaktive Codeblöcke reduziert.  
  
## <a name="editor-help"></a>Editor-Hilfe  
 Fehler im Editor unterstreichen  
 Identifiziert Buildfehler im Code. Wenn diese Option aktiviert ist, werden wellenförmige Unterstreichungen in Farben angezeigt, die eine bestimmte Bedeutung haben:  
  
-   Analysefehler werden rot dargestellt.  
  
-   Buildfehler werden blau dargestellt.  
  
-   Buildwarnungen werden grün dargestellt.  
  
-   Ungültige Bearbeitungen in [Bearbeiten und Fortfahren](../../debugger/edit-and-continue.md) werden violett dargestellt.  
  
Bewegen Sie den Zeiger über das unterstrichene Codesegment. Hierdurch wird eine QuickInfo mit Informationen über den Fehler angezeigt.  
  
Livesemantikfehler anzeigen  
Erkennt bestimmte Kompilierungsfehler ohne explizite Kompilierung, z.B. das Angeben und Verwenden eines unbekannten Typs oder Verweise auf eine unbekannte Eigenschaft.  
  
Verweise auf Symbole unter dem Cursor markieren  
Wenn sich der Cursor innerhalb eines Symbols befindet, oder wenn Sie auf ein Symbol klicken, werden alle Instanzen dieses Symbols in der Codedatei hervorgehoben.  
  
## <a name="refactoring"></a>Umgestaltung  
 Ergebnisse der Umgestaltung überprüfen  
 Zeigt das Dialogfeld **Ergebnisse der Verifizierung** an, wenn Sie versuchen, Code umzugestalten, der Buildfehler enthält, oder wenn die Umgestaltung dazu führen würde, dass ein Codeverweis sich an etwas anderes als die Originalbindung bindet.  
  
 Warnung bei Membern mit vom Compiler generierten Verweisen  
 Zeigt ein Warndialogfeld an, wenn Sie versuchen, einen Member umzugestalten, der mit dem Namen eines vom Compiler generierten Verweises übereinstimmt.  
  
## <a name="xml-documentation-comments"></a>XML-Dokumentationskommentare  
 XML-Dokumentationskommentare generieren für ///  
 Bei Auswahl dieser Option werden die \<summary>-Start- und Endtags automatisch bei XML-Dokumentationskommentaren eingefügt, wenn Sie die ///-Kommentareinführung eingegeben haben. Weitere Informationen über die XML-Dokumentation finden Sie unter [XML-Dokumentationskommentare](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).  
  
## <a name="implement-interface"></a>Schnittstelle implementieren  
 Generierten Code mit #region umschließen  
 Fügt einen #region \<*Schnittstellenname*>-Member um die Methoden ein, wenn „Schnittstelle implementieren“ oder „Schnittstelle explizit implementieren“ ausgewählt ist.  
  
## <a name="organize-usings"></a>Using-Direktiven organisieren  
 System-Direktiven beim Sortieren von Using-Direktiven an erster Stelle platzieren  
 Wenn diese Option aktiviert ist, werden using-Direktiven des `System` vor anderen using-Direktiven angezeigt. Weitere Informationen finden Sie unter „Using-Direktiven organisieren“ in [Visual C#-IntelliSense](../../ide/visual-csharp-intellisense.md#automatic-code-generation).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Dokumentationskommentare](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [Festlegen von sprachspezifischen Editor-Optionen](../../ide/reference/setting-language-specific-editor-options.md)   
 [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)