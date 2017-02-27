---
title: "Schaltfl&#228;chen-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schaltflächen-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, Schaltflächen"
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Schaltfl&#228;chen-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gruppen [Schaltfläche](../extensibility/button-element.md) \-Elemente, die einzelnen Befehle darstellen.  
  
## Syntax  
  
```  
<Buttons>  
  <Button>... </Button>  
  <Button>... </Button>  
</Buttons>  
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
|[Buttons Element](../extensibility/buttons-element.md)|Gruppen\-Button\-Elemente.|  
|[Button\-Element](../extensibility/button-element.md)|Definiert einen Befehl, mit dem der Benutzer interagieren kann.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Commands\-Element](../extensibility/commands-element.md)|Stellt die Auflistung von Befehlen auf der Symbolleiste des VSPackage.|  
  
## Beispiel  
  
```  
<Buttons> <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button"> <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/> <Icon guid="guidGenericCmdBmp" id="bmpArrow"/> <Strings> <ButtonText>C# Command Sample</ButtonText> </Strings> </Button> </Buttons>  
```  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)