---
title: VSCT-XML-Schema bedingte Attribute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 018c78d10af48a946ded543210404f397eee5ca4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522342"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Bedingte Attribute des VSCT-XML-Schemas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [VSCT XML-Schema bedingten Attribute](https://docs.microsoft.com/visualstudio/extensibility/vsct-xml-schema-conditional-attributes).  
  
Bedingte Attribute können auf alle Listen und Elemente angewendet werden. Logische Operatoren und Ausdrücke der Symbol-Erweiterung, die zu "true" oder "false" ausgewertet werden. Bei "true", ist das zugeordnete Liste oder das Element in der Ausgabe enthalten.  
  
 Token-Erweiterungen können mit anderen token Erweiterungen oder Konstanten getestet werden. Die Funktion Defined() Dient zum Überprüfen, ob es sich bei ein bestimmter Namen definiert wurde, auch wenn sie keinen Wert besitzt.  
  
 Wenn ein Condition-Attribut auf eine Liste angewendet wird, wird die Bedingung auf alle untergeordneten Elemente in der Liste angewendet. Wenn ein untergeordnetes Element selbst ein Condition-Attribut enthält, wird die Bedingung mit dem übergeordneten Ausdruck durch eine AND-Operation kombiniert.  
  
 Die Werte 1, "1" und "true" werden als "true" ausgewertet, und 0, "0" und "false" werden als "false" ausgewertet.  
  
## <a name="operators"></a>Operatoren  
 Die folgenden Operatoren können zum Auswerten von bedingten Ausdrücken verwendet werden.  
  
|Operator|Definition|  
|--------------|----------------|  
|(,)|Gruppieren|  
|!|Logisches Nicht|  
|\<, >, \<=, >=, ==, !=|Relation und Gleichheit|  
|und|Boolesch|  
|oder|Boolesch|  
  
## <a name="examples"></a>Beispiele  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

