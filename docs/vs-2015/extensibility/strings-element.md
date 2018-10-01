---
title: Zeichenfolgen-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 12e6b1cbc12e7b0deff97a239db08977ac38144c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516323"
---
# <a name="strings-element"></a>Strings-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Strings-Element](https://docs.microsoft.com/visualstudio/extensibility/strings-element).  
  
Das Zeichenfolgen-Element muss mindestens einen enthalten **ButtonText** untergeordnetes Element. Alle anderen untergeordneten Elemente sind optional. Ungültiges XML-Zeichen wie '&' und ' <' codiert werden als Entitäten ("&amp;'und'&lt;" und so weiter).  
  
 Ein kaufmännisches und-Zeichen in der Textzeichenfolge gibt an, die Tastenkombination für den Befehl.  
  
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
|ButtonText|Dieses Feld und die fünf folgenden Textfelder in einer Befehlsdefinition können Sie die Text erscheint in verschiedenen Menüs angeben. In der Standardeinstellung die `ButtonText` Feld wird in Menücontroller angezeigt. Die `ButtonText` Feld wird auch die Standardeinstellung, wenn die anderen Textfelder leer sind. Die `ButtonText` Feld darf nicht leer sein, auch wenn die anderen Textfelder angegeben werden.|  
|ToolTipText|Die `ToolTipText` Feld gibt den Text, der angezeigt wird, in der QuickInfo für ein Menüelement.<br /><br /> Wenn die `ToolTipText` Feld leer ist, ist die `ButtonText` Feld verwendet wird.|  
|MenuText|Die `MenuText` Feld gibt den Text an, die für einen Befehl angezeigt wird, wenn sie im Hauptmenü, eine Symbolleiste, die in einem Kontextmenü oder in einem Untermenü wird. Wenn die `MenuText` Feld leer ist, werden die integrierte Entwicklungsumgebung (IDE) verwendet die `ButtonText` Feld. Die `MenuText` Feld kann auch für die Lokalisierung verwendet werden.<br /><br /> Für Kontextmenüs das `MenuText` Feld enthält den Namen, die in der Symbolleiste Kontextmenüs angezeigt wird, die Anpassung von Kontextmenüs in der IDE ermöglicht. Aus diesem Grund werden Sie in der Sie Ihre Kontextmenü Namen bestimmte; Verwenden Sie z. B. "-Widget-Paket im Kontextmenü" anstelle von "Verknüpfung".<br /><br /> Wenn die `MenuText` Feld nicht angegeben ist, die `ButtonText` Feld verwendet wird.|  
|commandName|Die `CommandName` Feld gibt den Text, der angezeigt wird, in der Kategorie "Tastatur" in der **Befehle** Registerkarte der **anpassen** Dialogfeld (verfügbar, indem Sie auf **anpassen**auf die **Tools** Menü).|  
|CanonicalName-Element|Die englische `CanonicalName` Feld gibt den Namen des Befehls in englischem Text, die in eingegeben werden, können die **Befehl** Fenster, um das Menüelement auszuführen. Die IDE entfernt alle Zeichen, die keine Buchstaben, Ziffern, Unterstriche oder eingebettete Punkte sind. Dieser Text wird dann verkettet, um zu den `ButtonText` Feld, um den Befehl definieren. Z. B. **neues Projekt** auf die **Datei** Startmenü den Befehl aus, File.NewProject.<br /><br /> Wenn die englische `CanonicalName` Feld nicht angegeben ist, verwendet die IDE die `ButtonText` Feld, und Leisten Sie alle mit Ausnahme von Buchstaben, Ziffern, Unterstriche und eingebettete Punkte. Zum Beispiel den Text der Schaltfläche "& definieren... Befehle" wird DefineCommands, in dem das kaufmännische und-Zeichen, den Speicherplatz und mit den Auslassungspunkten entfernt werden.<br /><br /> Wenn die `TextChanges` Flag angegeben wird und der Text des Befehls geändert wird, wird des entsprechenden Befehls erkannt werden, indem die **Befehl** Fenster wird nicht geändert, bleibt die kanonische Form des ursprünglichen `ButtonText` oder einem englischen `CanonicalName` Felder.|  
|LocCanonicalName|Die `LocCanonicalName` Feld verhält sich genau wie die englische `CanonicalName` Feld ermöglicht jedoch das lokalisierte Befehlstext angegeben werden. Beide kanonische Felder können angegeben werden. Da die IDE in eingegebenen Text analysiert die **Befehl** Fenster und ordnet es mit einem Befehl sowohl für Englisch als auch für nicht-englischen Text kann den gleichen Befehl zugeordnet werden.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Button-Element](../extensibility/button-element.md)|Definiert ein Element, das der Benutzer interagieren kann.|  
|[Menu-Element](../extensibility/menu-element.md)|Definiert ein einzelnes Menüelement.|  
|[Combo-Element](../extensibility/combo-element.md)|Definiert die Befehle, die in einem Kombinationsfeld angezeigt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

