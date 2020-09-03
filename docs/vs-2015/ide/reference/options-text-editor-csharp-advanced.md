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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f2d11e78c2402a6541bc87748ed6ba348ba80fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662322"
---
# <a name="options-text-editor-c-advanced"></a>Optionen, Text-Editor, C#, Erweitert
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mithilfe dieses Dialogfelds können Sie die Einstellungen für Formatierungen mithilfe des Editors, Coderefactoring und XML-Dokumentationskommentaren verändern. Klicken Sie zum Öffnen dieses Dialogfelds im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Text-Editor**, erweitern Sie **C#**, und klicken Sie dann auf **Erweitert**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="outlining"></a>Gliedern
 In den Gliederungs Modus wechseln wenn Dateien geöffnet werden, wird die Codedatei automatisch umrissen, wodurch redusible Code Blöcke erstellt werden. Beim ersten Öffnen einer Datei werden #Region-Blöcke und inaktive Codeblöcke reduziert.

## <a name="editor-help"></a>Editor-Hilfe
 Die Unterstreichung von Fehlern im Editor identifiziert Buildfehler im Code. Wenn diese Option aktiviert ist, werden wellenförmige Unterstreichungen in Farben angezeigt, die eine bestimmte Bedeutung haben:

- Analysefehler werden rot dargestellt.

- Buildfehler werden blau dargestellt.

- Buildwarnungen werden grün dargestellt.

- Ungültige Bearbeitungen in [Bearbeiten und Fortfahren](../../debugger/edit-and-continue.md) werden violett dargestellt.

  Bewegen Sie den Zeiger über das unterstrichene Codesegment. Hierdurch wird eine QuickInfo mit Informationen über den Fehler angezeigt.

  Livesemantik Fehler anzeigen identifiziert bestimmte Kompilierungsfehler ohne explizite Kompilierung, z. b. das Deklarieren und Verwenden eines unbekannten Typs oder das verweisen auf eine unbekannte Eigenschaft.

  Verweise auf Symbole unter dem Cursor markieren, wenn sich der Cursor innerhalb eines Symbols befindet, oder wenn Sie auf ein Symbol klicken, werden alle Instanzen dieses Symbols in der Codedatei hervorgehoben.

## <a name="refactoring"></a>Refactoring
 Überprüfen der Ergebnisse der Umgestaltung zeigt das Dialogfeld **Überprüfungs Ergebnisse** an, wenn Sie versuchen, Code zu umgestalten, der Buildfehler enthält, oder wenn ein Refactoring dazu führen würde, dass ein Code Verweis an etwas anderes als seine ursprüngliche Bindung gebunden wird.

 Warnen für Member mit vom Compiler generierten verweisen zeigt ein Warn Dialogfeld an, wenn Sie versuchen, einen Member zu umgestalten, der denselben Namen wie ein vom Compiler generierter Verweis hat.

## <a name="xml-documentation-comments"></a>XML-Dokumentationskommentare
 XML-Dokumentations Kommentare für///generieren, wenn diese Option ausgewählt ist, werden die \<summary> Start-und Endtags automatisch für XML-Dokumentations Kommentare eingefügt, nachdem Sie die///Kommentar-Einführung eingeben. Weitere Informationen über die XML-Dokumentation finden Sie unter [XML-Dokumentationskommentare](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).

## <a name="implement-interface"></a>Schnittstelle implementieren
 Umschließen von generiertem Code mit #Region fügt ein #Region \<*interface name*> Member um die Methoden ein, wenn eine Schnittstelle implementieren oder die Schnittstelle explizit implementiert wird.

## <a name="organize-usings"></a>Using-Direktiven organisieren
 System-Direktiven beim Sortieren von using-Direktiven zuerst platzieren; `System` using-Direktiven werden vor anderen using-Direktiven angezeigt. Weitere Informationen finden Sie unter [Sortieren von using-Anweisungen](../../misc/sort-usings.md).

## <a name="see-also"></a>Weitere Informationen
 [XML-Dokumentations Kommentare](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [Festlegen von sprachspezifischen Editor Optionen](../../ide/reference/setting-language-specific-editor-options.md) [Visual c# IntelliSense](../../ide/visual-csharp-intellisense.md)
