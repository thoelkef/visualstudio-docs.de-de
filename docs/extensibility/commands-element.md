---
title: Befehle Element | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7c5cce390ad786ad530153e1850850509990b039
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="commands-element"></a>Commands-Element
Stellt die Auflistung von Befehlen auf der Symbolleiste des VSPackage. Die Auflistung kann bis zu fünf Unterabschnitte haben, wie folgt: Gruppen, Menüs, Schaltflächen, Tastenkürzel und Bitmaps.  
  
 Jedes Unterabschnitt untergeordnete Element, z. B. \<Menü >, wird durch eine eindeutige Befehls-ID, die eine GUID und die numerische ID-Paar wird identifiziert. Die GUID den "Befehlssatz" bezeichnet und wird verwendet, um eine Gruppe von logisch verwandter Befehle. Das VSPackage sollten eigene Befehlssatz Konflikte mit der Befehls-IDs zu vermeiden, die von anderen VSPackages definiert sind definieren.  
  
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
|package|Eine GUID, die das VSPackage bestimmt wird, das Befehle bereitstellt.<br /><br /> Beispielsweise packen = "guidVsPackage1Pkg".|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Menus-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die eine VSPackage implementiert.|  
|[Groups-Element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehlsgruppen in einem VSPackage definieren.|  
|[Buttons-Element](../extensibility/buttons-element.md)|Gruppiert die Elemente der Schaltfläche.|  
|[Bitmaps-Element](../extensibility/bitmaps-element.md)|Gruppiert die Elemente mithilfe einer Bitmap.|  
|[Combos-Element](../extensibility/combos-element.md)|Gruppiert Kombinationsfeld Elemente.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die die Befehle darstellen, die eine VSPackage mit der IDE ermöglicht. Mögliche Elemente sind Menüelemente, Menüs, Symbolleisten und Kombinationsfelder.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie eine [Commands-Element](../extensibility/commands-element.md).  
  
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
 [Wie VSPackages Elemente der Benutzeroberfläche hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)