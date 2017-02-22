---
title: "Optionen, Text-Editor, C#, Erweitert | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced"
helpviewer_keywords: 
  - "XML-Kommentare"
  - "XML-Dokumentation, generieren"
  - "Gliederungsoptionen [C#]"
  - "Gliederungsoptionen [J#]"
  - "XML-Dokumentation, erstellen"
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Optionen, Text-Editor, C#, Erweitert
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie dieses Dialogfeld, um Einstellungen zur Editorformatierung, Umgestaltung von Code sowie zu XML\-Dokumentationskommentaren für Visual C\# zu ändern.  Um dieses Dialogfeld zu öffnen, klicken Sie im Menü **Extras** auf **Optionen**, erweitern den Ordner **Text\-Editor**, erweitern **C\#** und klicken dann auf **Erweitert**.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Gliederung  
 Entwurfsmodus beim Öffnen der Datei starten  
 Bei Auswahl dieser Option wird die Codedatei automatisch gegliedert, wodurch reduzierbare Codeblöcke erstellt werden.  Wenn eine Datei zum ersten Mal geöffnet wird, werden \#region\-Blöcke und inaktive Codeblöcke reduziert.  
  
## Editor\-Hilfe  
 Fehler im Editor unterstreichen  
 Kennzeichnet Buildfehler im Code.  Bei Auswahl dieser Option werden farbige wellenförmige Unterstreichungen angezeigt, deren jeweilige Farbe eine bestimmte Bedeutung hat:  
  
-   Analysefehler sind rot.  
  
-   Buildfehler sind blau.  
  
-   Buildwarnungen sind grün.  
  
-   Ungültige ["Bearbeiten und Fortfahren"](../../debugger/edit-and-continue.md)\-Vorgänge sind violett.  
  
 Bewegen Sie den Mauszeiger über das unterstrichene Codesegment, um eine QuickInfo mit Informationen zum Fehler zu erhalten.  
  
 Livesemantikfehler anzeigen  
 Identifiziert bestimmte Compilerfehler ohne explizite Kompilierung, z. B. Deklarieren und Verwenden eines unbekannten Typs oder Verweisen auf eine unbekannte Eigenschaft.  
  
 Verweise auf Symbol unter Cursor hervorheben  
 Wenn sich der Cursor innerhalb eines Symbols befindet oder Sie auf ein Symbol klicken, werden alle Instanzen dieses Symbols in der Codedatei hervorgehoben.  
  
## Umgestaltung  
 Überprüfen der Ergebnisse der Umgestaltung  
 Zeigt das Dialogfeld **Ergebnisse der Verifizierung** an, wenn Sie versuchen, Code umzugestalten, der Buildfehler enthält, oder wenn eine Umgestaltung dazu führen würde, dass für einen Codeverweis eine abweichende Bindung als die ursprüngliche Bindung hergestellt wird.  
  
 Warnen bei Membern mit vom Compiler generierten Verweisen  
 Blendet ein Warndialogfeld ein, wenn Sie versuchen, einen Member umzugestalten, der über denselben Namen wie ein vom Compiler generierter Verweis verfügt.  
  
## XML\-Dokumentationskommentare  
 XML\-Dokumentationskommentare generieren für \/\/\/  
 Bei Auswahl dieser Option werden automatisch \<summary\>\-Starttags und \-Endtags für XML\-Dokumentationskommentare eingefügt, nachdem Sie die Zeichen \/\/\/ für den Kommentarbeginn eingegeben haben.  Weitere Informationen zur XML\-Dokumentation finden Sie unter [XML\-Dokumentationskommentare](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).  
  
## Schnittstelle implementieren  
 Generierten Code mit \#region umschließen  
 Fügt einen \#region \<*Schnittstellenname*\>\-Member vor und nach Methoden ein, wenn Schnittstelle implementieren oder Schnittstelle explizit implementieren verwendet wird.  
  
## Usings organisieren  
 System\-Direktiven beim Sortieren von Usings an erster Stelle platzieren  
 Falls aktiviert, werden `System` Using\-Direktiven vor anderen Using\-Direktiven angezeigt.  Weitere Informationen finden Sie unter [Sortieren von Usings](../../misc/sort-usings.md).  
  
## Siehe auch  
 [XML\-Dokumentationskommentare](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [Festlegen von sprachspezifischen Editoroptionen](../../ide/reference/setting-language-specific-editor-options.md)   
 [Visual C\#\-IntelliSense](../../ide/visual-csharp-intellisense.md)