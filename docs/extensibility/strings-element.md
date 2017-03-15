---
title: "Zeichenfolgen-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Zeichenfolgen-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, Zeichenfolgen"
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Zeichenfolgen-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Zeichenfolgen\-Element muss mindestens eine enthalten **ButtonText** untergeordnetes Element. Alle anderen untergeordneten Elemente sind optional. Ungültiges XML\-Zeichen wie '&' und ' \<' codiert werden müssen, als Entitäten \("& Amp;' und '& Lt;' usw.\).  
  
 Ein kaufmännisches und\-Zeichen in der Zeichenfolge gibt die Tastenkombination für den Befehl.  
  
## Syntax  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|language|Optional. Language \= ".".|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|ButtonText|Dieses Feld und die fünf folgenden Textfelder in einer Befehlsdefinition können Sie die angezeigten Text in verschiedenen Menüs angeben. In der Standardeinstellung die `ButtonText` Feld wird im Menücontroller angezeigt. Die `ButtonText` Feld wird auch die Standardeinstellung, wenn die anderen Felder leer sind. Die `ButtonText` Feld darf nicht leer sein, auch wenn die anderen Felder angegeben werden.|  
|ToolTipText|Die `ToolTipText` Feld Text erscheint in der QuickInfo für ein Menüelement angibt.<br /><br /> Wenn die `ToolTipText` Feld leer ist, ist die `ButtonText` Feld verwendet wird.|  
|MenuText|Die `MenuText` Feld gibt den Text an, die für einen Befehl angezeigt wird, wenn sie im Hauptmenü, eine Symbolleiste, die in einem Kontextmenü oder ein Untermenü wird. Wenn die `MenuText` Feld leer ist, verwendet die integrierte Entwicklungsumgebung \(IDE\) die `ButtonText` Feld. Die `MenuText` Feld kann auch für die Lokalisierung verwendet werden.<br /><br /> Für die Kontextmenüs die `MenuText` Feld enthält den Namen, die in der Symbolleiste Kontextmenüs angezeigt wird, die Anpassung des Kontextmenüs in der IDE ermöglicht. Daher werden Sie bestimmte in der Sie Ihre Kontextmenü Namen; Verwenden Sie z. B. "Widget Paket Kontextmenü" anstelle von "Verknüpfung".<br /><br /> Wenn die `MenuText` Feld nicht angegeben wird, die `ButtonText` Feld verwendet wird.|  
|CommandName|Die `CommandName` Feld gibt Text erscheint in der Kategorie "Tastatur" in der **Befehle** Registerkarte der **Anpassen** \(Dialogfeld\) \(durch Klicken auf **Anpassen** auf der **Tools** im Menü\).|  
|CanonicalName\-Element|Die englische `CanonicalName` Feld gibt den Namen des Befehls in englischem Text, die in eingegeben werden, können die **Befehl** ausführen, das Menüelement. Die IDE entfernt alle Zeichen, die keine Buchstaben, Ziffern, Unterstriche oder eingebettete Punkte sind. Dieser Text wird dann verkettet, um zu den `ButtonText` Feld, um den Befehl zu definieren. Beispielsweise **Neues Projekt** auf der **Datei** Menü wird der Befehl File.NewProject.<br /><br /> Wenn der englischen `CanonicalName` Feld nicht angegeben wird, verwendet die IDE das `ButtonText` Feld und entfernt alle außer Buchstaben, Ziffern, Unterstriche und eingebettete Punkte. Zum Beispiel den Text der Schaltfläche "& definieren Befehle..." wird DefineCommands, der das kaufmännische und\-Zeichen, Leerzeichen und die Schaltfläche entfernt.<br /><br /> Wenn die `TextChanges` \-Flag angegeben ist und der Text des Befehls geändert wird, wird des entsprechenden Befehls erkannt wird die **Befehl** Fenster wird nicht geändert, bleibt die kanonische Form des ursprünglichen `ButtonText` bzw. aus dem englischen `CanonicalName` Felder.|  
|LocCanonicalName|Die `LocCanonicalName` Feld verhält sich genauso wie die englische `CanonicalName` Feld ermöglicht jedoch das lokalisierte Befehlstext angegeben werden. Kanonische Felder können angegeben werden. Da die IDE nur im eingegebenen Text analysiert die **Befehl** Fenster und verknüpft sie mit einem Befehl sowohl für Englisch als auch für nicht\-englischen Text kann mit den gleichen Befehl verknüpft werden.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Button\-Element](../extensibility/button-element.md)|Definiert ein Element, mit denen der Benutzer interagieren kann.|  
|[Menu\-Element](../extensibility/menu-element.md)|Definiert ein einzelnes Menüelement.|  
|[Kombinationsfeld\-Element](../extensibility/combo-element.md)|Definiert die Befehle, die in einem Kombinationsfeld angezeigt werden.|  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)