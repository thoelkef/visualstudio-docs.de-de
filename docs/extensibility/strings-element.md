---
title: Zeichenfolgen-Element | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5994144f07b8af84f61d7833737f45593c551b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143886"
---
# <a name="strings-element"></a>Zeichenfolgen-Element
Das Zeichenfolgen-Element muss mindestens eine enthalten **ButtonText** untergeordnetes Element. Alle untergeordneten Elemente sind optional. Ungültiges XML-Zeichen wie '&' und ' <' als Entitäten codiert werden ("&amp;'und'&lt;" usw.).  
  
 Ein kaufmännisches und-Zeichen in der Zeichenfolge gibt die Tastenkombination für den Befehl an.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|language|Dies ist optional. Language = ".".|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|ButtonText|Dieses Feld und die fünf folgenden Textfelder in der Befehlsdefinition eines können Sie die Geben Sie den Text, der angezeigt wird, in verschiedenen Menüs. Wird standardmäßig die `ButtonText` Feld wird in Menüsteuerelemente angezeigt. Die `ButtonText` des Felds wird auch die Standardeinstellung, wenn alle anderen Textfelder leer sind. Die `ButtonText` Feld darf nicht leer sein, auch wenn die anderen Textfelder angegeben sind.|  
|ToolTipText|Die `ToolTipText` Feld gibt den Text, der angezeigt wird, in der QuickInfo für ein Menüelement.<br /><br /> Wenn die `ToolTipText` Feld leer ist, ist die `ButtonText` Feld verwendet wird.|  
|MenuText|Die `MenuText` Feld gibt den Text, der für einen Befehl angezeigt wird, sofern es sich im Hauptmenü eine Symbolleiste, die in einem Kontextmenü oder in einem Untermenü handelt. Wenn die `MenuText` Feld leer ist, verwendet die integrierte Entwicklungsumgebung (IDE) die `ButtonText` Feld. Die `MenuText` Feld kann auch für die Lokalisierung verwendet werden.<br /><br /> Für die Kontextmenüs die `MenuText` Feld ist der Name, der auf der Symbolleiste Kontextmenüs angezeigt wird, die Anpassung von Kontextmenüs in der IDE ermöglicht. Aus diesem Grund werden Sie in der Sie Ihre Kontextmenü Namen bestimmte; Verwenden Sie z. B. "Widget Paket Kontextmenü" anstelle von "Verknüpfung".<br /><br /> Wenn die `MenuText` Feld nicht angegeben wird, die `ButtonText` Feld verwendet wird.|  
|CommandName|Die `CommandName` Feld gibt den Text, der angezeigt wird, in der Kategorie "Tastatur" in der **Befehle** Registerkarte der **anpassen** (Dialogfeld) (verfügbar, indem Sie auf **anpassen**auf die **Tools** Menü).|  
|CanonicalName-Element|Die englische `CanonicalName` Feld gibt den Namen des Befehls in englischem Text, die in eingegeben werden, kann die **Befehl** ausführen, das Menüelement. Die IDE entfernt alle Zeichen, die keine Buchstaben, Ziffern, Unterstriche oder eingebettete Punkte sind. Dieser Text wird dann verkettet, um die `ButtonText` Feld, um den Befehl zu definieren. Beispielsweise **neues Projekt** auf die **Datei** Menü wird der Befehl File.NewProject.<br /><br /> Wenn der englischen `CanonicalName` Feld nicht angegeben wird, verwendet die IDE die `ButtonText` Feld und alle mit Ausnahme von Buchstaben, Ziffern, Unterstriche und eingebettete Punkte leisten. Z. B. den Text der Schaltfläche "& definieren... Befehle" wird DefineCommands, in dem das kaufmännische und-Zeichen, Leerzeichen und mit den Auslassungspunkten entfernt werden.<br /><br /> Wenn die `TextChanges` Flag angegeben wird und der Text des Befehls geändert wird, wird des entsprechenden Befehls vom erkannt die **Befehl** Fenster wird nicht geändert, bleibt die kanonische Form des ursprünglichen `ButtonText` oder Englisch `CanonicalName` Felder.|  
|LocCanonicalName|Die `LocCanonicalName` Feld verhält sich ebenso wie Englisch `CanonicalName` Feld ermöglicht jedoch lokalisierte Befehlstext angegeben werden. Beide kanonische Felder können angegeben werden. Daran, dass die IDE im eingegebenen Text nur analysiert die **Befehl** Fenster und ordnet sie mit einem Befehl, der sowohl für Englisch als auch für nicht-englischen Text kann mit den gleichen Befehl verknüpft werden.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Button-Element](../extensibility/button-element.md)|Definiert ein Element, das der Benutzer interagieren kann.|  
|[Menu-Element](../extensibility/menu-element.md)|Definiert ein einzelnes Menüelement an.|  
|[Combo-Element](../extensibility/combo-element.md)|Definiert die Befehle, die in einem Kombinationsfeld angezeigt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)