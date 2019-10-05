---
title: Element-Befehle | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 194768a3b540511996e1d99e6450a7a9b24ebc74
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184290"
---
# <a name="commands-element"></a>Commands-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stellt die Auflistung von Befehlen auf der Symbolleiste des VSPackage. Die Auflistung kann bis zu fünf Unterabschnitte, wie folgt aufweisen: Gruppen, Menüs, Schaltflächen, Combos und Bitmaps.  
  
 Jeder Unterabschnitt untergeordnetes Element, z. B. \<Menü >, wird durch eine eindeutige Befehls-ID, die eine GUID und die numerische ID-Paar ist identifiziert. Die GUID identifiziert den "Befehlssatz" und wird verwendet, um eine Gruppe von logisch verwandte Befehle. Das VSPackage sollten eigene-Befehlssatz zum Vermeiden von Konflikten mit der Befehls-IDs, die von anderen VSPackages definiert sind, definieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|[Menus-Element](../extensibility/menus-element.md)|Definiert die Menüs aus, denen eine VSPackage implementiert.|  
|[Groups-Element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehlsgruppen in einem VSPackage definieren.|  
|[Buttons-Element](../extensibility/buttons-element.md)|Gruppiert Elemente der Schaltfläche.|  
|[Bitmaps-Element](../extensibility/bitmaps-element.md)|Gruppiert Elemente der Bitmap.|  
|[Combos-Element](../extensibility/combos-element.md)|Gruppen-Kombinationsfeld Elemente.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die die Befehle darstellen, die eine VSPackage für der IDE bereitstellt. Mögliche Elemente werden, Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern.|  
  
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
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
