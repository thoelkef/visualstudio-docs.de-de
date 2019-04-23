---
title: Optionen, Text-Editor, C#, Erweitert | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed1260d414c21d40bd0dc57f885cf5996594b7d6
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664546"
---
# <a name="options-text-editor-c-advanced"></a>Optionen, Text-Editor, C#, Erweitert
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mithilfe dieses Dialogfelds können Sie die Einstellungen für Formatierungen mithilfe des Editors, Coderefactoring und XML-Dokumentationskommentaren verändern. Klicken Sie zum Öffnen dieses Dialogfelds im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Text-Editor**, erweitern Sie **C#**, und klicken Sie dann auf **Erweitert**.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="outlining"></a>Gliedern  
 Beim Öffnen von Dateien in Gliederungsmodus wechseln  
 Wenn diese Option aktiviert ist, wird die Codedatei automatisch gegliedert. Hierdurch werden reduzierbare Codeblöcke erstellt. Beim ersten Öffnen einer Datei werden #Region-Blöcke und inaktive Codeblöcke reduziert.  
  
## <a name="editor-help"></a>Editor-Hilfe  
 Fehler im Editor unterstreichen  
 Identifiziert Buildfehler im Code. Wenn diese Option aktiviert ist, werden wellenförmige Unterstreichungen in Farben angezeigt, die eine bestimmte Bedeutung haben:  
  
- Analysefehler werden rot dargestellt.  
  
- Buildfehler werden blau dargestellt.  
  
- Buildwarnungen werden grün dargestellt.  
  
- Ungültige Bearbeitungen in [Bearbeiten und Fortfahren](../../debugger/edit-and-continue.md) werden violett dargestellt.  
  
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
 Bei Auswahl dieser Option werden die \<summary>-Start- und Endtags automatisch bei XML-Dokumentationskommentaren eingefügt, wenn Sie die ///-Kommentareinführung eingegeben haben. Weitere Informationen über die XML-Dokumentation finden Sie unter [XML-Dokumentationskommentare](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).  
  
## <a name="implement-interface"></a>Schnittstelle implementieren  
 Generierten Code mit #region umschließen  
 Fügt einen #region \<*Schnittstellenname*>-Member um die Methoden ein, wenn „Schnittstelle implementieren“ oder „Schnittstelle explizit implementieren“ ausgewählt ist.  
  
## <a name="organize-usings"></a>Using-Direktiven organisieren  
 System-Direktiven beim Sortieren von Using-Direktiven an erster Stelle platzieren  
 Wenn diese Option aktiviert ist, werden using-Direktiven des `System` vor anderen using-Direktiven angezeigt. Weitere Informationen finden Sie unter [Sortieren von using-Anweisungen](../../misc/sort-usings.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Dokumentationskommentare](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [Festlegen von sprachspezifischen Editor-Optionen](../../ide/reference/setting-language-specific-editor-options.md)   
 [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)
