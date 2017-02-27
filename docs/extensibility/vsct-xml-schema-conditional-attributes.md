---
title: "Bedingte VSCT XML-Schema-Attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML-Schemaelemente, bedingten Attribute"
  - "bedingten Attribute (VSCT-XML-Schema)"
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Bedingte VSCT XML-Schema-Attribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bedingte Attribute können auf alle Listen und Elemente angewendet werden. Logische Operatoren und Symbol Erweiterung Ausdrücke ergeben true oder false. Wenn true, ist die zugehörige Liste bzw. das Element in der Ausgabe enthalten.  
  
 Token\-Erweiterungen können andere token Erweiterungen oder Konstanten verglichen werden soll. Die Funktion Defined\(\) wird verwendet, zu testen, ob es sich bei ein bestimmter Namen definiert wurde, auch wenn sie keinen Wert hat.  
  
 Wenn ein Condition\-Attribut auf eine Liste angewendet wird, wird die Bedingung auf alle untergeordneten Elemente in der Liste angewendet. Wenn ein untergeordnetes Element selbst ein Condition\-Attribut enthält, wird die Bedingung mit dem übergeordneten Ausdruck durch eine AND\-Operation kombiniert.  
  
 Die Werte 1, '1' und 'true' werden als True ausgewertet, und 0, '0' und 'false' werden als "false" ausgewertet.  
  
## Operatoren  
 Die folgenden Operatoren können zum Auswerten von bedingten Ausdrücken verwendet werden.  
  
|Operator|Definition|  
|--------------|----------------|  
|\(,\)|Gruppierung|  
|\!|Logisches Nicht|  
|\<, \>, \<\=, \>\=, \=\=, \!\=|Relationale und Gleichheitsoperatoren|  
|und|Boolesch|  
|oder|Boolesch|  
  
## Beispiele  
  
```  
<Menu Condition="Defined(DEBUG)" … </Menu> <Menu Condition="%(SKU_MODE) = 'Demo'" … </Menu> <Menus Condition="Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menus Condition="Defined(DEMO_SKU)"> <Menus Condition="!Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menu … </Menu> </Menus> <Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU)) and !Defined(DEBUG)"> <Menu … </Menu> </Menus>  
```  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)