---
title: KeyBinding Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703145"
---
# <a name="keybinding-element"></a>KeyBinding-Element
Das KeyBinding-Element gibt Tastenkombinationen für die Befehle an.

 Befehlen können sowohl Einzel- als auch Dual-Key-Bindungen zugeordnet sein. Ein Beispiel für eine einzelne Schlüsselbindung ist **Strg**+**S** für den **Befehl Speichern.** Dual-Key-Bindungen erfordern zwei aufeinander folgende Tastenkombinationen, um einen Befehl auszulösen. Ein Beispiel für eine Doppelschlüsselbindung ist <strong>Strg*+</strong>K<strong>,</strong>Strg<strong>+</strong>K**, um eine Textmarke festzulegen.

## <a name="syntax"></a>Syntax

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich.|
|id|Erforderlich.|
|Editor|Erforderlich. Die Editor-GUID gibt den Bearbeitungskontext an, für den diese Tastenkombination aktiv ist. Der globale Bindungsbereichswert ist "guidVSStd97".|
|key1|Erforderlich. Gültige Werte umfassen alle typisierbaren Alphanumer, sowie zweistellige hexadezimale Werte, denen 0x und [VK_constants](/windows/desktop/inputdev/virtual-key-codes)vorangestellt sind.|
|mod1|Optional. Jede Beliebige Kombination von **Strg**, **Alt**und **Shift,** die durch Leerzeichen getrennt ist.|
|Schlüssel2|Optional. Gültige Werte umfassen alle typisierbaren Alphanumer, sowie zweistellige hexadezimale Werte, denen 0x und [VK_constants](/windows/desktop/inputdev/virtual-key-codes)vorangestellt sind.|
|mod2|Optional. Jede Beliebige Kombination von **Strg**, **Alt**und **Shift,** die durch Leerzeichen getrennt ist.|
|Emulator|Optional.|
|Bedingung|Optional. Siehe [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Parent||
|Anmerkung||

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[KeyBindings-Element](../extensibility/keybindings-element.md)|Gruppiert KeyBinding-Elemente und andere KeyBindings-Gruppierungen.|

## <a name="example"></a>Beispiel

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>Weitere Informationen
- [KeyBindings-Element](../extensibility/keybindings-element.md)
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
