---
title: Element-Befehle | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab8629fb3ef83277f1366a5141c400b8eeea70e3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341899"
---
# <a name="commands-element"></a>Commands-element
Stellt die Auflistung von Befehlen auf der Symbolleiste des VSPackage. Die Auflistung kann bis zu fünf Unterabschnitte, wie folgt aufweisen: Gruppen, Menüs, Schaltflächen, Combos und Bitmaps.

 Jeder Unterabschnitt untergeordnetes Element, z. B. \<Menü >, wird durch eine eindeutige Befehls-ID, die eine GUID und die numerische ID-Paar ist identifiziert. Die GUID identifiziert den "Befehlssatz" und wird verwendet, um eine Gruppe von logisch verwandte Befehle. Das VSPackage sollten eigene-Befehlssatz zum Vermeiden von Konflikten mit der Befehls-IDs, die von anderen VSPackages definiert sind, definieren.

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

|Attribut|Beschreibung|
|---------------|-----------------|
|package|Eine GUID, die das VSPackage identifiziert, die die Befehle bereitstellt.<br /><br /> Beispielsweise = "guidVsPackage1Pkg".|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Menus-element](../extensibility/menus-element.md)|Definiert die Menüs aus, denen eine VSPackage implementiert.|
|[Groups-element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehlsgruppen in einem VSPackage definieren.|
|[Buttons-element](../extensibility/buttons-element.md)|Gruppiert Elemente der Schaltfläche.|
|[Bitmaps-element](../extensibility/bitmaps-element.md)|Gruppiert Elemente der Bitmap.|
|[Combos-element](../extensibility/combos-element.md)|Gruppen-Kombinationsfeld Elemente.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CommandTable-element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die die Befehle darstellen, die eine VSPackage für der IDE bereitstellt. Mögliche Elemente werden, Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern.|

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt, wie Sie mit einem [Commands-Element](../extensibility/commands-element.md).

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

## <a name="see-also"></a>Siehe auch
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)