---
title: VSCT-XML-Schema bedingte Attribute | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 975ca2f5fa6f070baf07b26cbfa0d8c3aa3b67d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138355"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Bedingte VSCT-XML-Schema-Attribute
Bedingte Attribute möglicherweise für alle Listen und Elemente angewendet werden. Logische Operatoren und Ausdrücke der Symbol-Erweiterung, die zu "true" oder "false" ausgewertet werden. Bei "true", ist der zugeordneten Liste oder ein Element in der Ausgabe enthalten.  
  
 Token Erweiterungen können für andere token Erweiterungen oder Konstanten getestet werden soll. Die Funktion Defined() Dient zum Testen, ob es sich bei ein bestimmter Namen definiert wurde, auch wenn sie keinen Wert verfügt.  
  
 Wenn ein Condition-Attribut auf eine Liste angewendet wird, wird die Bedingung auf alle untergeordneten Elemente in der Liste angewendet. Wenn ein untergeordnetes Element selbst ein Condition-Attribut enthält, wird die Bedingung mit dem übergeordneten Ausdruck durch eine AND-Operation kombiniert.  
  
 Die Werte 1, "1" und "true" werden als "true" ausgewertet, und 0, "0" und "false" werden als "false" ausgewertet.  
  
## <a name="operators"></a>Operatoren  
 Bedingte Ausdrücke ausgewertet, können die folgenden Operatoren verwendet werden.  
  
|Operator|Definition|  
|--------------|----------------|  
|(,)|Gruppieren|  
|!|Logisches Nicht|  
|\<, >, \<=, >=, ==, !=|Relation und Gleichheit|  
|und|Boolesch|  
|oder|Boolesch|  
  
## <a name="examples"></a>Beispiele  
  
```  
<Menu Condition="Defined(DEBUG)" ...  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" ...  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu ...  
        </Menu>  
    </Menus>  
  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)