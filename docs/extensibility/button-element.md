---
title: Button-Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05bd73764e96a27a92d741f144c222acc48fa518
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739940"
---
# <a name="button-element"></a>Button-Element
Definiert ein Element, mit dem der Benutzer interagieren kann. Schaltflächen können verschiedene Arten haben: Button, MenuButton und SplitDropDown.

## <a name="syntax"></a>Syntax

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. GUID des Befehlsbezeichners GUID/ID.|
|id|Erforderlich. ID des BEFEHLsbezeichners GUID/ID.|
|priority|Optional. Ein numerischer Wert, der die Priorität angibt.|
|type|Optional. Ein aufgezählter Wert, der die Art der Schaltfläche angibt.<br /><br /> Wenn nicht angegeben, verwendet Button.<br /><br /> Schaltfläche<br /> Ein Standardbefehl, der auf Symbolleisten (in der Regel als ikonische Schaltfläche), Menüs und Kontextmenüs angezeigt wird.<br /><br /> MenuButton<br /> Ein Menüelement, das keinen Befehl ausführt, aber ein anderes Menü erstellt.<br /><br /> SplitDropDown<br /> Steuerelemente, z. B. die Schaltflächen Rückgängig und Wiederholen auf der Standardsymbolleiste in Microsoft Word.|
|Bedingung|Optional. Siehe [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Übergeordnetes Element](../extensibility/parent-element.md)|Optional. Das übergeordnete Element der Schaltfläche.|
|[Icon-Element](../extensibility/icon-element.md)|Optional. Das Symbol, das der Schaltfläche zugeordnet ist.|
|[Befehlsflag-Element](../extensibility/command-flag-element.md)|Erforderlich. Die gültigen CommandFlag-Werte für eine Schaltfläche lauten wie folgt.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> - Pikt<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextÄnderungen<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - Nur Text|
|[Strings-Element](../extensibility/strings-element.md)|Erforderlich. Das untergeordnete [ButtonText-Element](../extensibility/buttontext-element.md) muss definiert werden.|
|Anmerkung|Optionaler Kommentar.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Buttons-Element](../extensibility/buttons-element.md)|Gruppen-Schaltflächenelemente.|

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird eine Schaltfläche in einer *.vsct-Datei* definiert.

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
