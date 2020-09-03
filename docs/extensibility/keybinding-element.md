---
title: KeyBinding-Element | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703145"
---
# <a name="keybinding-element"></a>KeyBinding-Element
Das KeyBinding-Element gibt Tastenkombinationen für die Befehle an.

 Befehlen können sowohl einfache als auch Dual-Key-Bindungen zugeordnet werden. Ein Beispiel für eine einzelne tastenbindung ist **STRG** + **S** für den **Save** -Befehl. Dual-Key-Bindungen erfordern zwei aufeinander folgende Tastenkombinationen, um einen Befehl zu initiieren. Ein Beispiel für eine Dual-Key-Bindung ist <strong>STRG *+</strong> k<strong>,</strong>STRG <strong>+</strong> k** zum Festlegen eines Lesezeichens.

## <a name="syntax"></a>Syntax

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|guid|Erforderlich.|
|id|Erforderlich.|
|Editor|Erforderlich. Die Editor-GUID gibt den Bearbeitungs Kontext an, für den diese Tastenkombination aktiviert wird. Der Wert des globalen Bindungs Bereichs ist "guidVSStd97".|
|key1|Erforderlich. Zu den gültigen Werten gehören alle typbaren alphanumerischen Werte und zweistellige hexadezimal Werte, denen 0x und [VK_constants](/windows/desktop/inputdev/virtual-key-codes)vorangestellt sind.|
|mod1|Optional. Eine beliebige Kombination von **STRG**, **alt**und **UMSCHALT** durch Leerzeichen voneinander getrennt.|
|Schlüssel2|Optional. Zu den gültigen Werten gehören alle typbaren alphanumerischen Werte und zweistellige hexadezimal Werte, denen 0x und [VK_constants](/windows/desktop/inputdev/virtual-key-codes)vorangestellt sind.|
|mod2|Optional. Eine beliebige Kombination von **STRG**, **alt**und **UMSCHALT** durch Leerzeichen voneinander getrennt.|
|Emulator|Optional.|
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|Parent||
|Anmerkung||

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[KeyBinding-Element](../extensibility/keybindings-element.md)|Gruppiert KeyBinding-Elemente und andere keybindungs Gruppierungen.|

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
- [KeyBinding-Element](../extensibility/keybindings-element.md)
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
