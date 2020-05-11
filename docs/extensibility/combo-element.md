---
title: Combo-Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ff9d9e20ec221a86f1cce5f9c43a4e47ed6dc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739821"
---
# <a name="combo-element"></a>Combo-Element
Definiert Befehle, die in einem Kombinationsfeld angezeigt werden. Es gibt vier Arten von Kombinationsfeldern, wie folgt: DropDownCombo, DynamicCombo, IndexCombo und MRUCombo.

## <a name="syntax"></a>Syntax

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. GUID des Befehlsbezeichners GUID/ID.|
|id|Erforderlich. ID des BEFEHLsbezeichners GUID/ID.|
|defaultWidth|Erforderlich. Eine ganze Zahl, die eine Pixelbreite für das Kombinationsfeld angibt.|
|idCommandList|Erforderlich. Eine ID, die an das aktive Befehlsziel gesendet wird, um die Liste der Elemente abzurufen, die im Kombinationsfeld angezeigt werden sollen. Die ID befindet sich im gleichen GUID-Bereich wie das Steuerelement.|
|priority|Optional. Ein numerischer Wert, der die Priorität angibt.|
|type|Optional. Ein aufgezählter Wert, der den Typ der Schaltfläche angibt.<br /><br /> Wenn nicht angegeben, verwendet Button.<br /><br /> DropDownCombo<br /> Das VSPackage ist für das Ausfüllen des Inhalts für dieses Kombinationsfeld verantwortlich. Der Benutzer kann nichts in das Textfeld dieser Dropdownliste eingeben.<br /><br /> DynamicCombo<br /> Das VSPackage ist für das Ausfüllen des Inhalts dieses Kombinationsfeldes verantwortlich. Der Benutzer kann diese Kombination bearbeiten und auch Elemente darin auswählen.<br /><br /> IndexCombo<br /> Das gleiche wie DynamicCombo, außer dass es den Index des Elements anstelle seines Textes erhöht.<br /><br /> MRUCombo<br /> Gefüllt mit der integrierten Entwicklungsumgebung (IDE) im Auftrag des VSPackage.  Der Benutzer kann in diesem Kombinationsfeld bearbeiten. Die IDE speichert bis zu den letzten 16 Einträge pro Kombinationsfeld.<br /><br /> Wenn der Benutzer etwas im Kombinationsfeld auswählt oder etwas Neues eingibt, benachrichtigt die IDE das entsprechende VSPackage.|
|Bedingung|Optional. Siehe [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Parent|Optional. Das übergeordnete Element der Schaltfläche.|
|CommandFlag|Erforderlich. Siehe [Befehlsflag-Element](../extensibility/command-flag-element.md). Die gültigen CommandFlag-Werte für eine Schaltfläche lauten wie folgt.<br /><br /> - CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> - FilterKeys<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|Zeichenfolgen|Erforderlich. Siehe [Strings-Element](../extensibility/strings-element.md). Das untergeordnete ButtonText-Element muss definiert werden.|
|Anmerkung|Optionaler Kommentar.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Befehlselement](../extensibility/commands-element.md)|Stellt die Auflistung von Befehlen auf der VSPackage-Symbolleiste dar.|

## <a name="example"></a>Beispiel

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
