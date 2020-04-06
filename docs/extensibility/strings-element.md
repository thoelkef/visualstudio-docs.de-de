---
title: Strings Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699722"
---
# <a name="strings-element"></a>Strings-Element
Das Strings-Element muss mindestens ein **untergeordnetes ButtonText-Element** enthalten. Alle anderen untergeordneten Elemente sind optional. Ungültige XML-Zeichen wie "&" und "<" müssen&amp;als Entitäten codiert werden (' ' und '&lt;' usw.).

 Ein spersand in der Textzeichenfolge gibt die Tastenkombination für den Befehl an.

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

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|language|Optional. Sprache=".".|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Buttontext|Mit diesem Feld und den fünf folgenden Textfeldern in einer Befehlsdefinition können Sie den Text angeben, der in verschiedenen Menüs angezeigt wird. Standardmäßig wird `ButtonText` das Feld in Menücontrollern angezeigt. Das `ButtonText` Feld wird auch zum Standard, wenn die anderen Textfelder leer sind. Das `ButtonText` Feld darf auch dann nicht leer sein, wenn die anderen Textfelder angegeben sind.|
|Tooltiptext|Das `ToolTipText` Feld gibt den Text an, der in der QuickInfo für ein Menüelement angezeigt wird.<br /><br /> Wenn `ToolTipText` das Feld leer `ButtonText` ist, wird das Feld verwendet.|
|MenuText|Das `MenuText` Feld gibt den Text an, der für einen Befehl angezeigt wird, wenn er sich im Hauptmenü, in einer Symbolleiste, in einem Kontextmenü oder in einem Untermenü befindet. Wenn `MenuText` das Feld leer ist, verwendet die `ButtonText` integrierte Entwicklungsumgebung (IDE) das Feld. Das `MenuText` Feld kann auch für die Lokalisierung verwendet werden.<br /><br /> Bei Verknüpfungsmenüs `MenuText` ist das Feld der Name, der in der Symbolleiste Shortcut-Menüs angezeigt wird, wodurch die Anpassung von Kontextmenüs in der IDE ermöglicht wird. Seien Sie daher in dem Kontextmenü spezifisch. Verwenden Sie beispielsweise "Widget Package Shortcut Menu" anstelle von "Shortcut".<br /><br /> Wenn `MenuText` das Feld nicht `ButtonText` angegeben ist, wird das Feld verwendet.|
|CommandName|Das `CommandName` Feld gibt den Text an, der in der Tastaturkategorie auf der Registerkarte **Befehle** im Dialogfeld **Anpassen** angezeigt wird (verfügbar durch Klicken auf **Anpassen** im Menü **Extras).**|
|CanonicalName|Das `CanonicalName` Feld Englisch gibt den Namen des Befehls in englischem Text an, der im **Befehlsfenster** eingegeben werden kann, um das Menüelement auszuführen. Die IDE entfernt alle Zeichen, die keine Buchstaben, Ziffern, Unterstriche oder eingebettete Punkte sind. Dieser Text wird dann mit dem `ButtonText` Feld verkettet, um den Befehl zu definieren. Beispielsweise wird **New Project** im Menü **Datei** zum Befehl File.NewProject.<br /><br /> Wenn das `CanonicalName` Feld Englisch nicht angegeben `ButtonText` ist, verwendet die IDE das Feld und entfernt alle Mitschrift mit Ausnahme von Buchstaben, Ziffern, Unterstrichen und eingebetteten Punkten. Der Schaltflächentext "&Befehle definieren..." wird DefineCommands, wo das vom perpersand, das Leerzeichen und die Auslassungspunkte entfernt werden.<br /><br /> Wenn `TextChanges` das Flag angegeben wird und der Text des Befehls geändert wird, ändert sich der entsprechende Befehl, der vom **Befehlsfenster** erkannt wird, nicht. es bleibt die kanonische `ButtonText` Form `CanonicalName` der ursprünglichen oder englischen Felder.|
|LocCanonicalName|Das `LocCanonicalName` Feld verhält sich identisch `CanonicalName` mit dem englischen Feld, ermöglicht jedoch die Angabe des lokalisierten Befehlstextes. Beide kanonischen Felder können angegeben werden. Da die IDE nur den im **Befehlsfenster** eingegebenen Text analysiert und ihm einen Befehl zuordnet, können sowohl englischer als auch nicht-englischer Text demselben Befehl zugeordnet werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Button-Element](../extensibility/button-element.md)|Definiert ein Element, mit dem der Benutzer interagieren kann.|
|[Menu-Element](../extensibility/menu-element.md)|Definiert ein einzelnes Menüelement.|
|[Combo-Element](../extensibility/combo-element.md)|Definiert Befehle, die in einem Kombinationsfeld angezeigt werden.|

## <a name="see-also"></a>Weitere Informationen
- [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
