---
title: "Group-Element | Microsoft Docs"
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
  - "VSCT XML-Schemaelemente, Gruppen"
  - "Groups-Element (VSCT-XML-Schema)"
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Group-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definiert eine Gruppe der VSPackage\-Befehl.  
  
## Syntax  
  
```  
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">  
  <Parent>... </Parent>  
</Group>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|GUID|Erforderlich. Die GUID der GUID\-ID\-Befehls\-ID.|  
|ID|Erforderlich. ID der GUID\-ID\-Befehls\-ID.|  
|priority|Optional. Einen numerischen Wert, der die Priorität angibt.|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Übergeordnetes Element|Optional. Das übergeordnete Element der Schaltfläche.|  
|Anmerkung|Optionaler Kommentar.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Groups\-Element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehl Benutzergruppen ein VSPackage definieren.|  
  
## Beispiel  
  
```  
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/> </Group>  
```  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)