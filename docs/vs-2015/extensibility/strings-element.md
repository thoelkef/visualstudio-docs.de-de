---
title: Strings-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0eae2fd7490269d713beb9950163071dd3ba32f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160566"
---
# <a name="strings-element"></a>Strings-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Strings-Element muss mindestens ein untergeordnetes **ButtonText** -Element enthalten. Alle anderen untergeordneten Elemente sind optional. Ungültige XML-Zeichen wie z. b. ' & ' und ' < ' müssen als Entitäten (' &amp; ' und ' &lt; ' usw.) codiert werden.  
  
 Ein kaufmännisches und-Zeichen in der Text Zeichenfolge gibt die Tastenkombination für den Befehl an.  
  
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
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|language|Optional. Language = ".".|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Folgendes|Mithilfe dieses Felds und der fünf folgenden Textfelder in einer Befehls Definition können Sie den Text angeben, der in verschiedenen Menüs angezeigt wird. Standardmäßig wird das `ButtonText` Feld in den Menü Controllern angezeigt. Das `ButtonText` Feld wird auch zur Standardeinstellung, wenn die anderen Textfelder leer sind. Das `ButtonText` Feld darf nicht leer sein, auch wenn die anderen Textfelder angegeben werden.|  
|ToolTip Text|Das- `ToolTipText` Feld gibt den Text an, der in der QuickInfo für ein Menü Element angezeigt wird.<br /><br /> Wenn das `ToolTipText` Feld leer ist, `ButtonText` wird das Feld verwendet.|  
|MenuText|Das- `MenuText` Feld gibt den Text an, der für einen Befehl angezeigt wird, wenn er im Hauptmenü, in einer Symbolleiste, in einem Kontextmenü oder in einem Untermenü angezeigt wird. Wenn das `MenuText` Feld leer ist, verwendet die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) das `ButtonText` Feld. Das `MenuText` Feld kann auch für die Lokalisierung verwendet werden.<br /><br /> Bei Kontextmenüs ist das `MenuText` Feld der Name, der auf der Symbolleiste der Kontextmenüs angezeigt wird, wodurch die Anpassung von Kontextmenüs in der IDE ermöglicht wird. Achten Sie daher auf die Bezeichnung für das Kontextmenü. Verwenden Sie z. b. "Widget Package-Kontextmenü" anstelle von "Verknüpfung".<br /><br /> Wenn das `MenuText` Feld nicht angegeben wird, `ButtonText` wird das Feld verwendet.|  
|CommandName|Das `CommandName` -Feld gibt den Text an, der in der Tastatur Kategorie auf der Registerkarte **Befehle** im Dialogfeld **Anpassen** angezeigt wird (verfügbar, **Tools** Wenn Sie im Menü Extras auf **Anpassen** klicken).|  
|CanonicalName|Das englische `CanonicalName` Feld gibt den Namen des Befehls in englischem Text an, der im **Befehls** Fenster eingegeben werden kann, um das Menü Element auszuführen. Die IDE entfernt alle Zeichen, die keine Buchstaben, Ziffern, Unterstriche oder eingebetteten Zeiträume darstellen. Dieser Text wird dann mit dem Feld verkettet `ButtonText` , um den Befehl zu definieren. Beispielsweise wird das **neue Projekt** im Menü **Datei** zum Befehl File. NewProject.<br /><br /> Wenn das englische `CanonicalName` Feld nicht angegeben wird, verwendet die IDE das `ButtonText` -Feld und entfernt alle außer Buchstaben, Ziffern, Unterstriche und eingebettete Zeiträume. Beispielsweise der Schaltflächen Text "&definieren von Befehlen..." wird zu definecommands, wobei das kaufmännische und-Zeichen, der Platz und die Auslassungs Zeichen entfernt werden.<br /><br /> Wenn das `TextChanges` -Flag angegeben wird und der Text des Befehls geändert wird, ändert sich der entsprechende Befehl, der vom **Befehls** Fenster erkannt wird, nicht. er bleibt die kanonische Form der ursprünglichen `ButtonText` oder englischen `CanonicalName` Felder.|  
|Loccanonicalname|Das `LocCanonicalName` Feld verhält sich identisch mit dem englischen `CanonicalName` Feld, ermöglicht jedoch das Angeben von lokalisiertem Befehls Text. Beide kanonischen Felder können angegeben werden. Da die IDE nur im **Befehls** Fenster eingegebenen Text analysiert und einem Befehl zuordnet, können sowohl englischer als auch nicht englischer Text dem gleichen Befehl zugeordnet werden.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Button-Element](../extensibility/button-element.md)|Definiert ein Element, mit dem der Benutzer interagieren kann.|  
|[Menu-Element](../extensibility/menu-element.md)|Definiert ein einzelnes Menü Element.|  
|[Combo-Element](../extensibility/combo-element.md)|Definiert Befehle, die in einem Kombinations Feld angezeigt werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
