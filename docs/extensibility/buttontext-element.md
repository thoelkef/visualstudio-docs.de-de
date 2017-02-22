---
title: "ButtonText-Element | Microsoft Docs"
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
  - "ButtonText-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, ButtonText"
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# ButtonText-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Feld ermöglicht die Angabe den angezeigte Text in verschiedenen Menüs. In der Standardeinstellung die `ButtonText` Element wird im Menücontroller angezeigt. Die `ButtonText` Element wird auch die Standardeinstellung, wenn die anderen Felder leer sind. Die `ButtonText` Element darf nicht leer sein, auch wenn die anderen Felder angegeben werden.  
  
## Syntax  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine  
  
### Untergeordnete Elemente  
 Keine  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Zeichenfolgen\-Element](../extensibility/strings-element.md)|Text\-Elemente, wie z. B. Gruppen `ButtonText` und `CommandName`.|  
  
## Textwert  
 Der Textwert, der die `ButtonText` Element enthält den Text, der angezeigt wird, für Menüelemente, Kombinationen und andere Elemente der Benutzeroberfläche \(UI\), die sichtbaren Text enthält.  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)