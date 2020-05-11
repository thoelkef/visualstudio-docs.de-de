---
title: Befehle Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739688"
---
# <a name="commands-element"></a>Commands-Element
Stellt die Auflistung von Befehlen auf der VSPackage-Symbolleiste dar. Die Auflistung kann wie folgt aus bis zu fünf Unterabschnitten bestehen: Menüs, Gruppen, Schaltflächen, Kombinationen und Bitmaps.

 Jedes untergeordnete Unterabschnittselement, \<z. B. Menü>, wird durch eine eindeutige Befehls-ID identifiziert, die ein GUID- und numerisches Bezeichnerpaar ist. Die GUID identifiziert den "Befehlssatz" und wird verwendet, um logisch verwandte Befehle zu gruppieren. Das VSPackage sollte einen eigenen Befehlssatz definieren, um Kollisionen mit Befehls-IDs zu vermeiden, die von anderen VSPackages definiert werden.

## <a name="syntax"></a>Syntax

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|package|Eine GUID, die das VSPackage identifiziert, das die Befehle bereitstellt.<br /><br /> Beispiel: package="guidVsPackage1Pkg".|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Menus-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die ein VSPackage implementiert.|
|[Gruppenelement](../extensibility/groups-element.md)|Enthält Einträge, die die Befehlsgruppen in einem VSPackage definieren.|
|[Buttons-Element](../extensibility/buttons-element.md)|Gruppen-Schaltflächenelemente.|
|[Bitmaps-Element](../extensibility/bitmaps-element.md)|Gruppiert Bitmap-Elemente.|
|[Combos-Element](../extensibility/combos-element.md)|Gruppen Combo-Elemente.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die die Befehle darstellen, die ein VSPackage für die IDE bereitstellt. Mögliche Elemente sind Menüpunkte, Menüs, Symbolleisten und Kombinationsfelder.|

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt, wie ein [Befehlselement](../extensibility/commands-element.md)verwendet wird.

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>Weitere Informationen
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
