---
title: Combos-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: ef48d2d2-0c47-4f93-8cfe-52026b6c463e
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7842bd2e0a6cebc5980781bae1fc89c1401fc08
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958396"
---
# <a name="combos-element"></a>Combos-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gruppen [Combo-Element](../extensibility/combo-element.md) Elemente.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Combos>  
  <Combo>... </Combo>  
  <Combo>... </Combo>  
</Combos>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Combos-Element](../extensibility/combos-element.md)|Gruppen-Kombinationsfeld Elemente.|  
|[Combo-Element](../extensibility/combo-element.md)|Definiert die Befehle, die in einem Kombinationsfeld angezeigt werden.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Commands-Element](../extensibility/commands-element.md)|Stellt die Auflistung von Befehlen auf der Symbolleiste des VSPackage.|  
  
## <a name="example"></a>Beispiel  
  
```  
<Combos>  
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
</Combos>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
