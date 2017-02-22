---
title: "Bitmaps-Element | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML-Schemaelemente, Bitmaps"
  - "Bitmaps-Element (VSCT-XML-Schema)"
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Bitmaps-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gruppiert [Bitmapelement](../extensibility/bitmap-element.md)\-Elemente.  
  
## Syntax  
  
```  
<Bitmaps>  
  <Bitmap>... </Bitmap>  
  <Bitmap>... </Bitmap>  
</Bitmaps>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Bitmaps Element](../extensibility/bitmaps-element.md)|Gruppen\-Bitmap\-Elemente.|  
|[Bitmapelement](../extensibility/bitmap-element.md)|Definiert eine Bitmap.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Commands\-Element](../extensibility/commands-element.md)|Stellt die Auflistung von Befehlen auf der Symbolleiste des VSPackage.|  
  
## Beispiel  
  
```  
<Bitmaps> <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/> </Bitmaps>  
```  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)