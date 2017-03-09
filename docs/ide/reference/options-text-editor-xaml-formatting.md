---
title: "Optionen, Text-Editor, XAML, Formatierung | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous"
  - "VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing"
helpviewer_keywords: 
  - "Elementabstand, XAML-Ansichtseinstellungen"
  - "Attributabstand, XAML-Ansichtseinstellungen"
  - "XAML-Ansichtseinstellungen, Ereignisse für die automatische Formatierung"
  - "Ereignisse für die automatische Formatierung, XAML-Ansichtseinstellungen"
  - "XAML-Ansichtseinstellungen, Tagumbrüche"
  - "XAML-Ansichtseinstellungen, automatisches Einfügen"
  - "Fragezeichenformatierung, XAML-Ansichtseinstellungen"
  - "XAML-Formatierung, WPF-Designer"
  - "XAML-Ansichtseinstellungen, Toolbox"
  - "XAML-Ansichtseinstellungen, Elementabstand"
  - "XAML-Ansichtseinstellungen, Standardansicht"
  - "Automatisches Einfügen, XAML-Ansichtseinstellungen"
  - "XAML-Ansichtseinstellungen, Standardansicht"
  - "XAML-Ansichtseinstellungen, Fragezeichenformatierung"
  - "Tagumbrüche, XAML-Ansichtseinstellungen"
  - "WPF-Designer, XAML-Formatierung"
  - "XAML-Ansichtseinstellungen, Attributabstand"
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Optionen, Text-Editor, XAML, Formatierung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Geben Sie auf der Eigenschaftenseite **Formatierung** an, wie Elemente und Attribute in XAML\-Dokumenten formatiert werden.  Klicken Sie zum Öffnen des Dialogfelds **Optionen** auf das Menü **Extras**, und klicken Sie dann auf **Optionen**.  Wenn Sie auf die Eigenschaftenseite **Formatierung** zugreifen möchten, erweitern Sie den Knoten **Text\-Editor**, **XAML**, **Formatierung**.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Autoformatierungs\-Ereignisse  
 Autoformatierung tritt möglicherweise auf, wenn eines der folgenden Ereignisse erkannt wird.  
  
-   Abschließen eines Endtags oder einfachen Tags  
  
-   Abschließen eines Starttags  
  
-   Einfügen aus der Zwischenablage  
  
-   Formatierungsbefehle über die Tastatur  
  
 Sie können angeben, durch welche Ereignisse die Autoformatierung ausgelöst werden soll.  
  
|||  
|-|-|  
|**Bei Abschluss des Endtags oder eines einfachen Tags**|Autoformatierung tritt auf, wenn Sie mit dem Eingeben eines Endtags oder eines einfachen Tags fertig sind.  Ein einfaches Tag verfügt über keine Attribute, z. B. `<Button />`.|  
|**Bei Abschluss des Starttags**|Autoformatierung tritt auf, wenn Sie mit dem Eingeben eines Starttags fertig sind.|  
|**Bei Einfügen aus der Zwischenablage**|Autoformatierung tritt auf, wenn Sie XAML aus der Zwischenablage in die XAML\-Ansicht einfügen.|  
  
## Anführungszeichenformat  
 Diese Einstellung gibt an, ob Attributwerte in einfache oder doppelte Anführungszeichen eingeschlossen werden.  Sowohl die automatische Formatierung als auch die automatische Vervollständigung von IntelliSense verwenden diese Einstellung.  
  
 Nach dem Festlegen dieser Option sind nur die Attribute betroffen, die Sie anschließend mit dem Designer oder manuell in der XAML\-Ansicht hinzugefügt haben.  
  
|||  
|-|-|  
|**Doppelte Anführungszeichen \("\)**|Attributwerte werden in doppelte Anführungszeichen eingeschlossen.<br /><br /> `<Button Name="button1">Hello</Button>`|  
|**Einfache Anführungszeichen \('\)**|Attributwerte werden in einfache Anführungszeichen eingeschlossen.<br /><br /> `<Button Name='button1'>Hello</Button>`|  
  
## Tagumbrüche  
 Sie können eine Zeilenlänge für den Tagumbruch angeben.  Ist der Tagumbruch aktiviert, werden alle danach mit dem Designer hinzugefügten XAML\-Einträge entsprechend umbrochen.  
  
|||  
|-|-|  
|**Tags bei Überschreitung der angegebenen Länge umbrechen**|Gibt an, ob Zeilen bei der durch **Länge** angegebenen Zeilenlänge umbrochen werden.|  
|**Länge**|Die Anzahl von Zeichen, die eine Zeile enthalten darf.  Einige XAML\-Zeilen können die angegebene Zeilenlänge ggf. überschreiten.|  
  
## Attributabstand  
 Mit dieser Einstellung können Sie festlegen, wie Attribute im XAML\-Dokument angeordnet werden.  
  
|||  
|-|-|  
|**Zeilenvorschübe und Abstände zwischen Attributen beibehalten**|Neue Zeilen und Abstände zwischen Attributen sind von der automatischen Formatierung nicht betroffen.<br /><br /> `<Button Height="23"   Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Ein Leerzeichen zwischen Attributen einfügen**|Attribute nehmen eine Zeile ein, und die benachbarten Attribute sind durch ein Leerzeichen getrennt.  Die Einstellungen für den Tagumbruch werden angewendet.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|  
|**Jedes Attribut in einer eigenen Zeile anordnen**|Jedes Attribut ist in einer eigenen Zeile enthalten.  Dies ist nützlich, wenn viele Attribute vorhanden sind.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Erstes Attribut in der gleichen Zeile wie Starttag anordnen**|Ist diese Option aktiviert, wird das erste Attribut in derselben Zeile angezeigt wie das Starttag des Elements.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
  
## Elementabstand  
 Mit dieser Einstellung können Sie festlegen, wie Elemente im XAML\-Dokument angeordnet werden.  
  
|||  
|-|-|  
|**Neue Zeilen im Inhalt beibehalten**|Leere Zeilen im Elementinhalt werden nicht entfernt.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**Mehrere Leerzeilen im Inhalt zu einer Zeile reduzieren**|Leere Zeilen im Elementinhalt werden zu einer einzelnen Zeile reduziert.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**Leerzeilen im Inhalt entfernen**|Alle leeren Zeilen im Elementinhalt werden entfernt.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`|  
  
## Automatisch einfügen  
 Mit dieser Einstellung können Sie steuern, wann Tags und Anführungszeichen automatisch generiert werden.  
  
|||  
|-|-|  
|**Endtags**|Gibt an, ob das Endtag eines Elements automatisch generiert wird, wenn Sie das Starttag mit dem Größer als\-Zeichen \(\>\) schließen.|  
|**Attributanführungszeichen**|Gibt an, ob einschließende Anführungszeichen generiert werden, wenn aus der Dropdownliste für die Anweisungsvervollständigung ein Attributwert ausgewählt wird.|  
|**Schließende geschweifte Klammern für MarkupExtensions**|Gibt an, ob die schließende Klammer \(}\) einer Markuperweiterung automatisch generiert wird, wenn Sie das Zeichen für die öffnende Klammer eingeben \(}\).|  
|**Kommas, um MarkupExtension\-Parameter zu trennen**|Gibt an, ob Kommas generiert werden, wenn Sie mehr als einen Parameter in einer Markuperweiterung eingeben.|  
  
## Standardansicht  
 Mit dieser Einstellung können Sie steuern, ob beim Laden von XAML\-Dokumenten die Entwurfsansicht angezeigt wird.  
  
|||  
|-|-|  
|**Dokumente immer in XAML\-Vollansicht öffnen**|Gibt an, ob XAML\-Dokumente nur in der XAML\-Ansicht angezeigt werden, ohne die Entwurfsansicht.  Ist beim Laden großer Dokumente hilfreich.|  
  
## Toolbox  
 Verwenden Sie diese Einstellung, um anzugeben, ob Benutzersteuerelemente und benutzerdefinierte Steuerelemente in der Toolbox angezeigt werden.  
  
|||  
|-|-|  
|**Automatisch Toolboxelemente auffüllen**|Gibt an, ob Benutzersteuerelemente und benutzerdefinierte Steuerelemente in der aktuellen Projektmappe automatisch in der Toolbox angezeigt werden.|  
  
## Siehe auch  
 [XAML in WPF](../Topic/XAML%20in%20WPF.md)   
 [Gewusst wie: Ändern von XAML\-Ansichtseinstellungen](http://msdn.microsoft.com/de-de/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [Exemplarische Vorgehensweisen zu XAML und Code](http://msdn.microsoft.com/de-de/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)