---
title: Bedingte Attribute des vsct-XML-Schemas | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6294ee8027b61840149096561efc91b8a4a3c3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422148"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Bedingte Attribute des VSCT-XML-Schemas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bedingte Attribute können auf alle Listen und Elemente angewendet werden. Logische Operatoren und Symbol Erweiterungs Ausdrücke werden als true oder false ausgewertet. True gibt an, dass die zugeordnete Liste oder das zugehörige Element in der resultierenden Ausgabe enthalten ist.  
  
 Tokenerweiterungen können mit anderen tokenerweiterungen oder Konstanten getestet werden. Die definierte Funktion () wird verwendet, um zu testen, ob ein bestimmter Name definiert wurde, auch wenn kein Wert angegeben ist.  
  
 Wenn ein Condition-Attribut auf eine Liste angewendet wird, wird die Bedingung auf jedes untergeordnete Element in der Liste angewendet. Wenn ein untergeordnetes Element selbst ein Condition-Attribut enthält, wird die Bedingung mit dem übergeordneten Ausdruck durch eine and-Operation kombiniert.  
  
 Die Werte 1, "1" und "true" werden als "true" ausgewertet, und 0, "0" und "false" werden als "false" ausgewertet.  
  
## <a name="operators"></a>Operatoren  
 Die folgenden Operatoren können verwendet werden, um bedingte Ausdrücke auszuwerten.  
  
|Operator|Definition|  
|--------------|----------------|  
|(,)|Gruppierung|  
|!|Logisches Nicht|  
|\<, >, \<=, >=, ==, !=|Relation und Gleichheit|  
|und|Boolean|  
|oder|Boolean|  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
