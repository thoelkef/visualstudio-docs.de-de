---
title: Button-Element | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739940"
---
# <a name="button-element"></a>Button-Element
Definiert ein Element, mit dem der Benutzer interagieren kann. Schaltflächen können verschiedene Arten aufweisen: Schaltfläche, menubutton und splitdropdown.

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

|attribute|Beschreibung|
|---------------|-----------------|
|guid|Erforderlich. GUID des GUID-/ID-befehlsbezeichners.|
|id|Erforderlich. ID des GUID-/ID-befehlsbezeichners.|
|priority|Optional. Ein numerischer Wert, der die Priorität angibt.|
|type|Optional. Ein-Enumerationswert, der die Art der Schaltfläche angibt.<br /><br /> Wenn nicht angegeben, wird die Schaltfläche verwendet.<br /><br /> Schaltfläche<br /> Ein Standardbefehl, der auf Symbolleisten (in der Regel als Symbolleisten Schaltfläche), Menüs und Kontextmenüs angezeigt wird.<br /><br /> -Menubutton-<br /> Ein Menü Element, das keinen Befehl ausführt, sondern ein anderes Menü erzeugt.<br /><br /> Splitdropdown<br /> Steuerelemente, z. b. die Schaltflächen Rückgängig und wiederholen auf der Standard Symbolleiste in Microsoft Word.|
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Übergeordnetes Element](../extensibility/parent-element.md)|Optional. Das übergeordnete Element der Schaltfläche.|
|[Icon-Element](../extensibility/icon-element.md)|Optional. Das Symbol, das der Schaltfläche zugeordnet ist.|
|[Befehlsflag-Element](../extensibility/command-flag-element.md)|Erforderlich. Die gültigen CommandFlag-Werte für eine Schaltfläche lauten wie folgt.<br /><br /> -Allowparametriams<br /><br /> -Commandwellonly<br /><br /> -Defaultdeaktiviert<br /><br /> -Defaultinvisible<br /><br /> -DontCache<br /><br /> -Dynamicitemstart<br /><br /> -Dynamicvisibility<br /><br /> -Fixmenucontroller<br /><br /> -Iconandtext<br /><br /> -Nobuttoncustomize<br /><br /> -Nocustomize<br /><br /> -Nokeycustomize<br /><br /> -Noshowonmenucontroller<br /><br /> -PICT<br /><br /> -Postexec<br /><br /> -Profferedcmd<br /><br /> -Routeto docs<br /><br /> -Textcascadeusebtn<br /><br /> -Textmenuusebutton<br /><br /> -Textchanges<br /><br /> -Textchangesbutton<br /><br /> -Textcontextusebutton<br /><br /> -Textmenuctrlulmenu<br /><br /> -Textmenuusebutton<br /><br /> -TextOnly|
|[Strings-Element](../extensibility/strings-element.md)|Erforderlich. Das untergeordnete [ButtonText-Element](../extensibility/buttontext-element.md) muss definiert werden.|
|Anmerkung|Optionaler Kommentar.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Buttons-Element](../extensibility/buttons-element.md)|Gruppiert Schaltflächen Elemente.|

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird eine Schaltfläche in einer *vsct* -Datei definiert.

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

## <a name="see-also"></a>Siehe auch
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
