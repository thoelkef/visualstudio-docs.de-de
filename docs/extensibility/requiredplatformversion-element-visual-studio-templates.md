---
title: "RequiredPlatformVersion-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# RequiredPlatformVersion-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt die Mindestversion des Betriebssystems an, die vorliegen muss, damit die Projektvorlage ordnungsgemäß funktioniert. Dieses Element wird für Projektvorlagen verwendet, die [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]\-Apps erstellen.  
  
 Der Wert `RequiredPlatformVersion` wird unmittelbar mit der Version des Betriebssystems verglichen. Wenn `RequiredPlatformVersion` höher als die Version des Betriebssystems ist, wird die Vorlage im Dialogfeld **Neues Projekt** nicht angezeigt. Um eine Vorlage für [!INCLUDE[win8](../debugger/includes/win8_md.md)] oder höher anzugeben, legen Sie `RequiredPlatformVersion` auf 6.2.0 fest. Um eine Vorlage für [!INCLUDE[win81](../debugger/includes/win81_md.md)] oder höher anzugeben, legen Sie "RequiredPlatformVersion" auf 6.3.0 fest.  
  
 Vorlagen, die `RequiredPlatformVersion`\=8 angeben, sind mit früheren [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]\-Kundenvorlagen kompatibel.  
  
 VSTemplate  
TemplateData  
…..TargetPlatformName  
RequiredPlatformVersion  
  
## Syntax  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## Attribute und Elemente  
 Keine  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
 Keine  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Gibt die Plattform an, auf die die Projektvorlage abzielt.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
## Hinweise  
 Dieser Text gibt die Mindestversion des Betriebssystems an, die für die Vorlage erforderlich ist.  
  
## Beispiel  
 In diesem Beispiel wird angegeben, dass die Projektvorlage auf [!INCLUDE[win8](../debugger/includes/win8_md.md)] oder höher abzielt.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Siehe auch  
 [TargetPlatformName\-Element \(Visual Studio\-Vorlagen\)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)