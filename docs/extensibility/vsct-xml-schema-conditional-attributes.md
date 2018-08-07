---
title: VSCT-XML-Schema bedingte Attribute | Microsoft-Dokumentation
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
ms.openlocfilehash: b31b99e38eeec2ff1e5e31bc6bdaeed3d3be3d83
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586820"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Bedingte VSCT XML Schema-Attribute
Sie können bedingte Attribute für alle Listen und Elemente anwenden. Logische Operatoren und Ausdrücke der Symbol-Erweiterung, die zu "true" oder "false" ausgewertet werden. Bei "true", ist das zugeordnete Liste oder das Element in der Ausgabe enthalten.  
  
 Sie können die token-Erweiterungen für andere token Erweiterungen oder Konstanten testen. Die Funktion `Defined()` testet, ob es sich bei ein bestimmter Namen definiert wurde, auch wenn sie keinen Wert besitzt.  
  
 Wenn ein Condition-Attribut auf eine Liste angewendet wird, wird die Bedingung auf alle untergeordneten Elemente in der Liste angewendet. Wenn ein untergeordnetes Element selbst ein Condition-Attribut enthält, wird die Bedingung mit dem übergeordneten Ausdruck durch eine AND-Operation kombiniert.  
  
 Die Werte 1, "1" und "true" werden als "true" ausgewertet, und 0, "0" und "false" werden als "false" ausgewertet.  
  
## <a name="operators"></a>Operatoren  
 Verwenden Sie die folgenden Operatoren, um bedingte Ausdrücke auszuwerten.  
  
|Operator|Definition|  
|--------------|----------------|  
|(,)|Gruppieren|  
|!|Logisches Nicht|  
|\<, >, \<=, >=, ==, !=|Relation und Gleichheit|  
|und|Boolesch|  
|oder|Boolesch|  
  
## <a name="examples"></a>Beispiele  
  
```xml  
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
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)