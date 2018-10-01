---
title: Optionen, Text-Editor, XAML, Formatierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3bf43a9c13b273339d58f376b684a94444861d4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515848"
---
# <a name="options-text-editor-xaml-formatting"></a>Optionen, Text-Editor, XAML, Formatierung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Optionen, Text-Editor, XAML, Formatierung](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-xaml-formatting).  
  
  
Verwenden Sie die **Formatierung**-Eigenschaftenseite, um anzugeben, wie Elemente und Attribute in Ihren XAML-Dokumenten formatiert werden. Klicken Sie zum Öffnen des Dialogfelds **Optionen** auf das Menü **Tools** und anschließend auf **Optionen**. Erweitern Sie für den Zugriff auf die **Formatierung**-Eigenschaftenseite den **Text-Editor**, **XAML** und den **Formatierungs**-Knoten.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="auto-formatting-events"></a>Autoformatierungsereignisse  
 Die automatische Formatierung kann auftreten, wenn eines der folgenden Ereignisse erkannt wird.  
  
-   Bei Vervollständigung des Endtags oder eines einfachen Tags  
  
-   Bei Vervollständigung des Starttags  
  
-   Bei Einfügen aus der Zwischenablage  
  
-   Formatieren von Tastaturbefehlen  
  
 Sie können angeben, welche Ereignisse automatische Formatierung verursachen.  
  
|||  
|-|-|  
|**Bei Vervollständigung des Endtags oder eines einfachen Tags**|Automatische Formatierung tritt auf, wenn Sie einen Endtag oder ein einfaches Tag eingegeben haben. Ein einfaches Tag verfügt über keine Attribute, z.B. `<Button />`.|  
|**Bei Vervollständigung des Starttags**|Automatische Formatierung tritt auf, wenn Sie einen Starttag eingegeben haben.|  
|**Bei Einfügen aus der Zwischenablage**|Die automatische Formatierung tritt auf, wenn Sie XAML aus der Zwischenablage in XAML-Ansicht einfügen.|  
  
## <a name="quotation-mark-style"></a>Anführungszeichenformat  
 Diese Einstellung gibt an, ob Attributwerte in einfache oder doppelte Anführungszeichen eingeschlossen werden. Die automatische Formatierung und automatische Vervollständigung von IntelliSense verwenden diese Einstellung.  
  
 Nachdem Sie diese Option festgelegt haben, sind nur Attribute betroffen, die später entweder mithilfe des Designers oder manuell in die XAML-Ansicht hinzugefügt werden.  
  
|||  
|-|-|  
|**Doppelte Anführungszeichen (")**|Attributwerte werden in doppelte Anführungszeichen eingeschlossen.<br /><br /> `<Button Name="button1">Hello</Button>`|  
|**Einfache Anführungszeichen (')**|Attributwerte werden in einfache Anführungszeichen eingeschlossen.<br /><br /> `<Button Name='button1'>Hello</Button>`|  
  
## <a name="tag-wrapping"></a>Tagumbrüche  
 Sie können eine Zeilenlänge für Tagumbrüche angeben. Wenn Tagumbrüche aktiviert sind, wird jedes XAML, das später mithilfe des Designers hinzugefügt wird, entsprechend umgebrochen.  
  
|||  
|-|-|  
|**Tags bei Überschreitung der angegebenen Länge umbrechen**|Gibt an, ob Zeilen bei der durch **Länge** angegebenen Zeilenlänge umgebrochen werden.|  
|**Länge**|Die Anzahl der Zeichen, die eine Zeile enthalten kann. Falls erforderlich, könnten einige XAML-Zeilen die angegebene Zeilenlänge überschreiten.|  
  
## <a name="attribute-spacing"></a>Attributabstand  
 Mit dieser Einstellung können Sie steuern, wie Attribute im XAML-Dokument angeordnet sind  
  
|||  
|-|-|  
|**Neue Zeilen und Leerzeichen zwischen Attributen beibehalten**|Neue Zeilen und Leerzeichen zwischen Attributen sind von der automatischen Formatierung nicht betroffen.<br /><br /> `<Button Height="23"   Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Ein Leerzeichen zwischen Attributen einfügen**|Attribute umfassen eine Zeile mit durch ein Leerzeichen getrennten benachbarten Attributen. Die Einstellungen für Tagumbrüche werden angewendet.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|  
|**Jedes Attribut in einer eigenen Zeile anordnen**|Jedes Attribut umfasst seine eigene Zeile. Dies ist nützlich, wenn viele Attribute vorhanden sind.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Erstes Attribut in derselben Zeile wie Starttag positionieren**|Wenn dieses Kontrollkästchen aktiviert ist, wird das erste Attribut auf derselben Zeile wie der Starttag des Elements angezeigt.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
  
## <a name="element-spacing"></a>Elementabstand  
 Mit dieser Einstellung können Sie steuern, wie Attribute in Ihrem XAML-Dokument angeordnet sind.  
  
|||  
|-|-|  
|**Neue Zeilen im Inhalt beibehalten**|Leerzeilen im Elementinhalt werden nicht entfernt.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**Mehrere Leerzeilen im Inhalt auf eine Zeile reduzieren**|Leerzeilen im Elementinhalt werden zu einer einzelnen Zeile reduziert.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**Leerzeilen im Inhalt entfernen**|Alle Leerzeilen im Elementinhalt werden entfernt.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`|  
  
## <a name="auto-insert"></a>Automatisch einfügen  
 Verwenden Sie diese Einstellung, um zu steuern, wann Tags und Anführungszeichen automatisch generiert werden.  
  
|||  
|-|-|  
|**Endtags**|Gibt an, ob das Endtag eines Elements automatisch generiert wird, wenn Sie das Starttag mit dem Größer-als-Zeichen (>) schließen.|  
|**Attributanführungszeichen**|Gibt an, ob einschließende Anführungszeichen generiert werden, wenn ein Attributwert aus der Drop-down-Liste der Anweisungsvervollständigung ausgewählt ist.|  
|**Schließende geschweifte Klammern für MarkupExtensions**|Gibt an, ob eine Markuperweiterung schließende geschweifte Klammer (}) automatisch generiert wird, wenn Sie das öffnende geschweifte Klammerzeichen ({) eingeben.|  
|**Kommas zum Trennen von MarkupExtension-Parametern**|Gibt an, ob Kommas generiert werden, wenn Sie mehr als einen Parameter in einer Markuperweiterung eingeben.|  
  
## <a name="default-view"></a>Standardansicht  
 Mit dieser Einstellung wird gesteuert, ob die Entwurfsansicht angezeigt wird, wenn XAML-Dokumente geladen werden.  
  
|||  
|-|-|  
|**Öffnen Sie die Dokumente immer in vollständige XAML-Ansicht**|Gibt an, ob der XAML-Dokumente nur in XAML-Ansicht, ohne die Entwurfsansicht angezeigt werden. Beim Laden großer Dokumente hilfreich.|  
  
## <a name="toolbox"></a>Werkzeugkasten  
 Verwenden Sie diese Einstellung, um anzugeben, ob Benutzersteuerelemente und benutzerdefinierte Steuerelemente in der Toolbox angezeigt werden.  
  
|||  
|-|-|  
|**Toolboxelemente automatisch ausfüllen**|Gibt an, ob Benutzersteuerelemente und benutzerdefinierte Steuerelemente in der aktuellen Projektmappe automatisch in der Toolbox angezeigt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [XAML in WPF](http://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)   
 [Gewusst wie: Ändern von XAML-Ansichtseinstellungen](http://msdn.microsoft.com/en-us/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [Exemplarische Vorgehensweisen zu XAML und Code](http://msdn.microsoft.com/en-us/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)



