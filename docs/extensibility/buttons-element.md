---
title: Schaltflächen-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b4b28112abad97dae3c4edcb46b5f93109df4a4e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980309"
---
# <a name="buttons-element"></a>Buttons-element
Gruppen [Schaltfläche](../extensibility/button-element.md) -Elemente, die einzelnen Befehle darstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Buttons>  
  <Button>... </Button>  
  <Button>... </Button>  
</Buttons>  
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
|[Buttons-element](../extensibility/buttons-element.md)|Gruppiert Elemente der Schaltfläche.|  
|[Button-element](../extensibility/button-element.md)|Definiert einen Befehl, mit dem der Benutzer interagieren kann.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Commands-element](../extensibility/commands-element.md)|Stellt die Auflistung von Befehlen auf der Symbolleiste des VSPackage.|  
  
## <a name="example"></a>Beispiel  
  
```  
<Buttons>  
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">  
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>  
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>  
    <Strings>  
      <ButtonText>C# Command Sample</ButtonText>  
    </Strings>  
  </Button>  
</Buttons>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)